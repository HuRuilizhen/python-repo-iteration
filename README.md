# python-repo-iteration

`python-repo-iteration` is a reusable Codex skill for disciplined iteration in
Python repositories.

It is designed for repositories that want a consistent workflow for:

- release planning
- branch strategy
- commit and PR splitting
- review-driven follow-up
- release preparation
- final build, tag, and publish steps

## Install

Clone the repository directly into your Codex skills directory:

```bash
git clone https://github.com/HuRuilizhen/python-repo-iteration ~/.codex/skills/python-repo-iteration
```

If the skill is already present locally and you want to update it:

```bash
git -C ~/.codex/skills/python-repo-iteration pull
```

## What This Skill Covers

The skill is intended for Python repository iteration workflow, not for Python
coding style itself.

It helps Codex:

- decide when direct iteration on `main` is acceptable in very early-stage work
- switch to branch-and-PR workflow after the first formal release
- split work into feature PRs and release-prep PRs
- propose branch names, commit groupings, and PR structure
- respond to review comments without losing scope discipline
- run final release checks before tagging or publishing

## Included Files

- `SKILL.md`: main workflow guidance
- `agents/openai.yaml`: UI-facing metadata
- `references/pr-flow.md`: branch and PR structure guidance
- `references/commit-style.md`: commit and PR title style guidance
- `references/release-checklist.md`: final release checklist

## Intended Usage

Use this skill when starting or running a versioned iteration in a Python
repository.

Typical examples:

- planning `0.0.1`, `0.1.0`, or another release iteration
- deciding how to split work into branches and PRs
- moving from review comments to merge-ready state
- preparing the final release branch and package publication steps

## Workflow Philosophy

This skill assumes two operating modes:

1. Early-stage exception
   - before the first real release, direct iteration on `main` can be acceptable
   - this is intended for fast initial convergence
2. Post-first-release workflow
   - avoid direct work on `main` by default
   - prefer feature branches, review-ready PRs, and release-prep follow-up

## Publishing

This directory is structured so it can be used directly from `~/.codex/skills`
or copied into a standalone GitHub repository for sharing.
