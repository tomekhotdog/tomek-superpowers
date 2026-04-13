---
name: finish-branch
description: Use when implementation is complete, all tests pass, and you need to decide how to integrate the work — guides completion with pre-launch checklist and structured options
---

# Finish Branch

## Overview

Guide completion of development work by verifying readiness, presenting clear options, and handling the chosen workflow.

**Core principle:** Verify tests → Pre-launch checklist → Present options → Execute choice → Clean up.

**Announce at start:** "I'm using the finish-branch skill to complete this work."

## Process

### Step 1: Verify Tests

Run the project's test suite. If tests fail, stop — cannot proceed until they pass.

### Step 2: Pre-Launch Checklist

Read the plan file from `docs/plans/` and verify:

- [ ] All plan tasks marked complete
- [ ] e2e tests derived from `docs/spec.md` pass
- [ ] No `TODO` / `FIXME` / `HACK` introduced without a tracked plan item
- [ ] No secrets or credentials in committed files
- [ ] No debug logging left in production code paths
- [ ] `docs/spec.md` still accurate after implementation (no spec drift)
- [ ] `docs/language.md` terms used consistently in new code

If any item fails, fix it before proceeding.

### Step 3: Present Options

Present exactly these 4 options:

```
Implementation complete. What would you like to do?

1. Merge back to <base-branch> locally
2. Push and create a Pull Request
3. Keep the branch as-is (I'll handle it later)
4. Discard this work

Which option?
```

### Step 4: Execute Choice

**Option 1: Merge Locally**
- Switch to base branch, pull latest, merge feature branch
- Verify tests on merged result
- Delete feature branch

**Option 2: Push and Create PR**
- Push branch with `-u` flag
- Create PR with summary and test plan

**Option 3: Keep As-Is**
- Report branch name and location
- Don't clean up

**Option 4: Discard**
- Confirm first — require typed "discard" confirmation
- Show what will be deleted (branch, commits, worktree)
- Only proceed with explicit confirmation

### Step 5: Cleanup

For Options 1, 2, 4: clean up worktree if in one.
For Option 3: keep worktree.

## Hard Gates

- Tests must pass before presenting options
- Pre-launch checklist must pass before presenting options
- Plan file must have all items checked
- Option 4 requires typed "discard" confirmation

## Anti-Patterns

- Skipping test verification — never merge broken code
- Open-ended "what should I do next?" — present exactly 4 structured options
- Automatic worktree cleanup for Option 3 — user may need it
- Discarding without confirmation — always require explicit "discard"
- Skipping the pre-launch checklist — it catches what tests don't

## Output

- Pre-launch checklist verified
- Chosen integration path executed
- Worktree cleaned up (if applicable)

## Next Step

Work complete. Start a new task or end the session.
