# Quality checks

Firstmate runs this checklist before telling Sara a delegated task is done. The owner's claim that the work is finished moves the task to **verifying**. It becomes **done** only after the checks pass.

Evidence means something Firstmate inspected: the diff, the test output, the page, or the link that was actually opened. A paraphrase of someone else's summary is not evidence.

## Before delegating

- [ ] The request is quoted or restated in one sentence Sara would recognize
- [ ] The work is larger than one tool call, so delegation is the right path
- [ ] One teammate is named, and the [playbook](delegation-playbook.md) agrees with that choice
- [ ] The brief has an outcome, context, constraints, and a done condition
- [ ] The tracker has an owner, a status, and a next check

## Before a progress update

- [ ] The update says who owns the work
- [ ] The status matches the tracker
- [ ] The next check is included
- [ ] Any failure is named in this same update
- [ ] The update is plain language, short enough to read once

## Before calling it done

- [ ] The original request is restated next to the result
- [ ] Every asked-for outcome is present
- [ ] Extra changes are listed, or the report says there were none
- [ ] Evidence was inspected, and the report points to it
- [ ] Open questions and follow-ups are listed, or the report says there are none
- [ ] The tracker status is done only after this list passes
- [ ] Sara could forward the answer without reading an agent transcript

If a box fails, send the work back with the missing piece. Tell Sara it went back and what you asked for. Leave the status at in progress or verifying.

## Tech Lead reviews

Use this when the teammate is the Tech Lead.

- [ ] The review discusses the real diff, not only the pull request description
- [ ] Tests are mentioned with what was run and what happened, or the review says tests could not be run and why
- [ ] Findings are concrete: file, behavior, or missing case
- [ ] The verdict answers the question Sara asked, such as whether the change looks safe to merge
- [ ] The report separates the recommendation from Sara's merge decision

A review that cannot point at the diff fails this check. Firstmate sends it back.

## Cursor Cloud Agent changes

Use this when a cloud agent changed a repository.

- [ ] A pull request or other requested outcome exists
- [ ] The diff was opened and compared with the brief
- [ ] Requested edits are in the diff
- [ ] Files the brief said to leave alone are unchanged
- [ ] The report includes the link Firstmate actually used

If the agent reports success and there is no diff to read, the task is not done.

## Product builds

Use this when the UI/UX Designer / Product Engineer did the work.

- [ ] The result matches the user-facing outcome in the brief
- [ ] The screens or flows Sara named are covered
- [ ] The build stays on the stack in the brief: Convex, TanStack, and React, unless Sara asked for something else
- [ ] Visible gaps are listed as follow-ups
- [ ] If a pull request was part of the work, the cloud-agent checks above pass too

## General delegated work

Use this for the Grok Bot and assistant, and for any other multi-step task.

- [ ] The result answers the question that was asked
- [ ] Sources or inputs the teammate used are identifiable
- [ ] Claims Firstmate could not check are labeled as unverified
- [ ] The answer is rewritten in Firstmate's plain-language report

## When a check fails

1. Tell the owner exactly which check failed.
2. Tell Sara, in one short update, that the result is not accepted yet and what was sent back.
3. Set the next check to the owner's reply.
4. Run the checklist again on the new result.

Repeated misses of the same check are a signal for the [feedback loop](feedback-loop.md). Add the miss as an example in this file and, if it changes routing or tone, in the [persona](../config/firstmate-persona.md) and the [playbook](delegation-playbook.md).
