---
name: issue-to-pr
description: Turn a single, well-defined issue into a focused Git branch, small commits, and a review-ready pull request description.
ai: claude
version: 0.1.0
---

# 🔀 Issue → Pull Request

> **One-line summary:** Take one clearly scoped issue and deliver a branch with tested, focused commits plus a pull request description a reviewer can approve quickly.

| Field | Value |
|---|---|
| **Owner** | _your name_ |
| **Status** | `active` |
| **Inputs** | Issue title + description (pasted text or a link the user provides), access to the local Git repository |
| **Output** | A pushed-ready branch with commits, and a Markdown PR description |
| **Related** | [`shared/guides/writing-great-skills.md`](../../../shared/guides/writing-great-skills.md) |

---

<!-- ═══════════════════════════ PART A — CONTEXT ═══════════════════════════ -->

## 📘 Part A — Context

### 1. What the skill is

A repeatable path from *"here is an issue"* to *"here is a change ready for review."* It covers understanding the issue, making the smallest correct change on its own branch, verifying it with the project's existing checks, and writing a PR description that explains **what** changed and **why**. It does not merge anything or open the PR on a hosting service — it stops at a branch and a description the user can submit.

### 2. When to use it

✅ **Use this skill when:**

- The user hands over a bug report or feature request and says *"fix this"* / *"implement this"*
- The issue has a clear expected outcome (e.g., "the button should be disabled while saving")
- The change fits in one reviewable PR (roughly a few files, not a redesign)

🚫 **Do NOT use this skill when:**

- The issue is vague or is really several issues — ask the user to split or clarify first
- The work needs a design decision the user hasn't made (e.g., choosing between two architectures)
- The user only wants an explanation or a plan, not code changes

📋 **Prerequisites:**

- [ ] The project is a Git repository with a clean or committed working tree
- [ ] The issue text is available (pasted or readable)
- [ ] You know how the project runs its tests/checks (README, scripts, or ask)

---

<!-- ═══════════════════════════ PART B — PROCEDURE ═══════════════════════════ -->

## 🛠 Part B — How to do it

> [!IMPORTANT]
> Follow the steps in order. Do not move on until each **✔ Check** passes.

### Step 1 — Restate the issue

Summarize the issue in three lines: **current behavior**, **expected behavior**, **acceptance criteria**. If any of the three is unknown, ask the user before continuing.

**✔ Check:** The user could read your summary and agree it matches the issue.

### Step 2 — Confirm a clean starting point

```bash
git status
git switch main            # or the project's default branch
git pull                   # only if the repo has a remote and the user expects it
```

**✔ Check:** `git status` shows no uncommitted changes you didn't make. If it does, stop and ask.

### Step 3 — Create a focused branch

Name it `<type>/<issue-id>-<short-slug>`, where `<type>` is `fix`, `feat`, `docs`, or `chore`.

```bash
git switch -c fix/42-disable-save-button
```

**✔ Check:** `git branch --show-current` prints the new branch name.

### Step 4 — Locate the relevant code

Search for the feature, error message, or component named in the issue. Read the surrounding code and any existing tests before editing.

```bash
git grep -n "Save"          # adjust the search term to the issue
```

**✔ Check:** You can name the file(s) and function(s) you will change, and why.

### Step 5 — Reproduce or pin down the behavior

For a bug, write (or describe) a failing test or a manual reproduction. For a feature, write the test that describes the new behavior.

**✔ Check:** You have seen the failure (bug) or have a test that will prove the feature.

### Step 6 — Make the smallest correct change

Edit only what the issue requires. Match the existing code style. Avoid drive-by refactors — note them for a separate issue instead.

**✔ Check:** `git diff` contains only changes that trace back to the acceptance criteria.

### Step 7 — Run the project's checks

Run the test, lint, or build commands the project already uses (from its README or scripts). Do not invent new tooling.

**✔ Check:** All checks pass, *or* you report exactly which ones fail and why.

### Step 8 — Commit in small, meaningful pieces

```bash
git add -p                                   # stage hunks intentionally
git commit -m "Disable Save button while request is in flight (#42)"
```

Use imperative, present-tense messages that reference the issue.

**✔ Check:** `git log --oneline main..HEAD` reads like a short story of the change.

### Step 9 — Write the PR description

Use this structure:

```markdown
## Summary
Closes #<id>. <One sentence on what changed.>

## Why
<The problem from the issue, in one or two sentences.>

## What changed
- <Change 1>
- <Change 2>

## How to verify
1. <Step a reviewer can follow>
2. <Expected result>

## Notes
<Trade-offs, follow-ups, or anything not done.>
```

**✔ Check:** A reviewer who hasn't read the issue can understand and verify the change.

### ✅ Definition of done

- [ ] Branch exists with only issue-related commits
- [ ] Project checks pass (or failures are clearly reported)
- [ ] PR description is written and shared with the user
- [ ] Nothing has been pushed, merged, or published without the user's go-ahead

---

## 🛡 Guardrails

| ✅ Always | 🚫 Never |
|---|---|
| Work on a new branch | Commit directly to `main` / the default branch |
| Keep the diff scoped to the issue | Bundle unrelated refactors or formatting sweeps |
| Use the project's existing checks | Add new dependencies or tools without asking |
| Report failing checks honestly | Disable, skip, or delete tests to make them pass |
| Ask before `git push` | Force-push, rewrite shared history, or merge |
| Reference the issue in commits & PR | Include secrets, tokens, or personal data in code or messages |

> [!WARNING]
> **Stop and ask the user if:** the acceptance criteria are unclear · the working tree has someone else's uncommitted changes · the fix needs a design decision · checks were already failing before your change · the change grows beyond a single reviewable PR.

---

## 💡 Example

**Input**

```text
Issue #42 — Save button can be clicked twice
Clicking "Save" quickly twice creates duplicate records.
Expected: the button is disabled until the save request finishes.
```

**Walkthrough**

1. **Restate** → Current: double-click creates duplicates. Expected: button disabled while saving. Acceptance: one record per click burst; button re-enables after success or error.
2. **Clean start** → `git status` is clean on `main`.
3. **Branch** → `git switch -c fix/42-disable-save-button`
4. **Locate** → `git grep -n "onSave"` finds `src/components/SaveButton.js` and `tests/SaveButton.test.js`.
5. **Reproduce** → Add a test: "calls save once when clicked twice rapidly" → fails.
6. **Change** → Add an `isSaving` flag; set `disabled={isSaving}`; reset in `finally`.
7. **Checks** → Project test command passes, including the new test.
8. **Commits** →
   ```text
   a1b2c3d Add test for double-click on Save (#42)
   d4e5f6a Disable Save button while request is in flight (#42)
   ```
9. **PR description** → written (below).

**Output**

```markdown
## Summary
Closes #42. The Save button is now disabled while a save is in progress.

## Why
Rapid double-clicks sent two save requests and created duplicate records.

## What changed
- Added an `isSaving` state to `SaveButton`; the button is disabled while true
- State resets after success or error
- Added a regression test for rapid double-clicks

## How to verify
1. Open the form and click **Save** twice quickly
2. Exactly one record is created; the button re-enables afterward

## Notes
No API changes. Retry behavior on network errors is unchanged.
```

---

## 📝 Changelog

| Version | Date | Change |
|---|---|---|
| 0.1.0 | 2026-11-25 | Initial version |
