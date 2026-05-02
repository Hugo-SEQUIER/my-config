---
description: Review a plan with a lean, risk-first pipeline.
agent: plan-critic
subtask: true
---
Review this plan and return a lean execution strategy: $ARGUMENTS

Pipeline:
1) If repository discovery is needed, delegate exploration to `@repo-explorer`.
2) If docs can answer first, delegate to `@doc-router`.
3) Critique assumptions, risks, ordering, and complexity.
4) Return a revised lean plan. Include stop/go checkpoints only for high-risk work.

Output format:
- Verdict
- Top risks (max 5)
- Simplifications
- Revised plan (short)
