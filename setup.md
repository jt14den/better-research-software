---
title: Setup
---

## Software Setup

Before starting the course, make sure you have the following tools installed and working:

- [Visual Studio Code (VS Code)](installation-instructions.html#step-1--install-visual-studio-code) — your main workspace and terminal
- [Git + Git Bash](installation-instructions.html#step-2--install-git) — for version control and running commands 
- [Python 3 (via uv)](installation-instructions.html#step-5--install-python-using-uv) — for running and managing code
- [GitHub account](installation-instructions.html#step-8--connect-to-github-simplified-setup) — for saving and sharing work 
- [Spacewalks data and example code](installation-instructions.html#step-6--download-course-files) — used in the exercises

These steps work on **Windows, macOS, and Linux**.  
Windows users will use **Git Bash inside VS Code** instead of PowerShell.

---

## What’s New

::::::::::::::::::::: callout

### Updated authentication and environment setup

- **GitHub authentication is simpler** — sign in through your browser using **Git Credential Manager** (no SSH keys or tokens needed).  
- **Python installation uses uv**, a modern, fast installer that avoids manual setup.  
- **VS Code is your single workspace** — all setup steps run inside its built-in terminal.

::::::::::::::::::::::::::::::::

---

## Get Started

Follow the step-by-step [**Installation Instructions**](installation-instructions.md)  
to install everything and verify your setup before the workshop.

If you’ve used older Git or Python workflows, note that these instructions reflect the **current recommended Carpentries practices** for reproducible, low-friction setup.

---

::::::::::::::::::::: instructor

### Instructor Notes

**Timing:**  
- Allow **20–30 minutes** at the start of the workshop (or in a separate install session).  
- Encourage participants to complete installation **before** the workshop if possible.

**Verification steps:**  
Ask learners to open the VS Code terminal and confirm the following commands return without errors:

```bash
git --version
uv --version
python3 --version  # or python --version on Windows
```

**Common issues to check:**  
- On Windows: Git Bash must be selected as the default VS Code terminal.  
- On macOS/Linux: If `uv` is not found, VS Code may need to be restarted.  
- If pushing to GitHub fails, confirm **Git Credential Manager** is active with:  
  ```bash
  git config --global credential.helper manager
  ```

**Troubleshooting resources:**  
- [Git for Windows documentation](https://gitforwindows.org/)  
- [Visual Studio Code integrated terminal guide](https://code.visualstudio.com/docs/terminal/basics)  
- [Astral uv installation docs](https://docs.astral.sh/uv/getting-started/)  
- [GitHub authentication help](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)

::::::::::::::::::::::::::::::::::
