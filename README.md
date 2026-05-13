# Project Work System

This repository groups Jane's reusable project workflow skills into one place.

The system is designed to help a user and an AI agent work in the same language, with clear structure, visible assumptions, and a repeatable handoff between project stages. It also gives the workflow a safe way to ask domain experts for input when the team does not know enough yet.

## Current workflow modules

- `project-work-system/01-grill-me/SKILL.md` — Step 1. Stress-test and clarify a new project, task, idea, plan, or workflow until shared understanding exists.
- `project-work-system/02-to-prd/SKILL.md` — Step 2. Convert the clarified context into a PRD that can later be broken into implementation issues.
- `project-work-system/03-to-issues/SKILL.md` — Step 3. Break an approved PRD, plan, spec, or project context into independently grabbable tracer-bullet issues.

## Intended full workflow

- Step 1: `grill-me` — Drill down, stress-test, and align the idea.
- Step 2: `to-prd` — Turn the current context into a PRD.
- Step 3: `to-issues` — Break the PRD into independently grabbable tracer-bullet issues.
- Step 4: `tdd` — Build with a red-green-refactor loop.
- Step 5: `triage` — Move issues through a role-based state machine.
- Step 6: `prototype` — Build a throwaway prototype to test design decisions.
- Step 7: `zoom-out` — Review the bigger picture before looping into the next development phase.

## Structure

```text
project-work-system/
└── project-work-system/
    ├── 01-grill-me/
    │   └── SKILL.md
    ├── 02-to-prd/
    │   └── SKILL.md
    └── 03-to-issues/
        └── SKILL.md
```

## Notes

- Each workflow module keeps its own `SKILL.md` so it can still be reused independently.
- The numbered folders preserve the intended order of the workflow.
- `to-issues` prepares implementation issues for Step 4 `tdd`, but final readiness and AFK execution decisions belong to Step 5 `triage`.
- Future skills can be added as `04-tdd`, `05-triage`, `06-prototype`, and `07-zoom-out`.
