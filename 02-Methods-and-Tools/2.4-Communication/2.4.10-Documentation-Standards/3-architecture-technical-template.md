# Architecture / Technical Documentation Template

## Overview

Use this template when documenting how a system, service, or integration works. This is for the engineer who joins the team next month, the on-call responder at 2 AM, or the tech lead evaluating whether to build on top of your service.

Architecture docs are **living documents**. Unlike decision records (which are snapshots), these must reflect the current state of the system. That means they need an owner who updates them when the system changes.

**Language guidance:** Technical documentation should default to English. Code, API names, and system components are already in English. Writing the surrounding context in Danish creates unnecessary language switching. Metadata should always be in English.

---

## Architecture / Technical Documentation Template

```
---
title: [System/Service Name — Technical Overview]
doc-type: architecture
status: draft | review | current | archived
audience: [engineering | cross-team]
owner: [Name — the person who keeps this doc current]
created: [YYYY-MM-DD]
last-reviewed: [YYYY-MM-DD]
next-review: [YYYY-MM-DD — set 3-6 months out]
language: [en | da]
tags: [system name, domain, technology stack keywords]
---

# [System/Service Name] — Technical Overview

## Purpose

[What does this system/service do? Why does it exist? 2-3 sentences max.
Write for someone who has never heard of this system.

Example: "The Settlement Service calculates and distributes payments
to advisors based on completed consultations. It runs nightly,
processes ~15K transactions per batch, and feeds into the finance
reporting pipeline."]


## Context and Boundaries

[Where does this system sit in the broader architecture? What does it
own vs. what does it delegate to other systems?]

### System Boundary

[Define clearly what is IN scope and OUT of scope for this system.
What does it do? What does it explicitly NOT do?]

### Key Integrations

| System | Direction | Protocol | What it does |
|--------|-----------|----------|-------------|
| [System A] | Inbound | [REST/Events/DB] | [Brief description] |
| [System B] | Outbound | [REST/Events/DB] | [Brief description] |
| [System C] | Bidirectional | [Protocol] | [Brief description] |


## Architecture Overview

[High-level description of the architecture. If you have a diagram,
reference it here — but ALWAYS include a text description alongside it.
AI agents can't read diagrams; future engineers might not have access
to the diagramming tool.]

### Components

| Component | Responsibility | Technology |
|-----------|---------------|------------|
| [Component A] | [What it does] | [Tech stack] |
| [Component B] | [What it does] | [Tech stack] |
| [Component C] | [What it does] | [Tech stack] |

### Data Flow

[Describe how data moves through the system. Use a numbered sequence
when possible:

1. [Source] sends [what] via [how]
2. [Component A] processes [what] by [doing what]
3. [Component B] stores [what] in [where]
4. [Output] is sent to [destination] via [how]]


## Data Model

[Key entities, their relationships, and where they live.
You don't need to document every column — focus on the entities
and relationships that matter for understanding the system.]

### Key Entities

| Entity | Description | Storage | Retention |
|--------|------------|---------|-----------|
| [Entity A] | [What it represents] | [DB/Cache/File] | [How long kept] |
| [Entity B] | [What it represents] | [DB/Cache/File] | [How long kept] |


## Operational Context

### Infrastructure

[Where does this run? Cloud/on-prem? What environment(s)?
What are the deployment characteristics?]

### Monitoring and Alerting

[How do you know if this system is healthy? What alerts exist?
Where do you look when something goes wrong?]

### Performance Characteristics

[Rough numbers: throughput, latency, typical load.
Not exact benchmarks — just enough to set expectations.

Example: "Handles ~500 req/s at p95 < 200ms. Batch jobs process
~15K records in ~45 minutes. Peak load is Monday mornings."]


## Known Limitations and Technical Debt

[Be honest. What doesn't work well? What would you fix if you had
time? What workarounds exist?

This section is incredibly valuable for new team members — it saves
them from discovering these the hard way.]

- [Limitation 1: description and impact]
- [Limitation 2: description and impact]
- [Known debt: what it is, why it exists, rough effort to fix]


## Decision History

[Link to relevant Decision Records (DR-NNNN) that shaped this
system's architecture. Don't duplicate the reasoning — just
link and provide a one-line summary.]

| Decision | Summary | Link |
|----------|---------|------|
| [DR-NNNN] | [One-line summary] | [Link] |
| [DR-NNNN] | [One-line summary] | [Link] |


## Getting Started (for new team members)

[Quick pointers to get a new engineer productive:

- Where is the code? [repo link]
- How do you run it locally? [brief or link to setup guide]
- How do you deploy? [brief or link to deployment guide]
- Who should I talk to? [team/person]]


## Related Documents

- [Link to API documentation]
- [Link to runbooks / incident playbooks]
- [Link to related architecture docs]
- [Link to Confluence pages, Jira boards, etc.]
```

---

## Usage Notes

### Living Doc Maintenance

This is a living document. The deal is simple: **when you change the system, update the doc.** The `owner` in the metadata header is responsible for enforcing this.

Practical tips:
- Add "update architecture doc" as a checklist item in your PR template or definition of done
- Review the doc during sprint planning when the team picks up work in this system's area
- Set the `next-review` date 3-6 months out and actually review when it arrives

### On Diagrams

Diagrams are valuable but insufficient alone. Always pair a diagram with a text description that covers the same information. Reasons:

1. **AI agents can't read diagrams.** They can read text descriptions.
2. **Diagrams go stale.** Updating a Mermaid/draw.io diagram has higher friction than updating text.
3. **Accessibility.** Not everyone can view images in every context.

If you use Mermaid, Markdown-rendered diagrams, or ASCII art — those are better than image files because they're version-controlled, diff-able, and text-searchable.

### How Deep Should You Go?

Deep enough that a new engineer can understand the system without reading all the code. Not so deep that the doc becomes a line-by-line code walkthrough. The test: if an engineer reads this doc and then opens the codebase, do they have enough context to navigate it effectively?

### The "Known Limitations" Section Is NOT Optional

This is often the most valuable section in the entire doc. Every system has warts, tech debt, and workarounds. Documenting them openly:
- Saves new team members from costly surprises
- Creates visibility for prioritizing tech debt work
- Prevents the same problems from being rediscovered repeatedly

If this section is empty, either the system is perfect (unlikely) or the author skipped it (fix this).
