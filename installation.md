# 🛠️ Git & GitHub Workshop — Pre-Workshop Setup Manual

> **Please complete this BEFORE you arrive at the workshop.**  
> The session moves fast — if Git isn't installed, you'll fall behind in the first 15 minutes.  
> If you get stuck at any step, ping us on the group and we'll help you sort it out.

---

## 📋 Table of Contents

1. [What You're Installing & Why](#1-what-youre-installing--why)
2. [macOS — Installing Git via Homebrew](#2-macos--installing-git-via-homebrew)
3. [Linux — Installing Git via APT](#3-linux--installing-git-via-apt)
4. [Windows — Installing Git](#4-windows--installing-git)
5. [Configuring Git (All Platforms)](#5-configuring-git-all-platforms)
6. [Setting Up VS Code Integration](#6-setting-up-vs-code-integration)
7. [Verify Everything Works](#7-verify-everything-works)
8. [Common Issues & Fixes](#8-common-issues--fixes)
9. [Quick Reference Cheatsheet](#9-quick-reference-cheatsheet)

---

## 1. What You're Installing & Why

| Tool | What it is | Why you need it |
|------|-----------|-----------------|
| **Git** | A version control system | Tracks changes to your code, lets you collaborate |
| **Homebrew** (Mac only) | A package manager for macOS | Makes installing developer tools like Git simple |
| **VS Code** | Code editor | Where you'll write code — we'll connect it to Git |

> **Not sure which OS you have?**  
> - Mac: Apple logo top-left → "About This Mac"  
> - Windows: Start → Settings → System → About  
> - Linux: You already know. 😄

---

## 2. macOS — Installing Git via Homebrew

> 🎬 **Video walkthrough:** https://www.youtube.com/watch?v=flQxyoyBX5M  
> 🎬 **Apple Silicon (M1/M2/M3/M4) specific:** [EASY Homebrew Installation on Apple Silicon](https://www.youtube.com/watch?v=4JMIfljw7GA)

---

### Step 1 — Open Terminal

Press **`Cmd + Space`** to open Spotlight Search, type **Terminal**, and hit Enter.

> Terminal is your command-line interface. Don't worry if it looks intimidating — you'll be using just a handful of commands.

---

### Step 2 — Install Homebrew

Paste the following command into Terminal and press **Enter**:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

What happens next:

1. It will ask for your **Mac login password**. Type it and press Enter.  
   ⚠️ You won't see any characters as you type — that's completely normal. Just type your password and press Enter.

2. It will ask you to **press Enter** to confirm the installation. Do that.

3. It will download and install everything on its own. **This takes 2–5 minutes.** Don't close the terminal.

---

### Step 3 — Run the two post-install commands

When Homebrew finishes, it will display something like this at the bottom:

```
==> Next steps:
Run these two commands in your terminal to add Homebrew to your PATH:
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
```

**Copy those two commands from YOUR terminal output** (not from here — they may differ slightly based on your Mac model) and run them one by one.

> ⚠️ This step is critical. Without it, your terminal won't recognise the `brew` command.

---

### Step 4 — Verify Homebrew installed correctly

```bash
brew --version
```

You should see something like: `Homebrew 4.x.x`

If you see that, Homebrew is working. ✅

---

### Step 5 — Install Git

```bash
brew install git
```

---

### Step 6 — Verify Git is installed

```bash
git --version
```

Expected output: `git version 2.x.x`  ✅

---

## 3. Linux — Installing Git via APT

> This guide is for **Ubuntu / Debian-based** distributions (Ubuntu, Pop!_OS, Linux Mint, etc.).  
> If you're on Arch, Fedora, or another distro, use your respective package manager (`pacman -S git`, `dnf install git`, etc.).

---

### Step 1 — Open Terminal

Press **`Ctrl + Alt + T`** or search for "Terminal" in your app launcher.

---

### Step 2 — Update your package list

```bash
sudo apt update
```

You'll be asked for your password. Type it and press Enter.

> `sudo` means "run as administrator". It's normal — don't skip it.

---

### Step 3 — Install Git

```bash
sudo apt install git
```

When prompted `Do you want to continue? [Y/n]`, press **Y** and Enter.

---

### Step 4 — Verify installation

```bash
git --version
```

Expected output: `git version 2.x.x` ✅

---

## 4. Windows — Installing Git

> 🎬 **Video walkthrough:** [How to Download & Install Git | Windows, Mac & Linux (Step by Step)](https://www.youtube.com/watch?v=lh-O3hZBqdQ)  
> 🎬 **Windows-only tutorial:** [How to Install Git on Windows | Full Guide](https://www.youtube.com/watch?v=VWbX2B3Q-1g)

---

### Step 1 — Download the installer

Go to: **[git-scm.com/download/win](https://git-scm.com/download/win)**

The download should start automatically. If it doesn't, click the link for "64-bit Git for Windows Setup."

---

### Step 2 — Run the installer

Double-click the downloaded `.exe` file. Click **Yes** on the security popup.

---

### Step 3 — Go through the installer (keep defaults)

The installer has many screens. Here's what to watch for:

| Screen | What to do |
|--------|-----------|
| License | Click **Next** |
| Select Destination | Keep default, click **Next** |
| Select Components | Keep defaults, click **Next** |
| Default Editor | Change to **Visual Studio Code** if you use it, else keep default |
| **Adjusting PATH** ⭐ | Select **"Git from the command line and also from 3rd-party software"** |
| HTTPS transport backend | Keep **"Use the OpenSSL library"**, click **Next** |
| Line ending conversions | Keep **"Checkout Windows-style, commit Unix-style"**, click **Next** |
| Terminal emulator | Keep **"Use MinTTY"**, click **Next** |
| Default behavior of `git pull` | Keep **"Default (fast-forward or merge)"**, click **Next** |
| Credential helper | Keep **"Git Credential Manager"**, click **Next** |
| Extra options | Keep defaults, click **Next** |
| Experimental options | Leave everything unchecked, click **Install** |

---

### Step 4 — Verify installation

After install completes, open **Git Bash** (search for it in the Start menu) or **Command Prompt**, and run:

```bash
git --version
```

Expected output: `git version 2.x.x` ✅

---

## 5. Configuring Git (All Platforms)

This step is required on **every OS**. Git needs to know who you are before it can track your commits.

Open your terminal (Git Bash on Windows) and run these four commands **one at a time**, replacing the placeholder text with your actual name and email:

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "you@example.com"
```
```bash
git config --global init.defaultBranch main
```

> Use the same email you use (or plan to use) for your GitHub account. This is how GitHub links your commits to your profile.

---

### Verify your configuration

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `init.defaultBranch` in the output. ✅

---

## 6. Setting Up VS Code Integration

We'll be using VS Code as our editor during the workshop. This step connects VS Code to your terminal so you can open any folder instantly.

### Step 1 — Open VS Code

If you don't have VS Code, download it from **[code.visualstudio.com](https://code.visualstudio.com/)** and install it.

---

### Step 2 — Install the `code` command (macOS/Linux only)

> Windows users: VS Code's `code` command is added automatically during installation. Skip to Step 3.

1. Open VS Code
2. Press **`Cmd + Shift + P`** (Mac) or **`Ctrl + Shift + P`** (Linux) to open the Command Palette
3. Type `shell command`
4. Click **"Shell Command: Install 'code' command in PATH"**
5. Close your terminal completely and reopen it

---

### Step 3 — Test the `code` command

Navigate to any folder and type:

```bash
code .
```

This should open that folder in VS Code instantly. ✅

---

### Step 4 — Set VS Code as Git's default editor (optional but recommended)

```bash
git config --global core.editor "code --wait"
```

---

## 7. Verify Everything Works

Run through this quick checklist before the workshop:

```bash
# 1. Check Git version
git --version

# 2. Check your Git config
git config --list

# 3. Check VS Code CLI
code --version
```

If all three return output without errors, **you're fully set up.** 🎉

---

## 8. Common Issues & Fixes

### 🍎 macOS Issues

---

**❌ `brew: command not found` after installation**

You skipped or miscopied the two PATH commands after installation.

Fix:
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
Close and reopen your terminal. Run `brew --version` again.

---

**❌ `curl: (7) Failed to connect` or network errors during Homebrew install**

Your internet connection dropped or a firewall blocked the download.

Fix: Check your connection, disable VPN if you're using one, and re-run the install command. Homebrew will resume from where it left off.

---

**❌ Homebrew installer says "Xcode Command Line Tools" are missing**

This is normal on a fresh Mac. Homebrew will prompt to install them automatically. Just press **Enter** when it asks and wait — this can take 5–10 minutes on its own.

---

**❌ `git version` still shows an old system version after `brew install git`**

macOS ships with an older version of Git. Homebrew installs a newer one, but you may need to restart your terminal first. If it still shows the old version:

```bash
which git
```

If the output is `/usr/bin/git` (not `/opt/homebrew/bin/git`), run:
```bash
echo 'export PATH="/opt/homebrew/bin:$PATH"' >> ~/.zprofile
source ~/.zprofile
```

---

**❌ `brew install git` says "already installed" but `git --version` shows old version**

```bash
brew upgrade git
```

---

### 🐧 Linux Issues

---

**❌ `sudo: command not found`**

You might be logged in as root already. Try running without `sudo`:
```bash
apt update && apt install git
```

---

**❌ `E: Unable to fetch some archives` or network errors**

Try switching to a different mirror or check your internet connection:
```bash
sudo apt update --fix-missing
sudo apt install git
```

---

**❌ `Permission denied` errors**

Make sure you're using `sudo`. Without it, you don't have admin rights to install packages.

---

### 🪟 Windows Issues

---

**❌ `git` is not recognised in Command Prompt after installation**

During setup, you may have chosen the wrong PATH option. The fix:

1. Uninstall Git from Add/Remove Programs
2. Reinstall from [git-scm.com/download/win](https://git-scm.com/download/win)
3. On the "Adjusting your PATH environment" screen, select **"Git from the command line and also from 3rd-party software"**

Alternatively, use **Git Bash** instead of Command Prompt — it always works.

---

**❌ Windows Defender or antivirus blocked the installer**

Right-click the `.exe` → **Properties** → check **"Unblock"** at the bottom → click OK → run again.

---

**❌ `code .` doesn't work in Git Bash**

VS Code may not have been added to PATH. Fix:

1. Open VS Code
2. Press `Ctrl + Shift + P`
3. Type `shell command`
4. Click **"Shell Command: Install 'code' command in PATH"**
5. Restart Git Bash

---

**❌ Git asks for username and password every time you push**

You need to set up a credential helper. Git for Windows installs one by default — if it didn't activate:

```bash
git config --global credential.helper manager
```

---

### 🔧 General / All Platforms

---

**❌ `git config --list` shows no user.name or user.email**

You skipped the configuration step. Run:
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

**❌ `error: Your local changes to the following files would be overwritten by merge`**

You have uncommitted local changes. Either commit them or stash them:
```bash
git stash
git pull
git stash pop
```

---

**❌ Default branch is `master` instead of `main`**

Run:
```bash
git config --global init.defaultBranch main
```
This only affects new repositories. Existing repos keep their branch name.

---

## 9. Quick Reference Cheatsheet

```bash
# ── Installation Verification ──────────────────────────────
git --version                          # Check Git version
brew --version                         # Check Homebrew (Mac only)
code --version                         # Check VS Code CLI

# ── Configuration ──────────────────────────────────────────
git config --global user.name "Name"
git config --global user.email "email@example.com"
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
git config --list                      # View all config

# ── Terminal Navigation ────────────────────────────────────
cd folder-name                         # Enter a folder
cd ..                                  # Go up one folder
ls                                     # List files (Mac/Linux)
dir                                    # List files (Windows CMD)
pwd                                    # Print current path

# ── Open VS Code ───────────────────────────────────────────
code .                                 # Open current folder in VS Code
```

---

## ✅ Pre-Workshop Checklist

Before you show up, make sure you can tick all of these:

- [ ] `git --version` returns a version number
- [ ] `git config --list` shows your name and email
- [ ] `code .` opens VS Code from the terminal
- [ ] You have a [GitHub account](https://github.com) (create one if you don't)

---

> **Questions?** Drop a message in the workshop group or reach out before the session.  
> See you there! 🚀
