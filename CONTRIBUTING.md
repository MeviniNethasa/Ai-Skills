# 🤝 Contributing

> How to add, update, or retire a skill in this repository.

---

## ➕ Add a Skill

| Step | Action |
|:-:|---|
| 1 | Pick the AI folder (`claude/`, `antigravity/`, …) — or `shared/` for cross-AI guides |
| 2 | `mkdir -p <ai>/skills/<skill-name>` |
| 3 | `cp templates/SKILL_TEMPLATE.md <ai>/skills/<skill-name>/SKILL.md` |
| 4 | Fill in every section; delete any placeholder text in _italics_ |
| 5 | Add a row to `<ai>/README.md` **and** the root `README.md` catalog |
| 6 | Run through the [review checklist](shared/guides/writing-great-skills.md#-review-checklist) |
| 7 | Commit on a branch: `git switch -c add/<skill-name>` |

---

## ✏️ Update a Skill

- Bump `version` in the frontmatter (`0.1.0` → `0.2.0` for new steps, `0.1.1` for wording fixes)
- Add a row to the skill's **Changelog**
- Keep the example in sync with the steps

## 🗄 Retire a Skill

- Set **Status** to `deprecated` and add a note pointing to the replacement
- Leave it in place for one release cycle, then remove it and its catalog rows

---

## 📐 Naming

| Item | Convention | Example |
|---|---|---|
| AI folder | lowercase | `claude/` |
| Skill folder | `kebab-case`, verb or outcome | `issue-to-pr/` |
| Main file | always `SKILL.md` | — |
| Branch | `add/`, `update/`, `remove/` + skill name | `add/issue-to-pr` |
| Commit | imperative, present tense | `Add issue-to-pr skill for Claude` |
