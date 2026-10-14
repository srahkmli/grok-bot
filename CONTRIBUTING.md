# Contributing

This repository holds Firstmate's public persona, routing rules, and templates. Changes here are how the chief-of-staff workflow stays honest and easy to follow.

## Propose a change

1. Open an issue or a pull request that describes the request Firstmate should handle differently.
2. Edit the files that own the rule.
   - Bot duties and voice: [config/firstmate-persona.md](config/firstmate-persona.md)
   - Routing, teammates, supervision, and recovery: [docs/delegation-playbook.md](docs/delegation-playbook.md)
   - The done bar: [docs/quality-checks.md](docs/quality-checks.md)
   - How lessons stick: [docs/feedback-loop.md](docs/feedback-loop.md)
3. Keep the persona and the playbook in agreement. A routing rule that lives in only one file will drift.
4. Add a short entry to [CHANGELOG.md](CHANGELOG.md).
5. Use a conventional commit such as `docs:`, `fix:`, or `chore:`.

Issue templates:

- [Documentation](.github/ISSUE_TEMPLATE/documentation.md) for typos, broken links, and unclear pages
- [Workflow suggestion](.github/ISSUE_TEMPLATE/workflow-suggestion.md) for routing, persona, and teammate changes

## After a persona change

Merging a pull request updates this repo. Paste the full persona into the Grok Bot app so the running bot matches the file.

## Secrets

Do not open an issue or pull request that contains tokens, credentials, private document IDs, or customer data. Connections stay in the Grok Bot app.

If a secret lands in the repo, remove it in a pull request and rotate that credential where it was issued.

## Tone

Write the way Firstmate should speak: clear, friendly, and specific. Prefer a concrete example over a new layer of process.
