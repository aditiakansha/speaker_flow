# 🍴 Fork-This Competition — Participant Guide

Welcome! This competition is about finding and fixing real issues in our repository. Follow the steps below from start to finish.

## How It Works

1. **Browse the Issues**
   Go to the repository's **Issues** tab and pick an open issue you want to solve. Make sure it's not already assigned or being worked on by someone else.

2. **Fork the Repository**
   Click the **Fork** button (top-right of the repo page) to create your own copy under your GitHub account.

3. **Clone Your Fork Locally**
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```

4. **Create a Branch (recommended)**
   You can work directly on your fork's `main` branch, but creating a dedicated branch keeps things clean:
   ```bash
   git checkout -b fix/issue-<issue-number>
   ```

5. **Debug and Fix**
   Make your changes, test them locally, and confirm the issue is resolved.

6. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Fix: <short description of the fix>"
   git push origin fix/issue-<issue-number>
   ```

7. **Open a Pull Request**
   - Go to the original repository (not your fork).
   - Click **New Pull Request** → **compare across forks**.
   - Select your fork and branch as the source.
   - In the **PR description**, you must include:
     ```
     Fixes issue #<issue-number>
     ```
     (Replace `<issue-number>` with the actual issue number you solved.)

## PR Description Template

```markdown
## Summary
Briefly describe what was wrong and how you fixed it.

## Changes
- Change 1
- Change 2

## Testing
Explain how you verified the fix works.

Fixes issue #<issue-number>
```

## Rules & Notes

- ✅ One issue per PR — don't bundle multiple fixes together.
- ✅ Always reference the issue number using `Fixes issue #<number>` (this auto-links and closes the issue when merged).
- ✅ Keep commits clean and descriptive.
- ❌ Don't submit PRs without linking an issue.
- ❌ Don't edit unrelated files.

Good luck, and happy debugging! 🚀
