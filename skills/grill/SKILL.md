---
name: grill
description: Use when user wants to stress-test a plan or design, says "grill me", or when you need to interrogate decisions relentlessly before proceeding — usable at any phase of the workflow
---

# Grill

## Overview

Relentless design interrogation. Walk down each branch of the decision tree, resolving dependencies between decisions one by one. Usable at any phase — design, plan, build, or review.

## Process

1. **Ask one question at a time.** Never batch questions.
2. **Provide your recommended answer** for each question — the user can accept, reject, or modify.
3. **Explore the codebase instead of asking** when a question can be answered by reading code. Only ask the user when the answer requires human judgment.
4. **Walk the decision tree systematically.** Follow each branch to its conclusion before starting the next.
5. **Challenge assumptions.** If the user says "obviously X", ask why X and not Y.
6. **Stop when you reach shared understanding** — when every branch has been resolved with a clear decision.

## Hard Gates

- One question per message. No exceptions.
- Every question must have a recommended answer.
- Do not skip branches because they seem obvious.

## Anti-Patterns

- Batching multiple questions in one message — shallow answers, missed nuance
- Accepting "I think so" without probing — decisions must be definitive
- Asking questions you could answer by reading code — waste of user's time
- Stopping early because "we have enough" — every branch must resolve

## Output

No document output. The value is the decisions made during the conversation. These decisions feed into whatever phase invoked the grill (design doc, plan file, etc.).

## Next Step

Return to whichever phase invoked the grill.
