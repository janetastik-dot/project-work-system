# Agent Briefs Reference

Use this reference when triage recommends `ready-for-agent`, `ready-for-human`, or a post-TDD review handoff. The purpose is to make delegated work safe, bounded, and understandable without requiring the next agent or human to reconstruct the full conversation.

## Briefing Principle

A good brief describes the **desired behavior and boundaries**, not every implementation step. It should give enough context for autonomous work while preventing scope creep, hidden assumptions, and silent domain-rule invention.

## When To Write A Brief

Write or update a brief when:

- An issue is safe to delegate to an AFK agent.
- A human reviewer needs a concise review target.
- Step 4 `tdd` has produced an implementation handoff.
- Work is blocked and must be transferred to a domain expert or Jane.
- A tracker comment would otherwise become too long or too fragile.

Do not write a brief when the issue is still vague, lacks acceptance criteria, or needs expert input before safe action.

## Standard Agent Brief Template

```markdown
# Agent Brief: [Issue Title]

## Source

- Issue: [ID/link]
- Source step: Step 3 `to-issues` / Step 4 `tdd` / Step 5 `triage`
- Related PRD/spec: [link or none]
- Current recommended state: [state]

## Goal

[One paragraph describing the outcome that must be true when the work is done.]

## User Value

[Why this matters to the user or project.]

## Scope

In scope:
- [specific behavior or artifact]
- [specific behavior or artifact]

Out of scope:
- [boundary]
- [boundary]

## Acceptance Criteria

- [observable criterion]
- [observable criterion]
- [observable criterion]

## Test / Verification Plan

- [command, test type, or manual check]
- [command, test type, or manual check]

## Domain Expert Status

- Expert input needed: yes/no
- Expert type: [if needed]
- Exact question: [if needed]
- Safe temporary assumption: [if approved]

## Important Context

[Relevant constraints, dependencies, business rules, or codebase notes.]

## Risks And Watchouts

- [risk]
- [risk]

## Done Means

[Clear final condition that lets triage or a reviewer close or move the issue.]
```

## Post-TDD Review Brief Template

Use this when Step 4 `tdd` has already produced a handoff and triage is deciding whether the issue is `ready-for-review`, `needs-fix`, or `needs-expert-input`.

```markdown
# Post-TDD Review Brief: [Issue Title]

## Source

- Issue: [ID/link]
- TDD handoff: [link or summary]
- Recommended state: [ready-for-review / needs-fix / needs-expert-input]

## What Changed

[Short implementation summary.]

## Acceptance Criteria Check

| Criterion | Status | Evidence |
| --- | --- | --- |
| [criterion] | met/not met/unclear | [test, file, or explanation] |

## Tests And Verification

- Tests added/updated: [summary]
- Commands run: [commands]
- Result: pass/fail/not run
- Manual checks: [summary]

## Remaining Questions

- [question or none]

## Triage Recommendation

[Explain whether this should move to review, return to TDD, or wait for expert input.]
```

## Human Reviewer Brief Template

Use this when the issue requires human review, access, approval, or manual operation.

```markdown
# Human Reviewer Brief: [Issue Title]

## Decision Needed

[The exact decision or action needed from the human.]

## Background

[Short context.]

## Options

1. [Option A with consequence]
2. [Option B with consequence]
3. [Option C with consequence]

## Recommendation

[Recommended option and why.]

## Evidence

- [evidence]
- [evidence]

## If Approved

[What the agent should do next.]
```

## Domain Expert Brief Template

Use this when triage routes an issue to `needs-expert-input`.

```markdown
# Domain Expert Brief: [Issue Title]

## Question

[Exact missing rule or judgment.]

## Why It Matters

[How the answer affects product behavior, tests, scope, or risk.]

## Current Assumption

[Assumption, if any. Mark whether Jane approved it.]

## Options Observed

- [Option A]
- [Option B]

## Needed Answer Format

[Example of what answer would unblock the issue.]

## Blocks Progress

yes/no
```

## Brief Quality Checklist

Before attaching or posting a brief, verify that it:

1. Names the issue and source step.
2. States the desired behavior in business/user terms.
3. Includes acceptance criteria and verification.
4. States what is out of scope.
5. Marks expert input as resolved, needed, or not needed.
6. Identifies risks and dependencies.
7. Avoids brittle implementation-only instructions.
8. Avoids asking the next agent to infer missing domain rules.

## Anti-Patterns

Avoid these common failures:

- Writing a brief that only says "implement this" without acceptance criteria.
- Copying a full conversation instead of summarizing decisions.
- Hiding unresolved expert questions inside implementation notes.
- Delegating a broad PRD as one issue.
- Using `ready-for-agent` when credentials, user approval, or sensitive actions are required.
- Giving line-number-specific instructions when the file may change before the agent starts.
