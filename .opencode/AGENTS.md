# OpenCode Global Rules

Global rules should keep agents useful, not force a workflow. Put project-specific details in each repo's `.opencode/AGENTS.md`.

## Default Behavior

- For implementation requests, inspect enough context, make the smallest correct change, and verify it.
- For implementation requests, do not answer with only acknowledgement or intent; use a relevant tool in the same turn.
- In large or syntax-dense files, especially JSX/TSX, patch one coherent requirement at a time. Avoid broad rewrites.
- Do not enter planning mode unless the user asks for a plan, the task is high-risk, or the implementation path is unclear.
- Ask only blocking questions. Otherwise make a reasonable assumption, state it briefly when useful, and continue.
- Prefer direct edits over extra orchestration once relevant files are known.

## Context Control

- Use `TASK_CONTEXT.md` for non-trivial work, but keep it short.
- Recommended sections: Goal, Files read, Assumptions, Files to change, Verification.
- Do not let `TASK_CONTEXT.md` become an approval gate or a stopping point.
- Use `session-start` at the beginning of a task only when durable project/vault context is likely to help.

## Planning Tools

- Use `repo-explorer` when relevant files are unknown and discovery would otherwise bloat the main thread.
- Use `doc-router` when docs/specs likely define expected behavior.
- Use `plan-critic` for risky, unclear, or cross-cutting plans.
- Use `plan-review-skill` when the user asks for a plan or the task needs an evidence-backed plan before edits.
- Do not use planning subagents for straightforward edits where the target files are obvious.

## Shell And Safety

- Prefer `rtk` for noisy commands, but do not block useful normal commands.
- Never run destructive filesystem or git commands unless explicitly requested.
- Do not revert, overwrite, or clean up user changes unless explicitly requested.

## Verification

- Run relevant checks after edits when available.
- After each meaningful patch in large or syntax-dense files, run the fastest available syntax/lint/typecheck before continuing.
- If checks fail, fix the issue when the fix is in scope.
- If checks are skipped or fail, report that clearly.

## Final Response

- Keep it concise.
- Include summary, files changed, verification run, failures or remaining risks, and confidence when the task was substantial.
