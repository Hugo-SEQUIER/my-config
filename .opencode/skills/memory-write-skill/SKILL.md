---
name: memory-write-skill
description: Save a durable learning, decision, or reusable pattern in vault memory with evidence.
---

# Memory write: $ARGUMENTS

Write a durable memory note in `$CLAUDE_VAULT`.

## Arguments

`/memory-write <learning|decision|knowledge> <title>`

## Target paths

- `learning` -> `global/learnings/YYYY-MM-DD-<slug>.md`
- `decision` -> `global/decisions/YYYY-MM-DD-<slug>.md`
- `knowledge` -> `global/knowledge/patterns/YYYY-MM-DD-<slug>.md`

## Use only when

- The user explicitly asks to save memory, or
- The user confirms that a learning/decision should be durable.

Do not save temporary task notes, unverified guesses, stale observations, or implementation details that belong in project docs.

## Rules

- One focused note per file.
- Prefer project-local docs for project-specific architecture decisions.
- Include evidence/source paths when available.
- Include scope and revalidation guidance for knowledge that may become stale.
- Use `[[wikilinks]]` only when they are useful.
- Confirm saved path and title after write.

## Required note format

# <Title>

## Type

learning | decision | knowledge

## Date

YYYY-MM-DD

## Scope

Where this applies.

## Context

Why this note exists.

## Evidence

- Source paths, commands, docs, or user-confirmed facts.

## Takeaway

The durable learning, decision, or pattern.

## Consequences / Gotchas

What future agents should watch for.

## Revalidation

When or why to check this again.

## Related

- Optional wikilinks.
