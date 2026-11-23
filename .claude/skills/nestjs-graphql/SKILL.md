---
name: nestjs-graphql
description: GraphQL conventions for this project (NestJS, Apollo, code-first). Use when configuring GraphQLModule, writing resolvers, object types, inputs, or anything that changes the GraphQL schema.
---

# GraphQL

## Setup

`numberScalarMode: 'integer'` keeps every TypeScript `number` an `Int` in the schema, so the generated SDL does not drift between `Int` and `Float` depending on who wrote the field.

## Loading nested data

The card serves exactly one profile with a few dozen related rows, and the
frontend renders the whole card on one page, so every client query asks for
the profile together with all of its relations. Keep the read path simple:

- `ProfileService.getProfile()` loads the whole aggregate in one Prisma call,
  `findFirst` with `include` for `skills`, `experience` and `projects`
  (ordered), and the `profile` query returns that object as is.
- Do not add `@ResolveField` resolvers or DataLoader for these relations.
  With a single profile they only add a database round trip per field and a
  second code path to test, and no client asks for a profile without its
  relations.
- Keep it this way even when it looks like over-fetching: for a single
  business card, per-field resolvers are more machinery than the data
  justifies.
