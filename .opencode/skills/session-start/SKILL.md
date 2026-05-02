---
name: session-start
description: Load minimal, fresh, project-relevant vault context at session start.
---

# Session start

Load only the minimum context needed to start work safely. Skip this skill when the task is trivial or the current repository already provides enough context.

## Purpose

Avoid stale or excessive context while preserving useful project continuity.

## Workflow

1. Infer active project from current working directory.

2. Load global preferences only when they are likely to affect the task:
   - `global/preferences/code-style.md`
   - `global/preferences/stack.md`
   - `global/preferences/workflow.md`

3. Load project context only when it is likely to affect the task:
   - `projects/<project>/_project.md`
   - `projects/<project>/kanban.md`
   - `projects/<project>/versions.md`

4. Optionally load at most one of:
   - latest scratch note
   - open proposed ADRs
   - active task note

5. Check freshness:
   - Mark every loaded item with source path and date when available.
   - Treat scratch notes older than 14 days as possibly stale.
   - Treat decisions and ADRs as durable unless superseded.
   - Prefer current repository docs over vault notes when they conflict.

6. Return a short status summary.

## Limits

- Read-only.
- Never edit during session start.
- Skip missing files without error.
- Do not load more than 3 files unless the user asks.
- Do not load unrelated project history.
- Do not treat memory as truth without current repo evidence.

## Required output

## Session Context
- Project:
- Loaded files:
- Version/status:
- In-progress work:
- Suggested next action:
