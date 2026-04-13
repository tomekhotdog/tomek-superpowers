---
name: receive-review
description: Use when receiving code review feedback, before implementing suggestions — requires technical evaluation and verification, not performative agreement or blind implementation
---

# Receive Review

## Overview

Code review requires technical evaluation, not emotional performance.

**Core principle:** Verify before implementing. Ask before assuming. Technical correctness over social comfort.

## Process

### The Response Pattern

```
WHEN receiving code review feedback:

1. READ: Complete feedback without reacting
2. UNDERSTAND: Restate requirement in own words (or ask)
3. VERIFY: Check against codebase reality
4. EVALUATE: Technically sound for THIS codebase?
5. RESPOND: Technical acknowledgment or reasoned pushback
6. IMPLEMENT: One item at a time, test each
```

### If Any Item is Unclear

**STOP** — do not implement anything yet. Ask for clarification on unclear items.

Items may be related. Partial understanding = wrong implementation.

### YAGNI Check

If reviewer suggests "implementing properly":
- Grep codebase for actual usage
- If unused: "This isn't called. Remove it (YAGNI)?"
- If used: implement properly

### Implementation Order

For multi-item feedback:
1. Clarify anything unclear FIRST
2. Blocking issues (breaks, security)
3. Simple fixes (typos, imports)
4. Complex fixes (refactoring, logic)
5. Test each fix individually
6. Verify no regressions

### Write Lessons

If feedback reveals a non-obvious pattern, append to `docs/lessons.md`.

## Hard Gates

- No performative agreement ("You're absolutely right!", "Great point!", "Thanks for catching that!")
- Verify against codebase before implementing external reviewer suggestions
- Push back with technical reasoning when suggestions are wrong

## Anti-Patterns

| Mistake | Fix |
|---|---|
| Performative agreement | State requirement or just act |
| Blind implementation | Verify against codebase first |
| Batch without testing | One at a time, test each |
| Assuming reviewer is right | Check if it breaks things |
| Avoiding pushback | Technical correctness > comfort |
| Partial implementation | Clarify all items first |

### Acknowledging Correct Feedback

```
GOOD: "Fixed. [Brief description of what changed]"
GOOD: "Good catch — [specific issue]. Fixed in [location]."
GOOD: [Just fix it and show in the code]

BAD: "You're absolutely right!"
BAD: "Great point!"
BAD: "Thanks for catching that!"
BAD: ANY gratitude expression
```

Actions speak. Just fix it.

## Output

- Fixes implemented with test verification
- Technical pushback where appropriate
- `docs/lessons.md` updated with non-obvious insights from feedback

## Next Step

Return to `verify` after implementing fixes.
