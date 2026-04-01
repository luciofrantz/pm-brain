# Documentation Standards — Evaluation Framework

> **Before running structured evaluation:** Use your gut first. Read the doc and ask: does this feel useful? Would I actually come back to this? Could someone who wasn't in the room understand it? Then use the structured framework below to validate and deepen your assessment.

> **Note:** For creation-time quality checks (lightweight, automatic), see the "Quick Quality Checks" section in `1-documentation-standards-framework.md`. This comprehensive evaluation framework is for peer review, documentation audits, or quality gates.

---

## Usage Instructions

**Use this evaluation when:**
- Reviewing documentation created by team members
- Auditing existing documentation for quality and freshness
- Establishing a quality bar for documentation in your team
- Assessing whether documentation is ready for AI agent consumption

**Don't use this for:**
- Creating documentation (use the templates instead)
- Quick sanity checks during creation (use Quick Quality Checks in the framework doc)

---

## AI Agent Instructions

When helping a user evaluate documentation:

1. Follow the step sequence in order (0 → 1 → 2 → 3 → 4)
2. Help the user THINK about their documentation quality — don't just score it for them
3. Ask clarifying questions if the doc's purpose or audience isn't clear
4. Reference `1-documentation-standards-framework.md` for taxonomy and principles
5. Output format: use the scoring template provided in Step 2

---

## STEP 0: GUT CHECK & DOC SENSE (Do this first!)

*5 minutes. Before structured evaluation.*

### Doc Sense Questions

- **What's your gut feeling about this doc?** What feels right? What feels off?
- **If you needed this doc at 2 AM during an incident, would it actually help?**
- **Could a new team member understand this without calling the author?**
- **Could an AI agent answer questions using this doc?** Or would it need to guess?
- **Is this doc earning its maintenance cost?** Will someone keep it current?
- **What's the single biggest problem with this doc right now?**

### Bias Check

- Am I rating this doc highly because I wrote it (or someone I like wrote it)?
- Am I rating it poorly because of the author rather than the content?
- Am I confusing "long" with "thorough" or "short" with "incomplete"?
- Am I judging it against a perfect doc that doesn't exist, or against "useful enough"?

### Capture Your Initial Thoughts

Write 2-3 sentences before moving to structured evaluation:
- What works: ___
- What's broken: ___
- Priority fix: ___

---

## STEP 1: DOCUMENTATION_QUALITY_CHECK

Quick scan for critical issues. Each red flag is a signal that the doc needs work before it's useful.

### RED FLAGS (each = -1 score multiplier, minimum 0.1x)

| # | Red Flag | Present? |
|---|----------|----------|
| 1 | **No metadata header** — Missing structured frontmatter entirely | ☐ |
| 2 | **No owner** — Nobody is responsible for this doc | ☐ |
| 3 | **Stale** — `last-reviewed` is more than 6 months ago (living docs) or status doesn't match reality | ☐ |
| 4 | **Wrong doc type** — Template and content don't match (e.g., decision record template used for a how-to guide) | ☐ |
| 5 | **No audience** — Unclear who this doc is for | ☐ |
| 6 | **Duplicated content** — Information is copied from another doc instead of linked | ☐ |
| 7 | **Screenshots only** — No structured text, just images | ☐ |
| 8 | **Mixed languages** — Switches between English and Danish within the content | ☐ |

**Red flag count:** ___ → Multiplier: max(0.1, 1.0 - count × 0.15)

### GREEN FLAGS (each = +0.5 multiplier bonus, max +2.0)

| # | Green Flag | Present? |
|---|------------|----------|
| 1 | **Complete metadata** — All required fields filled and accurate | ☐ |
| 2 | **Clear audience** — Specific and appropriate audience named | ☐ |
| 3 | **Linked, not duplicated** — References other docs as sources of truth | ☐ |
| 4 | **Review date set and honored** — `next-review` is set and doc was reviewed on schedule | ☐ |
| 5 | **Honest limitations** — Acknowledges gaps, unknowns, or areas that need work | ☐ |
| 6 | **AI-parseable** — Structured headers, explicit context, machine-readable dates | ☐ |

**Green flag count:** ___ → Bonus: min(2.0, count × 0.5)

**Quality Multiplier:** (1.0 - red_flags × 0.15) + green_bonus = ___

---

## STEP 2: DOCUMENTATION_EVALUATOR_PROMPT

Comprehensive weighted rubric. Score each criterion 1-10, then calculate the weighted average.

### Criterion 1: Audience Fit (25%)

*Does the doc serve its stated audience effectively?*

| Score | Description |
|-------|-------------|
| 9-10 | Audience is clearly named, content is perfectly pitched for them, a reader from that audience can use the doc without help |
| 7-8 | Audience is named, content is mostly appropriate, minor gaps in pitch or detail level |
| 4-6 | Audience is vague or content doesn't match the stated audience well |
| 1-3 | No audience identified, or content is clearly written for a different audience |

### Criterion 2: Completeness and Structure (25%)

*Does the doc cover what it needs to, using the right structure for its type?*

| Score | Description |
|-------|-------------|
| 9-10 | All sections from the template are meaningfully filled. Structure matches the doc type. No major gaps. |
| 7-8 | Most sections filled, structure is right, 1-2 minor gaps |
| 4-6 | Several sections missing or superficial. Structure partially matches doc type |
| 1-3 | Major sections missing, wrong structure for the doc type, or content is a wall of unstructured text |

### Criterion 3: AI-Readiness (20%)

*Can an AI agent effectively find, parse, and reason over this doc?*

| Score | Description |
|-------|-------------|
| 9-10 | Complete metadata, structured headers, explicit context, machine-readable dates, linked references, single language |
| 7-8 | Metadata mostly complete, good structure, minor issues (e.g., missing tags, one date not ISO format) |
| 4-6 | Partial metadata, some structure, but AI would struggle with ambiguity or missing context |
| 1-3 | No metadata, unstructured, screenshots as primary content, implicit context |

### Criterion 4: Maintainability (15%)

*Is this doc set up to stay current, or is it destined to go stale?*

| Score | Description |
|-------|-------------|
| 9-10 | Owner assigned, review date set, clear scope that limits maintenance burden, links to upstream sources |
| 7-8 | Owner and review date set, scope is mostly clear |
| 4-6 | Owner or review date missing, scope is unclear, some duplicated content that will drift |
| 1-3 | No owner, no review date, lots of duplicated content, nobody will maintain this |

### Criterion 5: Clarity and Honesty (15%)

*Is the writing clear, direct, and honest about limitations?*

| Score | Description |
|-------|-------------|
| 9-10 | Clear, direct language. Acknowledges unknowns and limitations. No jargon without explanation. Honest about tradeoffs. |
| 7-8 | Mostly clear, minor jargon or ambiguity. Touches on limitations. |
| 4-6 | Some unclear sections, jargon-heavy, or avoids acknowledging problems |
| 1-3 | Confusing, corporate speak, hides limitations, or reads as marketing rather than documentation |

### Scoring Output

```
=== DOCUMENTATION QUALITY SCORE ===

Doc: [title]
Type: [doc-type]
Evaluator: [name]
Date: [YYYY-MM-DD]

Criterion Scores:
  Audience Fit (25%):        ___ / 10
  Completeness (25%):        ___ / 10
  AI-Readiness (20%):        ___ / 10
  Maintainability (15%):     ___ / 10
  Clarity & Honesty (15%):   ___ / 10

  Weighted Base Score:        ___ / 10
  Quality Multiplier:         ___x (from Step 1)
  Final Score:                ___ / 10

Verdict:
  9-10: Excellent — reference-quality documentation
  7-8:  Good — usable and maintainable, minor improvements possible
  5-6:  Fair — usable but needs work on specific areas
  3-4:  Poor — significant gaps, not reliably usable
  1-2:  Critical — needs fundamental rework

Top 3 improvements:
  1. ___
  2. ___
  3. ___
```

---

## STEP 3: DOCUMENTATION_ANTIPATTERN_DETECTOR

Check for these specific patterns. Each one has a fix.

| # | Antipattern | Detected? | Fix |
|---|------------|-----------|-----|
| 1 | **The Everything Doc** — tries to be a decision record AND a how-to AND an architecture doc | ☐ | Split into separate docs by type |
| 2 | **The Ghost Doc** — no owner, no review date, clearly abandoned | ☐ | Assign an owner or archive it |
| 3 | **The Copy-Paste Doc** — duplicates content from other docs | ☐ | Replace with links to the source of truth |
| 4 | **The Screenshot Novel** — 90%+ screenshots, minimal text | ☐ | Add structured text descriptions; use screenshots as supplements |
| 5 | **The Optimist Doc** — no limitations, no risks, everything is great | ☐ | Add Known Limitations section; be honest |
| 6 | **The Time Capsule** — was accurate when written, clearly outdated now | ☐ | Review, update, and set next-review date |
| 7 | **The Mystery Audience** — unclear who should read this | ☐ | Name the specific audience in metadata |
| 8 | **The Orphan** — not linked from anywhere, not findable | ☐ | Link from relevant READMEs, navigation pages, or parent docs |

---

## STEP 4: DOCUMENTATION_IMPROVEMENT_GENERATOR

Based on the evaluation, generate specific, prioritized improvements.

### Priority Matrix

| Effort | High Impact | Low Impact |
|--------|------------|------------|
| **Low effort** | Do NOW | Do if convenient |
| **High effort** | Plan and schedule | Skip for now |

### Improvement Template

For each improvement:

```
Improvement #___:
  What: [Specific change needed]
  Why: [Which criterion or antipattern triggered this]
  Effort: [Low / Medium / High]
  Impact: [Low / Medium / High]
  Suggested approach: [How to fix it — 1-2 sentences]
```

### Common Quick Wins (Low Effort, High Impact)

- Add metadata header (15 minutes)
- Name the audience explicitly (5 minutes)
- Set an owner and review date (5 minutes)
- Replace duplicated content with links (30 minutes)
- Add a one-line context sentence at the top (5 minutes)
- Convert mixed-language doc to single language (varies)
