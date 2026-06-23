---
name: design
description: Use when building new features, making architectural decisions, or when user says "design", "investigate", "how does X work", or "research" — explores codebase, interviews user, and produces a design doc before any code is written
---

# Design

## Overview

Turn ideas into fully formed designs through research, collaborative dialogue, and structured documentation. Merges brainstorming, PRD writing, ubiquitous language extraction, and codebase research into a single phase.

**Announce at start:** "I'm using the design skill to explore this idea before writing code."

## Process

### Step 1: Research Phase (Before Proposing Anything)

Dispatch the `research` skill as a subagent to explore the codebase. It dispatches the three documentarian agents in parallel, synthesizes findings, and persists a research document to `docs/plans/`.

Wait for the research subagent to complete, then read its research document before proceeding.

### Step 2: Interview the User

Ask questions one at a time (prefer multiple choice). Focus on:
- Purpose and constraints
- Success criteria
- Edge cases and failure modes
- Who uses this and how

Only one question per message. If a topic needs more exploration, break it into multiple questions.

### Step 3: Propose Approaches

Present 2-3 different approaches with trade-offs:
- Lead with your recommendation and reasoning
- Identify deep module opportunities (Ousterhout: small interface, powerful implementation)
- Consider each through the lens of simplicity (rule 14) and minimal impact (rule 16)

### Step 4: Present the Design

Once you understand what you're building, present the design section by section. Scale each section to its complexity. Ask after each section whether it looks right.

Cover: architecture, components, data flow, error handling, testing approach.

### Step 5: Update Project Documentation

After design approval:

1. **Write design doc** to `docs/plans/YYYY-MM-DD-<topic>-design.md` using the format below
2. **Rewrite `docs/spec.md`** — the persistent product spec reflecting the product as it will be after this iteration (rewritten clean, not appended)
3. **Invoke the `language` skill** to update `docs/language.md` with any new or changed domain terminology from this design
4. **Invoke the `features` skill** to update `docs/features.md` with any new or changed features from this design
5. **Prune stale entries from `docs/lessons.md`** — remove lessons that are no longer relevant

### Step 6: Commit the Design

Commit all documentation changes to git.

## Hard Gates

- **No code until design is approved.** Not one line. Not "just scaffolding." Nothing.
- Research output must be included in the design doc (not discarded)
- User must explicitly approve the design before proceeding

## Anti-Patterns

- Skipping research because "I already know the codebase" — research reveals things you missed
- Asking multiple questions at once — overwhelms the user, gets shallow answers
- Proposing only one approach — always offer 2-3 with trade-offs
- Writing code "to explore" — exploration is research agents, not implementation
- Appending to spec.md instead of rewriting — spec.md reflects the product as it will be, clean

## Output

### Design Doc Format (`docs/plans/YYYY-MM-DD-<topic>-design.md`)

```markdown
# [Feature Name] Design

## Research

[Output from documentarian agents — what was explored and found]

## Problem Statement

[What problem are we solving and why]

## Solution

[Chosen approach and rationale]

## User Stories

1. As a [actor], I want [feature], so that [benefit]
...

## Implementation Decisions

- [Architecture, module design, interfaces, schema changes]
- [Deep module opportunities identified]
- [Trade-offs accepted and why]

## Testing Decisions

- [What to test, how to test, testing boundaries]
- [Which modules get tests, prior art for test patterns]

## Out of Scope

- [What we're explicitly NOT doing]
```

## Next Step

Invoke the `plan` skill to create the implementation plan.
