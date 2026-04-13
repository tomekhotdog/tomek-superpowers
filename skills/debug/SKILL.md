---
name: debug
description: Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes — requires root cause investigation before any fix attempt
---

# Debug

## Overview

Random fixes waste time and create new bugs. Quick patches mask underlying issues.

**Core principle:** ALWAYS find root cause before attempting fixes. Symptom fixes are failure.

**Violating the letter of this process is violating the spirit of debugging.**

## Process

### Phase 1: Root Cause Investigation

**BEFORE attempting ANY fix:**

1. **Read error messages carefully** — don't skip past them. They often contain the exact solution. Read stack traces completely. Note line numbers, file paths, error codes.

2. **Reproduce consistently** — can you trigger it reliably? What are the exact steps? If not reproducible, gather more data — don't guess.

3. **Check recent changes** — git diff, recent commits, new dependencies, config changes, environmental differences.

4. **Gather evidence in multi-component systems** — before proposing fixes, add diagnostic instrumentation at each component boundary. Log what enters and exits each component. Run once to gather evidence showing WHERE it breaks.

5. **Trace data flow** — see `root-cause-tracing.md` for the complete backward tracing technique. Quick version: where does bad value originate? What called this with bad value? Keep tracing up until you find the source. Fix at source, not at symptom.

### Phase 2: Pattern Analysis

1. **Find working examples** — locate similar working code in the same codebase
2. **Compare against references** — read reference implementations COMPLETELY, don't skim
3. **Identify differences** — list every difference between working and broken, however small
4. **Understand dependencies** — what components, settings, config, environment does this need?

### Phase 3: Hypothesis and Testing

1. **Form single hypothesis** — state clearly: "I think X is the root cause because Y"
2. **Test minimally** — smallest possible change to test hypothesis, one variable at a time
3. **Verify before continuing** — did it work? Yes → Phase 4. No → NEW hypothesis, don't pile on fixes.

### Phase 4: Implementation

1. **Create failing test case** — simplest possible reproduction, automated if possible
2. **Implement single fix** — address root cause, ONE change at a time, no "while I'm here" improvements
3. **Verify fix** — test passes? No other tests broken? Issue resolved?
4. **If fix doesn't work** — count fixes tried. If < 3, return to Phase 1. **If >= 3, STOP and question the architecture.**
5. **Write lesson** — after resolution, append root cause insights to `docs/lessons.md`

## Hard Gates

- No fixes without completing Phase 1 (root cause investigation)
- If 3+ fixes failed: question the architecture, discuss with user before attempting more
- Write root cause to `docs/lessons.md` after every resolution

## Anti-Patterns

| Excuse | Reality |
|---|---|
| "Issue is simple, don't need process" | Simple issues have root causes too. Process is fast for simple bugs. |
| "Emergency, no time for process" | Systematic debugging is FASTER than guess-and-check thrashing. |
| "Just try this first, then investigate" | First fix sets the pattern. Do it right from the start. |
| "I see the problem, let me fix it" | Seeing symptoms ≠ understanding root cause. |
| "One more fix attempt" (after 2+ failures) | 3+ failures = architectural problem. Question pattern, don't fix again. |

## Red Flags — STOP and Return to Phase 1

- "Quick fix for now, investigate later"
- "Just try changing X and see if it works"
- "Add multiple changes, run tests"
- "It's probably X, let me fix that"
- Proposing solutions before tracing data flow
- Each fix reveals new problem in different place

## Output

- Root cause identified and documented
- Fix implemented with failing test
- `docs/lessons.md` updated with root cause insight

## Next Step

Invoke the `verify` skill.
