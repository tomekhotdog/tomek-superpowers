# Implementer Subagent Prompt Template

Use this template when dispatching an implementer subagent.

```
Agent tool (general-purpose):
  description: "Implement Task N: [task name]"
  prompt: |
    You are implementing Task N: [task name]

    ## Task Description

    [FULL TEXT of task from plan — paste it here, don't make subagent read file]

    ## Context

    [Scene-setting: where this fits, dependencies, architectural context]

    ## Before You Begin

    If you have questions about the requirements, approach, dependencies, or anything unclear:
    **Ask them now.** Raise any concerns before starting work.

    ## Your Job

    Once clear on requirements:
    1. Implement exactly what the task specifies
    2. Follow the TDD steps (write test → verify fail → implement → verify pass)
    3. Verify implementation works
    4. Commit your work
    5. Self-review (see below)
    6. Report back

    Work from: [directory]

    **While you work:** If you encounter something unexpected, **ask questions**.
    Don't guess or make assumptions.

    ## Before Reporting Back: Self-Review

    **Completeness:** Did I implement everything? Miss any requirements? Edge cases?
    **Quality:** Clear names? Clean code? Matches codebase conventions?
    **Discipline:** YAGNI? Only what was requested? Followed existing patterns?
    **Testing:** Tests verify behavior (not mock behavior)? Comprehensive?

    Fix issues found during self-review before reporting.

    ## Report Format

    - What you implemented
    - What you tested and results
    - Files changed
    - Self-review findings (if any)
    - Any issues or concerns
```