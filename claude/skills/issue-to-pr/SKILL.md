---
name: issue-to-pr
description: Turn a single, clear issue into a Git branch, small commits, and a pull request description ready for review.
---

# Issue to Pull Request

---

## What This Skill Does

Takes one clearly described issue and turns it into a change ready for review. It covers understanding the issue, making the smallest correct change on its own branch, checking it with the project's existing tests, and writing a pull request description. It stops there: it does not push, merge, or open the pull request.

---

## When to Use It

**Use it when:**

- Someone shares a bug report or feature request and asks you to fix or build it.
- The issue has a clear expected result, for example "the button should be disabled while saving".
- The change fits in one pull request, a few files rather than a redesign.

**Do not use it when:**

- The issue is vague or is really several issues. Ask for it to be clarified or split first.
- The work needs a design decision nobody has made yet.
- The person only wants an explanation or a plan, not code changes.

**Before you start, you need:**

- A Git repository with no unsaved changes from someone else.
- The issue text.
- To know how the project runs its tests (check its README, or ask).

---

## How to Do It (Step-by-Step)

1. **Restate the issue.** Write three lines: what happens now, what should happen, and how you will know it is fixed. If any of these is unclear, ask before going further.
   Check: The person agrees your summary matches the issue.

2. **Start from a clean state.** Run `git status` and switch to the main branch.
   Check: `git status` shows no changes you did not make. If it does, stop and ask.

3. **Create a branch.** Name it after the issue, for example `fix/42-disable-save-button`.
   Check: `git branch --show-current` shows the new branch name.

4. **Find the relevant code.** Search for the feature, error message, or component named in the issue. Read the code and its tests before editing.
   Check: You can name the files you will change and why.

5. **Reproduce the problem.** For a bug, write a test that fails. For a feature, write a test that describes the new behavior.
   Check: You have seen the test fail.

6. **Make the smallest correct change.** Change only what the issue needs, in the existing code style. Note any other improvements for a separate issue.
   Check: `git diff` shows only changes related to the issue.

7. **Run the project's tests.** Use the commands the project already uses.
   Check: All tests pass, or you report exactly which ones fail and why.

8. **Commit.** Use short messages that describe the change and mention the issue, for example `Disable Save button while saving (#42)`.
   Check: `git log --oneline` reads like a short summary of the change.

9. **Write the pull request description.** Use the format in the example below: Summary, Why, What changed, How to check.
   Check: Someone who has not read the issue can understand and check the change.

**Done when:**

- The branch contains only commits for this issue.
- Tests pass, or failures are clearly reported.
- The pull request description has been shared with the person.

---

## Rules

| Always | Never |
|---|---|
| Work on a new branch | Commit directly to the main branch |
| Keep changes limited to the issue | Mix in unrelated cleanups |
| Use the project's existing tests | Add new tools or dependencies without asking |
| Report failing tests honestly | Skip or delete tests to make them pass |
| Ask before pushing | Force-push or merge |

**Stop and ask if:** the expected result is unclear, the repository has someone else's unsaved changes, the fix needs a design decision, tests were already failing before your change, or the change is growing beyond one pull request.

---

## Example

**Input:**

```text
Issue #42: Save button can be clicked twice
Clicking "Save" quickly twice creates duplicate records.
Expected: the button is disabled until saving finishes.
```

**Steps taken:**

1. Restated: double-click creates duplicates; button should be disabled while saving; one record per click and the button re-enables afterward.
2. `git status` was clean on the main branch.
3. Created the branch `fix/42-disable-save-button`.
4. Found `src/components/SaveButton.js` and its test file.
5. Added a test, "calls save once when clicked twice quickly". It failed.
6. Added an `isSaving` flag that disables the button and resets when saving finishes.
7. Ran the project's tests. All passed, including the new one.
8. Made two commits: one for the test, one for the fix.
9. Wrote the pull request description below.

**Result:**

```markdown
## Summary
Closes #42. The Save button is now disabled while saving.

## Why
Clicking Save twice quickly sent two requests and created duplicate records.

## What changed
- Added an `isSaving` state to `SaveButton`; the button is disabled while it is true
- The state resets after success or error
- Added a test for quick double-clicks

## How to check
1. Open the form and click Save twice quickly
2. Only one record is created, and the button works again afterward
```
