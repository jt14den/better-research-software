---
title: "Installation Instructions"
---

::::::::::::::::::::: objectives

- Prepare your computer for the “Building Better Research Software” workshop.
- Install Visual Studio Code (VS Code), Git, and Python using **uv**.
- Verify everything works in the integrated VS Code terminal.

::::::::::::::::::::::::::::::::::

::::::::::::::::::::: prereq

You’ll need basic familiarity with opening applications, downloading files, and copy-pasting commands.  
No prior experience with programming or Git is required.

::::::::::::::::::::::::::::::::::

## Setup Overview

These steps prepare your computer for the workshop.  
They work on **Windows, macOS, and Linux** — look for tabs marked  
🪟 *Windows only* or 🐧 *macOS/Linux only* where steps differ.

We’ll use **Visual Studio Code (VS Code)** as the main workspace and terminal.

---

## Step 1 — Install Visual Studio Code

Download and install **VS Code** for your operating system:  
👉 <https://code.visualstudio.com/Download>

After installation, open VS Code once to complete setup.

::::::::::::::::::::: callout

### What to expect

You should see the **Welcome screen** with tabs for “Start” and “Extensions.”

::::::::::::::::::::::::::::::::

![VS Code Home Screen](fig/vscode-home.png){alt="VS Code start screen showing welcome tab and extensions icon highlighted"}

---

### Add Helpful Extensions

From the menu, choose **View → Extensions** (or press `Ctrl+Shift+X` / `Cmd+Shift+X`).  
Search for and install these extensions:

- **Python (by Microsoft)** – enables Python coding and linting  
- **GitLens** – adds Git history and collaboration features  
- **Git Graph** – shows branch and commit history visually  
- **Excel Viewer** – view CSV and Excel files  
- **JSON Editor** – improve JSON readability  
- 🪟 **Start git-bash** – adds a Git Bash terminal inside VS Code (Windows only)

![Installing VS Code Extensions](fig/vscode-extensions.png){alt="VS Code Extensions sidebar with Python, GitLens, Git Graph, Excel Viewer, JSON Editor, and Start git-bash visible"}

---

### Set up the Integrated Terminal

::::::::::::::::::::: tab

### 🪟 Windows

1. Install **Start git-bash** (from the Extensions Marketplace).  
2. Go to **Terminal → New Terminal**.  
3. Click the **▼** next to `+`, choose **Select Default Profile**, and select **Git Bash**.  
4. Open a new terminal tab — you should see `bash` on the right.

::::::::::::::::::::::::::::::

::::::::::::::::::::: tab

### 🐧 macOS / Linux

1. Go to **Terminal → New Terminal**.  
2. Click the **▼** next to `+`, choose **Select Default Profile**, and select **bash** or **zsh**.  
3. Open a new terminal tab to verify the shell name on the right.

::::::::::::::::::::::::::::::

![VS Code Terminal set to Git Bash](fig/vscode-terminal.png){alt="VS Code integrated terminal with Git Bash selected as the current shell"}

You’ll use this terminal for **all remaining steps**.

---

## Step 2 — Install Git

::::::::::::::::::::: tab

### 🪟 Windows

Download **Git for Windows** from <https://gitforwindows.org/>.  
During setup:  
- Set **Editor** to **Visual Studio Code**  
- Set **default branch name** to `main`  
- Leave other options at default  

This also installs **Git Bash**, which you’ll now use inside VS Code.

::::::::::::::::::::::::::::::

::::::::::::::::::::: tab

### 🐧 macOS / Linux

Git is usually pre-installed.  
If not, install with your package manager or from <https://git-scm.com/downloads>.

::::::::::::::::::::::::::::::

---

## Step 3 — Check Terminal and Git

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

## Step 4 — Install Python using uv

We use **uv** to install Python and manage project environments automatically.

Run this in your VS Code terminal:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

When it finishes, **close and reopen the terminal**, then verify:

```bash
uv --version
uv python --version
```

::::::::::::::::::::: callout

### 🪟 Tip for Windows users

You don’t need PowerShell or separate installers — everything runs inside VS Code’s Git Bash.

::::::::::::::::::::::::::::::

![Testing uv in VS Code terminal](fig/vscode-test-uv.png){alt="VS Code terminal showing successful output from 'uv --version' and 'uv python --version' commands"}

---

## Step 5 — Download Course Files

Download the practice data:  
👉 <https://github.com/carpentries-incubator/better-research-software/raw/refs/heads/main/learners/spacewalks.zip>

Unzip `spacewalks.zip` to an easy location (e.g., Desktop).  
In VS Code, open the folder (**File → Open Folder…**) to see the files in the Explorer panel.

![VS Code Explorer showing spacewalks folder](fig/vscode-explorer-spacewalks.png){alt="VS Code Explorer showing extracted spacewalks folder and files"}

---

## Step 6 — Set up Your Project Environment

In the VS Code terminal:

```bash
uv init
```

Edit the new `pyproject.toml` so it looks like:

```toml
[project]
name = "spacewalks"
version = "0.1.0"
dependencies = ["pandas", "matplotlib"]
```

Then install and run the code:

```bash
uv sync
uv run python spacewalks.py
```

::::::::::::::::::::: challenge

### Test your setup

If you see a plot or printed output, everything works!

::::::::::::::::::::::::::::::

![Python plot result](fig/vscode-spacewalks-plot.png){alt="Example plot output from running the spacewalks.py analysis"}

---

## Step 7 — (Optional) Set up GitHub

::::::::::::::::::::: checklist

### Optional: Save your work online

1. Create a GitHub account: <https://github.com/>  
2. Follow the SSH setup guide: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh>  
3. Test your connection:

```bash
ssh -T git@github.com
```

✅ You should see a greeting message from GitHub.

::::::::::::::::::::::::::::::::::

---

::::::::::::::::::::: keypoints

- Use **VS Code** as your coding workspace and terminal.  
- **Git** manages version control and integrates with VS Code.  
- **uv** simplifies Python installation and environment management.  
- You’re now fully set up for the workshop!

::::::::::::::::::::::::::::::::::

This version should paste cleanly and render correctly within the Carpentries Workbench build system (sandpaper::build_lesson()) without breaking from nested code blocks.
