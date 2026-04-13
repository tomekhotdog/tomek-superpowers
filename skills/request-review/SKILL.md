---
name: request-review
description: Use when completing tasks, implementing major features, or before merging to verify work meets requirements — dispatches five-axis code review
---

# Request Review

## Overview

Dispatch the `code-reviewer` agent to catch issues before they cascade. The reviewer performs a **five-axis review** — correctness, readability, architecture, security, performance — each as a separate pass with `file:line` references.

## Process

### Step 1: Get Git SHAs

```bash
BASE_SHA=$(git rev-parse HEAD~1)  # or origin/main
HEAD_SHA=$(git rev-parse HEAD)
```

### Step 2: Dispatch Code-Reviewer Agent

Use the `code-reviewer` agent with these placeholders:

- `{WHAT_WAS_IMPLEMENTED}` — what you just built
- `{PLAN_OR_REQUIREMENTS}` — what it should do
- `{BASE_SHA}` — starting commit
- `{HEAD_SHA}` — ending commit
- `{DESCRIPTION}` — brief summary

### Step 3: Act on Feedback

- **Critical** issues: fix immediately
- **Important** issues: fix before proceeding
- **Minor** issues: note for later
- Push back if reviewer is wrong (with technical reasoning)

## Hard Gates

- Mandatory after each task in build workflow
- Mandatory before merge to main
- Never skip because "it's simple"
- Never proceed with unfixed Critical or Important issues

## Anti-Patterns

- Skipping review because "it's a small change" — small changes cause big bugs
- Ignoring Critical issues — they're critical for a reason
- Arguing with valid technical feedback — fix it, don't debate it
- Accepting review without reading the findings — engage with the feedback

## Output

- Five-axis review with `file:line` references
- Issues categorised by severity (Critical/Important/Minor)
- Assessment: Ready to merge? Yes/No/With fixes

## Next Step

If changes needed, fix them. Then invoke `verify` and `finish-branch`.
