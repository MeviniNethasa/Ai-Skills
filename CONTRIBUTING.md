# Contributing

There are two ways to contribute. Both use [`templates/SKILL_TEMPLATE.md`](templates/SKILL_TEMPLATE.md).

---

## Path A: Add a skill to an existing AI

1. Open the AI's `skills/` folder, for example `claude/skills/`.
2. Create a new folder named after the skill, for example `summarize-meeting`.
3. Copy `templates/SKILL_TEMPLATE.md` into that folder and rename it `SKILL.md`.
4. Fill in each section and delete the placeholder text.
5. Add the skill to the list in that AI's `README.md`.

```text
claude/
└── skills/
    └── summarize-meeting/
        └── SKILL.md
```

---

## Path B: Add a new AI tool

1. Create a new top-level folder named after the tool, for example `cursor/` or `gemini/`.
2. Inside it, add a `README.md` with one or two lines about the tool.
3. Inside it, add an empty `skills/` folder.
4. Add skills the same way as Path A.
5. Add the new folder to the **Folders** table in the main [`README.md`](README.md).

```text
gemini/
├── README.md
└── skills/
```

---

## Naming Tips

| Item | Rule | Example |
|---|---|---|
| AI folder | lowercase | `gemini/` |
| Skill folder | lowercase words joined by dashes | `summarize-meeting/` |
| Skill file | always `SKILL.md` | `SKILL.md` |

If a guide applies to every AI tool, put it in `shared/guides/` instead of an AI folder.
