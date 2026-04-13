---
name: refactor
description: Use when you spot architectural friction during implementation — explores codebase for shallow modules and tight coupling, proposes deepening refactors guided by Ousterhout's design principles
---

# Refactor

## Overview

Triggered during implementation when you encounter friction — not as a separate post-build phase. Explore for friction, surface candidates, design interfaces in parallel, and write an RFC.

Guided by the Ousterhout principles in CLAUDE.md: deepen shallow modules, push complexity downward, eliminate special cases, reject cross-module reasoning.

## Process

### Step 1: Explore for Friction

Use the Agent tool with subagent_type=Explore to navigate the codebase. Note where you experience friction:

- Where does understanding one concept require bouncing between many small files?
- Where are modules so shallow that the interface is nearly as complex as the implementation?
- Where have pure functions been extracted just for testability, but the real bugs hide in how they're called?
- Where do tightly-coupled modules create integration risk?

The friction you encounter IS the signal.

### Step 2: Present Candidates

Present a numbered list of deepening opportunities. For each candidate, show:

- **Cluster:** which modules/concepts are involved
- **Why they're coupled:** shared types, call patterns, co-ownership
- **Dependency category:** in-process, local-substitutable, remote-but-owned, or true-external (see `reference.md`)
- **Test impact:** what existing tests would be replaced by boundary tests

Do NOT propose interfaces yet. Ask: "Which of these would you like to explore?"

### Step 3: Frame the Problem Space

For the chosen candidate, write:
- Constraints any new interface must satisfy
- Dependencies it would need to rely on
- A rough illustrative code sketch to ground the constraints

Show this to the user, then immediately proceed to Step 4.

### Step 4: Design Multiple Interfaces

Spawn 3+ sub-agents in parallel. Each produces a **radically different** interface:

- Agent 1: "Minimise the interface — aim for 1-3 entry points max"
- Agent 2: "Maximise flexibility — support many use cases and extension"
- Agent 3: "Optimise for the most common caller — make the default case trivial"
- Agent 4 (if applicable): "Design around ports & adapters for cross-boundary dependencies"

Each outputs: interface signature, usage example, what complexity it hides, dependency strategy, trade-offs.

Present designs, compare them, give your recommendation.

### Step 5: Write RFC

After user picks an interface, write the RFC to `docs/plans/YYYY-MM-DD-<topic>-refactor.md` using the template in `reference.md`.

## Hard Gates

- Do not propose interfaces before user picks a candidate
- Do not skip the parallel design step — minimum 3 agents with different constraints
- Testing strategy must be "replace, don't layer" — delete old shallow tests when boundary tests exist

## Anti-Patterns

- Refactoring for its own sake — only triggered by real friction during implementation
- Single design proposal — always explore 3+ radically different interfaces
- Layering new tests on top of old ones — replace, don't layer
- Preserving shallow modules "for backwards compatibility" — deepen them

## Output

- RFC document at `docs/plans/YYYY-MM-DD-<topic>-refactor.md`
- Candidate analysis with dependency categories
- Chosen interface design with testing strategy

## Next Step

If approved, create a plan for the refactoring work using the `plan` skill.
