# Delegated task tracker

Copy this template for work Firstmate hands to a teammate. One task block per owner. If a request is split, use one block per part and one combined report for Sara.

Statuses: `queued`, `in progress`, `blocked`, `verifying`, `done`, `rerouted`, `failed`.

A task is `verifying` once the owner returns a result. It is `done` only after the [quality checks](../docs/quality-checks.md) pass.

## Summary

| ID | Request | Owner | Status | Next check |
| --- | --- | --- | --- | --- |
| T-001 | | | | |

## Task

- **ID:** T-001
- **Request:**
- **Requested by:** Sara
- **Opened:**
- **Owner:**
- **Status:** queued
- **Next check:**
- **Brief:**
  - Outcome:
  - Context:
  - Constraints:
  - Done when:
- **Result:**
- **Verification:** not yet
- **Evidence:**
- **Failure and recovery:**
- **Feedback to keep:**

## Example

The sample below shows a filled block. It is an illustration, not a live task.

### Example summary

| ID | Request | Owner | Status | Next check |
| --- | --- | --- | --- | --- |
| T-014 | Add a Trial note heading and one sentence to the README, then open a pull request | Cursor Cloud Agent | verifying | When the diff has been read |

### Example task

- **ID:** T-014
- **Request:** Add a short "Trial note" heading to the README, with one sentence under it, and open a pull request.
- **Requested by:** Sara
- **Opened:** 2026-10-14
- **Owner:** Cursor Cloud Agent
- **Previous owner:** none
- **Status:** verifying
- **Next check:** As soon as the pull request diff is available to read
- **Brief:**
  - Outcome: The README contains a "Trial note" heading and one sentence under it.
  - Context: The Firstmate docs repository Sara named.
  - Constraints: Do not change any other section.
  - Done when: A pull request is open and the diff contains only that addition.
- **Result:** The agent reported an open pull request. Firstmate has not finished reading the diff.
- **Verification:** not yet
- **Evidence:** Pull request link, pending diff review
- **Failure and recovery:** The first run stopped before opening a pull request. Firstmate said so and retried once. The second run opened the pull request. The owner stayed the Cursor Cloud Agent.
- **Feedback to keep:** For README trials, state "no other section changes" in the brief so the diff is easy to verify.
