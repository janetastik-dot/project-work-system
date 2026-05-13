# Project Work System Skills

This folder contains Jane's project workflow skills in execution order.

## Skills

- `01-grill-me` starts the project by stress-testing the idea, clarifying assumptions, and creating shared understanding.
- `02-to-prd` turns that shared understanding into a structured PRD ready for later issue breakdown.
- `03-to-issues` turns an approved PRD, plan, spec, or current context into independently grabbable tracer-bullet issues with TDD readiness and triage handoff notes.
- `04-tdd` builds one approved issue at a time through behavior-first red-green-refactor cycles, surfaces domain expert gaps, and hands the completed issue to triage.

## Full intended sequence

Future workflow steps should follow the same numbered naming pattern:

- `05-triage`
- `06-prototype`
- `07-zoom-out`

## Handoff logic

The current chain is:

```text
01-grill-me → 02-to-prd → 03-to-issues → 04-tdd
```

Step 3 prepares work for Step 4 `tdd` by defining independently testable issues. Step 4 implements one issue at a time and produces evidence for Step 5 `triage`. Step 5 decides final execution readiness, owner, priority, state, and route.
