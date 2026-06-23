---
name: cross-examine
description: Use when user wants to stress-test a plan or design, says "cross-examine", "grill me", or when you need to interrogate decisions relentlessly before proceeding — usable at any phase of the workflow
---

# Cross-Examine

## Overview

Relentless design interrogation. Walk down each branch of the decision tree, resolving dependencies between decisions one by one. Usable at any phase — design, plan, build, or review.

Side effects happen inline as decisions crystallize: sharpen `docs/language.md` when terms get clarified, record load-bearing decisions in `docs/lessons.md` when they're worth remembering.

## Process

1. **Ask one question at a time.** Never batch questions.
2. **Provide your recommended answer** for each question — the user can accept, reject, or modify.
3. **Explore the codebase instead of asking** when a question can be answered by reading code. Only ask the user when the answer requires human judgment.
4. **Walk the decision tree systematically.** Follow each branch to its conclusion before starting the next.
5. **Challenge assumptions.** If the user says "obviously X", ask why X and not Y.
6. **Stop when you reach shared understanding** — when every branch has been resolved with a clear decision.

## Side effects during grilling

Don't batch documentation updates until the end — capture them as decisions crystallize.

- **Sharpening a fuzzy term during the conversation?** Update `docs/language.md` right there. If the term isn't in there yet, add it (invoke the `language` skill if the file doesn't exist).
- **User rejects an option with a load-bearing reason?** Offer to record it in `docs/lessons.md` as a `[decision]` entry: _"Want me to record this so future design reviews don't re-suggest it?"_ Apply the gating criteria below.
- **User picks an option for a non-obvious reason?** Same rule — offer to record if the choice meets the criteria.
- **Ambiguity blocks a branch?** Resolve it against `docs/language.md` before continuing. Don't silently pick an interpretation.

### When to record a decision

All three of these must be true:

1. **Hard to reverse** — the cost of changing your mind later is meaningful
2. **Surprising without context** — a future reader will look at the code and wonder "why on earth did they do it this way?"
3. **The result of a real trade-off** — there were genuine alternatives and you picked one for specific reasons

If a decision is easy to reverse, skip it. If it's not surprising, nobody will wonder why. If there was no real alternative, there's nothing to record beyond "we did the obvious thing."

### Format

Append to `docs/lessons.md` under a `## Decisions` section (create if absent):

```md
- [decision] {short title}: {1-3 sentences — context, what we decided, why}. Date: YYYY-MM-DD.
```

Match the format of existing entries if `lessons.md` already uses a different shape.

## Hard Gates

- One question per message. No exceptions.
- Every question must have a recommended answer.
- Do not skip branches because they seem obvious.
- Do not offer to record every decision — apply the three criteria above.

## Anti-Patterns

- Batching multiple questions in one message — shallow answers, missed nuance
- Accepting "I think so" without probing — decisions must be definitive
- Asking questions you could answer by reading code — waste of user's time
- Stopping early because "we have enough" — every branch must resolve
- Offering to record every rejected option — noise, not signal
- Deferring language/decision updates until the end — they rot while context is still fresh

## Output

No primary document output. The value is the decisions made during the conversation. Incidental outputs as decisions crystallize:

- Updates to `docs/language.md` (terms clarified)
- New entries in `docs/lessons.md` (load-bearing decisions recorded)

These feed into whatever phase invoked the cross-examine (design doc, plan file, etc.).

## Next Step

Return to whichever phase invoked the cross-examine.