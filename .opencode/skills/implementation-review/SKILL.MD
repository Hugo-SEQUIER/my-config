---
name: implementation-review
description: Review the final diff against the original goal, plan, and verification results.
---

# Implementation Review: $ARGUMENTS

Review the completed implementation before final response.

## Required inputs

- Original user request
- Approved plan or TASK_CONTEXT.md
- Files changed
- Git diff
- Commands run
- Test/lint/typecheck output

## Checklist

1. Scope check
   - Did implementation only touch planned files?
   - Are there unrelated changes?
   - Did it solve the actual user request?

2. Correctness check
   - Does behavior match acceptance criteria?
   - Are edge cases handled?
   - Are errors handled explicitly?
   - Are types/interfaces/contracts preserved?

3. Regression check
   - Could this break existing behavior?
   - Are public APIs changed?
   - Are migrations/config/docs needed?

4. Verification check
   - Were relevant commands run?
   - Did any command fail?
   - If not run, explain why.

5. Final risk assessment
   - Remaining risks
   - Confidence level
   - Recommended next action

## Output

- Verdict: pass / pass-with-risk / fail
- Changed files reviewed
- Issues found
- Required fixes before final
- Verification summary
- Confidence