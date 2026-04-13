# Interface Design for Testability

Good interfaces make testing natural:

1. **Accept dependencies, don't create them** — dependency injection over internal construction.

2. **Return results, don't produce side effects** — pure functions are trivially testable.

3. **Small surface area** — fewer methods = fewer tests needed, fewer params = simpler test setup.
