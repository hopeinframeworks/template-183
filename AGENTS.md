# Agent guide

Project conventions live in `.claude/skills/*/SKILL.md`, one file per area
(architecture, Prisma, NestJS, GraphQL, Docker, Helm, testing, commits,
decisions). Before changing code in an area, read the matching skill and
follow it, so the codebase stays consistent no matter who or what wrote a
given part.

- TypeScript strict mode, no `any`.
- Code, comments and docs in English.
- `npm run lint` and `npm test` must pass before a commit.
- Design decisions are logged in `DECISIONS.md` following the `decisions`
  skill; the rationale in it belongs to the owner.
