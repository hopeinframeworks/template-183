---
name: testing
description: Testing conventions for this project (Jest). Use when writing or changing unit or e2e tests, spec files, mocks, or test configuration.
---

# Testing

- Specs live only in the `tests/` directory, mirroring the source tree
  (`tests/profile/profile.service.spec.ts`), never next to the code: one
  folder shows at a glance which modules are covered.
- Point Jest at it: `"rootDir": "."` and `"roots": ["<rootDir>/tests"]` in
  the `jest` section of `package.json`.
