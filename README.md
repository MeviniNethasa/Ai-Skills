<div align="center">

# 🧠 AI Skills & Workflows

**One home for reusable, step-by-step skills across multiple AI assistants.**

![Format: Markdown](https://img.shields.io/badge/format-Markdown-000?logo=markdown)
![Versioned with Git](https://img.shields.io/badge/versioned%20with-Git-F05032?logo=git&logoColor=white)
![AI folders: 2](https://img.shields.io/badge/AI%20folders-2-6E56CF)
![Skills: 1](https://img.shields.io/badge/skills-1-2EA44F)
![Status: Starter](https://img.shields.io/badge/status-starter-blue)

[Structure](#-structure) · [AI Index](#-ai-folder-index) · [Quick Start](#-quick-start) · [Conventions](#-conventions) · [Skill Catalog](#-skill-catalog)

</div>

---

## ✨ What This Is

A plain-Markdown, Git-friendly library of **skills**: small, self-contained playbooks that tell an AI assistant *what* a task is, *when* to use it, and *exactly how* to do it.

- 📁 **One folder per AI** — keep assistant-specific skills separate
- 🔁 **Shared guides** — write cross-AI knowledge once, link it everywhere
- 🧩 **One template** — every skill has the same predictable shape
- 🪶 **Zero tooling** — just Markdown files and Git history

> [!NOTE]
> Nothing here requires a build step, package manager, or plugin. If you can read Markdown and run `git`, you can use and extend this repo.

---

## 🗂 Structure

```text
ai-skills/
├── README.md                     ← you are here
├── CONTRIBUTING.md               ← how to add or change a skill
│
├── templates/
│   └── SKILL_TEMPLATE.md         ← copy this to start any new skill
│
├── claude/
│   ├── README.md                 ← Claude-specific notes + skill index
│   └── skills/
│       └── issue-to-pr/
│           └── SKILL.md          ← sample complete skill
│
├── antigravity/
│   ├── README.md                 ← Antigravity-specific notes + skill index
│   └── skills/
│       └── .gitkeep              ← empty for now
│
└── shared/
    ├── README.md                 ← index of shared material
    └── guides/
        └── writing-great-skills.md
```

| Path | Purpose | Contains | Edit when… |
|---|---|---|---|
| `README.md` | Front door & index | Overview, catalog | You add an AI folder or skill |
| `CONTRIBUTING.md` | House rules | Naming, review checklist | Conventions change |
| `templates/` | Starting points | `SKILL_TEMPLATE.md` | The skill format evolves |
| `claude/` | Claude skills | `skills/<name>/SKILL.md` | Adding a Claude skill |
| `antigravity/` | Antigravity skills | `skills/<name>/SKILL.md` | Adding an Antigravity skill |
| `shared/` | Cross-AI knowledge | Guides, checklists | Knowledge applies to every AI |

---

## 🤖 AI Folder Index

| AI | Folder | Skills | Notes |
|---|---|:---:|---|
| 🟣 **Claude** | [`claude/`](claude/README.md) | 1 | Starter skill: [`issue-to-pr`](claude/skills/issue-to-pr/SKILL.md) |
| 🔵 **Antigravity** | [`antigravity/`](antigravity/README.md) | 0 | Ready for your first skill |
| 🟢 **Shared** | [`shared/`](shared/README.md) | — | Guides used by every AI folder |

> [!TIP]
> Adding another assistant? Create `<ai-name>/README.md` and `<ai-name>/skills/`, then add a row to the table above.

---

## 🚀 Quick Start

**1. Copy the template into the right AI folder**

```bash
mkdir -p claude/skills/my-new-skill
cp templates/SKILL_TEMPLATE.md claude/skills/my-new-skill/SKILL.md
```

**2. Fill in the sections** — keep *What / When* separate from *How*.

**3. Register it** — add a row to the AI folder's `README.md` and to the [Skill Catalog](#-skill-catalog) below.

**4. Commit it**

```bash
git add claude/skills/my-new-skill
git commit -m "Add my-new-skill for Claude"
```

---

## 📐 Conventions

| Rule | Example |
|---|---|
| Skill folders use `kebab-case` | `issue-to-pr/` |
| Each skill lives in its own folder | `claude/skills/issue-to-pr/SKILL.md` |
| The main file is always `SKILL.md` | — |
| Extra files sit beside `SKILL.md` | `examples.md`, `checklist.md` |
| Cross-AI content goes in `shared/` and is linked, not copied | `../../shared/guides/…` |

Every `SKILL.md` follows the same skeleton:

```text
1. What the skill is        ┐
2. When to use it           ┘  ← context: read first, decide if it applies
3. How to do it (steps)     ← the procedure
4. Guardrails               ← must / must-not rules
5. Example                  ← one worked run-through
```

➡️ Full details: [`CONTRIBUTING.md`](CONTRIBUTING.md) · [`shared/guides/writing-great-skills.md`](shared/guides/writing-great-skills.md)

---

## 📚 Skill Catalog

| Skill | AI | Summary |
|---|---|---|
| [`issue-to-pr`](claude/skills/issue-to-pr/SKILL.md) | 🟣 Claude | Turn a well-defined issue into a focused branch, commits, and a review-ready pull request description |

---

<div align="center">

<sub>Plain Markdown · Versioned with Git · Built to be copied</sub>

</div>
