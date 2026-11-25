# AI Skills

A shared library of step-by-step skills for the AI tools our team uses. Each skill is one Markdown file that explains what a task is, when to use it, and exactly how to do it.

---

## Folder Structure

```text
AI_skills/
├── README.md
├── CONTRIBUTING.md
├── templates/
│   └── SKILL_TEMPLATE.md
├── claude/
│   ├── README.md
│   └── skills/
│       └── issue-to-pr/
│           └── SKILL.md
├── antigravity/
│   ├── README.md
│   └── skills/
└── shared/
    ├── README.md
    └── guides/
        └── writing-great-skills.md
```

---

## Folders

| Folder | What it holds |
|---|---|
| [`claude/`](claude/README.md) | Skills for Claude |
| [`antigravity/`](antigravity/README.md) | Skills for Antigravity |
| [`shared/`](shared/README.md) | Guides that apply to every AI tool |
| [`templates/`](templates/SKILL_TEMPLATE.md) | The template every new skill starts from |

---

## How to Contribute

Every skill starts from [`templates/SKILL_TEMPLATE.md`](templates/SKILL_TEMPLATE.md).

### Path A: Add a skill to an existing AI

1. Open the AI's `skills/` folder, for example `claude/skills/`.
2. Create a new folder named after the skill, for example `summarize-meeting`.
3. Copy `templates/SKILL_TEMPLATE.md` into that folder and rename it `SKILL.md`.
4. Fill in each section.

### Path B: Add a new AI tool

1. Create a new top-level folder named after the tool, for example `cursor/` or `gemini/`.
2. Inside it, add a short `README.md` and an empty `skills/` folder.
3. Add skills to it the same way as Path A.
4. Add the new folder to the **Folders** table above.

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for a few naming tips.
