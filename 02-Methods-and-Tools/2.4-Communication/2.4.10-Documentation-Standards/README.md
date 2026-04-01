# Documentation Standards Framework

Documentation is not one thing. A how-to guide for a helpdesk agent, an architecture decision record for engineering, and a product decision rationale for Confluence are three fundamentally different products serving different audiences with different jobs-to-be-done. Most teams treat "documentation" as a monolith, which is exactly why it goes stale, nobody reads it, and AI tools can't make sense of it.

This framework helps you recognize the different types of documentation, choose the right one, and produce docs that are useful for both humans today AND AI agents tomorrow.

## Files

- `1-documentation-standards-framework.md` — Full framework: documentation taxonomy, AI-readiness principles, language guidance, structured metadata, and the "For Agents" section
- `2-decision-record-template.md` — Template for capturing product and technical decisions (why we chose X, what alternatives we considered, what we expect to happen)
- `3-architecture-technical-template.md` — Template for documenting how systems work, component relationships, data flows, and technical context
- `4-documentation-standards-evaluation.md` — Evaluation framework for assessing documentation quality (freshness, findability, audience fit, AI-readiness)

## Before Using This Framework

⚠️ **Don't jump straight to writing docs.**

### 1. Read the Golden Rule

See: [`/PRODUCT-SENSE-RULES.md`](../../../PRODUCT-SENSE-RULES.md)

### 2. Think First (5–10 min)

Use the prompts: [`2-product-sense-prompts.md`](../../2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/2-product-sense-prompts.md) — "Always-Ask Core Prompts" and the situation-specific sections.
Or start from the entry point: [`0-start-here-product-thinking.md`](../../2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md).

Before you write, answer these questions honestly:

- **Who is going to READ this?** (Be specific — "the team" is not an audience.)
- **What job is this doc doing for them?** (Finding an answer? Understanding a decision? Onboarding?)
- **Where will they look for it?** (Confluence? A repo? A helpdesk KB? Slack search?)
- **What happens when this information changes?** (Who updates it? When?)
- **Should an AI agent be able to find and use this?** (Not everything needs to be AI-optimized.)

**Documentation structures the knowledge — it doesn't create it.** If you don't have clarity on what you're capturing, no template will save you.

### 3. Then Use the Templates

After you've answered the questions above, pick the right template based on your documentation type (see taxonomy in `1-documentation-standards-framework.md`).

---

## How to Use This Framework

### Step 1: Identify the Documentation Type

Read the taxonomy in `1-documentation-standards-framework.md` → **Documentation Taxonomy**. Name the type of doc you're creating. If you can't name it, you haven't thought it through.

### Step 2: Choose the Right Template

Use the template that matches your doc type. This framework ships with Decision Record and Architecture/Technical. Other types (how-to, troubleshooting, onboarding, runbook) can use the same structural principles — metadata header, clear audience, plain language — adapted to their purpose.

### Step 3: Fill in the Metadata Header

Every doc starts with structured metadata. This is what makes docs findable, maintainable, and machine-readable. Don't skip it.

### Step 4: Write the Content

Use the template structure. Write in the language appropriate for your audience (see language guidance in the framework doc). Default to English for new docs unless there's a strong reason not to.

### Step 5: Quality Check

Use `4-documentation-standards-evaluation.md` or the Quick Quality Checks in the framework doc to verify your doc meets the bar.

### Step 6: Publish and Set a Review Date

Every doc needs an owner and a next-review date. No exceptions. Stale docs are worse than no docs.

---

## When to Use

- You're creating a new document and want to follow team standards
- You're capturing a product or technical decision
- You're documenting system architecture or technical context
- You need to assess whether existing documentation is fit for purpose
- You're onboarding someone to documentation practices
- You want to show stakeholders what "good documentation" looks like in practice

## The Documentation Taxonomy (Quick Reference)

| Type | Primary Audience | Job-to-be-Done | Template |
|------|-----------------|-----------------|----------|
| **Decision Record** | Product team, future PMs, stakeholders | Understand why we chose X | `2-decision-record-template.md` |
| **Architecture / Technical** | Engineering, tech leads, on-call | Understand how the system works | `3-architecture-technical-template.md` |
| **How-to / Procedural** | End users, helpdesk, support agents | Complete a specific task | *(future — build when user feedback patterns emerge)* |
| **Troubleshooting** | Support, engineering | Diagnose and fix a problem | *(future)* |
| **Onboarding / Conceptual** | New hires, cross-team | Understand what something is and why it exists | *(future)* |
| **Runbook / Process** | Ops, on-call, support escalation | Follow a procedure when X happens | *(future)* |

## How to Maintain

- **Quarterly:** Review all docs in this framework for accuracy
- **On use:** When you create a doc using these templates, note what worked and what didn't
- **On feedback:** When someone says "I couldn't find X" or "this doc was wrong," treat it as a signal — update the doc AND check if the template needs adjustment

## Links

- Documentation Standards Framework: `1-documentation-standards-framework.md`
- Decision Record Template: `2-decision-record-template.md`
- Architecture/Technical Template: `3-architecture-technical-template.md`
- Documentation Evaluation: `4-documentation-standards-evaluation.md`
- One-Pagers (for communicating decisions): `../2.4.3-One-Pagers/README.md`
- PRD (for detailed requirements): `../../2.3-Execution/2.3.4-PRD/README.md`
- Product Sense (braindump first): `../../2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md`
