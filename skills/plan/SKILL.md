---
name: plan
description: Use when you have a design doc or requirements for a multi-step task, before touching code — decomposes work into vertical slices with TDD baked in
---

# Plan

## Overview

Decompose a design into a numbered, dependency-annotated task list using vertical slices. Assume the implementing agent has zero context and questionable taste. Every task includes exact file paths, complete code, TDD steps, and commands with expected output.

**Announce at start:** "I'm using the plan skill to create the implementation plan."

## Process

### Step 1: Read the Design Doc

Read the design doc from `docs/plans/`. All questions should already be resolved by `design` + `cross-examine`. If anything is ambiguous, resolve it now — do not leave gaps for the implementer to figure out.

### Step 2: Decompose Using Vertical Slices

Break the work into **tracer bullet** slices — each cuts end-to-end through ALL layers, not horizontal slabs.

Each slice:
- Delivers a narrow but COMPLETE path through every layer (schema, API, logic, UI, tests)
- Is demoable or verifiable on its own
- Prefer many thin slices over few thick ones

### Step 3: Flatten Into Numbered Tasks

Convert slices into numbered tasks with dependency annotations (for parallel subagent execution). Independent tasks can run in parallel; dependent tasks must wait.

### Step 4: Write Each Task

Each task includes:
- Exact file paths (create/modify/test)
- Complete code (not "add validation" — the actual code)
- TDD baked in: write failing test → run to confirm fail → implement → run to confirm pass → commit
- Exact commands with expected output
- e2e tests derived from `docs/spec.md` — new features get e2e coverage

### Step 5: Write the Plan File

Save to `docs/plans/YYYY-MM-DD-<topic>-plan.md` using the format below.

### Step 6: Offer Execution Choice

**"Plan complete and saved. Two execution options:**

**1. Subagent-Driven (this session)** — I dispatch fresh subagent per task, review between tasks, fast iteration

**2. New session** — Open new session, load the plan, execute with checkpoints

**Which approach?"**

## Hard Gates

- Design doc must exist and be approved before planning
- Every task must have complete code — no placeholders
- Every task must include TDD steps (write test → verify fail → implement → verify pass → commit)
- Dependency annotations must be present between tasks

## Anti-Patterns

- Horizontal slicing: "First write all tests, then all implementation" — NO. Vertical slices only.
- Placeholder code: "Add validation here" — NO. Write the actual validation.
- Missing test commands: "Run tests" — NO. Exact command with expected output.
- Skipping dependency annotations — prevents parallel execution
- Leaving questions for the implementer — resolve everything in the plan

## Output

### Plan File Format (`docs/plans/YYYY-MM-DD-<topic>-plan.md`)

````markdown
# [Feature Name] Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use tomek-superpowers:build to implement this plan task-by-task.

**Goal:** [One sentence]
**Architecture:** [2-3 sentences]
**Tech Stack:** [Key technologies]
**Design:** `docs/plans/YYYY-MM-DD-<topic>-design.md`

---

### Task 1: [Name]
**Depends on:** none

**Files:**
- Create: `exact/path/to/file.ts`
- Test: `tests/exact/path/to/test.ts`

**Step 1: Write the failing test**
```typescript
test("user can create account", async () => {
  const result = await createUser({ name: "Alice" });
  expect(result.id).toBeDefined();
});
```

**Step 2: Run test to verify it fails**
Run: `npm test -- tests/path/test.ts`
Expected: FAIL

**Step 3: Write minimal implementation**
```typescript
export async function createUser(data: { name: string }) {
  // ...complete code...
}
```

**Step 4: Run test to verify it passes**
Run: `npm test -- tests/path/test.ts`
Expected: PASS

**Step 5: Commit**
```bash
git add tests/path/test.ts src/path/file.ts
git commit -m "feat: add user creation"
```

### Task 2: [Name]
**Depends on:** Task 1

...

### Task 3: [Name]
**Depends on:** none (can run parallel with Task 2)

...

## Review
- [ ] Code review requested
- [ ] All feedback addressed
- [ ] Final verification passed
````

## Plan Iteration

When feedback requires reworking a plan:
1. Read the existing plan file
2. Incorporate feedback
3. Rewrite — preserve completed task markers so in-progress work isn't lost

## Next Step

Invoke the `build` skill to execute the plan.
