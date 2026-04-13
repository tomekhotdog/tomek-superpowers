# Root Cause Tracing

## Overview

Bugs often manifest deep in the call stack. Your instinct is to fix where the error appears, but that's treating a symptom.

**Core principle:** Trace backward through the call chain until you find the original trigger, then fix at the source.

## The Tracing Process

### 1. Observe the Symptom
Note the error message, location, and context.

### 2. Find Immediate Cause
What code directly causes this?

### 3. Ask: What Called This?
Trace one level up. What passed the bad value?

### 4. Keep Tracing Up
Continue until you find where the bad value originates.

### 5. Find Original Trigger
What is the root — the first place the bad value was created or the correct value was lost?

## Adding Stack Traces

When you can't trace manually, add instrumentation:

```typescript
// Before the problematic operation
const stack = new Error().stack;
console.error('DEBUG operation:', {
  param,
  cwd: process.cwd(),
  stack,
});
```

**Use `console.error()` in tests** — loggers may be suppressed.

## Key Principle

**NEVER fix just where the error appears.** Trace back to find the original trigger.

After fixing at source, add defense-in-depth validation at each layer (see `defense-in-depth.md`).
