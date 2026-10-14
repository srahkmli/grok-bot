# Contributing

This repository holds Firstmate's public persona, routing rules, and templates. Changes here are how the chief-of-staff workflow stays honest and easy to follow.

People who contribute follow the [code of conduct](CODE_OF_CONDUCT.md). Versions are documentation snapshots, described in [docs/releases/versioning.md](docs/releases/versioning.md).

## Branches

- Start from `main`. That is the default branch.
- Use a short branch name that says what the change does.
- Keep one change on a branch. A routing correction and an unrelated rewrite belong in separate pull requests.

## Propose a change

1. Open an issue or a pull request that describes the request Firstmate should handle differently.
2. Edit the files that own the rule.
   - Bot duties and voice: [config/firstmate-persona.md](config/firstmate-persona.md)
   - Routing, teammates, supervision, and recovery: [docs/delegation-playbook.md](docs/delegation-playbook.md)
   - The done bar: [docs/quality-checks.md](docs/quality-checks.md)
   - How lessons stick: [docs/feedback-loop.md](docs/feedback-loop.md)
3. Keep the persona and the playbook in agreement. A routing rule that lives in only one file will drift.
4. Add a short entry under Unreleased in [CHANGELOG.md](CHANGELOG.md).
5. Use a conventional commit such as `docs:`, `fix:`, or `chore:`.

Issue templates:

- [Documentation](.github/ISSUE_TEMPLATE/documentation.md) for typos, broken links, and unclear pages
- [Workflow suggestion](.github/ISSUE_TEMPLATE/workflow-suggestion.md) for routing, persona, and teammate changes

## Pull requests

1. Open the pull request against `main`.
2. Fill in the pull request template, including the testing and risk checklist.
3. Describe the request Firstmate should handle differently, or the page you corrected.
4. Wait for the Markdown link check to pass. A failing check means a link or a heading anchor in the diff does not resolve.

Merging updates this repo. It does not by itself change repository settings, tags, or releases.

## Link check

Pull requests to `main` run [Markdown links](.github/workflows/markdown-links.yml). The check does two things:

- It fails if a Markdown file links at a `master` branch. Link to `main`.
- It requests every Markdown link, including heading anchors on files in this repo.

Run through the relative links you added before you ask for review. A heading anchor has to match the heading GitHub will generate.

## After a persona change

Merging a pull request updates this repo. Paste the full persona into the Grok Bot app so the running bot matches the file.

## Secrets

Do not open an issue or pull request that contains tokens, credentials, private document IDs, or customer data. Connections stay in the Grok Bot app.

Report a vulnerability through the [security policy](SECURITY.md). If a secret lands in the repo, remove it in a pull request and rotate that credential where it was issued.

## Tone

Write the way Firstmate should speak: clear, friendly, and specific. Prefer a concrete example over a new layer of process.
