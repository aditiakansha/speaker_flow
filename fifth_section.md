# Open Source & CI/CD

---

## What is Open Source?

Open source means the code is public. Anyone can read it, use it, suggest changes, or build on top of it.

Most of the tools you use every day are open source: VS Code, Python, React, Linux. They are not built by one company behind closed doors. They are built by thousands of developers around the world contributing to a shared codebase on GitHub.

When you contribute to an open source project, your name goes into the commit history of software that might be used by millions of people. It is also one of the best things you can put on a resume as a developer: real code, in a real project, reviewed by real engineers.

![What is Open Source](https://i.postimg.cc/GpGRS7NM/image.png)

---

## Examples of Open Source Projects

These are all public repositories on GitHub that anyone can contribute to:

**[facebook/react](https://github.com/facebook/react)** — the JavaScript library that powers Facebook, Instagram, and thousands of other apps.

**[microsoft/vscode](https://github.com/microsoft/vscode)** — VS Code itself. The editor you have been using this entire workshop is open source.

**[python/cpython](https://github.com/python/cpython)** — the Python programming language. The language runs open source.

**[torvalds/linux](https://github.com/torvalds/linux)** — the Linux kernel. Started by one person in 1991, now maintained by thousands.

**[home-assistant/core](https://github.com/home-assistant/core)** — a home automation platform built entirely by volunteers.

The pattern is the same for all of them. Code lives on GitHub. Anyone can open an issue, suggest a fix, or submit a pull request. Maintainers review and decide what goes in.

![Open Source Projects That Changed the World](https://i.postimg.cc/Kc96Qhzd/0029-15-open-source-projects-that-changed-the-world.png)

---

## Open Source Best Practices

Before you contribute to any project, or run your own, these are the standards the open source world follows.

---

### Files Every Good Repo Should Have

**README.md** — the homepage of your project. It should explain what the project does, how to install it, and how to run it. If someone lands on your repo and cannot figure out what it is in 30 seconds, the README is not good enough.

**CONTRIBUTING.md** — a guide for people who want to contribute. It covers how to report bugs, how to set up the project locally, what branch to work on, how to name commits, and how to open a pull request. Without this, new contributors have no idea where to start.

**LICENSE** — tells people what they are legally allowed to do with your code. MIT is the most common open source license. It lets anyone use, copy, and modify your code as long as they credit you.

**.gitignore** — tells Git which files to never track. Things like `node_modules/`, `.env`, `__pycache__/`, compiled binaries. These should never go into version control.

**CHANGELOG.md** — a record of what changed in each release. When you ship a new version, you write a short entry here saying what was added, fixed, or removed.

**.github/workflows/** — this is where your automated pipeline lives. More on this below.

---

### Branching

A clean branch structure keeps a project from turning into chaos when multiple people are working at the same time.

```
main          — stable, production-ready code only
dev           — active development happens here
feature/name  — one branch per feature or bug fix
```

Never push directly to `main`. Work happens on feature branches. Those branches get reviewed via a pull request before anything reaches `main`. This protects the stable version of the project at all times.

---

### Commit Messages: Conventional Commits

Conventional commits is a standard format for writing commit messages that the entire open source world has adopted. It makes history readable and allows tools to auto-generate changelogs.

```
feat: add login page
fix: correct typo in navbar
docs: update README
chore: update dependencies
refactor: simplify auth logic
test: add unit tests for cart
```

The format is `type: short description`. The type tells anyone reading the history what kind of change it was without having to open the diff.

---

### Pull Requests

A pull request (PR) is how you propose a change to a project. You push your feature branch to GitHub, then open a PR asking the maintainers to review and merge it.

- Never merge your own PR. Someone else always reviews it.
- Keep PRs small and focused on one thing. A PR that changes 20 files across 5 features is impossible to review well.
- Write a clear description: what changed, why, and how to test it.
- If the project has a PR template, fill it out fully.

---

### Issues

Issues are how bugs get reported and features get requested. Good projects label their issues so contributors know what to pick up.

Common labels:
- `bug` — something is broken
- `enhancement` — a new feature request
- `documentation` — something needs to be written or updated
- `good first issue` — specifically tagged for newcomers. These are simpler, well-scoped tasks that do not require deep knowledge of the codebase. This is where you should start when contributing to any project for the first time.

---

## What is CI/CD?

Think of CI/CD like the quality checks at a factory assembly line. Every product that comes off the line gets tested automatically before it ships. If it fails the test, it does not go out. No one has to remember to check manually; the process runs on its own every single time.

That is exactly what CI/CD does for code.

**CI: Continuous Integration**

Every time someone pushes code or opens a pull request, a set of automated tests runs automatically. If the tests fail, the PR cannot be merged. This catches bugs before they reach `main`.

**CD: Continuous Deployment**

Once tests pass and the PR is merged, the code is automatically deployed to production. No one has to manually upload files or run a deploy script.

The full flow looks like this:

```
Push code → tests run automatically → if all pass → deploys
                                     → if any fail → blocks the merge
```

No manual steps. No "works on my machine." Every change is tested the same way, every time.

![CI/CD Pipeline](https://i.postimg.cc/Vv1kRQkh/ci-cd.png)

---

## GitHub Actions

GitHub Actions is the CI/CD tool built directly into GitHub. You do not need to sign up for any external service or connect anything. You write one `.yml` file, drop it into `.github/workflows/`, and GitHub picks it up automatically.

```
your-project/
└── .github/
    └── workflows/
        └── main.yml
```

Every time you push or open a PR, GitHub spins up a fresh virtual machine in the cloud, runs the steps you defined in that file, and reports back with a pass or fail. You can see the results live in the Actions tab of your repo.

You can also have multiple workflow files for different jobs: one for running tests, one for checking code style, one for deploying. They all live in the same folder and run independently.

A basic workflow file looks like this:

```yaml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install
      - run: npm test
```

Breaking it down:

`on: [push, pull_request]` — when to run this. Every push and every PR triggers it.

`runs-on: ubuntu-latest` — GitHub spins up a fresh Ubuntu machine to run your code in.

`uses: actions/checkout@v3` — downloads your repo onto that machine so the next steps can use it.

`run: npm install` — installs dependencies.

`run: npm test` — runs your test suite. If any test fails, the whole workflow fails and GitHub blocks the merge.

When you open a PR, you will see a section at the bottom showing whether the checks passed or failed. That is GitHub Actions running in real time.

---

## Walking Through a Real Repo: facebook/react

**Link: [github.com/facebook/react](https://github.com/facebook/react)**

Here is what to look at and in what order:

**1. CONTRIBUTING.md** — open this from the root of the repo. It tells you exactly how the React team expects contributions, how to set up the project locally, and what the PR process looks like. Every serious open source project has one of these.

**2. A merged pull request** — click Pull Requests, filter by Closed, open any merged PR. Scroll to the bottom and you will see the CI checks that ran automatically: tests, linting, type checks. All had to pass before it could be merged.

**3. Issues filtered by `good first issue`** — click Issues and filter by that label. These are the tasks the React team has specifically flagged as suitable for new contributors. This is where you start.

**4. The .github/workflows/ folder** — navigate into it from the file list and open any `.yml` file. You will see the same structure as the example above. This is the actual CI pipeline that runs on every PR to React.

---

## The Open Source Contribution Loop

```
1. Fork the repo          — makes a copy under your GitHub account
2. Clone your fork        — brings it to your local machine
3. Create a feature branch
4. Make your change
5. git add . && git commit -m "feat: describe your change"
6. git push origin your-branch
7. Open a Pull Request    — from your fork to the original repo
8. CI runs automatically  — tests run on your PR
9. Maintainer reviews     — they may request changes
10. PR gets merged        — your code is now part of the project
```

Every open source contribution in the world follows this loop.

---

## Competition: What to Expect

You will be given a repository with intentional bugs in it. Your job is to find them, fix them, and submit a pull request with your changes.

**What will be evaluated:**
- Whether the bug is actually fixed and the code works
- How clean and readable your fix is
- Your commit message: does it follow conventional commits?
- Your PR description: is it clear what you changed and why?
- Whether you touched only what needed to be touched

**The mindset:** you are not building something from scratch. You are reading someone else's code, understanding it well enough to find what is wrong, and fixing it cleanly. The best fixes are the smallest ones.

A good repo to practice on before the competition: **[firstcontributions/first-contributions](https://github.com/firstcontributions/first-contributions)** — specifically designed to walk you through the fork → clone → branch → PR cycle with no pressure.

---

## Quick Reference

```bash
# Fork on GitHub (done in the browser), then clone your fork:
git clone https://github.com/yourusername/repo-name

# Create a feature branch
git checkout -b fix/bug-description

# Make your changes, then:
git add .
git commit -m "fix: describe what you fixed"
git push origin fix/bug-description

# Then open a Pull Request on GitHub from your branch
```

| Term | What it means |
|------|--------------|
| Fork | Your own copy of someone else's repo on GitHub |
| Clone | Download a repo to your local machine |
| PR | A request to merge your branch into the main project |
| CI | Automated tests that run on every push or PR |
| CD | Automatic deployment after tests pass |
| `good first issue` | Issues tagged for new contributors |