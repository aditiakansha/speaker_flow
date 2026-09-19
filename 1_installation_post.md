# Git & VS Code — Post-Installation Setup

> Complete this after you have installed Git, VS Code, and Python.  
> These steps are the same for Windows, macOS, and Linux unless noted.

---

## Table of Contents

1. [Configure Git](#1-configure-git)
2. [Set Up the `code` Command](#2-set-up-the-code-command)
3. [Install GitLens](#3-install-gitlens)
4. [Set VS Code as Git's Default Editor](#4-set-vs-code-as-gits-default-editor)
5. [Verify Everything](#5-verify-everything)

---

## 1. Configure Git

Git needs to know who you are before it can track your commits. Open your terminal (Git Bash on Windows, Terminal on macOS/Linux) and run these three commands one at a time, replacing the placeholder text with your actual name and email:

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "you@example.com"
```
```bash
git config --global init.defaultBranch main
```

> Use the same email you use (or plan to use) for your GitHub account — this is how GitHub links your commits to your profile.

Then verify it worked:

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `init.defaultBranch` in the output.

---

## 2. Install GitLens

GitLens is a VS Code extension that shows Git history, inline blame, and branch activity directly in the editor.

1. Open VS Code
2. Click the Extensions icon in the left sidebar (or press `Ctrl + Shift + X`)
3. Search for **GitLens**
4. Click **Install**
5. If prompted to restart extensions, click **Restart Extensions**

You can also install GitLens directly from the terminal:

```bash
code --install-extension eamodio.gitlens
```

---

## 3. Verify Everything

Run these one by one and confirm each returns output:

```bash
git --version
git config --list
```

Your `git config --list` output should include:

```
user.name=Your Name
user.email=you@example.com
init.defaultbranch=main

```

If all of the above work and GitLens is visible in your Extensions sidebar, you are ready for the workshop.

