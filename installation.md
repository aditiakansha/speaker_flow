# 🛠️ Git & GitHub Workshop — Pre-Workshop Setup Manual

> **Please complete this BEFORE you arrive at the workshop.**  
> The session moves fast — if Git isn't installed, you'll fall behind in the first 15 minutes.  
> If you get stuck at any step, ping us on the group and we'll help you sort it out.

---

## 📋 Table of Contents

1. [What You're Installing & Why](#1-what-youre-installing--why)
2. [Windows — Git Setup](#2-windows--git-setup)
3. [macOS — Git Setup](#3-macos--git-setup)
4. [Linux — Git Setup](#4-linux--git-setup)
5. [VS Code Setup (All Platforms)](#5-vs-code-setup-all-platforms)
6. [Quick Reference Cheatsheet](#6-quick-reference-cheatsheet)
7. [Pre-Workshop Checklist](#7-pre-workshop-checklist)

---

## 1. What You're Installing & Why

| Tool | What it is | Why you need it |
|------|-----------|-----------------|
| **Git** | A version control system | Tracks changes to your code, lets you collaborate |
| **Homebrew** (Mac only) | A package manager for macOS | Makes installing developer tools like Git simple |
| **VS Code** | Code editor | Where you'll write code — we'll connect it to Git |
| **GitLens** | A VS Code extension | Supercharges Git inside the editor with blame, history, and more |

> **Not sure which OS you have?**  
> - Windows: Start → Settings → System → About  
> - Mac: Apple logo top-left → "About This Mac"  
> - Linux: You already know. 😄

---

## 2. Windows — Git Setup

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

### Step 4 — Verify Git is installed

After install completes, open **Git Bash** (search for it in the Start menu) and run:

```bash
git --version
```

Expected output: `git version 2.x.x` ✅

---

### Step 5 — Configure Git

Git needs to know who you are before it can track your commits. Run these three commands in Git Bash, one at a time, replacing the placeholder text with your actual name and email:

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

You should see your `user.name`, `user.email`, and `init.defaultBranch` in the output. ✅

---

### ⚠️ Common Issues — Windows

---

**❌ `git` is not recognised in Command Prompt after installation**

During setup, you may have chosen the wrong PATH option.

Fix — reinstall and select the right option:
1. Uninstall Git from Add/Remove Programs
2. Reinstall from [git-scm.com/download/win](https://git-scm.com/download/win)
3. On the "Adjusting your PATH environment" screen, select **"Git from the command line and also from 3rd-party software"**

Alternatively, use **Git Bash** instead of Command Prompt — it always works regardless of PATH.

---

**❌ Windows Defender or antivirus blocked the installer**

Right-click the `.exe` → **Properties** → check **"Unblock"** at the bottom → click OK → run again.

---

**❌ Git asks for username and password every time you push**

You need a credential helper. Git for Windows installs one by default — if it didn't activate:

```bash
git config --global credential.helper manager
```

---

**❌ Default branch shows as `master` instead of `main`**

```bash
git config --global init.defaultBranch main
```

This only affects new repositories going forward. Existing repos keep their branch name.

---

**❌ `git config --list` shows no user.name or user.email**

You skipped Step 5. Go back and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## 3. macOS — Git Setup

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

Expected output: `git version 2.x.x` ✅

---

### Step 7 — Configure Git

Git needs to know who you are before it can track your commits. Run these three commands in Terminal, one at a time:

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "you@example.com"
```
```bash
git config --global init.defaultBranch main
```

> Use the same email you use (or plan to use) for your GitHub account.

Then verify it worked:

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `init.defaultBranch` in the output. ✅

---

### ⚠️ Common Issues — macOS

---

**❌ `brew: command not found` after installation**

You skipped or miscopied the two PATH commands after installation.

Fix:
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
Close and reopen your terminal, then run `brew --version` again.

---

**❌ `curl: (7) Failed to connect` or network errors during Homebrew install**

Your internet connection dropped, or a firewall blocked the download.

Fix: Check your connection, disable VPN if you're using one, and re-run the install command. Homebrew will resume from where it left off.

---

**❌ Homebrew installer says "Xcode Command Line Tools" are missing**

This is normal on a fresh Mac. Homebrew will prompt to install them automatically. Just press **Enter** when it asks and wait — this can take 5–10 minutes on its own.

---

**❌ `git --version` still shows an old system version after `brew install git`**

macOS ships with an older built-in Git. Homebrew installs a newer one, but you may need to restart your terminal first. If it still shows the old version:

```bash
which git
```

If the output is `/usr/bin/git` instead of `/opt/homebrew/bin/git`, run:

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

**❌ `git config --list` shows no user.name or user.email**

You skipped Step 7. Go back and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## 4. Linux — Git Setup

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

> `sudo` means "run as administrator." It's normal — don't skip it.

---

### Step 3 — Install Git

```bash
sudo apt install git
```

When prompted `Do you want to continue? [Y/n]`, press **Y** and Enter.

---

### Step 4 — Verify Git is installed

```bash
git --version
```

Expected output: `git version 2.x.x` ✅

---

### Step 5 — Configure Git

Run these three commands in Terminal, one at a time:

```bash
git config --global user.name "Your Name"
```
```bash
git config --global user.email "you@example.com"
```
```bash
git config --global init.defaultBranch main
```

> Use the same email you use (or plan to use) for your GitHub account.

Then verify it worked:

```bash
git config --list
```

You should see your `user.name`, `user.email`, and `init.defaultBranch` in the output. ✅

---

### ⚠️ Common Issues — Linux

---

**❌ `sudo: command not found`**

You might be logged in as root already. Try running without `sudo`:

```bash
apt update && apt install git
```

---

**❌ `E: Unable to fetch some archives` or network errors**

```bash
sudo apt update --fix-missing
sudo apt install git
```

---

**❌ `Permission denied` errors**

Make sure you're using `sudo`. Without it, you don't have admin rights to install packages.

---

**❌ `git config --list` shows no user.name or user.email**

You skipped Step 5. Go back and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

**❌ Default branch shows as `master` instead of `main`**

```bash
git config --global init.defaultBranch main
```

---

## 5. VS Code Setup (All Platforms)

We'll be using VS Code as our editor during the workshop. This section covers three things:
1. Connecting VS Code to your terminal with `code .`
2. Installing GitLens

---

### Part A — Install VS Code

If you don't have VS Code yet, download it from **[code.visualstudio.com](https://code.visualstudio.com/)** and install it for your OS.

---

### Part B — Install the `code` command in Terminal

This lets you type `code .` in any terminal to instantly open that folder in VS Code.

#### Windows

The `code` command is added to PATH **automatically** during VS Code installation. Open Command Prompt or Git Bash and verify:

```bash
code --version
```

If it works, you're done. ✅

If it doesn't work, open VS Code manually, press `Ctrl + Shift + P`, type `shell command`, and select **"Shell Command: Install 'code' command in PATH"**. Then restart your terminal.

---

#### macOS

1. Open VS Code
2. Press **`Cmd + Shift + P`** to open the Command Palette
3. Type `shell command`
4. Click **"Shell Command: Install 'code' command in PATH"**
5. **Close your terminal completely and reopen it**

Now test it:

```bash
code --version
```

And open any folder:

```bash
code .
```

This should open that folder in VS Code instantly. ✅

---

#### Linux

Same as macOS — open VS Code, press **`Ctrl + Shift + P`**, type `shell command`, and click **"Shell Command: Install 'code' command in PATH"**. Restart your terminal and verify:

```bash
code --version
```

---

### Set VS Code as Git's default editor

Run this after the `code` command is working:

```bash
git config --global core.editor "code --wait"
```

---

### ⚠️ Common Issues — VS Code / `code .`

---

**❌ `code: command not found` on macOS or Linux**

You either skipped the Command Palette step or didn't restart your terminal. Close Terminal fully (not just the tab) and reopen it. If it still fails, redo the Command Palette step.

---

**❌ `code .` opens VS Code but in the wrong folder**

You're in the wrong directory. Use `cd` to navigate to the right folder first, then run `code .`.

---

**❌ `code --version` works but VS Code opens blank with no folder**

`code .` needs the `.` — that dot means "current folder." Without it, VS Code opens with no folder.

---

### Part C — Install GitLens

GitLens is a free VS Code extension that supercharges Git inside the editor. Instead of running terminal commands to find out who changed a line, why it exists, or what the file looked like before — GitLens shows all of that directly in your code.

---

#### What GitLens Does

**1. 🔍 Inline Blame Annotations**

Every line of code gets a subtle annotation at the end showing who last changed it, when, and with what commit message. Hover over it for the full commit details.

![GitLens screenshot](<assets/Screenshot 2026-09-17 at 3.26.02 PM.png>)

![GitLens screenshot](<assets/Screenshot 2026-09-17 at 3.30.46 PM.png>)

> This is the single biggest beginner unlock — instead of guessing why code exists, you immediately see the context.

---






#### Why Install It? (Quick Comparison)

| Situation | Without GitLens | With GitLens |
|-----------|----------------|--------------|
| "Who wrote this line?" | `git blame` in terminal | Hover over the line |
| "Why does this function exist?" | Dig through commit logs | Click the blame annotation |
| "What changed in this file recently?" | `git log -- filename` | Open File History in one click |
| "Did I break something before?" | Compare diffs via terminal | Visual side-by-side diff |
| "Who else has worked on this?" | Multiple `git log` commands | Sidebar at a glance |

---

#### How to Install GitLens

**Method 1 — Extensions Panel (Easiest)**

1. In VS Code, press:
   - **Mac:** `Cmd + Shift + X`
   - **Windows/Linux:** `Ctrl + Shift + X`

2. In the search box, type:
   ```
   GitLens
   ```

3. Click on **GitLens — Git supercharged** by **GitKraken**

   > ⚠️ Make sure it's the one by **GitKraken** with millions of downloads — not a clone with a similar name.

4. Click the blue **Install** button. No restart needed — GitLens activates immediately. ✅

---

**Method 2 — Browser Marketplace**

1. Go to: **[marketplace.visualstudio.com/items?itemName=eamodio.gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)**
2. Click the green **Install** button
3. Your browser will ask to open VS Code — click **Open Visual Studio Code**
4. VS Code opens the extension page — click **Install** again

---

**Method 3 — Terminal**

```bash
code --install-extension eamodio.gitlens
```

---

#### Verifying GitLens is Active

Open any folder that has a Git repository. You should immediately see:

- Faint grey text at the end of whichever line your cursor is on — that's inline blame
- A new **GitLens icon** in the left sidebar
- A "GitLens" item in the bottom status bar

---





**❌ GitLens installed but I see no inline blame**

Open a file inside a Git repository (a folder where `git init` has been run or that was cloned from GitHub). GitLens only activates inside Git repos — it won't show on random files outside one.

---

**❌ The blame text is there but it's distracting / I want to turn it off**

Press `Cmd/Ctrl + Shift + P`, type `GitLens: Toggle Line Blame` and hit Enter. It toggles off instantly. You can turn it back on the same way.

---

**❌ GitLens shows "No commits yet" on everything**

You haven't made any commits in this repo yet. Make your first commit and GitLens will start showing history.

---

## 6. Quick Reference Cheatsheet

```bash
# ── Terminal Navigation ────────────────────────────────────
cd folder-name          # Enter a folder
cd ..                   # Go up one level
cd ~                    # Go to your home directory
ls                      # List files and folders (Mac/Linux)
ls -la                  # List all files including hidden ones (Mac/Linux)
dir                     # List files and folders (Windows CMD)
pwd                     # Print the full path of where you are now

# ── Installation Verification ──────────────────────────────
git --version           # Check Git version
brew --version          # Check Homebrew (Mac only)
code --version          # Check VS Code CLI

# ── Git Configuration ──────────────────────────────────────
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
git config --list       # View all your current config

# ── Open VS Code ───────────────────────────────────────────
code .                  # Open the current folder in VS Code
code filename.txt       # Open a specific file in VS Code

# ── GitLens via Terminal ───────────────────────────────────
code --install-extension eamodio.gitlens   # Install GitLens
```

---

## 7. Pre-Workshop Checklist

Before you show up, make sure you can tick all of these:

- [ ] `git --version` returns a version number
- [ ] `git config --list` shows your name and email
- [ ] `code .` opens VS Code from the terminal
- [ ] You have a [GitHub account](https://github.com) (create one if you don't)
- [ ] GitLens is installed — you can see inline blame text when you open a file in a Git repo

---

> **Questions?** Drop a message in the workshop group or reach out before the session.  
> See you there! 🚀
