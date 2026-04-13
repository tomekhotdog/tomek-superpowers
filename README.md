```
 ___________                    __       _________                                                              
 \__    ___/___   _____   ____ |  | __  /   _____/__ ________   ________________   ______  _  __ ___________  ______
   |    | /  _ \ /     \_/ __ \|  |/ /  \_____  \|  |  \____ \_/ __ \_  __ \____ \ /  _ \ \/ \/ // __ \_  __ \/  ___/
   |    |(  <_> )  Y Y  \  ___/|    <   /        \  |  /  |_> >  ___/|  | \/  |_> >  <_> )     /\  ___/|  | \/\___ \ 
   |____| \____/|__|_|  /\___  >__|_ \ /_______  /____/|   __/ \___  >__|  |   __/ \____/ \/\_/  \___  >__|  /____  >
                      \/     \/     \/         \/      |__|        \/      |__|                      \/           \/ 
```

# tomek-superpowers

A Claude Code plugin that replaces [superpowers](https://github.com/obra/superpowers) with a personal, opinionated engineering workflow. Combines [AI Hero](https://www.aihero.dev/)'s structured product pipeline and deep module philosophy with [Boris Cherny](https://github.com/bcherny)'s behavioral rules and self-improvement loop.

## Installation

```bash
claude plugin add tomekhotdog/tomek-superpowers
```

## Workflow

```
 Task arrives → using-tomek-superpowers (router)
                        │
    ┌───────────────────┼──────────────────────────┐
    │                   │                          │
    ▼                   ▼                          ▼
  Bug/error         Small task              New feature
    │                   │                          │
    ▼                   │                          ▼
  debug                 │                       design ─── research (3 agents)
    │                   │                          │        ├─ codebase-locator
    │                   ▼                          │        ├─ codebase-analyzer
    │                 plan                         │        └─ codebase-pattern-finder
    │                   │                          ▼
    │                   │                        plan
    │                   ▼                          │
    │                 build ── subagent per task    ▼
    │                   │     ├─ implementer      build
    │                   │     ├─ spec reviewer      │
    │                   │     └─ quality reviewer    │
    ▼                   ▼                          ▼
  verify              verify                    verify
    │                   │                          │
    ▼                   ▼                          ▼
  finish-branch     finish-branch           request-review (5-axis)
                                                   │
                                                   ▼
                                             finish-branch

 Trivial (< 5 min): just do it → verify

 Available at any point:
   grill      ── stress-test decisions
   refactor   ── when you spot friction
   handoff    ── transfer work between sessions
```

## What's Inside

### 32 Behavioral Rules (`CLAUDE.md`)

Always-on directives covering workflow orchestration, self-improvement loop, quality bar, autonomy, core principles, Ousterhout's design principles, and project documentation conventions.

### 13 Skills

| Phase | Skill | What it does |
|---|---|---|
| **Define** | `design` | Research codebase, interview user, produce design doc |
| **Define** | `grill` | Adversarial design interrogation, one question at a time |
| **Decompose** | `plan` | Vertical slice decomposition with TDD baked in |
| **Build** | `build` | Subagent dispatch with two-stage review (spec + quality) |
| **Build** | `debug` | 4-phase systematic debugging with root cause tracing |
| **Build** | `refactor` | Ousterhout-guided module deepening with parallel design |
| **Review** | `verify` | Iron law: no completion claims without evidence |
| **Review** | `request-review` | Five-axis code review (correctness, readability, architecture, security, performance) |
| **Review** | `receive-review` | Technical evaluation, not performative agreement |
| **Complete** | `finish-branch` | Pre-launch checklist + 4 structured options |
| **Transfer** | `handoff` | Structured session transfer documents |
| **Meta** | `write-skill` | TDD for process documentation |
| **Bootstrap** | `using-tomek-superpowers` | Routes tasks to the right workflow phase |

### 4 Agents

| Agent | Model | Role |
|---|---|---|
| `codebase-locator` | Sonnet | Finds WHERE code lives (documentarian) |
| `codebase-analyzer` | Sonnet | Explains HOW code works (documentarian) |
| `codebase-pattern-finder` | Sonnet | Discovers reusable patterns (documentarian) |
| `code-reviewer` | Sonnet | Five-axis review against plan |

Documentarian agents are strictly factual reporters — they describe what exists without suggesting improvements.

### 3 Commands

| Command | Shortcut for |
|---|---|
| `/design` | `tomek-superpowers:design` |
| `/plan` | `tomek-superpowers:plan` |
| `/build` | `tomek-superpowers:build` |

## Project Files

The workflow writes structured documentation under `docs/`:

```
 PERSISTENT                           PER-ITERATION
 ──────────                           ─────────────
 docs/spec.md        (product spec)   docs/plans/YYYY-MM-DD-<topic>-design.md
 docs/language.md    (domain terms)   docs/plans/YYYY-MM-DD-<topic>-plan.md
 docs/lessons.md     (learning log)

 SESSION TRANSFER
 ────────────────
 docs/handoffs/YYYY-MM-DD-<topic>-handoff.md
```

## Design Principles

Built on [John Ousterhout's *A Philosophy of Software Design*](https://web.stanford.edu/~ouster/cgi-bin/book.php):

- **Deep modules** — small interface, powerful hidden implementation
- **Push complexity downward** — keep top-level flows linear and obvious
- **Eliminate special cases** — generalise instead of branching
- **Information hiding** — expose *what*, not *how*
- **Strategic over tactical** — design is a first-class activity

## Sources

This plugin synthesises ideas from:

- **[Superpowers](https://github.com/obra/superpowers)** — enforcement patterns, pressure resistance, TDD discipline
- **[AI Hero](https://www.aihero.dev/)** — PRDs, vertical slicing, deep modules, parallel interface design
- **[Boris Cherny](https://github.com/bcherny)** — self-improvement loop, elegance checks, autonomous debugging
- **[HumanLayer](https://humanlayer.dev/)** — documentarian agents, research-first design, structured handoffs
- **[Agent-Skills](https://github.com/anthropics/agent-skills)** — five-axis review, pre-launch checklist, standardised skill anatomy

## License

MIT
