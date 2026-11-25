# ✍️ Writing Great Skills

> A short guide to making skills that are easy to find, easy to follow, and safe to run.

---

## 🧭 The Core Idea

A skill answers three questions, **in this order**:

| # | Question | Section | Tone |
|:-:|---|---|---|
| 1 | What is this? | **What the skill is** | Descriptive |
| 2 | Should I use it right now? | **When to use it** | Decisive |
| 3 | How exactly do I do it? | **How to do it** | Imperative |

> [!IMPORTANT]
> Keep **context** (1–2) and **procedure** (3) separate. A reader should be able to decide *whether* to use a skill without wading through *how*.

---

## ✅ Do

- **Start steps with a verb** — "Create a branch", not "A branch should be created"
- **Give every step a check** — how do you know it worked?
- **Name the stop conditions** — when should the AI pause and ask?
- **Show one real example** — input → walkthrough → output
- **Link, don't duplicate** — point to `shared/` guides instead of copying them

## 🚫 Don't

- Mix "when" conditions into the steps
- Write steps that depend on tools the project doesn't already use
- Hide risky actions (push, delete, publish) inside a step without a guardrail
- Let one skill do several unrelated jobs — split it

---

## 📏 Size Guide

| Part | Target |
|---|---|
| What the skill is | 2–4 sentences |
| When to use it | 3–5 bullets each for ✅ / 🚫 |
| Steps | 3–8 steps |
| Guardrails | 3–6 rows |
| Example | 1 complete run |

---

## 🔍 Review Checklist

- [ ] Frontmatter `name` matches the folder name
- [ ] `description` says what it does **and** when to trigger it
- [ ] Part A contains no instructions; Part B contains no background essays
- [ ] Every step has a **✔ Check**
- [ ] Guardrails cover anything irreversible
- [ ] The example matches the steps exactly
- [ ] The skill is listed in its AI folder README and the root catalog
