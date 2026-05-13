---
name: grill-me
description: Project intake and relentless design-review interview skill. Use when opening a new chat with Jane, when the user says “grill me”, asks to stress-test a plan/design, starts a new project, creates a PRD, business plan, website/app, workflow, content system, research plan, or any task where ambiguity, dependency, assumptions, scope, risks, or success criteria must be resolved before execution.
---

# Grill Me

Use this skill to control the beginning of a project, stress-test a plan, and interview the user until there is shared understanding. The goal is to make the work clear enough that the assistant can execute it as if Jane had done it herself.

## Opening Rule

When starting a new chat with Jane, use this exact opener before deep planning unless the user has already chosen a level:

> Jane, Its /Grill me time. pick what level 1/2/3/4/5 you want and reply me with the number of level you want to be grilled with

If Jane gives a task without choosing a level, briefly assess complexity. For small, clear tasks, ask only 1–3 essential questions. For larger, risky, or ambiguous tasks, recommend a level and ask Jane to confirm before full grilling.

## Grill Levels

Level 1 = ละเอียด. Use for quick alignment. Confirm goal, scope, key risk, deliverable, and next action.

Level 2 = ละเอียดปานกลาง. Add user/customer, measurable result, constraints, available assets, and start requirements.

Level 3 = ละเอียดมาก. Cover the main decision tree: goal, user, problem, success metrics, scope, constraints, assets, risks, assumptions, delivery format, and verification.

Level 4 = ละเอียดมากมาก. Walk important branches, resolve dependencies between decisions, expose trade-offs, and maintain an assumption/risk log.

Level 5 = ละเอียดระดับเซลล์ เจาะทุกรูคุมขนไม่มีอะไรให้คลุมเคลือ. Investigate every unclear requirement, edge case, risk, dependency, evidence gap, and acceptance criterion before execution.

## Non-Negotiable Interview Rules

1. Ask only necessary questions. Before asking, check whether the answer already exists in the user’s previous response, attached files, project files, codebase, links, or visible context.
2. If a question can be answered by exploring the codebase or documents, explore first instead of asking.
3. Do not ask duplicate questions. If a previous answer partially resolves a later question, narrow the next question to the remaining gap only.
4. Use numbered questions in the format `Question 1`, `Question 2`, `Question 3`, continuing across rounds when useful.
5. For each question, include three parts: the question, the recommended answer, and the reason.
6. Ask in rounds. Do not dump the whole forest at once. After each answer, update the decision tree and ask the next unresolved branch.
7. When a problem, missing input, contradiction, or blocker appears, notify Jane immediately and ask for help. Do not assume, invent, or hide uncertainty.
8. Separate facts, assumptions, and recommendations. Make clear what was verified, what was inferred, and what is only a proposed direction.
9. Keep writing short, direct, and practical. Avoid oversized tables for question lists because important text may be hidden. Use paragraphs and numbered lists instead.
10. Recommend other relevant skills when they would improve quality, such as research, GTM, project management, web development, automation, LinkedIn, Excel, stock analysis, image/video generation, or other domain-specific skills. Explain why in one concise sentence.

## Default Decision Tree

Start with these branches unless the project context clearly requires a different order:

1. Goal: What outcome must exist when the task is done?
2. User or customer: Who is it for, and what do they care about?
3. Problem: What pain, opportunity, or decision is being solved?
4. Success metric: How will Jane know the result is correct, useful, or worth doing?
5. Scope: What is included, excluded, and intentionally postponed?
6. Constraints: What limits time, budget, tools, data, brand, legal, technical, or resources?
7. Assets: What files, code, examples, data, accounts, links, or prior decisions already exist?
8. Assumptions: What must be true for the plan to work?
9. Risks: What can fail, become inefficient, mislead users, or waste time?
10. Dependencies: Which decisions must be made before other decisions can be resolved?
11. Delivery format: What exact output should be delivered?
12. Verification: How will the result be checked for correctness and efficiency?

## Question Format

Use this format for the interview. Do not compress the questions into a table.

**Question 1: [Specific decision or missing information]**

**Recommended answer:** [Give a practical recommended answer. If the answer depends on context, give 2–3 options with trade-offs.]

**Reason:** [Explain why this decision matters and what downstream decisions depend on it.]

## When to Stop Grilling

Stop grilling and begin execution when these four conditions are met:

1. The goal is clear.
2. The deliverable is clear.
3. The key constraints and risks are known.
4. A double-check plan exists.

If some uncertainty remains but work can proceed, record it under `Open Questions/Risks` rather than asking forever.

## Final Shared Understanding Format

At the end of the grill phase, summarize briefly using this structure:

## Shared Understanding

State the agreed project goal, target user, deliverable, and success standard in one short paragraph.

## Decisions Made

List the confirmed decisions that will guide execution.

## Open Questions/Risks

List only unresolved items that matter. For each one, state whether it blocks work or can be monitored later.

## Double-check Plan

Check the result against five standards: correctness to the goal, requirement completeness, feasibility with time/resources, efficiency of method, and measurable verification after delivery.

## Handoff to Execution

After the shared understanding is confirmed, proceed with the task plan. If another skill should be used, recommend it before execution and explain why.
