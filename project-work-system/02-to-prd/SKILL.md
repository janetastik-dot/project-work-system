---
name: to-prd
description: Convert the current project conversation, grill-me output, files, links, and codebase context into a clear Product Requirements Document (PRD). Use when the user wants to turn an explored idea, plan, specification, workflow, product concept, feature request, or task context into a PRD that can later be broken into implementation issues.
---

# To PRD

Use this skill as Step 2 in Jane's project workflow. It turns the current context into a PRD after the idea has been clarified or stress-tested. The goal is to create a shared source of truth that the next step, `to-issues`, can convert into independently grabbable implementation issues.

## Core Rule

Do not re-interview the user. Synthesize what is already known from the conversation, `grill-me` output, attached files, project files, repo/codebase, links, domain notes, and prior decisions.

Ask Jane only when there is a real blocker that prevents a useful PRD from being written. If asking is unavoidable, ask no more than 1–3 short numbered questions. For each question, include a recommended answer and reason.

## Required Inputs to Check First

Before writing the PRD, check for these inputs in the current context and available materials:

1. `grill-me` handoff, especially Shared Understanding, Decisions Made, Open Questions/Risks, and Double-check Plan.
2. User goals, target users, problem, constraints, assets, risks, assumptions, and success standard.
3. Existing project files, codebase, repo structure, domain glossary, architecture notes, ADRs, examples, or prior PRDs, when available.
4. Issue tracker conventions, labels, status vocabulary, and publishing target, when available.
5. Domain expert notes or requested expert inputs, when the project requires knowledge the agent should not invent.

If a repo or codebase exists, inspect it enough to understand the current state before writing implementation-facing sections. If no repo exists, write the PRD at the product/workflow level and avoid pretending technical details are known.

## PRD Creation Process

1. Identify the source context used to create the PRD. Separate verified facts, inferred assumptions, and recommendations.
2. Preserve Jane's vocabulary and the project's domain language. If the project has a glossary, use it consistently.
3. Convert uncertainty into `Assumptions`, `Open Questions`, or `Domain Expert Inputs Needed`; do not hide gaps inside confident prose.
4. Define the goal, users, problem, success metrics, scope, acceptance criteria, and validation approach clearly enough that another agent or developer can execute from it.
5. Describe components, workstreams, or modules that may need to be created or changed. Use `components/workstreams/modules` instead of only `modules` so the PRD works for software, business, content, automation, app, website, and workflow projects.
6. Look for deep modules or clean work units when relevant: parts that encapsulate meaningful functionality behind a simple, testable interface.
7. Avoid specific file paths and code snippets in the PRD because they become stale quickly. Exception: include a short prototype-derived snippet only if it captures a decision more precisely than prose, such as a state machine, reducer, schema, or type shape.
8. Create the PRD as a draft first unless Jane explicitly asked to publish and the issue tracker target is known.
9. If publishing is requested and safe, ask for a short approval before creating or updating tracker items. Use the project's label conventions if available. If no convention exists, suggest labels such as `prd`, `ready-for-issues`, or `needs-triage`; do not force `ready-for-agent` or skip the later `triage` step.
10. End with a Double-check Plan and a handoff note to Step 3: `to-issues`.

## PRD Template

Use this template unless the project context clearly requires a different structure.

```markdown
# PRD: [Clear Project or Feature Name]

## 1. Context Source

State what this PRD is based on: conversation context, grill-me output, attached files, repo/codebase review, links, domain notes, prior decisions, or expert input. Note any important source that was unavailable.

## 2. Problem Statement

Describe the problem from the user's or customer's perspective. Explain why it matters now and what pain, opportunity, or decision this PRD addresses.

## 3. Goal and Success Metrics

State the desired outcome in plain language. Include measurable or observable success criteria where possible.

## 4. Target Users / Actors

Identify who will use the result, who will be affected by it, and what each actor cares about.

## 5. Solution Overview

Describe the proposed solution from the user's perspective. Keep this section clear enough for non-technical stakeholders.

## 6. Scope

### In Scope

List what this PRD includes.

### Out of Scope

List what this PRD intentionally excludes.

### Later / Future Phase

List useful ideas that should be postponed rather than mixed into the current build.

## 7. User Stories

Use a long numbered list. Each story should follow this format:

1. As a [actor], I want [feature or capability], so that [benefit].

Cover the main happy paths, important edge cases, admin/operator needs, and downstream handoffs.

## 8. Acceptance Criteria

Write testable criteria that define when the work is done. Prefer observable behavior over internal implementation details.

## 9. Components / Workstreams / Modules

Describe the main parts that need to be created, modified, researched, or coordinated. For each part, state its responsibility and whether it should be testable in isolation.

## 10. Implementation Decisions

List decisions already made about architecture, workflow, schema, APIs, integrations, data flow, permissions, content model, UX behavior, or operating process. Do not include fragile file paths unless unavoidable.

## 11. Testing and Validation Decisions

Describe how the result should be checked. Include what makes a good test, which components/workstreams/modules need tests or validation, and any similar prior tests or examples in the project.

## 12. Known Facts

List facts verified from the conversation, files, codebase, links, or expert notes.

## 13. Assumptions

List assumptions that are reasonable enough to proceed with. Mark assumptions that could materially change the plan if wrong.

## 14. Open Questions / Domain Expert Inputs Needed

List unresolved questions. For each item, state whether it blocks work, who should answer it, and what kind of input is needed. Use this section when a domain expert should advise instead of letting the agent guess.

## 15. Risks and Constraints

List key risks, constraints, dependencies, and trade-offs. Include mitigation ideas where useful.

## 16. Handoff to Step 3: to-issues

Summarize how this PRD should be broken into issues next. Identify the first tracer-bullet vertical slice, likely follow-up slices, and any issue tracker labels or workflow rules to apply.

## 17. Double-check Plan

Check the PRD against these five standards:

1. Correctness to the goal.
2. Requirement completeness.
3. Feasibility with available time, resources, tools, and knowledge.
4. Efficiency of the proposed method.
5. Measurable verification after delivery.
```

## Publishing Rules

Only publish the PRD to a project issue tracker when all of these are true:

1. Jane explicitly asked to publish or approved publishing.
2. The issue tracker target is known.
3. The tracker label/status conventions are known or Jane approved the suggested labels.
4. The content does not include private or sensitive information that should stay out of the tracker.

If any condition is missing, deliver the PRD draft and state what is needed before publishing.

## Question Format for Blockers Only

Use this format only when a blocker prevents a useful PRD.

**Question 1: [Specific missing decision]**

**Recommended answer:** [Practical recommendation or 2–3 options with trade-offs.]

**Reason:** [Why this decision matters and what downstream work depends on it.]

## Final Response Format

When the PRD is ready, provide:

1. A short summary of what was created.
2. The PRD draft or attached PRD file.
3. Any blocker, open question, or domain expert input needed.
4. Whether the PRD is ready for Step 3: `to-issues`.
5. The Double-check Plan result.

Keep the response concise and direct. Do not move to Step 3 until Jane approves the PRD or asks to continue.
