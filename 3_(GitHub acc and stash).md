# GitHub — Pushing Your Code Online

At this point you have a local Git repository with at least one commit. This section covers how to put that code on GitHub so it lives on the internet and others (or you, from another machine) can access it.

---

## 1. Create a GitHub Account

Go to [github.com](https://github.com) and click **Sign up**. You can sign up with your email or continue with Google.

---

## 2. SSH Setup for GitHub

Before pushing code, you need to connect your machine to GitHub securely using SSH.

### Windows (PowerShell)

**Generate SSH Key**
```powershell
ssh-keygen -t ed25519 -C "your@email.com" -f "$env:USERPROFILE\.ssh\github_ed25519"
```
Press Enter twice to skip the passphrase.

**Copy the Public Key**
```powershell
Get-Content "$env:USERPROFILE\.ssh\github_ed25519.pub" | Set-Clipboard
```

**Test the Connection**
```powershell
ssh -T -i "$env:USERPROFILE\.ssh\github_ed25519" git@github.com
```

### Mac (Terminal)

**Generate SSH Key**
```bash
ssh-keygen -t ed25519 -C "your@email.com" -f ~/.ssh/github_ed25519
```
Press Enter twice to skip the passphrase.

**Copy the Public Key**
```bash
pbcopy < ~/.ssh/github_ed25519.pub
```

**Test the Connection**
```bash
ssh -T -i ~/.ssh/github_ed25519 git@github.com
```

### Add Key to GitHub (both platforms)

1. Go to **GitHub > Settings > SSH and GPG keys**
2. Click **New SSH key**
3. Paste the key and save

You should see: `Hi username! You've successfully authenticated`

---

## 3. Create a New Repository

A repository on GitHub is where your project lives online. Think of it as the cloud version of the folder on your laptop.

Fill in the details:

**Repository name** — keep it short and clear. No spaces, use hyphens instead (e.g. `my-project`).

**Description** — a one-line summary of what the project does. Optional but worth filling in.

**Public vs Private**
- Public means anyone on the internet can view your code. Good for portfolios, open source, or anything you want to show.
- Private means only you and people you invite can see it.

**Add README** — leave this off for now because you already have files locally. Creating one here would cause a conflict when you push.

**Add .gitignore** — tells Git which files to never track. Select the template matching your language.

**Add license** — MIT is the most common choice for open source. It lets anyone use, copy, and modify your code as long as they give you credit.

Click **Create repository**.

---

## 4. Connect Your Local Repo to GitHub

After creating the repo, GitHub shows an empty repository page. Copy your repo URL from the browser and run:

```bash
git remote add origin "https://github.com/yourusername/reponame"
```

This tells your local Git repo where to send your code. The name `origin` is just a convention everyone uses for their main remote.

To confirm the connection:

```bash
git remote -v
```

If you see your GitHub link, you are good to go.

---

## 5. Push Your Code to GitHub

```bash
git push -u origin main
```

This sends all your local commits up to GitHub. Your files are now online.

The `-u` flag sets up a permanent link between your local `main` branch and the one on GitHub. You only need it on your very first push. After that just run:

```bash
git push
```

---

## 6. See Your Files on GitHub

Refresh the GitHub page in your browser. Your files are now live.

---

## 7. Edit a File Directly on GitHub

You can make changes to files right in the browser without going back to your terminal. This is useful for quick edits and simulates what happens when a teammate makes a change you do not have locally yet.

Click on `calc.py` in the file list, then click the pencil icon in the top right corner. Delete the `subtract` function, then scroll down and click **Commit changes**.

That change now exists on GitHub but not on your local machine. This is exactly what `git fetch` and `git pull` are designed to handle.

---

## 8. git fetch

`git fetch` checks GitHub for any new changes and downloads information about them but does not touch your local files. You are just asking Git to look at what is new and make a note of it.

```bash
git fetch
```

---

## 9. git pull

`git pull` brings the changes from GitHub into your local machine and applies them. It is fetch and merge in a single step.

```bash
git pull
```

After this runs, open `calc.py` and the subtract function is gone. Your local file now matches what is on GitHub.

**fetch vs pull**

Use `git fetch` when you want to see what changed before deciding what to do. Use `git pull` when you are ready to bring those changes in. In day-to-day work most people just run `git pull` directly.

> ![git pull meme](assets/RSuqRY6cb.jpeg.webp)
> Always commit your changes before pulling, and fetch first to see what is coming.

---

## 10. git stash

Sometimes you are in the middle of a change and something else comes up. Your work is half done and you are not ready to commit it. `git stash` takes all your uncommitted changes and puts them into a temporary pocket, leaving your working directory clean.

```bash
git stash
```

```bash
git status
```

Nothing to commit, working tree clean. You can now safely switch branches or pull without your unfinished work getting in the way.

When you are ready to come back:

```bash
git stash pop
```

```bash
git stash list
```

Empty, because `git stash pop` already consumed it. Run `git stash list` before `git stash pop` if you want to show a non-empty list during a demo.

---

## Quick Reference

| What you want to do | Command |
|---------------------|---------|
| Connect repo to GitHub | `git remote add origin <url>` |
| Check the connection | `git remote -v` |
| First push | `git push -u origin main` |
| Every push after | `git push` |
| See what changed on GitHub | `git fetch` |
| Bring GitHub changes to your machine | `git pull` |
| Save unfinished work temporarily | `git stash` |