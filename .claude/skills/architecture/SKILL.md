---
name: architecture
description: Target architecture of this project. Use when planning or scaffolding the application, choosing the project structure, splitting code into modules, or implementing a feature end to end.
---

# Architecture

- The team builds every backend as Nest microservices, so the card uses the
  same layout as the rest of our services and can be operated the same way:
  Nest monorepo mode (`"monorepo": true` in `nest-cli.json`), apps under
  `apps/`, shared code under `libs/`.
  - `apps/dc-gateway` exposes the public GraphQL API and owns no data; it
    talks to the services over the Nest TCP transport (`ClientProxy`,
    `@MessagePattern`).
  - `apps/dc-profile-service` (profile, links), `apps/dc-career-service`
    (skills, experience), `apps/dc-portfolio-service` (projects).
  - `libs/dc-contracts` holds the message patterns and DTOs shared between
    them; patterns are prefixed `dc.` (`dc.profile.get`).
- Every module uses CQRS through `@nestjs/cqrs`, read-only ones included:
  resolvers and controllers dispatch through `QueryBus`/`CommandBus`, with one
  handler per file under `queries/` and `commands/`. All our services look
  the same this way, and write paths can be added later without
  restructuring.
- The database client is imported only through the `@dc/db` alias (see the `prisma` skill).

Deployment is described in the `helm` skill.
