---
name: prisma
description: Prisma conventions for this project. Use when editing schema.prisma, creating migrations, writing the seed script or seed data, or touching PrismaService.
---

# Prisma

## Generated client

The generated client is committed to the repository together with every
schema change, in the same commit as the migration. The build and the
tests then use exactly the client that was reviewed, independent of the
Prisma CLI version installed on the machine; do not add the folder to
`.gitignore` and do not regenerate it in the Dockerfile.

- Generate the client into `src/generated/prisma`.
- Import the client only through the `@dc/db` path alias, never by a
  relative path:

  ```jsonc
  // tsconfig.json
  "paths": { "@dc/db": ["src/generated/prisma/client"] }
  ```

  so moving the generated folder later is a one-line change.
