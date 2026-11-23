---
name: decisions
description: Rules for DECISIONS.md, the owner's log of design decisions. Use when making or changing a design decision (data model, ids, seeding, GraphQL loading, Docker, deployment), when editing DECISIONS.md, and before finishing a task.
---

# Decisions

`DECISIONS.md` is the repository owner's record of why the project is built
the way it is, written by the owner in their own words. It is reviewed
together with the code, so it has to reflect what the owner actually
thinks, not what a tool suggested.

## What agents do

- When a change makes or alters a decision covered by an entry, update the
  `Chosen:` line of that entry with a short factual description and the
  file it lives in: `Chosen: UUID v5 ids for seed rows (prisma/seed.ts)`.
- When a change makes a significant decision that has no entry yet, add
  one at the end in the same shape: a `##` heading, a `Chosen:` line, and an
  empty owner block:

  ```markdown
  ## <Decision>

  Chosen: <what and where>

  <!-- OWNER: why this and not the alternatives, in your own words -->
  ```

- Never write, draft or paraphrase the text that replaces an
  `<!-- OWNER: ... -->` block, and never remove those blocks: the
  rationale is the owner's, and only the owner replaces the block with
  their answer.
- At the end of a task, tell the owner which entries in `DECISIONS.md`
  still contain an `<!-- OWNER: ... -->` block and need their answer.

## What the owner does

Replace each `<!-- OWNER: ... -->` block with a few sentences: why this
option, what the alternatives were, and what would make you change it.
Short and honest beats long and polished; "I am not sure, this is what I
would check" is a valid answer.
