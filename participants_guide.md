# Git & GitHub Workshop — Pre-Workshop Setup Manual

> Please complete this BEFORE you arrive at the workshop.

---

## Table of Contents

1. [What You're Installing & Why](#1-whats-youre-installing--why)
2. [Git Setup](#2-git-setup)
3. [VS Code Setup (All Platforms)](#3-vs-code-setup-all-platforms)
4. [Python Setup (All Platforms)](#4-python-setup-all-platforms)
5. [Pre-Workshop Checklist](#5-pre-workshop-checklist)

---

## 1. What You're Installing & Why

| Tool | What it is | Why you need it |
|------|------------|-----------------|
| **Git** | A version control system | Tracks changes to your code, lets you collaborate |
| **VS Code** | Code editor | Where you'll write code — we'll connect it to Git |
| **Python** | A programming language | Useful for scripting, automation, and open-source contributions |

---

## 2. Git Setup

<details>
<summary><strong>Windows</strong></summary>

<br>

### Step 1 — Download the installer

Go to: **[git-scm.com/download/win](https://git-scm.com/download/win)**

The current latest version is Git 2.55.0 (released 2026-08-20). The page looks like this — click the top download link for the x64 Setup:

![git-scm.com install page showing Git 2.55.0 for Windows](https://i.postimg.cc/DfDcnq6V/gitscm-screenshot-2.png)

Click the link for "64-bit Git for Windows Setup."

---

### Step 2 — Run the installer

Double-click the downloaded `.exe` file. Click **Yes** on the security popup.

---

### Step 3 — Go through the installer (keep defaults)

| Screen | What to do |
|--------|------------|
| License | Click **Next** |
| Select Destination | Keep default, click **Next** |
| Select Components | Keep defaults, click **Next** |
| Default Editor | Change to **Visual Studio Code** if you use it, else keep default |
| **Adjusting PATH** | Select **"Git from the command line and also from 3rd-party software"** |
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

Expected output: `git version 2.x.x`

</details>

---

<details>
<summary><strong>macOS</strong></summary>

<br>

### Step 1 — Open Terminal

Press `Cmd + Space` to open Spotlight Search, type **Terminal**, and hit Enter.

---

### Step 2 — Install Homebrew

Homebrew is the most popular package manager for macOS — think of it as an app store for developer tools that you control from the terminal. The official site looks like this:

![Homebrew website showing the install command](https://i.postimg.cc/7YFXMgJN/homebrew-screenshot.png)

Paste the following into Terminal and press Enter:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

It will ask for your Mac login password. Type it and press Enter — you won't see any characters as you type; that's normal. It will then ask you to press Enter to confirm. The download takes 2–5 minutes. Don't close the terminal.

---

### Step 3 — Run the post-install commands

When Homebrew finishes, it will display something like this:

```
==> Next steps:
Run these two commands in your terminal to add Homebrew to your PATH:
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
```

Copy those two commands from **your** terminal output (not from here — they may differ based on your Mac model) and run them one by one.

---

### Step 4 — Verify Homebrew

```bash
brew --version
```

Expected output: `Homebrew 4.x.x`

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

Expected output: `git version 2.x.x`

</details>

---

<details>
<summary><strong>Linux</strong></summary>

<br>

This guide is for Ubuntu / Debian-based distributions (Ubuntu, Pop!\_OS, Linux Mint, etc.). If you're on Arch, Fedora, or another distro, use your respective package manager (`pacman -S git`, `dnf install git`, etc.).

---

### Step 1 — Open Terminal

Press `Ctrl + Alt + T` or search for "Terminal" in your app launcher.

---

### Step 2 — Update your package list

```bash
sudo apt update
```

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

Expected output: `git version 2.x.x`

</details>

---

## 3. VS Code Setup (All Platforms)

Download from **[code.visualstudio.com](https://code.visualstudio.com/)** and install it for your OS.

---

## 4. Python Setup (All Platforms)

Python is used heavily in open-source projects. Having it set up means you can run scripts, install packages, and contribute to a wider range of repos.

---

### Windows

**Step 1 — Download the installer**

Go to: **[python.org/downloads](https://www.python.org/downloads/)** and click the **"Download Python 3.x.x"** button.

**Step 2 — Run the installer**

Double-click the downloaded `.exe`. On the first screen, check **"Add Python to PATH"** before clicking anything else. Then click **"Install Now"**.

**Step 3 — Verify**

Open a new Git Bash or Command Prompt window:

```bash
python --version
pip --version
```

---

### macOS

**Step 1 — Install via Homebrew**

```bash
brew install python
```

**Step 2 — Verify**

```bash
python3 --version
pip3 --version
```

On macOS with Homebrew, the commands are `python3` and `pip3` — this avoids conflicts with the system Python.

**Step 3 — (Optional) Alias `python` to `python3`**

```bash
echo 'alias python=python3' >> ~/.zprofile
echo 'alias pip=pip3' >> ~/.zprofile
source ~/.zprofile
```

---

### Linux

**Step 1 — Check if Python is already installed**

```bash
python3 --version
```

If you see `Python 3.x.x`, skip to Step 3.

**Step 2 — Install if missing**

```bash
sudo apt update
sudo apt install python3 python3-pip
```

**Step 3 — Verify pip**

```bash
pip3 --version
```

**Step 4 — (Optional) Point `python` to Python 3**

```bash
sudo apt install python-is-python3
```

---

## 5. Pre-Workshop Checklist

- [ ] `git --version` returns a version number
- [ ] VS Code is installed and opens
- [ ] You have a [GitHub account](https://github.com)
- [ ] `python3 --version` (Mac/Linux) or `python --version` (Windows) returns a version number
- [ ] `pip3 --version` (Mac/Linux) or `pip --version` (Windows) works

---

> Questions? Drop a message in the workshop group or reach out before the session.