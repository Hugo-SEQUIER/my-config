# OpenCode Global Template Notes

This directory is your reusable global OpenCode base.

## What is global and reusable

- `AGENTS.md`: minimal orchestration router.
- `agents/*`: task-specific subagents for scoped tasks.
- `commands/*`: command-to-subagent routing with `subtask: true` to isolate context.
- `opencode.json`: shared model/provider defaults and quality-aware agent settings.
- `plugins/rtk.ts`: command rewrite optimization via RTK.

## What to customize per project later

- Add `.opencode/AGENTS.md` in each repo for architecture, conventions, and workflow specifics.
- Add `.opencode/commands/*` for project commands (build/test/release/deploy).
- Add project-only agents only if they provide real operational gain.

## Recommended model policy

- Main coding: `openai/gpt-5.3-codex` via `build-codex` (default) and `plan-codex`.
- Discovery tasks: `openai/gpt-5.4-mini` via `repo-explorer` and `doc-router`.
- Local model usage: reserve `llama/local` (Qwen) for low-risk helper tasks only.

## Optional Ollama migration step

Current local model configured:

- `llama/local` (Qwen 3.6 via local llama.cpp)

If you change quantization/tag later, update model IDs in `agents/*.md` and `opencode.json`.

Quick check:

```bash
rtk opencode models
```

Then replace model IDs in `agents/*.md` (and in `opencode.json` if needed).
