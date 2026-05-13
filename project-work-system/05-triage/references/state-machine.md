# Triage State Machine Reference

Use this reference when mapping project labels, resolving workflow conflicts, or explaining why an issue should move from one state to another.

## State Machine Purpose

The triage state machine exists to keep Jane, the AI agent, human reviewers, and domain experts speaking the same operational language. It separates three decisions that are often mixed together: **what the issue is**, **whether it is ready**, and **who should act next**.

## Canonical Fields

| Field | Purpose | Example Values |
| --- | --- | --- |
| Category | What kind of work this is | `bug`, `enhancement`, `research`, `expert-input`, `prototype`, `operations` |
| State | Current readiness stage | `needs-triage`, `ready-for-tdd`, `needs-fix`, `ready-for-review` |
| Priority | Relative urgency or value | `high`, `medium`, `low` |
| Owner Route | Who or what should act next | `AFK agent`, `Jane`, `domain expert`, `prototype`, `zoom-out`, `TDD` |
| Expert Status | Whether specialist input is required | `not-needed`, `needed-blocking`, `needed-non-blocking`, `resolved` |

## Canonical States

| State | Meaning | Typical Next Step |
| --- | --- | --- |
| `needs-triage` | The issue has not been evaluated. | Intake triage. |
| `needs-info` | A reporter, user, or maintainer must answer concrete questions. | Ask targeted questions. |
| `needs-expert-input` | A domain expert must provide rules, constraints, or judgment. | Ask exact expert question. |
| `ready-for-tdd` | The issue is clear, bounded, and testable. | Step 4 `tdd`. |
| `in-tdd` | The issue is actively being implemented with red-green-refactor. | Continue Step 4. |
| `needs-fix` | Work was attempted but does not yet satisfy acceptance criteria. | Return to Step 4 or assign fix. |
| `ready-for-review` | The implementation appears complete and needs reviewer approval. | Human or automated review. |
| `ready-for-agent` | The work can safely be delegated with a durable brief. | Create or update agent brief. |
| `ready-for-human` | Human judgment, access, approval, or manual operation is required. | Human action. |
| `ready-for-prototype` | The right answer is unclear without throwaway exploration. | Step 6 `prototype`. |
| `wontfix` | The project intentionally will not act on this request. | Close with reasoning, optionally record out-of-scope memory. |

## Category Rules

| Category | Use When | Do Not Use When |
| --- | --- | --- |
| `bug` | Existing promised behavior is broken, wrong, or failing. | The request is actually a new capability. |
| `enhancement` | The user wants new or improved capability. | A current behavior is broken. |
| `research` | The team needs investigation before deciding scope. | A domain expert answer alone would unblock it. |
| `expert-input` | Specialist judgment is the main blocker. | The missing answer is merely project preference and Jane can decide. |
| `prototype` | A throwaway model, CLI, or UI variation should be tried first. | The issue is already clear enough for TDD. |
| `operations` | Workflow, tracker, release, documentation, maintenance, or coordination work. | The issue changes product behavior. |

## Priority Guidance

Priority is not the same as implementation order. Priority should express consequence and leverage.

| Priority | Use When | Examples |
| --- | --- | --- |
| `high` | Blocks project progress, causes visible failure, risks correctness, or prevents user validation. | Broken core flow, security/privacy issue, unresolved domain rule blocking launch. |
| `medium` | Important but not immediately blocking. | Valuable enhancement, test coverage improvement, UX friction. |
| `low` | Nice-to-have, cleanup, minor docs, or speculative improvement. | Cosmetic adjustment, non-blocking refactor, future idea. |

## Allowed Transitions

| From | To | Condition |
| --- | --- | --- |
| `needs-triage` | `needs-info` | Missing reporter/user detail. |
| `needs-triage` | `needs-expert-input` | Domain correctness is uncertain. |
| `needs-triage` | `ready-for-tdd` | Issue is bounded, testable, and safe. |
| `needs-triage` | `ready-for-prototype` | Need throwaway exploration before build. |
| `needs-triage` | `wontfix` | Request is intentionally rejected with durable reasoning. |
| `ready-for-tdd` | `in-tdd` | Step 4 implementation begins. |
| `in-tdd` | `needs-fix` | Tests fail, acceptance criteria missing, or implementation incomplete. |
| `in-tdd` | `needs-expert-input` | TDD exposes unresolved domain rules. |
| `in-tdd` | `ready-for-review` | Tests pass and acceptance criteria are met. |
| `ready-for-review` | `needs-fix` | Reviewer finds a gap. |
| `ready-for-review` | closed/done | Reviewer approves. |
| Any active state | `ready-for-human` | Human access, approval, or judgment is required. |
| Any active state | `ready-for-agent` | Work is safe to delegate with a durable brief. |

## Conflict Handling

If labels conflict, preserve the issue and ask before changing the tracker. Examples of conflicts include:

- `ready-for-tdd` and `needs-info` at the same time.
- `ready-for-review` with failing tests.
- `wontfix` with an active implementation route.
- `ready-for-agent` without a brief or enough acceptance criteria.

Use this conflict note:

```markdown
I found conflicting states: [state A] and [state B].
I recommend resolving to: [recommended state].
Reason: [evidence].
Approve this label/state cleanup?
```

## Handoff Rules Between Jane's Steps

| Current Finding | Route To | Reason |
| --- | --- | --- |
| Idea still unclear | Step 1 `grill-me` | Stress-test goal and assumptions. |
| Work is too broad | Step 2 `to-prd` | Needs product-level definition. |
| Work is defined but too large | Step 3 `to-issues` | Needs vertical slicing. |
| Issue is buildable and testable | Step 4 `tdd` | Ready for red-green-refactor. |
| Issue has been implemented | Step 5 `triage` | Needs readiness/review/routing decision. |
| Design or state logic is uncertain | Step 6 `prototype` | Explore before committing. |
| Context is too narrow or confusing | Step 7 `zoom-out` | Need broader system understanding. |

## Closing Standard

A triage decision is complete when a future agent or human can answer these questions without reading the whole conversation:

1. What is this issue?
2. Why is it in this state?
3. What evidence was checked?
4. What is blocking it, if anything?
5. Who should act next?
6. What exact next action should they take?
