---
title: Installation instructions
---

# Setup for the “Building Better Research Software” Course

These steps prepare your computer for the workshop.  
They work on **Windows, macOS, and Linux** — look for notes marked  
🪟 *Windows only* or 🐧 *macOS/Linux only* where steps differ.

We’ll use **Visual Studio Code (VS Code)** as the main workspace and terminal for all steps.

---

## Step 1 — Install Visual Studio Code

Download and install **VS Code** for your computer:  
👉 <https://code.visualstudio.com/Download>

After installation, open VS Code once so it can finish setup.  
You’ll see a screen like this:

![VS Code Home Screen](fig/vscode-home.png){alt="VS Code start screen showing welcome tab and extensions icon highlighted" .image-with-shadow }

---

### Add helpful extensions

From the menu, choose **View → Extensions** (or press `Ctrl+Shift+X` / `Cmd+Shift+X` on Mac).  
Search for and install these:

- **Python (by Microsoft)** – enables Python coding and linting  
- **GitLens** – adds Git history and collaboration features  
- **Git Graph** – shows branch and commit history visually  
- **Excel Viewer** – lets you view CSV and Excel files  
- **JSON Editor** – improves JSON file readability  
- 🪟 **Start git-bash** – adds a Git Bash terminal inside VS Code (Windows only)

![Installing VS Code Extensions](fig/vscode-extensions.png){alt="Screenshot of VS Code Extensions sidebar with Python, GitLens, Git Graph, Excel Viewer, JSON Editor, and Start git-bash visible and install buttons highlighted" .image-with-shadow }

---

### Set up the integrated terminal

1. Go to **Terminal → New Terminal**.  
2. Click the **▼** arrow next to the `+` and select **Select Default Profile**.  
3. Choose:
   - 🪟 **Git Bash** (after installing Start git-bash)
   - 🐧 **bash** or **zsh** (default on macOS or Linux)  
4. Open a new terminal tab. You should see your shell name (e.g., `bash`) on the right side.

![VS Code Terminal set to Git Bash](fig/vscode-terminal.png){alt="Screenshot of the VS Code integrated terminal with Git Bash selected as the current shell" .image-with-shadow }

You’ll use this terminal for **all remaining steps**.

---

## Step 2 — Install Git

- 🪟 **Windows only:**  
  Download **Git for Windows** from <https://gitforwindows.org/>  

  During setup:  
  - Set **Editor** to **Visual Studio Code**  
  - Set the **default branch name** to `main`  
  - Leave other options as default  

  This also installs **Git Bash**, which you’ll now use inside VS Code.

- 🐧 **macOS/Linux only:**  
  Git is already included on most systems. If not, install it with your package manager or from <https://git-scm.com/downloads>.

Once installed, return to VS Code.

---

## Step 3 — Check your terminal and Git

In the VS Code terminal, type:

```bash
date
git --version
```

You’re ready if you see today’s date and a Git version number.  
Keep this terminal open for the next step.

---

## Step 4 — Install Python using uv

We use **uv** to install Python and manage project environments automatically.  
It’s faster and easier than installing Python manually.

In your VS Code terminal, run:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

When it finishes, **close and reopen the terminal** in VS Code, then verify:

```bash
uv --version
uv python --version
```

You’re done when both commands show version numbers.

![Testing uv in VS Code terminal](fig/vscode-test-uv.png){alt="VS Code terminal showing successful output from 'uv --version' and 'uv python --version' commands" .image-with-shadow }

> 🪟 **Tip for Windows users:**  
> You don’t need PowerShell or separate installers — everything runs inside VS Code’s Git Bash.

---

## Step 5 — Download the course files

Download the practice data:  
👉 <https://github.com/carpentries-incubator/better-research-software/raw/refs/heads/main/learners/spacewalks.zip>

Unzip `spacewalks.zip` to an easy location (like Desktop).  
In VS Code, open that folder (**File → Open Folder…**)  
and you’ll see the files listed in the Explorer panel.

![VS Code Explorer showing spacewalks folder](fig/vscode-explorer-spacewalks.png){alt="VS Code Explorer panel displaying the extracted spacewalks folder and files" .image-with-shadow }

---

## Step 6 — Set up your project environment

In the VS Code terminal (bottom panel), run:

```bash
uv init
```

That creates a `pyproject.toml` file.  
Edit it in VS Code so it looks like this:

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

If you see a plot or printed output, everything works!

![Python plot result](fig/vscode-spacewalks-plot.png){alt="Example plot output window from running the spacewalks.py analysis" .image-with-shadow }

---

## Step 7 — (Optional) Set up GitHub

If you want to save or share your work later:

1. Create a free GitHub account: <https://github.com/>  
2. Follow GitHub’s SSH setup guide: <https://docs.github.com/en/authentication/connecting-to-github-with-ssh>  
3. Test your connection:

   ```bash
   ssh -T git@github.com
   ```

   You should see a greeting message from GitHub.

---

# You’re ready for the workshop

You now have:

- **Visual Studio Code** for editing and running code  
- **Git + Git Bash** for version control and command line work  
- **uv + Python** for reproducible, easy project management  

We’ll use these same tools during the session.  
Keep this page open in case you need to revisit a step.
