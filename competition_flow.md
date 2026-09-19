# Competition: Program Flow

---

## The Flow


1. Fork the repo
2. Clone your fork to your local machine
3. Solve the issue
4. Open a Pull Request


That is the entire loop. Four steps. No extra setup, no new tools.

---

## Step by Step

**1. Fork**

Go to the competition repository on GitHub and click Fork. This creates a copy of the repo under your own GitHub account. You work on your copy, not the original.

**2. Clone**

```bash
git clone https://github.com/yourusername/repo-name
cd repo-name
```

This brings your fork down to your local machine so you can actually edit the code.

**3. Solve the Issue**

Read the issue carefully. Understand what is broken before you touch anything. Make your fix on a feature branch, not on `main`.

```bash
git checkout -b fix/issue-description
```

Fix only what the issue describes. Do not refactor unrelated code, do not rename files, do not reformat things. Small, focused, clean.

**4. Open a Pull Request**

Push your branch and open a PR from your fork to the original repo.

```bash
git add .
git commit -m "fix: describe what you fixed"
git push origin fix/issue-description
```

---

## The PR Description Rule

This is not optional.

Your PR description **must** include a closing keyword linked to the issue number. GitHub recognises these:

```
Fixes #12
Closes #12
Resolves #12
```

Use any one of them, followed by the issue number. This links your PR to the issue and closes it automatically when merged.

**If your PR description does not have this, it will not be considered.**

---

## How Points Are Awarded

**Merged solution** — for each issue, the most optimal PR gets merged. The participant whose PR is merged earns points for that issue.

**Bonus points** — if your solution is exceptionally clean, well-structured, or goes beyond what was expected, the judges can award additional points manually even if your PR was not the one merged.

---

## What Makes a Solution Optimal

- The bug is actually fixed and the code works
- The fix is clean and readable
- You touched only what needed to be touched
- Commit follows conventional commits: `fix: describe what you fixed`
- PR description includes `Fixes #issue-number`

The best fixes are the smallest ones.