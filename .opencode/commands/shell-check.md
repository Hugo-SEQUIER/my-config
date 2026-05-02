---
description: Run lightweight shell sanity checks in isolated subtask.
agent: bash-runner
subtask: true
---
Run these shell checks and summarize results: $ARGUMENTS

Rules:
- Prefer `rtk` for noisy shell commands, but normal useful commands are allowed with approval.
- Do not edit files.
- Report only key failures and actionable next steps.
