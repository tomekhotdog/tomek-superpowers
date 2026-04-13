---
name: verify
description: Use when about to claim work is complete, fixed, or passing, before committing or creating PRs — requires running verification commands and confirming output before making any success claims
---

# Verify

## Overview

Claiming work is complete without verification is dishonesty, not efficiency.

**Core principle:** Evidence before claims, always.

**Violating the letter of this rule is violating the spirit of this rule.**

## The Iron Law

```
NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE
```

If you haven't run the verification command in this message, you cannot claim it passes.

## Process

### The Gate Function

```
BEFORE claiming any status or expressing satisfaction:

1. IDENTIFY: What command proves this claim?
2. RUN: Execute the FULL command (fresh, complete)
3. READ: Full output, check exit code, count failures
4. VERIFY: Does output confirm the claim?
   - If NO: State actual status with evidence
   - If YES: State claim WITH evidence
5. CHECK PLAN: Read the plan file, confirm all items checked off
6. ONLY THEN: Make the claim

Skip any step = lying, not verifying
```

### If Verification Catches a Miss

Write lesson to `docs/lessons.md` — the miss is a pattern worth documenting.

## Hard Gates

- No completion claim without running the actual command and showing its output
- Plan file must have all items checked before allowing `finish-branch`
- Re-run verification even if "I already tested this"

## Anti-Patterns

### Pressure Test Scenarios

| What you're thinking | What you should do |
|---|---|
| "I already tested this" | Re-run anyway. State changes between then and now. |
| "It's a trivial change" | Trivial changes break builds. Run the tests. |
| "The tests are slow" | Slow tests are still tests. Run them. |
| "Should work now" | RUN the verification. |
| "I'm confident" | Confidence is not evidence. |
| "Just this once" | No exceptions. |
| "Linter passed" | Linter is not compiler is not test suite. |
| "Agent said success" | Verify independently. |
| "I'm tired" | Exhaustion is not an excuse. |

## Red Flags — STOP

- Using "should", "probably", "seems to"
- Expressing satisfaction before verification ("Great!", "Perfect!", "Done!")
- About to commit/push/PR without verification
- Trusting agent success reports
- ANY wording implying success without having run verification

## Output

- Verification command output (full, not summarised)
- Plan file confirmation (all items checked)
- Status claim with evidence

## Next Step

If verification passes, invoke `finish-branch`.
