---
title: "Installation Instructions"
---

::::::::::::::::::::: objectives

- Prepare your computer for the “Building Better Research Software” workshop.  
- Install Visual Studio Code (VS Code), Git, and Python using **uv**.  
- Verify that everything runs smoothly inside the VS Code terminal.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: prereq

You’ll need basic familiarity with opening applications, downloading files, and copying text.  
No prior programming or Git experience is required.

::::::::::::::::::::::::::::::::::

## Setup Overview

These steps prepare your computer for the workshop.  
They work on **Windows, macOS, and Linux** — look for tabs marked  
🪟 *Windows only* or 🐧 *macOS/Linux only* where steps differ.

We’ll use **Visual Studio Code (VS Code)** as our workspace and terminal.

---

## Step 1 — Install Visual Studio Code

Download and install **VS Code**:  
👉 <https://code.visualstudio.com/Download>

After installation, open VS Code once to complete setup.

::::::::::::::::::::: callout

### What to expect

You should see the **Welcome screen** with “Start” and “Extensions.”  
If you’re on Windows, open VS Code as your regular user (not Administrator) so extensions install correctly.

::::::::::::::::::::::::::::::::

![VS Code Home Screen](fig/vscode-home.png){alt="VS Code start screen showing welcome tab and extensions icon highlighted"}

---

## Step 2 — Install Git

::::::::::::::::::::: tab

### 🪟 Windows

Download **Git for Windows** from <https://gitforwindows.org/>  

During setup:  
- Set **Editor** to **Visual Studio Code**  
- Set **default branch name** to `main`  
- Leave other options at default  

This also installs **Git Bash**, which you’ll use inside VS Code.

::::::::::::::::::::::::::::::

::::::::::::::::::::: tab

### 🐧 macOS / Linux

Git is usually pre-installed.  
If not, install it with your package manager or from <https://git-scm.com/downloads>.

::::::::::::::::::::::::::::::

---

## Step 3 — Add Helpful VS Code Extensions

From the **View → Extensions** menu (or press `Ctrl+Shift+X` / `Cmd+Shift+X`), search for and install these:

- **Python (by Microsoft)** – enables Python coding and linting  
- **GitLens** – shows Git history and collaboration tools  
- **Git Graph** – visualizes branches and commits  
- **Excel Viewer** – view CSV and Excel files  
- **JSON Editor** – makes JSON files easier to read  
- 🪟 **Start git-bash** – enables Git Bash inside VS Code (Windows only)

![Installing VS Code Extensions](fig/vscode-extensions.png){alt="VS Code Extensions sidebar with Python, GitLens, Git Graph, Excel Viewer, JSON Editor, and Start git-bash visible"}

---

### Set up the Integrated Terminal

::::::::::::::::::::: tab

### 🪟 Windows

1. After installing **Start git-bash**, go to **Terminal → New Terminal**.  
2. Click the **▼** next to `+`, choose **Select Default Profile**, and pick **Git Bash**.  
3. Open a new terminal tab — you should see `bash` in the prompt.

::::::::::::::::::::::::::::::

::::::::::::::::::::: tab

### 🐧 macOS / Linux

1. Go to **Terminal → New Terminal**.  
2. Click the **▼** next to `+`, choose **Select Default Profile**, and select **bash** or **zsh**.  
3. Open a new terminal tab and check the shell name.

::::::::::::::::::::::::::::::

![VS Code Terminal set to Git Bash](fig/vscode-terminal.png){alt="VS Code integrated terminal with Git Bash selected as the current shell"}

Use this terminal for **all remaining steps**.

---

## Step 4 — Check Terminal and Git

::::::::::::::::::::: checklist

### Verify your setup

In VS Code’s terminal, type:

```bash
date
git --version
```

✅ You should see today’s date and a Git version number.  
Keep this terminal open for the next step.

::::::::::::::::::::::::::::::::::

---

## Step 5 — Install Python using uv

We use **uv** to install Python and manage project environments automatically.

Run this in your VS Code terminal:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

When it finishes, **close and restart VS Code**, then verify:

```bash
uv --version
uv python install
uv python --version
```

::::::::::::::::::::: callout

### 🪟 Windows tip

You don’t need PowerShell or separate installers — everything runs inside VS Code’s Git Bash.  
If `uv` isn’t found, close and reopen VS Code to refresh your PATH.

::::::::::::::::::::::::::::::::::

![Testing uv in VS Code terminal](fig/vscode-test-uv.png){alt="VS Code terminal showing successful output from 'uv --version' and 'uv python --version' commands"}

---

## Step 6 — Download Course Files

Download the practice data:  
👉 <https://github.com/carpentries-incubator/better-research-software/raw/refs/heads/main/learners/spacewalks.zip>

Unzip `spacewalks.zip` to an easy location (e.g., Desktop).  
In VS Code, open the folder (**File → Open Folder…**) to view its files.

![VS Code Explorer showing spacewalks folder](fig/vscode-explorer-spacewalks.png){alt="VS Code Explorer showing extracted spacewalks folder and files"}

---

## Step 7 — Set up Your Project Environment

In the VS Code terminal:

```bash
uv init
```

Edit the new `pyproject.toml` so it looks like this:

```toml
[project]
name = "spacewalks"
version = "0.1.0"
dependencies = ["pandas", "matplotlib"]
```

Then install and run:

```bash
uv sync
uv run python spacewalks.py
```

::::::::::::::::::::: challenge

### Test your setup

If you see a plot or printed output, everything works!  
🪟 *If Windows Defender Firewall prompts you, you can safely allow access.*

::::::::::::::::::::::::::::::

![Python plot result](fig/vscode-spacewalks-plot.png){alt="Example plot output from running the spacewalks.py analysis"}

---

## Step 8 — Connect to GitHub (Simplified Setup)

::::::::::::::::::::: checklist

### Create your GitHub account

1. Go to <https://github.com/signup> and create a free account.  
2. Verify your email before continuing.  
3. Keep your username and password handy — you’ll use them once.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: callout

### Why we use HTTPS

GitHub now recommends **signing in with your browser** instead of SSH keys or manual tokens.  
This uses **Git Credential Manager (GCM)**, which securely remembers your login on your computer.

::::::::::::::::::::::::::::::::::

---

### 1. Check your Git configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

These identify you in Git commits.

---

### 2. Create a test repository on GitHub

1. Visit <https://github.com/new>  
2. Name it `test-repo`  
3. Choose **Public** and click **Create repository**

You’ll see the repository page with command-line instructions.

---

### 3. Connect from VS Code

In your VS Code terminal:

```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/test-repo.git
git push -u origin main
```

When you run the last command, Git opens a browser window asking you to **sign in to GitHub**.  
This uses **Git Credential Manager**, which:

- Authenticates in your browser  
- Stores credentials in the OS keychain  
- Works automatically for future pushes  

Once signed in, the push completes — no SSH keys or tokens required.

---

::::::::::::::::::::: callout

### 🪟 Windows tip

Git Credential Manager is installed automatically with Git for Windows.  
When you push, a browser window appears — just follow the prompts.  
Your credentials are saved securely.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: callout

### 🐧 macOS / Linux tip

If you don’t see the sign-in prompt, enable GCM manually:

```bash
git config --global credential.helper manager
```

Then push again to trigger the browser login.

::::::::::::::::::::::::::::::::::

---

::::::::::::::::::::: callout

### A note on GitHub authentication changes

GitHub’s login process has evolved significantly in recent years.  
Older tutorials often ask you to create **SSH keys** or **Personal Access Tokens (PATs)** to connect Git with GitHub.  
Those steps are no longer necessary for most users.

Today, GitHub supports secure **browser-based sign-in** through **Git Credential Manager (GCM)**.  
This tool is installed automatically with Git for Windows and included with most modern macOS and Linux Git distributions.  
When you push code for the first time, Git opens a browser window where you sign in — GitHub handles the rest and securely stores your credentials.

If you learned Git before 2022, this method replaces SSH and PAT authentication.

::::::::::::::::::::::::::::::::::

---

::::::::::::::::::::: keypoints

- Install **VS Code**, then **Git for Windows**, then the **Start git-bash** extension.  
- Use **Git Bash inside VS Code** for all commands.  
- **uv** manages Python quickly and reproducibly.  
- Restart VS Code after installing uv.  
- Connect to GitHub using **HTTPS with browser sign-in**, not SSH keys.  
- **Git Credential Manager** stores your login securely — no tokens needed.  
- GitHub authentication has changed — browser-based login is now the default.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: instructor

### Instructor Notes

If learners encounter authentication issues:
- Confirm they’re using **Git 2.41 or newer** (includes Git Credential Manager).  
- Have them run `git config --global credential.helper manager`.  
- On Windows, credentials can be reset via **Windows Credential Manager → Generic Credentials → git:https://github.com**.  
- On macOS/Linux, credentials are stored in the keychain and can be cleared with `git credential reject`.

::::::::::::::::::::::::::::::::::
