# Release Checklist

Use this checklist before tagging or publishing a Python package release.

## Repository State

- working tree is clean, or every remaining change is intentional and understood
- target release commit is on `main`
- release-prep PR work is merged

## Quality Checks

Run the repository's actual configured checks. Typical examples:

- `ruff check . --fix`
- `pyright`
- `pytest`

## Packaging Checks

Typical release checks:

- remove old artifacts if necessary
- `python -m build`
- `python -m twine check dist/*`

## Release Metadata

Confirm that release-facing information is aligned:

- package version
- README
- examples
- metadata such as classifiers, URLs, and license
- public API docs when the release changes the public contract

## Workflow Check

Before choosing a publish path:

- inspect `.github/workflows` for release or publish automation
- if a workflow exists, inspect whether it is triggered by tags, releases, or another explicit release event
- if that workflow already performs package publication, prefer using the repository's automation rather than uploading locally

## Tag And Publish Order

Recommended order when the repository publishes through workflow automation:

1. merge the release-ready state to `main`
2. run final checks if needed
3. create the annotated tag
4. push `main`
5. push the tag
6. let the configured workflow publish the package

Recommended order when the repository does not have automated publication:

1. merge the release-ready state to `main`
2. run final checks if needed
3. create the annotated tag
4. push `main`
5. push the tag
6. upload artifacts to the package index locally

## Post-Release

After publishing:

- verify the package page appears as expected
- verify the pushed tag exists remotely
- record any follow-up fixes in the next release plan rather than patching silently
