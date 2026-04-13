# When to Mock

Mock at **system boundaries** only:

- External APIs (payment, email, etc.)
- Databases (sometimes — prefer test DB)
- Time/randomness
- File system (sometimes)

Do not mock:

- Your own classes/modules
- Internal collaborators
- Anything you control

## Designing for Mockability

**1. Use dependency injection** — pass external dependencies in, don't create them internally.

**2. Prefer SDK-style interfaces** — specific functions per operation, not one generic fetcher with conditional logic.

The SDK approach means:
- Each mock returns one specific shape
- No conditional logic in test setup
- Type safety per endpoint
