---
name: plan-review-skill
description: Build an evidence-first implementation plan, stress-test it, and gate risky work before edits.
---

# Plan review: $ARGUMENTS

Create a plan before implementation when planning is useful. Do not edit code during this skill unless the user explicitly requested direct implementation.

## Purpose

Produce a compact, evidence-backed plan that improves coding-agent results by locking the relevant context before edits.

## When to use

Use this skill for:

- New features
- Bug fixes with unknown root cause
- Refactors
- Cross-file changes
- Test failures
- Architecture changes
- Security/auth/data changes
- Any task where relevant files are not already obvious

Do not use this skill for trivial one-file edits or tasks where the target file and change are obvious.

## Workflow

1. Classify task risk:
   - trivial
   - standard
   - complex
   - high-risk

2. Repository discovery:
   - Delegate to `repo-explorer` only when relevant files, tests, or entry points are not already known.
   - Ask for paths, symbols, tests, key lines, and files not yet read.
   - Do not ask for broad code reading in the main thread.

3. Documentation triage:
   - Delegate to `doc-router` only when docs/specs may define behavior.
   - Identify canonical docs, secondary docs, outdated duplicates, conflicts, and missing answers.

4. Vault lookup:
   - Use `/vault-search <query>` only if repository docs leave gaps or the user explicitly asks.
   - Treat vault memory as context, not truth.
   - Prefer current repository evidence when there is a conflict.

5. Targeted code reading:
   - Read source code only after discovery narrows the search.
   - Read tests before changing behavior when tests exist.

6. Draft compact context:
   - Goal
   - Current behavior
   - Expected behavior
   - Files to change
   - Files read
   - Assumptions
   - Verification commands

7. Critique:
   - Delegate to `plan-critic` for risky, unclear, cross-file, or high-impact work.
   - For high-risk work, ask for stop/go checkpoints and rollback strategy.

8. Final plan:
   - Incorporate critique.
   - Keep implementation scope small.
   - Wait for approval only if the user asked for a plan or the task is high-risk.

## Required output

## Task Classification
- Risk:
- Reason:

## Evidence Read
- Docs:
- Source:
- Tests:
- Vault context, if used:

## Context Contract
- Goal:
- Assumptions:
- Proposed files to change:
- Verification commands:

## Draft Plan
1.
2.
3.

## Review Findings
- Main risks:
- Simplifications:
- Stop/go checkpoints:

## Final Plan
1.
2.
3.

## Open Questions
- Only include questions that block safe implementation.
- If no question blocks progress, say `None`.

Before drafting the final plan, check whether the task has unresolved high-impact decisions.

Use `grill-me` only if:
- the user explicitly asks to be grilled
- multiple architecture/product paths are viable
- requirements are vague and cannot be resolved from docs/code
- the wrong choice would cause expensive rework

Do not use `grill-me` for straightforward bug fixes, small edits, or tasks where existing docs/code answer the question.
