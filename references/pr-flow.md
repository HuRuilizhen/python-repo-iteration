# PR Flow

## Default Iteration Structure

Use this structure for post-first-release Python repositories unless the user requests a different process.

### 1. Feature PR

Scope:

- implementation
- tests
- behavior changes
- internal refactors required for the feature

Recommended branch form:

- `feat/<version>-<topic>`
- `fix/<version>-<topic>`

Recommended commit style:

- `feat(...)`
- `fix(...)`
- `test(...)`
- `refactor(...)` only when truly needed

### 2. Release-Prep PR

Scope:

- public API docs
- README updates
- example scripts
- metadata updates
- packaging and release-facing cleanup

Recommended branch form:

- `release/<version>-prep`

Recommended commit style:

- `docs(...)`
- `chore(release): ...`
- `build(...)`

## Ready-For-Review Signal

Treat PR creation as the point where the branch is ready for review.

That means:

- code and tests for that PR scope are already in place
- local checks for that scope have already been run
- the author is now expecting review comments, not still doing broad unfinished work

## Review Response Rules

- Keep addressing comments on the same PR branch unless a re-split is clearly better.
- Prefer one commit per coherent review-response batch when that keeps history understandable.
- If a reviewer finds a contract issue, fix the code and the tests together.
- If a reviewer finds a docs drift issue, fix docs in the release-prep PR unless the docs are required to explain the feature PR itself.

## Anti-Patterns

Avoid these patterns:

- opening one PR that mixes feature work, examples, README updates, metadata, and release cleanup without a good reason
- continuing large unrelated development after a PR is already under review
- pushing broad cleanup changes while claiming to address a narrow review comment
- tagging from a feature branch that has not been merged to `main`
