---
name: write-skill
description: Use when creating new skills, editing existing skills, or verifying skills work before deployment
---

# Write Skill

## Overview

Writing skills IS Test-Driven Development applied to process documentation. Write test cases (pressure scenarios with subagents), watch them fail (baseline behavior), write the skill, watch tests pass (agents comply), and refactor (close loopholes).

**Core principle:** If you didn't watch an agent fail without the skill, you don't know if the skill teaches the right thing.

## Process

### RED: Write Failing Test (Baseline)

Run pressure scenario with subagent WITHOUT the skill. Document:
- What choices did the agent make?
- What rationalizations did it use (verbatim)?
- Which pressures triggered violations?

### GREEN: Write Minimal Skill

Write SKILL.md that addresses those specific rationalizations. Follow the standard anatomy:

```markdown
---
name: skill-name
description: Use when [triggering conditions — NO workflow summary]
---

# Skill Title

## Overview
[2-3 sentences: what and when]

## Process
[Numbered steps or flowchart]

## Hard Gates
[Non-negotiable requirements]

## Anti-Patterns
[Common mistakes and how to avoid them]

## Output
[What this skill produces]

## Next Step
[Which skill follows]
```

Run same scenarios WITH skill — agent should now comply.

### REFACTOR: Close Loopholes

Agent found new rationalization? Add explicit counter. Re-test until bulletproof.

## Hard Gates

- No skill without a failing test first (baseline behavior documented)
- Description must start with "Use when..." and contain NO workflow summary
- Every skill uses the same section structure in the same order
- Test each skill type appropriately (discipline → pressure scenarios, technique → application scenarios, reference → retrieval scenarios)

## Anti-Patterns

- Writing skill from scratch without reading originals — always read source material first
- Description that summarizes workflow — causes agents to follow description instead of reading full skill
- Narrative storytelling ("In session X, we found...") — skills are reference guides, not stories
- Skipping baseline testing — untested skills always have issues
- Batching multiple skills without testing each — deploy and test one at a time

## Output

- SKILL.md following standard anatomy
- Baseline test results documented
- Compliance verified with skill present

## Next Step

Commit skill and verify it loads correctly.
