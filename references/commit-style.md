# Commit And PR Style

Use concise, reviewable titles that describe scope clearly.

## Commit Prefixes

Preferred prefixes:

- `feat(...)`
- `fix(...)`
- `test(...)`
- `docs(...)`
- `chore(...)`
- `build(...)`
- `release(...)`

Use these prefixes only when they match the actual scope.

## Commit Splitting Rules

- Keep implementation and tests together when they form one coherent behavior change.
- Keep release-facing cleanup separate from feature implementation.
- Do not hide behavior changes inside `chore(...)` commits.
- Do not mix unrelated cleanup into review-response commits.

## PR Title Style

Prefer short titles that match the repository's existing style.

Good patterns:

- `feat(io): add json.gz persistence support`
- `test(io): cover compressed persistence round-trips`
- `docs(public-api): clarify provider configuration semantics`
- `chore(release): prepare 0.0.1 metadata and examples`

## PR Body Defaults

When useful, summarize:

- scope
- tests run
- open questions or known follow-up items

Keep PR titles concise. Put detail in the PR body, not the title.
