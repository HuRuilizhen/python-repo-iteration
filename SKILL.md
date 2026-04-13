---
name: python-repo-iteration
description: Run disciplined versioned iteration in Python repositories, including release planning, branch strategy, commit and PR splitting, review-driven follow-up, release preparation, and final tag/build/upload workflow. Use when a user wants to start a new version iteration, define or enforce a Python repo workflow, split work into feature and release-prep PRs, respond to review comments, or drive a Python package from development through release.
---

# Python Repo Iteration

Read [references/pr-flow.md](references/pr-flow.md) when starting a new iteration.
Read [references/commit-style.md](references/commit-style.md) when proposing commit plans, branch naming, or PR titles.
Read [references/release-checklist.md](references/release-checklist.md) before tagging or publishing.

## Scope

Use this skill for Python repository iteration and release workflow management.

Typical triggers:

- the user wants to start a new version iteration such as `0.0.1` or `0.1.0`
- the user wants branch, commit, and PR structure defined before coding
- the user wants feature work and release-prep work split into separate PRs
- the user wants review comments addressed on an in-flight PR
- the user wants final release checks, tagging, or package upload

This skill is about workflow discipline, not Python coding style.

## Default Workflow

1. Confirm the iteration scope from the current release plan or agreed task list.
2. Decide whether the repository is in early-stage mode or post-first-release mode.
3. In post-first-release mode, avoid direct work on `main` by default.
4. Split work into at least two PR tracks when appropriate:
   - feature PR: implementation and tests
   - release-prep PR: docs, examples, metadata, release-facing cleanup
5. Use small, reviewable commits with conventional prefixes such as `feat(...)`, `fix(...)`, `test(...)`, `docs(...)`, `chore(...)`, `build(...)`, or `release(...)`.
6. Treat an opened PR as a ready-for-review checkpoint.
7. After review comments arrive, address them on the same branch unless there is a strong reason to re-split work.
8. Before release, run the full repository checks and packaging checks.
9. Tag and publish only after the branch is merged and the release state is clean.

## Early-Stage Exception

Before the first real release, direct iteration on `main` can be acceptable when all of the following are true:

- the repository is still being shaped rapidly
- there is effectively one active maintainer driving the initial release
- the goal is to get to the first usable version quickly

Even in that mode:

- keep commits intentional and scoped
- keep tests and checks running
- still separate distinct concerns into distinct commits when possible

After the first formal release, switch to branch-and-PR workflow by default.

## Branching Rules

- Default to `feat/<version>-<topic>` for implementation branches.
- Default to `fix/<version>-<topic>` for bug-fix branches.
- Default to `release/<version>-prep` for release-preparation branches.
- Cut release-prep branches from the latest merged `main`, not from an old feature branch.
- Do not mix broad implementation work into release-prep branches.

## PR Splitting Rules

Prefer at least two PRs for each normal iteration after the first release:

- feature PR:
  - code changes
  - tests
  - behavior changes
- release-prep PR:
  - public API docs
  - README updates
  - examples
  - metadata
  - packaging cleanup
  - release-facing polish

Do not force exactly two PRs if the work naturally needs more than two, but do keep release-prep work distinct from feature implementation whenever possible.

## Review Handling

When a PR is open:

- assume the branch is in review-ready state
- expect review comments to drive the next edits
- keep fixes tightly scoped to the review feedback
- rerun the relevant checks after each meaningful review-response change
- avoid unrelated cleanup while addressing comments unless the reviewer requested it

## Release Planning

When the user asks for a new iteration:

1. identify the current released version and the target next version
2. gather the agreed release-scope items
3. separate implementation work from release-prep work
4. propose branch names and commit groupings before coding when useful
5. use future-plan documents as source material, then narrow them into a specific release plan

## Release Behavior

Before release:

- ensure the working tree is clean or intentionally understood
- inspect `.github/workflows` for release or publish automation
- if a release workflow exists, inspect its trigger conditions before deciding on local release steps
- run repository checks
- build the package artifacts
- run package validation checks
- confirm docs/examples/metadata match the release state
- tag only after the intended release commit is on the main branch

If the repository already publishes through CI or platform automation, treat tagging and pushing as the local release endpoint and let the configured workflow perform the actual upload.

Only perform a local package-index upload when the repository does not already have a release workflow for that responsibility, or when the user explicitly asks for a manual upload path.

## Practical Defaults

- Keep feature commits focused on behavior and tests.
- Keep release-prep commits focused on docs, metadata, examples, and packaging.
- Prefer deterministic release commands and explicit checks over ad hoc manual steps.
- Prefer documenting exceptions and temporary scope boundaries in release plans rather than letting them stay implicit.

## Output Expectations

When using this skill, provide:

- a proposed branch plan when starting a release iteration
- a commit plan when the work is large enough to benefit from one
- a clear statement of which PR track the current work belongs to
- a concise release-check summary before tagging or publishing
