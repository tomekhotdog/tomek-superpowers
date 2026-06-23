---
name: features
description: Use when user wants to document or update high-level features/user journeys, says "features", "user journeys", "what does this do", or when onboarding an existing codebase that has no docs/features.md
---

# Features

## Overview

Extract and document all high-level features of an application or library into `docs/features.md`. Primarily an extraction tool — it discovers what the application does by reading its public API surface (endpoints, exported functions, CLI commands, UI components) and organizes them into a hierarchical feature catalog.

**Announce at start:** "I'm using the features skill to extract and document application features."

## Process

### Step 1: Extract From Public API Surface

Dispatch documentarian sub-agents **in parallel**:

- **codebase-locator** — find all public API surfaces: route handlers, exported functions, CLI commands, UI components, database schemas
- **codebase-analyzer** — trace what each public endpoint/function does end-to-end, what user journey it supports
- **codebase-pattern-finder** — find feature groupings, shared patterns across related endpoints, naming conventions that reveal feature areas

Focus on: what a user can DO, not how it's implemented. Route definitions, exported APIs, CLI command registrations, UI page/component hierarchies — these are the features.

### Step 2: Extract From Documentation

Read all available docs: README, docs/, API docs, user guides, changelog. Note features described in docs but not in code (planned/removed) and features in code but not in docs (undocumented).

### Step 3: Group Into Feature Areas

Organize discovered features hierarchically:

- **Feature areas** — high-level groupings (e.g. "Authentication", "Collaboration", "Billing")
- **Features** — individual user journeys within each area (e.g. "Invite collaborators to a project")
- **API surface** — the public APIs that implement each feature

### Step 4: Read `docs/language.md`

If `docs/language.md` exists, read it and use canonical terms (bolded) in all feature descriptions. If it doesn't exist, recommend running the `language` skill first.

### Step 5: Present Findings

Present the feature hierarchy to the user. Ask them to:

- Confirm the grouping makes sense
- Correct any misframed features ("that's not one feature, it's two")
- Fill in intent the code can't express ("this exists because enterprise customers need audit trails")
- Flag features that are incomplete or deprecated

### Step 6: Write `docs/features.md`

Write using the format below. If `docs/features.md` already exists, read it first and rewrite clean — preserve decisions, incorporate new findings.

### Step 7: Commit

Commit the features file to git.

## Hard Gates

- Codebase extraction (Steps 1-2) must complete before presenting anything to the user
- Use canonical terms from `docs/language.md` if it exists
- User must confirm the feature hierarchy before writing the file
- Describe WHAT users can do, not HOW it's implemented

## Anti-Patterns

- Describing implementation details ("uses WebSockets for real-time sync") — features are behavioral, not technical
- Inventing features from user conversation that don't exist in code — ground to reality
- Flat list without hierarchy — grouping by area aids scoping
- Missing API surface links — the AI needs these to scope work against features
- Skipping the user confirmation — the human knows which features matter and how they relate

## Output Format (`docs/features.md`)

```markdown
# Features

## [Feature Area]

### [Feature Name]

[1-3 sentence description of what a user can do. Uses **canonical terms** from language.md.]

**API surface:**
- `POST /projects/:id/invites` — send invitation
- `acceptInvite(token)` — accept an invitation
- `RevokeInvite` component — UI for managing invitations

### [Another Feature]

...

## [Another Feature Area]

### [Feature Name]

...
```

## Re-running

When invoked on a project that already has `docs/features.md`:

1. Read the existing file
2. Re-run codebase extraction to find new, changed, or removed features
3. Update descriptions where functionality has evolved
4. Flag features in the file that no longer exist in code
5. Present changes to user for confirmation before writing

## Next Step

Return to whichever phase invoked the skill. If invoked standalone, work is complete.