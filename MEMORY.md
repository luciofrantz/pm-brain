# Sleeping Memory - What to Wake When

**What this file is:** The **sleeping memory manifest**: it lists context that lives in the repo but is not in the active prompt until "woken" - loaded when the conversation touches that area. The agent uses this to decide what to load after the always-on bootstrap set is already in place. Orchestration: [ORCHESTRATION.md](ORCHESTRATION.md) -> Context Loading Strategy.

**Concept:** This file is for **on-demand context only**. The always-on bootstrap set lives in [ORCHESTRATION.md](ORCHESTRATION.md): [AGENTS.md](AGENTS.md), [ORCHESTRATION.md](ORCHESTRATION.md), [.cursor/rules/voice.mdc](.cursor/rules/voice.mdc), [.cursor/rules/thinking.mdc](.cursor/rules/thinking.mdc), and [.cursor/rules/thinking.personal.mdc](.cursor/rules/thinking.personal.mdc). Content in 01-Company-Context, 03-Research-Artifacts, 04-Initiatives, conditional rules, skills, and evals is **sleeping memory** and should be woken only when relevant.

**Platform note:** Paths below assume the default repo layout. On **Cursor**, `.cursor/rules/` files with `alwaysApply: true` can satisfy part of the bootstrap automatically; skills and conditional rules still load on-demand. On **VS Code + GitHub Copilot**, `.github/copilot-instructions.md` is the bootstrap/invocation layer and should load the entire always-on bootstrap set into every conversation before responding. On **other platforms** (Claude Code, ChatGPT, Claude.ai, Codex, etc.), use that platform's startup mechanism or a manual setup prompt to load the bootstrap set first, then use this file for everything else.

---

## Bootstrap vs Sleeping Memory

**Always-on bootstrap (not sleeping memory):**
- [AGENTS.md](AGENTS.md)
- [ORCHESTRATION.md](ORCHESTRATION.md)
- [.cursor/rules/voice.mdc](.cursor/rules/voice.mdc)
- [.cursor/rules/thinking.mdc](.cursor/rules/thinking.mdc)
- [.cursor/rules/thinking.personal.mdc](.cursor/rules/thinking.personal.mdc)

**Sleeping memory (wake only when needed):**
- [version.json](version.json) — repo version and changelog (wake when user asks about version, recent changes, or when bumping after structural work)
- Company context under `01-Company-Context/`
- Research under `03-Research-Artifacts/`
- Initiative context under `04-Initiatives/`
- Conditional rules such as `template-finder.mdc`, `evaluation-orchestration.mdc`, and `product-sense.mdc`
- Evals under `.cursor/evals/`
- Skills under `.cursor/skills/`

---

## When to Wake What

| Trigger (user mentions or topic) | Wake (load or reference) |
|----------------------------------|--------------------------|
| Company, strategy, vision, roadmap, stakeholders, organization — **as background context** | [01-Company-Context/](01-Company-Context/README.md) (see below); start with [CONTEXT.md](01-Company-Context/CONTEXT.md) for name/company/team |
| Roadmap, OKRs, prioritization, discovery, stakeholder comms, politics — **as a framework/skill to apply** | See skill dispatch table in [ORCHESTRATION.md](ORCHESTRATION.md) → execution_mode entry |
| A specific initiative or "my initiative", "current bet" | 04-Initiatives/[initiative-name]/ (see below) |
| Research, interviews, discovery, evidence, user insights | [03-Research-Artifacts/](03-Research-Artifacts/README.md) or 04-Initiatives/[name]/research/ |
| Personalization beyond the bootstrap set (who I am, my team, my company context) | [01-Company-Context/CONTEXT.md](01-Company-Context/CONTEXT.md) |
| How to evaluate artifacts / when to run evals | [.cursor/rules/evaluation-orchestration.mdc](.cursor/rules/evaluation-orchestration.mdc), [.cursor/evals/](.cursor/evals/README.md) |
| Template finder / which doc to use | [02-Methods-and-Tools/0-template-finder.md](02-Methods-and-Tools/0-template-finder.md) |
| Product sense / braindump / golden rule | [PRODUCT-SENSE-RULES.md](PRODUCT-SENSE-RULES.md), [2-product-sense-prompts.md](02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/2-product-sense-prompts.md), [0-start-here-product-thinking.md](02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md) |
| Repo usage, maintenance, hygiene, "how should we use this repo?" | [docs/guidelines.md](docs/guidelines.md) |
| Repo structure, refactoring, architecture, adding files, reorganizing | [docs/architecture.md](docs/architecture.md) -> Design Principles section |
| Version, recent changes, changelog, version bump, "what changed" | [version.json](version.json) |
| Context health / "is this still roughly true?" when using company/initiative docs | [01-Company-Context/CONTEXT-HEALTH.md](01-Company-Context/CONTEXT-HEALTH.md) (see Freshness section below) |

---

## Company Context (01-Company-Context)

**When to wake:** User talks about company direction, strategy, vision, roadmap, stakeholders, BU/team structure, or context check asks for company context.

**Key paths (customize to your structure; may live in BU/team subfolders):**

| Purpose | Path |
|---------|------|
| Personalization (name, company, team/BU) | [01-Company-Context/CONTEXT.md](01-Company-Context/CONTEXT.md) |
| Setup / organization structure | [01-Company-Context/SETUP.md](01-Company-Context/SETUP.md) |
| Vision | 01-Company-Context/1-company-vision.md (or BU/team equivalent) |
| Strategy | 01-Company-Context/2-company-strategy.md (or BU/team equivalent) |
| Principles | 01-Company-Context/3-company-product-principles.md |
| Portfolio | 01-Company-Context/4-company-product-explanation.md |
| Roadmap | 01-Company-Context/5-company-roadmap.md |
| Stakeholders list | 01-Company-Context/6-company-stakeholders.md |
| OKRs (org language + private translation) | [01-Company-Context/7-team-okrs-styring-og-ledelse.md](01-Company-Context/7-team-okrs-styring-og-ledelse.md) |
| OKRs (proposed outcome-oriented) + Roadmap | [01-Company-Context/1.4-OKRs-and-Roadmap/](01-Company-Context/1.4-OKRs-and-Roadmap/README.md) |
| Stakeholder avatars / brainfeed cast | [01-Company-Context/1.1-Stakeholder-Avatars/](01-Company-Context/1.1-Stakeholder-Avatars/README.md) (folder; one file per avatar; agent lists and loads by name/role) |
| Organization survival (power, politics, red flags) | [01-Company-Context/1.2-Organization-Survival/](01-Company-Context/1.2-Organization-Survival/README.md) (folder; organization-level politics, power maps, alliances, stakeholder games, coalitions, red flags) |
| Overview | [01-Company-Context/README.md](01-Company-Context/README.md) |

---

## Context Health (living docs and anti-rot hints)

Some context docs are treated as **living inputs** to PM work (vision, strategy, company roadmap, stakeholders, politics, initiative roadmaps). Rather than putting `Last reviewed` headers on every file, [01-Company-Context/CONTEXT-HEALTH.md](01-Company-Context/CONTEXT-HEALTH.md) holds a **context health table** that tracks which docs matter most for staleness and how often they should be sanity-checked.

- **Table location:** [01-Company-Context/CONTEXT-HEALTH.md](01-Company-Context/CONTEXT-HEALTH.md).
- **What it contains:** Doc paths, roles, rough review cadences, rot risk, and optional "last reviewed" notes.
- **How the agent uses it:** When waking `01-Company-Context/`, `04-Initiatives/`, or `03-Research-Artifacts/` as inputs to a roadmap/OKR/strategy/PRD/initiative decision or a politics flow, the agent **may** consult this table and, if a doc is high/medium rot risk and overdue vs. its cadence, offer a short optional "is this still roughly true?" reminder.

Outside those flows (e.g. casual browsing, light questions), the agent should **not** use context health to nag about freshness.

---

## Initiatives (04-Initiatives)

**When to wake:** User mentions working on or thinking about a specific initiative (by name or "my initiative", "current bet").

**Pattern:** One folder per initiative under `04-Initiatives/`. List subfolders to discover initiative names (e.g. `4.1-Initiative-Codename`).

**Suggested files per initiative (load as relevant):**

- README.md - overview
- opportunity-assessment.md
- prd.md
- decisions.md
- roadmap.md
- summary.md
- research/ - initiative-specific research artifacts (if present)
- stakeholders/ - initiative-level stakeholder insights and communication rhythm (use together with company stakeholders, stakeholder avatars, and organization survival docs when politics are in play)

**Index:** See [04-Initiatives/README.md](04-Initiatives/README.md). To list initiatives, use the filesystem or README; paths are `04-Initiatives/<folder-name>/<file>.md`.

---

## Research Artifacts (03-Research-Artifacts)

**When to wake:** User refers to past research, interviews, synthesis, or evidence they want to use in thinking or a doc.

**Structure:**

- [03-Research-Artifacts/README.md](03-Research-Artifacts/README.md) - how research is stored, when to use 03 vs 04-Initiatives/[name]/research/
- 03-Research-Artifacts/3.1-User-Interviews/ - interview-related artifacts
- 03-Research-Artifacts/3.2-Qualitative-Research/ - qualitative research artifacts

Store analysis/snapshots here (or in initiative research/); raw data external with links.

---

## Conditional Rules (.cursor/rules)

**When to wake:** Agent needs rule files beyond the always-on bootstrap set, for example evaluation behavior, template-finder behavior, or product-sense-specific behavior.

| File | Purpose |
|------|---------|
| evaluation-orchestration.mdc | When to run Quick Quality Checks and full evals during artifact creation |
| template-finder.mdc | When user asks for a specific doc; route to 0-template-finder |
| product-sense.mdc | Golden rule, braindump before structure for product topics |

---

## Evals

**When to wake:** Agent needs eval functions for transition checks, agent-behavior guide for Level 2 evals, or test cases for replay.

| File | Purpose |
|------|---------|
| .cursor/evals/eval-functions.md | check_braindump_sufficient, check_questions_before_framework, match_scenario_type - used at state transitions |
| .cursor/evals/1-agent-behavior-guide.md | Level 2 agent behavior review: dimensions, reflection checklist, "where to update" map |
| .cursor/evals/2-checklist.md | When to run Level 1/2 evals, ongoing rhythm |
| .cursor/evals/agent-behavior-scenarios.json | Reference scenarios for matching conversation types (agent does not read directly) |
| .cursor/evals/test-generator.md | How to turn scenarios into test cases |
| .cursor/evals/eval-results/ | Log storage for eval results and test cases |

---

## Skills (.cursor/skills)

**When to wake:** Dispatched by ORCHESTRATION.md execution_mode entry — see the skill dispatch table there for exact topic → skill mappings. Do not load skills independently of that routing.

| Path | Purpose |
|------|---------|
| [.cursor/skills/pm-brain-workflow/SKILL.md](.cursor/skills/pm-brain-workflow/SKILL.md) | Overall PM workflow: Foundations -> Strategy -> Discovery -> Execution -> Communication; high-level routing. |
| [.cursor/skills/discovery-research/SKILL.md](.cursor/skills/discovery-research/SKILL.md) | Discovery workflows: research interviews, continuous discovery, JTBD, segmentation, opportunity assessment, idea validation, problem/solution space, PMF. |
| [.cursor/skills/strategy-planning/SKILL.md](.cursor/skills/strategy-planning/SKILL.md) | Strategy and planning: strategy docs, OKRs, roadmaps, prioritization. |
| [.cursor/skills/stakeholder-management/SKILL.md](.cursor/skills/stakeholder-management/SKILL.md) | Stakeholder communication: one-pagers, newsletters, stakeholder management, saying no, escalation, crisis management. |
| [.cursor/skills/politics-coach/SKILL.md](.cursor/skills/politics-coach/SKILL.md) | Politics and power dynamics: set up stakeholder/peer avatars (brainfeed cast), run politics checks, and simulate stakeholder reactions when people aren't in the room. |

---

## Summary

- **Company / strategy / organization** -> 01-Company-Context (CONTEXT.md first, then vision/strategy/roadmap/stakeholders as needed).
- **Initiative** -> 04-Initiatives/[initiative-name]/ (opportunity-assessment, prd, decisions, roadmap, summary).
- **Research / evidence** -> 03-Research-Artifacts or 04-Initiatives/[name]/research/.
- **Always-on coaching + personalization rules** -> already in the bootstrap set; do not treat them as sleeping memory.
- **Evals / template finder / product sense** -> See [ORCHESTRATION.md](ORCHESTRATION.md) and the rules/skills/evals sections above.

Do not load everything at once. Wake only what the conversation needs.
