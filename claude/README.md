# 🟣 Claude Skills

> Skills written for Claude. Each one lives in `skills/<skill-name>/SKILL.md` and follows [`templates/SKILL_TEMPLATE.md`](../templates/SKILL_TEMPLATE.md).

---

## 📚 Skill Index

| Skill | Status | Summary |
|---|---|---|
| [`issue-to-pr`](skills/issue-to-pr/SKILL.md) | `active` | Turn a well-defined issue into a focused branch, commits, and a PR description |

---

## ➕ Add a Claude Skill

```bash
mkdir -p claude/skills/<skill-name>
cp templates/SKILL_TEMPLATE.md claude/skills/<skill-name>/SKILL.md
```

Then add a row to the table above and to the catalog in the root [`README.md`](../README.md#-skill-catalog).

> [!TIP]
> Keep the `name` and `description` frontmatter accurate — the description is the quickest way for a reader (human or AI) to decide whether the skill applies.
