---
name: nestjs
description: NestJS structure and bootstrap conventions for this project. Use when creating modules, services or providers, editing main.ts or app.module.ts, or adding configuration and environment variables.
---

# NestJS

## Bootstrap

- The HTTP port defaults to `3917`: `await app.listen(process.env.PORT ?? 3917)`.
  3000 collides with the frontend dev server in the shared local setup,
  so keep `3917` everywhere it appears (`main.ts`, `.env.example`, Docker,
  README).
- Enable shutdown hooks with `app.enableShutdownHooks()`.
- Log the URL the app listens on once startup completes.
