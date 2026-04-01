# 🚀 PM Brain Setup Guide

> **Welcome!** This guide will help you get your PM Brain repository configured and ready to use. No technical knowledge required—just follow the steps.

## ⚠️ IMPORTANT: Fork Privacy

**If you're using PM Brain for real company work**, do NOT use a public fork. The original PM Brain repo is public, so any fork defaults to public too. Your company context, roadmaps, and stakeholder info should NOT be visible to everyone.

**Choose one:**

- **Option A (Recommended):** Create a **private repo** on GitHub, then clone PM Brain into it. See [Step 1: Get the Repository](#-step-1-get-the-repository) → Option B below for exact steps.
- **Option B:** Work locally without pushing to GitHub (use git locally only).
- **Option C:** Fork the public repo, but use `.gitignore` to prevent pushing sensitive files. See [Step 3: Choose Public / Private / Team Mode](#-step-3-choose-public--private--team-mode).

**Bottom line:** Don't accidentally push company strategy to the internet.

---

## 🔧 First: Choose Your AI Tool

Your tool choice affects how PM Brain configures itself — some tools auto-load rules, others require a manual setup prompt each session.

| Tool | Rules auto-load? | Setup effort |
|------|-----------------|---------------|
| **Cursor** | Yes (`.cursor/rules/`) | Minimal |
| **VS Code + GitHub Copilot** | Yes (`.github/copilot-instructions.md`) | Minimal |
| **Claude Code** | No — manual per session | Some |
| **ChatGPT / Claude.ai** | No — copy-paste per session | More |

See [platform-setup.md](platform-setup.md) for full per-tool instructions. If you’re using Cursor or VS Code + Copilot, the agent configures itself automatically once you’ve done the company context setup below. For other tools, follow the manual steps in that guide.

**Once setup is done:** open a chat with your agent and say “verify my PM Brain setup is complete and aligned with best practices” — it will check your configuration and flag anything missing.

---

## 📋 Quick Start Checklist

- [ ] Choose your GitHub approach (private repo, local-only, or managed .gitignore)
- [ ] Read this SETUP guide
- [ ] Review the main README.md
- [ ] Read [guidelines.md](guidelines.md) for best practices
- [ ] Read [platform-setup.md](platform-setup.md) if you're NOT using Cursor
- [ ] Customize Company Context (Priority 1)
- [ ] Review AI/Agent configuration (if using Cursor or similar)
- [ ] Try your first framework
- [ ] Set up your first initiative

---

## 🎯 Step 1: Get the Repository

### Option A: Personal Use (Clone or Private Fork)

- If you’re experimenting or building a **personal public portfolio**, you can clone directly:

  ```bash
  git clone https://github.com/andreaskelm/pm-brain.git
  cd pm-brain
  ```

- If you're working with **real company context**, create a **private repo first**:

  1. **Create a new private repo on GitHub** (empty, no README):
     - Go to github.com → New repository
     - Name it (e.g., `pm-brain-private`, `pm-brain-company`)
     - Set to **Private**
     - Click Create

  2. **Clone PM Brain locally and push to your private repo:**
     ```bash
     git clone https://github.com/andreaskelm/pm-brain.git
     cd pm-brain
     git remote set-url origin https://github.com/YOUR-USERNAME/pm-brain-private.git
     git branch -M main
     git push -u origin main
     ```

  3. **Add upstream to stay synced with PM Brain updates:**
     ```bash
     git remote add upstream https://github.com/andreaskelm/pm-brain.git
     git fetch upstream
     ```

  This keeps your company context private while pulling future updates.

### Option B: Team/Company Framework Repo

If you want a shared repo for your team’s frameworks/templates:

1. **Create a private org repo** on GitHub (coordinate with org admin).  
2. Clone PM Brain into it (same steps as Option A above).  
3. Use [Step 3](#-step-3-choose-public--private--team-mode) → **Team mode** to manage what's tracked (keep personal Meta logs private).

---

## 📚 Step 2: Understand the Structure

Before customizing, understand what each folder does:

```
pm-brain/
├── 00-Meta/                   # 🧠 Personal practice (daily log, learning log, growth portfolio, Product Judgment Test)
├── 01-Company-Context/        # 🏢 YOUR company vision, strategy, stakeholders
├── 02-Methods-and-Tools/      # 🧭 Frameworks & templates (Strategy, Discovery, Execution, Communication)
├── 03-Research-Artifacts/     # 🔍 Your research notes and findings
└── 04-Initiatives/            # 🚧 Your active product work
```

**Key insight:** 
- `00-Meta/` = **YOUR PRACTICE** (daily log, weekly/monthly reflection, growth portfolio, forecast calibration). Canonical prompts and templates live in `02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/`.
- `01-Company-Context/` = **YOU MUST CUSTOMIZE THIS** (your company info)
- `02-Methods-and-Tools/` = **READY TO USE** — **2.0-Foundations** (think first, product sense), **2.1-Strategy**, **2.2-Discovery**, **2.3-Execution**, **2.4-Communication**. Start product thinking from [0-start-here-product-thinking.md](..\/02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md).
- `03-Research-Artifacts/` = **YOUR RESEARCH** (add your interview notes, findings)
- `04-Initiatives/` = **YOUR WORK** (document your active initiatives)

---

## ⚙️ Step 3: Choose Public / Private / Team Mode

This repo supports three usage modes. Setup is **manual and simple**: you choose a mode by appending the right `.gitignore` template and committing. No scripts required.

### Modes at a Glance

- **🌍 Public** (default)
  - **Best for**: open learning, public examples, blog/portfolio content.  
  - **Tracked**: everything (frameworks, Meta logs, company context, initiatives).  

- **🔒 Private**
  - **Best for**: real company work or personal growth where content must not leak.  
  - **Tracked**: frameworks and docs.  
  - **Ignored** (via `.gitignore.private`): Meta logs, growth portfolio, company context, active initiatives (per patterns).  

- **👥 Team**
  - **Best for**: a shared frameworks repo, with each person keeping their own practice private.  
  - **Tracked**: `02-Methods-and-Tools/` and any shared docs.  
  - **Ignored** (via `.gitignore.team`): each contributor’s `00-Meta` logs and personal growth artefacts.

### How to Apply a Mode (Manual)

Run **one** of these in your fork’s root:

- **Public (do nothing)**  
  - Leave `.gitignore` as‑is. Everything can be tracked.

- **Private mode**:

  ```bash
  cat .gitignore.private >> .gitignore
  git add .gitignore
  git commit -m "setup: configure private mode"
  ```

- **Team mode**:

  ```bash
  cat .gitignore.team >> .gitignore
  git add .gitignore
  git commit -m "setup: configure team mode"
  ```

For details and decision help, see `00-Meta/MODE-SELECTION-GUIDE.md`.

---

## 📚 Step 4: Required Customizations (Priority Order)

### Priority 1: Company Context (`01-Company-Context/`)

**This is the most important step.** Your company context is what makes PM Brain useful for YOUR situation instead of generic advice.

#### Step 1: Fill out CONTEXT.md (2-3 minutes)

Open `01-Company-Context/CONTEXT.md` and add your name, role, company, and team. This is the quick-reference card that agents use to know who you are and where you sit.

#### Step 2: Create the core docs you actually need

> **Joining an existing org?** You probably don't need all of these. If your strategy lives in SharePoint and your roadmap is managed elsewhere, don't rebuild them here — mark them `Reference` or `External` in `01-Company-Context/CONTEXT-HEALTH.md` and move on. Only create what you actually own and will maintain.

The core documents (all in `01-Company-Context/`):

- `1-company-vision.md` — Mission, vision, values
- `2-company-strategy.md` — Strategic priorities
- `3-company-product-principles.md` — Product principles (skip if your org doesn't have explicit ones)
- `4-company-product-explanation.md` — Product portfolio
- `5-company-roadmap.md` — Roadmap (skip if managed elsewhere)
- `6-company-stakeholders.md` — Stakeholder directory

Replace `[Company]` placeholders with your actual company name. Replace placeholder content with real content. Skip files that don't apply.

#### Step 3: Structure (flat is fine)

Most orgs need a **flat structure** — all docs at root level inside `01-Company-Context/`. If you have distinct business units with separate strategies and roadmaps, create BU subfolders (e.g. `1.1-Business-Unit-A/`). If you're not sure, start flat — you can always add structure later.

#### Optional: Stakeholder Avatars

If you work with a recurring cast of stakeholders and want the agent to simulate "what would my manager say?" or run politics checks, set up stakeholder avatars in `01-Company-Context/1.1-Stakeholder-Avatars/`. One file per person. See the [setup guide there](../01-Company-Context/1.1-Stakeholder-Avatars/README.md) and the [framework](../02-Methods-and-Tools/2.4-Communication/2.4.8-Stakeholder-Avatars/README.md).

#### Step 4: Track freshness

Once your docs exist, populate `01-Company-Context/CONTEXT-HEALTH.md` with the docs you created, their rot risk, and whether they're `Maintained`, `Reference`, or `External`. This tells the agent when to nudge you about stale context.

---

### Priority 2: AI/Agent Configuration (If Using Cursor or Similar IDE)

If you're using **Cursor** (or similar AI-powered IDE), the repository includes agent configuration files.

#### Location: Root and `.cursor/rules/`

**Key files:**
- `AGENTS.md` (root) — PM Brain Coach persona and core instructions; points to orchestration and memory.
- `ORCHESTRATION.md` (root) — Routing, states (product_sense, execution_mode, meta_reflection, conversation), context loading; single source of truth for agent behavior.
- `MEMORY.md` (root) — Sleeping memory manifest: when to load company context, initiatives, research, rules, skills.
- `.cursor/rules/AGENTS.template.md` — Template for creating custom agents (separate from root `AGENTS.md`).
- `thinking.mdc` — High-level thinking support rules.
- `thinking.personal.mdc` — Personal context (you can customize this).

**What to do:**
1. **Review** `AGENTS.md` and `ORCHESTRATION.md` — Understand how the PM Brain Coach is configured and how it routes and loads context
2. **Fill out** `01-Company-Context/CONTEXT.md` - Add your name, company name, and team/Business Unit names (organizational context)
   - **Note:** In private/team modes, this file is ignored by default. In team mode, you can optionally track it for team consistency (see `.gitignore.team` comments).
3. **Customize** `.cursor/rules/thinking.personal.mdc` - Add your personal working style, preferences, and communication style (how you like to work)
   - **Note:** Both files may include your name - keep them consistent. `CONTEXT.md` focuses on organizational context; `thinking.personal.mdc` focuses on how you work.
   - **Git tracking:** This file is ignored in private and team modes (kept private). In public mode, sanitize any sensitive personal information.
4. **Optional:** Use `AGENTS.template.md` to create additional custom agents if needed
5. **Optional:** Add company-specific rules if needed

**Example personal context to add:**
```markdown
# Personal Context

## Working Style
- I prefer detailed explanations
- I like examples with real scenarios
- I want to understand the "why" behind recommendations

## Common Challenges
- I struggle with stakeholder alignment
- I need help prioritizing competing requests
- I want to improve my product sense

## Goals
- Become better at discovery
- Improve my communication with engineering
- Build stronger product intuition
```

**Time estimate:** 15-30 minutes

---

### Priority 3: 00-Meta (Personal Practice) — Optional

If you want to build product sense deliberately (daily log, weekly reflection, growth portfolio, forecast calibration):

1. **Read** [00-Meta/README.md](..\/00-Meta/README.md) for what lives there and the minimal workflow.
2. **Copy** the daily log template from `02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/templates/daily-log-template.md` to `00-Meta/1-daily-log-YYYY-QX.md` (e.g. `1-daily-log-2026-Q1.md`).
3. **Optional:** Before shipping a feature, log a forecast in `00-Meta/0.3-Product-Judgment-Test/forecast-log.md`; resolve when data is in (calibration).

Mode (Public/Private/Team) affects what in `00-Meta/` is tracked in git; see Step 3 and `00-Meta/MODE-SELECTION-GUIDE.md`.

---

### Priority 4: Optional Customizations

#### Customize Templates (If Needed)

The templates in `02-Methods-and-Tools/` work as-is, but you can customize them for your workflows:

- **PRD Template** (`2.3-Execution/2.3.4-PRD/2-prd-template.md`) - Add company-specific sections
- **Meeting Agendas** (`2.4-Communication/2.4.2-Meeting-Agendas/`) - Add your team's standard agenda items
- **One-Pagers** (`2.4-Communication/2.4.3-One-Pagers/`) - Customize for your communication style

**When to customize:**
- Your team has specific requirements
- You want to add company-specific sections
- You've found a better structure through experience

**When NOT to customize:**
- First time using the framework (try it as-is first)
- You're not sure what to change (use it, then iterate)

---

## 🧪 Step 5: Try Your First Framework

**Don't wait until you need it!** Try a framework now to get familiar with the system.

### Start with product thinking (braindump first)

1. **Open the entry point:** [0-start-here-product-thinking.md](..\/02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md)
2. **Copy the "Simple prompt to start"** at the top into a new chat (e.g. with Cursor or any AI). The agent will ask hard questions and braindump with you before suggesting any framework.
3. **Only after a braindump** use the **Frameworks by situation** table in that file (or the domain READMEs) to open the right framework: Strategy, Discovery, Execution, or Communication.

**Golden rule:** Braindump before structure. See [PRODUCT-SENSE-RULES.md](..\/PRODUCT-SENSE-RULES.md).

### Then try a framework

- **PRD:** `02-Methods-and-Tools/2.3-Execution/2.3.4-PRD/` — after braindump, read README + framework, then template
- **OKRs:** `02-Methods-and-Tools/2.1-Strategy/2.1.2-Strategic-Execution/1-OKR/` — goal-setting
- **Opportunity Assessment:** `02-Methods-and-Tools/2.2-Discovery/2.2.4-Opportunity-Assessment/` — evaluating new ideas
- **Meeting Agendas / One-Pagers:** `02-Methods-and-Tools/2.4-Communication/` — stakeholder communication

---

## 📝 Step 6: Set Up Your First Initiative

Create your first initiative folder to see how the system works:

1. **Navigate to:** `04-Initiatives/`
2. **Create a new folder:** `4.2-Your-Initiative-Name/` (or use the example: `4.1-Initiative-Codename/`)
3. **Copy the structure from the example:**
   - `README.md`
   - `summary.md`
   - `opportunity-assessment.md`
   - `prd.md`
   - `roadmap.md`
   - `decisions.md`

4. **Start with:** `summary.md` - Write a brief summary of what you're working on

**This is where you'll do your actual product work!**

---

## 🤖 Step 7: Platform Setup

PM Brain works on any AI platform. The core knowledge (frameworks, templates, orchestration) is platform-agnostic. Each platform just needs a different bootstrap method.

### Cursor (auto-loads)

1. **Open the repository** in Cursor — rules, skills, and commands load automatically from `.cursor/`.
2. The AI already knows the repo via `AGENTS.md`. For product thinking, it starts from [0-start-here-product-thinking.md](..\/02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md): braindump first, then frameworks.
3. **Slash commands** available (see `.cursor/commands/`): `/start`, `/braindump`, `/framework`, `/day`, `/week`, `/focus`, `/unstuck`, `/navigate`, `/bias`, `/evaluate`, `/meta`.

**Use PM Brain in any project (Cursor only):**
```bash
npx skills add andreaskelm/pm-brain
```

### Claude Code (reads CLAUDE.md)

1. Open the repo in Claude Code — it reads [CLAUDE.md](..\/CLAUDE.md) automatically.
2. Full file system access. The agent reads `AGENTS.md`, `ORCHESTRATION.md`, and `MEMORY.md` to know what to do.
3. Use `/compact` when context grows heavy. Use the checkpoint protocol (see `ORCHESTRATION.md` → Context Health) for long sessions.

### Claude.ai Projects

1. Create a Project and upload these files to Project Knowledge: `AGENTS.md`, `ORCHESTRATION.md`, `MEMORY.md`, `PRODUCT-SENSE-RULES.md`.
2. Upload `.cursor/rules/voice.mdc` content for communication style (recommended — this is the persona's tone and voice).
3. Reference framework files by asking the agent to work from them (paste or describe).

**For persistent coaching:** Use the [Product Coach setup template](..\/02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/templates/6-product-coach-setup.md) — copy it into a Claude Project for the same braindump-first coaching approach.

### ChatGPT / Gemini / Other

1. Create a GPT or Project and upload `AGENTS.md` + `PRODUCT-SENSE-RULES.md` as system context.
2. Browse to the framework you need, copy the README + framework + template files.
3. Paste into your chat with: "Here's the PRD framework I use. First, help me braindump my thoughts on [feature]. Then help me fill out the template."

### GitHub Copilot / VS Code

1. Open the repository in VS Code with the GitHub Copilot extension installed.
2. `.github/copilot-instructions.md` auto-loads into every Copilot conversation — it instructs the agent to read the full 5-file bootstrap set (AGENTS.md, ORCHESTRATION.md, voice.mdc, thinking.mdc, thinking.personal.mdc) before responding.
3. Use **Agent mode** in the Copilot Chat panel for full bootstrap compliance (file read tools required).
4. See [platform-setup.md](platform-setup.md) for detailed setup, model selection, known limitations, and troubleshooting.

### Universal (any platform)

Copy `AGENTS.md` content as your system prompt. Reference `ORCHESTRATION.md` for workflow. Paste framework content when needed. The checkpoint protocol (saving state to `checkpoints/` and resuming in a new conversation) works everywhere — it's just text files.

---

## ✅ Step 8: Verify Your Setup

Run through this checklist to ensure everything is configured:

- [ ] Company Context files updated with your information
- [ ] Agent rules reviewed (if using Cursor)
- [ ] Know the product-thinking entry point (`0-start-here-product-thinking.md`) and braindump-first rule
- [ ] Tried at least one framework successfully (after a braindump)
- [ ] Created your first initiative folder
- [ ] Understand where to store research (`03-Research-Artifacts/`)
- [ ] Know where to document active work (`04-Initiatives/`)
- [ ] (Optional) Set up `00-Meta/` daily log or forecast log if you want to practice product sense

---

## 🆘 Common Questions

### "Do I need to install anything?"

**No!** This is a markdown-based system. You just need:
- A text editor (VS Code, Cursor, Notepad, etc.)
- Git (if you want version control)
- Optional: AI tool (Cursor, ChatGPT, Claude, etc.)

### "What if I make a mistake?"

**No problem!** This is git-versioned:
- `git status` - See what changed
- `git diff` - See exact changes
- `git checkout -- <file>` - Undo changes to a file
- `git log` - See your history

### "Can I use this with my team?"

**Yes!** 
- Fork the repo for your team
- Customize Company Context together
- Share frameworks and templates
- Use git to collaborate

### "How do I keep it updated?"

If you forked from the main repo:
```bash
# Add the original repo as upstream
git remote add upstream https://github.com/andreaskelm/pm-brain.git

# Pull updates (merge carefully!)
git fetch upstream
git merge upstream/main
```

**Be careful:** Only merge framework updates. Don't overwrite your Company Context!

### "What if I don't know what to customize?"

**Start simple:**
1. Update Company Context (Priority 1)
2. Use frameworks as-is
3. Customize only when you discover a need

**Don't optimize prematurely!** Use the system first, then improve it.

---

## 🎓 Next Steps

Once you're set up:

1. **Read the main README.md** - Understand the philosophy
2. **Browse frameworks** - See what's available in `02-Methods-and-Tools/`
3. **Start using it** - Don't wait for perfect setup, start with real work
4. **Iterate** - Customize as you learn what works for you

---

## 📚 Additional Resources

- **Main README:** [README.md](..\/README.md) — Overview and philosophy
- **Product thinking entry point:** [0-start-here-product-thinking.md](..\/02-Methods-and-Tools/2.0-Foundations/2.0.1-Mental-Models/6-Product-Sense-Development/0-start-here-product-thinking.md) — Simple prompt to start; braindump first, then frameworks by situation
- **Golden rule:** [PRODUCT-SENSE-RULES.md](..\/PRODUCT-SENSE-RULES.md) — Braindump before structure
- **Guidelines:** [guidelines.md](guidelines.md) — Best practices for using and maintaining your PM brain
- **Agent configuration:** [AGENTS.md](..\/AGENTS.md) (persona), [ORCHESTRATION.md](..\/ORCHESTRATION.md) (routing & states), [MEMORY.md](..\/MEMORY.md) (what to wake); `.cursor/rules/AGENTS.template.md` for custom agents
- **Framework Navigation:** [02-Methods-and-Tools/README.md](..\/02-Methods-and-Tools/README.md) — Strategy, Discovery, Execution, Communication
- **00-Meta (practice):** [00-Meta/README.md](..\/00-Meta/README.md) — Daily log, learning log, growth portfolio, Product Judgment Test
- **Credits:** [credits.md](credits.md) — Attribution for frameworks and methods

---

## 💡 Pro Tips

1. **Braindump first, structure second** - Every framework encourages this. Don't skip it!
2. **Use git commits** - Commit after each major update. Your git history becomes your thinking log.
3. **Start small** - Don't try to set up everything at once. Use it, then improve it.
4. **Keep it updated** - Company Context should reflect current reality. Update it regularly.
5. **Share learnings** - If you improve a framework, consider contributing back!

---

## 🐛 Troubleshooting

### "I can't find a framework for X"

- Check `02-Methods-and-Tools/README.md` for navigation
- Search the repository for keywords

### "The AI assistant doesn't understand my question"

- Make sure you're in the repository directory
- Check that `AGENTS.md` (root) exists (this defines the PM Brain Coach)
- Try rephrasing your question more specifically

### "I'm overwhelmed by all the files"

- **Start with Company Context** - That's the most important
- **Pick one framework** - Try PRD or OKRs
- **Use it for real work** - You'll learn as you go

---

## ✨ You're Ready!

You've completed the setup. Now go build great products! 🚀

**Remember:** This is a living system. It should evolve with you. Don't be afraid to customize, experiment, and improve it.

---

**Questions?** Check the main `README.md` or explore the framework folders. The system is designed to be self-explanatory as you use it.

**Created by:** [Andreas Kelm](https://github.com/andreaskelm)  
**Last updated:** 2026-04-01
