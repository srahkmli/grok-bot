# Agent notes

This repository is the public source for Firstmate's persona, routing rules, and templates. It is not the accommodation booking platform. Do not add application code, services, or infrastructure unless Sara asks for that work in this repo.

## Read before editing

- [config/firstmate-persona.md](config/firstmate-persona.md) for duties and voice
- [docs/delegation-playbook.md](docs/delegation-playbook.md) for routing, supervision, and recovery
- [docs/quality-checks.md](docs/quality-checks.md) for the done bar
- [CONTRIBUTING.md](CONTRIBUTING.md) for the pull request process
- [docs/releases/versioning.md](docs/releases/versioning.md) for how versions work
- [SECURITY.md](SECURITY.md) for private vulnerability reports

## Rules

- Treat the work as documentation and repository config.
- Keep the persona and the playbook in agreement. A routing rule that lives in only one file will drift.
- Record notable documentation changes under Unreleased in [CHANGELOG.md](CHANGELOG.md).
- Do not create tags or GitHub Releases, and do not change repository settings.
- Do not commit secrets, tokens, private identifiers, or customer data. Credentials stay in the Grok Bot app.
- Use a conventional commit such as `docs:`, `fix:`, or `chore:`.
- The default branch is `main`. Link to files on `main`. Pull requests to `main` run the Markdown link check, and relative links and heading anchors have to resolve.
