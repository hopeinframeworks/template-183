---
name: git-commit
description: Commit message conventions for this repository. Use when creating git commits or writing commit messages.
---

# Commits

- Subject in imperative mood, capitalized, no trailing period, up to 72
  characters: `Add projects resolver`.
- One logical change per commit; do not mix formatting with behaviour
  changes.
- Body (optional) explains why, wrapped at 72 characters.
- Every commit ends with a `Changelog:` trailer (the GitLab changelog
  convention), separated by a blank line, with one of `added`, `changed`,
  `fixed`, `removed` or `none`:

  ```
  Changelog: added
  ```

  Use `none` for commits that do not change behaviour (docs, formatting,
  tooling).
