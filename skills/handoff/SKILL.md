---
name: handoff
description: Use when context is exhausted, work needs to continue later, or transferring work between sessions — creates structured handoff documents for session transfer
---

# Handoff

## Overview

Structured handoff documents for transferring work between sessions when context is exhausted or work needs to continue later.

## Process

### Creating a Handoff

When a session needs to end with work in progress:

1. **Capture current state** — what's done, what's in progress, what's next
2. **Document blockers** — what's preventing progress, what needs resolution
3. **Record key decisions** — decisions made during this session that context would be lost
4. **List file pointers** — plan file, design doc, spec, relevant source files
5. **Write handoff** to `docs/handoffs/YYYY-MM-DD-<topic>-handoff.md`

### Handoff Document Format

```markdown
# [Topic] Handoff

**Date:** YYYY-MM-DD
**Session:** [brief description of what this session worked on]

## Status

### Completed
- [x] [What was finished]

### In Progress
- [ ] [What was started but not finished — include current state]

### Not Started
- [ ] [What was planned but not reached]

## Blockers

- [What's preventing progress — errors, missing info, decisions needed]

## Key Decisions Made

- [Decision and rationale — these would be lost without documentation]

## File Pointers

- Plan: `docs/plans/YYYY-MM-DD-<topic>-plan.md`
- Design: `docs/plans/YYYY-MM-DD-<topic>-design.md`
- Spec: `docs/spec.md`
- Key files: [list relevant source files]

## Resume Instructions

[Specific instructions for the next session — what to do first, what to verify, what to watch out for]
```

### Resuming a Handoff

When starting a session and a handoff file exists:

1. **Read the handoff doc** — understand state, blockers, decisions
2. **Dispatch documentarian agents** to verify current state matches what's described
3. **Identify drift** — has anything changed since the handoff?
4. **Create action plan** for continuing the work

## Hard Gates

- Always write a handoff when ending a session with work in progress
- Always verify current state when resuming — don't trust the handoff blindly

## Anti-Patterns

- Ending a session without a handoff when work is incomplete — context is lost
- Trusting a handoff without verification — code may have changed since
- Vague resume instructions — "continue where I left off" helps no one
- Missing file pointers — the next session needs to know where things are

## Output

- Handoff document at `docs/handoffs/YYYY-MM-DD-<topic>-handoff.md`
- Or: action plan for resuming from an existing handoff

## Next Step

If creating: session ends.
If resuming: continue work per the action plan.
