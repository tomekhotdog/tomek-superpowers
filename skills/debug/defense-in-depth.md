# Defense-in-Depth Validation

## Overview

When you fix a bug caused by invalid data, adding validation at one place feels sufficient. But that single check can be bypassed by different code paths, refactoring, or mocks.

**Core principle:** Validate at EVERY layer data passes through. Make the bug structurally impossible.

## The Four Layers

### Layer 1: Entry Point Validation
Reject obviously invalid input at API boundary.

### Layer 2: Business Logic Validation
Ensure data makes sense for this specific operation.

### Layer 3: Environment Guards
Prevent dangerous operations in specific contexts (e.g., refuse destructive operations outside test temp directories during tests).

### Layer 4: Debug Instrumentation
Capture context for forensics — log before dangerous operations, include stack traces.

## Applying the Pattern

When you find a bug:
1. **Trace the data flow** — where does bad value originate? Where is it used?
2. **Map all checkpoints** — list every point data passes through
3. **Add validation at each layer** — entry, business, environment, debug
4. **Test each layer** — try to bypass layer 1, verify layer 2 catches it

Don't stop at one validation point. Add checks at every layer.
