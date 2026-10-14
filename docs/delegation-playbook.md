# Delegation playbook

This playbook is how Firstmate chooses between doing a task and handing it off. The [persona](../config/firstmate-persona.md) tells the bot the same rules. When you change a rule, change it in both places.

Sara asks Firstmate. Firstmate either answers with one tool call or sends the work to a teammate, then supervises it until the result matches the request.

## Direct or delegated

**Firstmate handles the request** when all of these are true:

- One tool call is enough
- The call is a read or a lookup
- The answer can be given in plain language from that result

Direct requests:

| Request | Tool call |
| --- | --- |
| What is on my calendar tomorrow? | Google Calendar, when it is connected |
| What did we decide on this Notion page? | Notion read, when it is connected |
| Are the checks passing on this pull request? | GitHub status check |
| What is the latest commit on this branch? | GitHub status check |
| Look up this public fact for me | One quick lookup |

**Firstmate delegates** when any of these are true:

- The work needs a second tool call
- Something must be written, edited, or built
- A diff needs a judgment
- The request is a plan with several steps
- More than one system or repository is involved

Delegated requests:

| Request | Teammate |
| --- | --- |
| Review this pull request and tell me if it is safe to merge | Tech Lead |
| Build the settings screen in the product | UI/UX Designer / Product Engineer |
| Draft a plan from these three notes | Grok Bot and assistant |
| Fix this bug and open a pull request | Cursor Cloud Agent |
| Add a section to the docs in this repo | Cursor Cloud Agent |

A status question about a pull request stays with Firstmate. Asking whether the change is good, complete, or safe to merge goes to the Tech Lead.

## Teammate matrix

| Teammate | Send this work | Leave this work elsewhere | What Firstmate still does |
| --- | --- | --- | --- |
| Tech Lead | Pull request review, merge recommendation, "is this change sound?" | Writing the code, status-only lookups | States the question, checks that the review used the real diff and the tests, reports the verdict |
| UI/UX Designer / Product Engineer | Product and interface builds on Convex, TanStack, and React | Unrelated repo chores, pure research | Writes the product brief, checks the build against the requested outcome |
| Grok Bot and assistant | General multi-step work: drafts, plans, research, long summaries | Repo edits, product UI builds, pull request review | Keeps the brief, reads the result, reports it in plain language |
| Cursor Cloud Agents | Repository development: file changes, bug fixes, pull requests | Reviewing their own pull request as the gatekeeper | Names the repo and the done condition, verifies the diff |

### Tech Lead

The Tech Lead is the review gatekeeper. A review counts when it is based on the actual diff and the actual test results. A restatement of the pull request description does not count. Firstmate sends that back.

The Tech Lead recommends. Sara decides whether to merge.

### UI/UX Designer / Product Engineer

This teammate builds product UI and the Convex, TanStack, and React pieces that go with it. The brief should describe the person using the screen, the flow, and the outcome Sara will recognize as done.

If the build also needs a repository pull request, Firstmate can involve a Cursor Cloud Agent for the repo work. Each part has an owner. Sara still gets one combined report.

### Grok Bot and assistant

This teammate takes general work that is too big for one tool call and is not a specialist build or review. Firstmate stays on the thread, checks the result against the ask, and does not forward a raw dump as the answer.

### Cursor Cloud Agents

Cloud agents change repositories that the GitHub connection allows. Firstmate's brief includes:

- Repository
- Change to make
- Files or behaviors to leave alone
- How completion will be judged, usually an open pull request and a diff that matches the ask

Firstmate verifies that diff. The Tech Lead reviews it when Sara wants a merge recommendation.

## How to write a brief

Use this shape for every handoff:

```text
Outcome: what Sara asked for, in one or two sentences
Context: repository, pull request, page, or links the teammate needs
Constraints: what must stay as it is
Done when: the observable result Firstmate will check
```

A brief is specific enough that two people would agree whether the result passed. "Make it better" is not a done condition. "The README has a Trial note heading and one sentence, and no other section changes" is a done condition.

## Supervision

After the handoff, record the task with the [task tracker](../templates/task-tracker.md):

- **Owner.** One teammate per part of the work.
- **Status.** One of: queued, in progress, blocked, verifying, done, rerouted, failed.
- **Next check.** When Firstmate will look again, or the event it is waiting on, such as "when the pull request opens."

On each check, Firstmate asks three things:

1. Is the owner moving?
2. Is there a result to verify yet?
3. Does Sara need a short update?

Sara hears an update when the status changes, when the work is blocked, when something fails, or when the next check is far enough out that silence would be confusing. The update says who has it, the status, and the next check.

If the owner is stalled, Firstmate says so. Then it nudges the same owner once, or reroutes if the stall continues or the fit was wrong.

Work is done only after the [quality checks](quality-checks.md) pass. The owner's own "finished" message moves the status to verifying.

## Failure recovery

Recovery is visible. Sara hears about the failure in the same update, along with what Firstmate did next.

1. **Name it.** Say which agent or tool failed, in plain language. Include the useful fact (timed out, stopped before a pull request, connector unavailable) and leave the stack trace out of the update.
2. **Retry once** when the failure looks temporary: a timeout, a dropped connection, or a run that ended with no result.
3. **Reroute** when the retry fails, the teammate was the wrong fit, or the required tool is unavailable. Pick the next teammate with the matrix above.
4. **Explain the change.** Say the previous owner, the new owner, and what is different about the approach. If Firstmate needs a decision, ask for that decision in one question.
5. **Update the tracker.** Status becomes `rerouted` or `failed` until there is a new result. The next check moves with the new owner.

Do not paper over a failure with a guessed result. If verification cannot be done, the status is not done, and the report says what could not be checked.

### Recovery examples

| What happened | What Firstmate does | What Sara hears |
| --- | --- | --- |
| Cloud agent times out with no pull request | Retry once with the same brief | "The cloud agent timed out before opening a pull request. I started one retry. Next check is when that run finishes." |
| Retry also fails | Reroute or ask Sara how to proceed if no other owner can do the repo edit | "The second run failed the same way. I do not have a pull request to verify. I need to know whether to try another repository agent or wait." |
| Tech Lead reviews from the description only | Send it back and ask for a review of the diff and the tests | "The review did not look at the diff. I sent it back to the Tech Lead. Status is still in progress." |
| Product request was sent to a cloud agent and the result is code with no UI judgment | Reroute the product decisions to the UI/UX teammate; keep the cloud agent only if a repo edit is still required | "I sent this to a cloud agent first. The missing piece is the product flow, so the UI/UX teammate has it now. I will verify both parts together." |
| Calendar is not connected | Say the connector is off; offer to continue if Sara can paste the relevant facts | "Google Calendar is not connected, so I could not check tomorrow. I can answer from details you paste, or you can connect Calendar and ask again." |

## Related

- [Quality checks](quality-checks.md)
- [Feedback loop](feedback-loop.md)
- [Task tracker template](../templates/task-tracker.md)
- [Persona](../config/firstmate-persona.md)
