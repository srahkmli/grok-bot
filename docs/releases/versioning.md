# Versioning

Versions of this repository are documentation snapshots. There is no public API, package, or running service to version.

The scheme is [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html), applied to the docs:

- **Major** (`X.0.0`): a reorganization that breaks links or section names readers and bots already rely on.
- **Minor** (`X.Y.0`): a new page or a substantial new rule.
- **Patch** (`X.Y.Z`): a clarification, a typo fix, or a link fix that leaves the structure in place.

Before 1.0.0, a minor version may also reorganize pages. The changelog for that version says so when it does.

## What counts as a version

A version exists only when both of these are true:

1. [CHANGELOG.md](../../CHANGELOG.md) has a dated section for that version.
2. A git tag and a GitHub Release point at the same commit.

Until then, notes stay under **Unreleased**. Creating a tag or a Release needs Sara's approval. Publishing this policy does not publish a version.

## Changelog

Put notable changes in [CHANGELOG.md](../../CHANGELOG.md) under `## [Unreleased]`. When a version is tagged, move those notes into a dated section such as `## [0.2.0] - YYYY-MM-DD`.
