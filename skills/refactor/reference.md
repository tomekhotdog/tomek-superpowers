# Refactor Reference

## Dependency Categories

When assessing a candidate for deepening, classify its dependencies:

### 1. In-process
Pure computation, in-memory state, no I/O. Always deepenable — just merge the modules and test directly.

### 2. Local-substitutable
Dependencies that have local test stand-ins (e.g., PGLite for Postgres, in-memory filesystem). Deepenable if the test substitute exists.

### 3. Remote but owned (Ports & Adapters)
Your own services across a network boundary. Define a port (interface) at the module boundary. The deep module owns the logic; the transport is injected.

### 4. True external (Mock)
Third-party services you don't control. Mock at the boundary. The deepened module takes the external dependency as an injected port.

## Testing Strategy: Replace, Don't Layer

- Old unit tests on shallow modules are waste once boundary tests exist — delete them
- Write new tests at the deepened module's interface boundary
- Tests assert on observable outcomes through the public interface
- Tests should survive internal refactors

## Design Heuristics (Ousterhout)

- **Deep modules** — small interface, large hidden implementation
- **Pull complexity downward** — keep high-level code simple and declarative
- **Eliminate special cases** — generalise instead of branching, normalise inputs early
- **Information hiding** — expose *what*, not *how*
- **Reject cross-module reasoning** — if understanding requires reading multiple modules, redesign
- **Strategic over tactical** — invest in design, not quick fixes
- **Naming as compression** — names should reduce cognitive load, not add to it

## RFC Template

```markdown
# [Topic] Refactoring RFC

## Problem

- Which modules are shallow and tightly coupled
- What integration risk exists in the seams
- Why this makes the codebase harder to navigate

## Proposed Interface

- Interface signature (types, methods, params)
- Usage example showing how callers use it
- What complexity it hides internally

## Dependency Strategy

Which category applies and how dependencies are handled.

## Testing Strategy

- New boundary tests to write
- Old tests to delete
- Test environment needs

## Implementation Recommendations

- What the module should own (responsibilities)
- What it should hide (implementation details)
- What it should expose (the interface contract)
- How callers should migrate to the new interface
```
