---
name: using-tomek-superpowers
description: Use when starting any conversation — routes tasks to the right workflow phase based on size and type, requiring Skill tool invocation before ANY response including clarifying questions
---

<EXTREMELY-IMPORTANT>
If you think there is even a 1% chance a skill might apply to what you are doing, you ABSOLUTELY MUST invoke the skill.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.

This is not negotiable. This is not optional. You cannot rationalize your way out of this.
</EXTREMELY-IMPORTANT>

# Using tomek-superpowers

## Session Start

Before doing anything:

1. Read `docs/spec.md` if it exists (product context)
2. Read `docs/lessons.md` if it exists (past lessons)
3. Check `docs/plans/` for in-progress plan files
4. Check `docs/handoffs/` for session handoffs to resume
5. Read `docs/language.md` if it exists (use canonical terms in all output)

## Task Routing

When a task arrives, classify it and follow the right path:

**Bug or error** → `debug` → `verify` → `finish-branch`

**Trivial change** (< 5 min, single file) → just do it → `verify`

**Small known task** (< 30 min, known approach) → `plan` → `build` → `verify` → `finish-branch`

**New feature or unknown approach** → `design` → `plan` → `build` → `verify` → `request-review` → `finish-branch`

**Available at any point:**
- `cross-examine` — stress-test decisions
- `refactor` — when you spot friction
- `handoff` — transfer work between sessions

## How to Access Skills

Use the `Skill` tool. When you invoke a skill, its content is loaded and presented to you — follow it directly. Never use the Read tool on skill files.

## Skill Priority

When multiple skills could apply:
1. **Process skills first** (design, debug) — these determine HOW to approach the task
2. **Implementation skills second** (plan, build) — these guide execution

"Let's build X" → design first, then plan, then build.
"Fix this bug" → debug first, then verify.

## Red Flags

These thoughts mean STOP — you're rationalizing:

| What you're thinking | What you should do instead |
|---|---|
| "This is just a simple question" | Questions are tasks. Check for skills. |
| "I need more context first" | Skill check comes BEFORE clarifying questions. |
| "Let me explore the codebase first" | Skills tell you HOW to explore. Check first. |
| "This doesn't need a formal skill" | If a skill exists, use it. |
| "I remember this skill" | Skills evolve. Read current version. |
| "The skill is overkill" | Simple things become complex. Use it. |
| "I'll just do this one thing first" | Check BEFORE doing anything. |
| "I can skip design for this" | If it's not trivial, it needs design. |
| "Tests take too long" | Slow tests are still tests. Run them. |
| "I already know the approach" | Known approach = `plan` → `build`. Not skip. |
| "Let me just fix it quickly" | Quick fixes cause slow rework. Use `debug`. |
| "This is too small to plan" | If it's > 5 min and > 1 file, it needs a plan. |

## Skill Types

**Rigid** (debug, verify, build): Follow exactly. Don't adapt away discipline.

**Flexible** (design, refactor): Adapt principles to context.

The skill itself tells you which.

## User Instructions

Instructions say WHAT, not HOW. "Add X" or "Fix Y" doesn't mean skip workflows.
