# Decision Record Template

## Overview

Use this template when a meaningful product or technical decision has been made and needs to be captured—the kind where someone will ask "why did we do it this way?" in 6 months.

Decision records are **snapshots**. They capture what was true and what was decided at a point in time. Don't update them when the world changes—create a new decision record that supersedes the old one.

**Language guidance:** Default to English. Use Danish only if the primary audience for this specific decision is exclusively Danish-speaking and will never need AI summarization or cross-referencing. Metadata should always be in English regardless of content language.

---

## Decision Record Template

```
---
title: [DR-NNNN: Clear, descriptive title of the decision]
doc-type: decision-record
status: draft | review | approved | current | superseded
audience: [product-team | engineering | leadership | cross-team]
owner: [Name]
created: [YYYY-MM-DD]
last-reviewed: [YYYY-MM-DD]
next-review: [N/A — decision records are snapshots, not living docs]
language: [en | da]
supersedes: [DR-NNNN or N/A]
superseded-by: [DR-NNNN or N/A]
tags: [relevant keywords]
---

# DR-NNNN: [Decision Title]

## Context

[What is the situation that requires a decision? What problem are we solving?
Include enough background that someone unfamiliar with the project can
understand why this decision matters.

Be specific: which system, which team, which users, what timeframe.
Reference related docs by linking, not duplicating.]


## Decision

[State the decision clearly in 1-3 sentences. Be direct.

Example: "We will use PostgreSQL as the primary data store for the
payments service, accessed through a shared data access layer."]


## Alternatives Considered

### Alternative A: [Name]

[Brief description]

- **Pros:** [What's good about this option]
- **Cons:** [What's problematic]
- **Why rejected:** [Specific reason this wasn't chosen]

### Alternative B: [Name]

[Brief description]

- **Pros:** [What's good about this option]
- **Cons:** [What's problematic]
- **Why rejected:** [Specific reason this wasn't chosen]

[Add more alternatives as needed. If you only considered one option,
that's a red flag — go back and identify at least one real alternative.]


## Rationale

[Why this decision over the alternatives. What were the decisive factors?
What constraints shaped the choice? What tradeoffs are we accepting?

This is the most important section. "We chose A because B" is not enough.
Explain the REASONING, not just the conclusion.]


## Consequences

### Expected Outcomes
[What do we expect to happen as a result of this decision?
Be specific enough that you could check in 6 months and say
"this played out as expected" or "this didn't."]

### Risks and Tradeoffs
[What are we giving up? What could go wrong? What are we betting on?
Be honest — every decision has downsides.]

### Dependencies
[What does this decision depend on? What other decisions does it affect?]


## Stakeholders

| Role | Name | Input / Sign-off |
|------|------|-------------------|
| Decision maker | [Name] | [Approved / Pending] |
| Consulted | [Name(s)] | [Input received] |
| Informed | [Name(s)] | [Notified] |


## Related Documents

- [Link to relevant PRD, one-pager, architecture doc, previous DR, etc.]
- [Link to Confluence page, Jira epic, or other external reference]
```

---

## How to Use This Template

### Numbering Convention

Use `DR-NNNN` (Decision Record + sequential number) as the identifier. This makes decision records searchable and referenceable. Example: `DR-0001`, `DR-0042`.

If your team prefers a different prefix (e.g., `ADR-` for Architecture Decision Records), that's fine — just be consistent.

### When to Create a New DR vs. Update an Old One

**Create a new DR when:**
- A previous decision is being reversed or significantly changed
- New information fundamentally changes the rationale
- A new constraint or requirement makes the old decision invalid

**Never do:**
- Edit the "Decision" or "Rationale" of an existing DR after it's been approved
- Delete an old DR because the decision changed

**Instead:** Create a new DR, set the old one's status to `superseded`, and fill in the `superseded-by` field with the new DR's number.

### How Detailed Should Alternatives Be?

Detailed enough that a reader can understand WHY they were rejected. One sentence per alternative is too little. A full page per alternative is too much. 3-5 bullet points covering pros, cons, and rejection reason is the sweet spot.

### When You Only Considered One Option

If there are no alternatives in your decision record, either:
- You didn't consider alternatives (bad — go back and think about this)
- There genuinely was only one viable option (rare, but it happens — document why)

Either way, the absence of alternatives is worth noting.
