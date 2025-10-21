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
## Step 8 — Connect to GitHub

::::::::::::::::::::: checklist

### Create your GitHub account

1. Go to <https://github.com/signup> and create a free account.
2. Verify your email before continuing.
3. Keep your username and password handy — you will sign in through your browser once.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: callout

### Why we use HTTPS

GitHub now recommends browser-based sign-in instead of SSH keys or manual tokens.
This uses the Git Credential Manager (GCM), which securely remembers your login in your operating system’s keychain.

::::::::::::::::::::::::::::::::::

### 1. Check your Git configuration

```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

These identify you in Git commits.

### 2. Install Git Credential Manager (GCM)

::::::::::::::::::::: group-tab

## 🪟 Windows

Git Credential Manager is installed automatically with Git for Windows.
You can skip this step.

## 🍎 macOS

Apple’s built-in Git does not include GCM. Install it once using Microsoft’s signed package:

1. Go to https://github.com/git-ecosystem/git-credential-manager/releases/latest
2. Under Assets, download the .pkg for your Mac:

```
gcm-osx-arm64.pkg for Apple Silicon
gcm-osx-x64.pkg for Intel
```

4. Double-click the .pkg and follow the installer.
5. In Terminal, verify installation:

```
git-credential-manager version
git config --global credential.helper manager
```

## 🐧 Linux

Many Linux distributions do not include GCM by default. Install it via your package manager or from the same GitHub releases page:

```
# Debian / Ubuntu
sudo apt install git-credential-manager-core
```

```
# Or install manually on any distro
curl -L https://aka.ms/gcm/latest/linux-install.sh | bash
git config --global credential.helper manager
```

:::::::::::::::::::::::::


### 3. Create a test repository on GitHub

1. Visit <https://github.com/new>
2. Name it `test-repo`
3. Choose Public and click Create repository

You will see the repository page with command-line instructions.

---

### 4. Connect from VS Code or Terminal

```
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/test-repo.git
git push -u origin main
```

When you run the last command, Git opens a browser window asking you to sign in to GitHub.
Once signed in, the push completes. No SSH keys or tokens required.
Your credentials are stored securely and reused automatically.

---

::::::::::::::::::::: callout

### A note on GitHub authentication changes

Older tutorials often tell you to set up SSH keys or create Personal Access Tokens (PATs).
That is no longer required for most users.

Today, GitHub supports secure, one-time browser authentication through Git Credential Manager.
• Installed automatically on Windows.
• Installable on macOS and Linux as shown above.

When you push for the first time, Git opens a browser window for you to sign in and stores your credentials securely in the system keychain.

::::::::::::::::::::::::::::::::::



::::::::::::::::::::: instructor

### Instructor Notes

If learners encounter authentication issues:
- Confirm they’re using **Git 2.41 or newer** (includes Git Credential Manager).  
- Have them run `git config --global credential.helper manager`.  
- On Windows, credentials can be reset via **Windows Credential Manager → Generic Credentials → git:https://github.com**.  
- On macOS/Linux, credentials are stored in the keychain and can be cleared with `git credential reject`.

::::::::::::::::::::::::::::::::::


::::::::::::::::::::: keypoints

- Install **VS Code**, then **Git for Windows**, then the **Start git-bash** extension.  
- Use **Git Bash inside VS Code** for all commands.  
- **uv** manages Python quickly and reproducibly.  
- Restart VS Code after installing uv.  
- Connect to GitHub using **HTTPS with browser sign-in**, not SSH keys.  
- **Git Credential Manager** stores your login securely — no tokens needed.  
- GitHub authentication has changed — browser-based login is now the default.

::::::::::::::::::::::::::::::::::
