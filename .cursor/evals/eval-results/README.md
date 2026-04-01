# Eval Results - Agent Behavior Logs

**What this directory is:** Logs of agent behavior evaluations for pattern detection and improvement tracking.

**How to use:** Agent (or you) can append eval results here to track behavior over time and identify patterns.

---

## Canonical Eval Log Format

Every eval result file MUST follow this structure. Use this template for new evals. Sections are in fixed order — include all of them, even if a section is "N/A" or brief.

```markdown
# Eval Log — [YYYY-MM-DD] — [Brief Description]

**Date:** YYYY-MM-DD
**Conversation Type:** [product_sense / execution_mode / meta_reflection / mixed — list transitions]
**User Request:** [Brief description of what the user asked]
**Platform:** [VS Code + GitHub Copilot / Cursor / Claude Code / other]

---

## Scenario Matched

[Which scenario_id from agent-behavior-scenarios.json best matches? If none, note "no exact match" and name the closest analog + whether a new scenario should be added.]

---

## Dimension Scores

| Dimension | Rating | Notes |
|---|---|---|
| Questioning quality | [Strong / Good / Medium / Weak] | [1-2 sentence justification] |
| Perspective taking | [Strong / Good / Medium / Weak] | [1-2 sentence justification] |
| Framework fit | [Strong / Good / Medium / Weak / N/A] | [1-2 sentence justification] |
| Artifact clarity | [Strong / Good / Medium / Weak / N/A] | [1-2 sentence justification] |
| Guidance quality | [Strong / Good / Medium / Weak] | [1-2 sentence justification] |
| User agency | [Strong / Good / Medium / Weak] | [1-2 sentence justification] |

---

## What Worked Well

[2-5 bullet points. Each should name a specific moment or pattern, not generic praise. Say WHY it worked, not just THAT it worked.]

---

## What Needs Improvement

[2-5 bullet points. Each should name the specific miss, what should have happened, and — critically — the structural root cause (not just "agent didn't follow the rule"). Apply the Root Cause Quality Check from 1-agent-behavior-guide.md §5.]

---

## Pattern Detection Notes

[Patterns confirmed from prior evals, new patterns identified, new failure modes. Reference prior eval files by name when a pattern recurs.]

---

## Success Indicators Met

[Checklist: ✅ / ❌ for each relevant success_indicator from the matched scenario. If no scenario matched, list the key behavioral checks and score them.]

---

## Files to Update

| What to change | Where (file path) | Priority | Status |
|---|---|---|---|
| [Description of fix] | [File path] | [High / Medium / Low] | [Open / Done YYYY-MM-DD] |

[Use "Done" with date when a fix has been implemented. This makes it possible to audit which eval recommendations were actioned.]
```

---

## Notes on the Format

**Why fixed sections:** Earlier evals used inconsistent structures (some had "Checkpoints" sections, some had "Key Findings", some had "Eval Findings"). The fixed structure makes it possible to scan across evals for patterns without re-learning each file's layout.

**Dimension Scores are mandatory.** Even for sessions where some dimensions don't apply (e.g. no framework in a reflection session), rate them "N/A" with a note — don't skip the row.

**Root cause quality matters.** In "What Needs Improvement", always ask: "Why was this structurally likely?" — not just "what happened." See [1-agent-behavior-guide.md](../1-agent-behavior-guide.md) §5.

**Files to Update tracks implementation.** Mark fixes as "Done" with a date when implemented. During eval review sessions, scan this column across all evals to find unresolved recommendations.

---

## Pattern Detection Queries

When reviewing logs, look for patterns:

- "Agent keeps jumping to templates in scenario X"
- "Braindump sufficient checklist rarely met before transition"
- "Preflight prompts skipped for non-trivial docs"
- "Questions asked before framework: consistently < 3"
- "Framework match quality: consistently Low"
- "Same structural root cause appearing across multiple evals"

**For agents:** When eval checkpoints are hit, append results to a log file in this directory. Use format above.

**For manual logging:** After important conversations, create a log file using the format above.

**For pattern detection:** Review multiple log files to identify systemic issues, then update instructions in `AGENTS.md`, `ORCHESTRATION.md`, or `.cursor/rules/` based on findings.

---

## File Naming

Use: `YYYY-MM-DD-brief-description.md`

Examples from actual evals:
- `2026-03-27-week-wrap-reflection-and-learning-capture.md`
- `2026-03-23-stakeholder-avatar-refactoring.md`
- `2026-03-13-user-research-planning.md`

---

## Git Tracking

**Decision:** Should eval logs be tracked in git?

- **Track them:** Enables pattern detection over time, team can review agent behavior
- **Ignore them:** Keeps repo clean, logs are temporary

**Recommendation:** Add `*.md` to `.gitignore` in this directory if you don't want to track logs. Or track them if you want to review agent behavior over time.

---

## Success Metrics to Track

Over time, track these metrics across logs:

- % of conversations where braindump sufficient checklist is met before framework
- Average questions asked before framework suggestion
- % of non-trivial docs where preflight prompts are asked
- Most common failure modes detected
- Framework match quality trends

**Goal:** Improve these metrics over time by updating instructions based on eval findings.
