# Out-of-Scope Memory Reference

Use this reference when an enhancement request, product idea, or feature proposal may be rejected, deferred indefinitely, or intentionally excluded from the project. The goal is to avoid repeatedly re-litigating the same decision while still allowing future reconsideration when context changes.

## Core Rule

Only create or update `.out-of-scope/` after Jane approves the `wontfix` or out-of-scope decision. Do not create out-of-scope memory for bugs. A bug can be invalid, duplicate, or not reproducible, but it is not an out-of-scope enhancement.

## When To Check `.out-of-scope/`

Check existing out-of-scope memory when:

- Triage receives an enhancement request.
- A request sounds familiar or previously rejected.
- A new issue conflicts with the current product direction.
- The user asks why a feature is not being built.
- An agent wants to reopen a rejected idea.

## When To Create A Record

Create a record only when all are true:

1. The request is an enhancement, not a bug.
2. Triage recommends `wontfix` or explicit out-of-scope.
3. The reasoning is durable enough to help future agents.
4. Jane approves the tracker action and memory record.

## Durable Versus Temporary Reasons

| Reason Type | Good For Out-of-Scope Memory? | Example |
| --- | --- | --- |
| Strategic mismatch | Yes | The product intentionally serves solo users, not enterprise teams. |
| Security or privacy constraint | Yes | The feature would require storing sensitive data the product will not store. |
| Business model mismatch | Yes | The request belongs in paid consulting, not the software product. |
| Technical impossibility for chosen architecture | Usually | The architecture intentionally avoids background workers. |
| Lack of time this week | No | This is backlog priority, not out-of-scope. |
| Not enough information | No | Use `needs-info` or `needs-expert-input`. |
| Reporter unclear | No | Ask a better question first. |

## File Naming

Use clear, stable names:

```text
.out-of-scope/<short-concept-name>.md
```

Examples:

```text
.out-of-scope/native-mobile-app.md
.out-of-scope/multi-tenant-admin-console.md
.out-of-scope/ai-autoposting-without-approval.md
```

## Out-of-Scope Record Template

```markdown
# Out of Scope: [Concept]

## Decision

[One paragraph stating what will not be built.]

## Date

YYYY-MM-DD

## Source

- Issue: [ID/link]
- Requester: [user/reporter if relevant]
- Triage decision: [link or summary]

## Why This Is Out Of Scope

[Durable reasoning. Focus on product direction, risk, architecture, compliance, or strategy.]

## What Is Still Allowed

- [Related smaller or safer feature]
- [Alternative approach]

## What Would Change This Decision

[Conditions that would justify revisiting the decision.]

## Related Issues

- [ID/link]
```

## Tracker Comment Template

Use this after Jane approves closing or labeling the issue:

```markdown
Thanks for the suggestion. We are marking this as out of scope for now because [durable reason].

This does not mean the underlying need is unimportant. It means this project will not solve it in this form. A future reconsideration would require [condition].
```

## Reconsideration Process

If a future issue matches an out-of-scope record, do not automatically close it. Compare what has changed:

1. Has the user segment changed?
2. Has the business model changed?
3. Has the architecture changed?
4. Has a domain expert reversed a prior constraint?
5. Has Jane explicitly asked to reopen the direction?

If nothing materially changed, recommend closing as duplicate/out-of-scope and cite the existing record. If context changed, recommend reopening the decision and route to `grill-me`, `to-prd`, or `prototype` depending on uncertainty.

## Do Not Misuse Out-of-Scope Memory

Do not use `.out-of-scope/` as a backlog, parking lot, TODO list, or excuse to avoid hard questions. If the answer is "not now," use backlog priority. If the answer is "we do not know," use `needs-info`, `research`, or `needs-expert-input`. If the answer is "we intentionally will not do this," then out-of-scope memory is appropriate.
