---
title: Reproducible software environments
teaching: 40
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions

- What are virtual environments and why do we use them?
- How can we manage Python and external libraries reliably and repeatably?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Understand what a virtual environment is and why it supports reproducible work.  
- Use **uv** to create, manage, and share a reproducible project environment.  
- Learn what information lives in `pyproject.toml` and `uv.lock`.  
- Practice recreating an environment and verifying that results match.

::::::::::::::::::::::::::::::::::::::::::::::::

So far, we have created a local Git repository to track changes in our software project and pushed it to GitHub
to enable others to see and contribute to it. We now want to start developing the code further — and ensure that it runs the same way every time.

:::::: spoiler

### Code state

At this point, the code in your local software project's directory should be as in:
<https://github.com/carpentries-incubator/bbrs-software-project/tree/03-reproducible-dev-environment>

::::::

::: instructor

With **uv**, we reduce many setup problems common to Python packaging.
Remind learners that they don’t need to “activate” environments — `uv run` always uses the right one.  
If learners previously set `PYTHONHOME` or `PYTHONPATH`, have them `unset` these before using uv.

If `uv` isn’t found on Windows, fully **restart VS Code**, not just the terminal.  
Test this workflow yourself on Windows before the workshop.

:::

## Software dependencies

If we have a look at our script, we may notice a few `import` lines such as:  
`import json`, `import csv`, `import datetime as dt`, and `import matplotlib.pyplot as plt`.

This means that our code depends on several **libraries** — some built in (standard library) and some external.

`json`, `csv`, and `datetime` come with Python.  
Packages like `matplotlib` or `pandas` must be installed separately.

Each project often needs **specific versions** of libraries. To avoid one project breaking another, we isolate each in its own **environment**.

::::::::::::::::: callout

### Key terms

+------------------+-----------------------------------------------------------+
| Term             | Meaning                                                   |
+==================+===========================================================+
| **Environment**  | A self-contained directory holding a Python interpreter   |
|                  | and installed packages.                                   |
+------------------+-----------------------------------------------------------+
| **Dependency**   | A library your code needs to run.                         |
+------------------+-----------------------------------------------------------+
| **Package manager** | A tool that installs and tracks dependencies           |
|                  | (e.g., `uv`, `pip`, or `conda`).                         |
+------------------+-----------------------------------------------------------+
| **Lockfile**     | A record of *exact* versions of dependencies for          |
|                  | reproducibility.                                          |
+------------------+-----------------------------------------------------------+

:::::::::::::::::::::::::::::::

## What are virtual software environments?

A Python virtual environment is an **isolated working copy** of Python plus the packages your project needs.  
This isolation prevents version conflicts and makes collaboration easier.

We can visualize multiple projects on the same computer, each with its own environment:

![Diagram to depict different Python environments containing different packages on the same machine](fig/virtual-env.png){alt='A single system might contain multiple virtual environments, each containing a different version of Python and the set of third-party libraries it needs (dependencies) e.g. NumPy, Pandas or Matplotlib. Each environment contains its own complete copy of the required version of each dependency.'}

:::::::::::::::::::::: callout

## True reproducibility is complex

Creating isolated environments makes your work much more reproducible,
but full computational reproducibility can also depend on the OS, CPU/GPU, and system libraries.
For most research projects, environment management like this is *good enough* — and a major improvement over doing nothing.

::::::::::::::::::::::::::::::

## Managing environments with uv

Historically, we used `venv` + `pip` and shared a `requirements.txt`.  
Now, **uv** does this in one step:

- Creates and manages a project environment (`.venv/`)  
- Declares dependencies in `pyproject.toml`  
- Locks exact versions in `uv.lock`  
- Runs commands in the environment (`uv run`)  
- Installs Python if needed

::::::::::::::::: checklist

### 1. Initialize the project

In your project root, run:

```bash
uv init
```

This creates a minimal `pyproject.toml` describing your project.

If Python isn’t already available, install one:

```bash
uv python install
```

::::::::::::::::::::::::::::

::::::::::::::::: checklist

### 2. Add dependencies

You can add dependencies via command or by editing the file.

**Command (recommended):**

```bash
uv add pandas matplotlib
```

**Or edit manually:**

```toml
[project]
name = "spacewalks"
version = "0.1.0"
dependencies = ["pandas", "matplotlib"]
```

Then install everything and generate the lockfile:

```bash
uv sync
```

::::::::::::::::::::::::::::

::::::::::::::::: challenge

### Explore the generated files

Open `pyproject.toml` in VS Code.  
Find the line listing your dependencies.  
Now open `uv.lock` — this file records *exact versions* so anyone can reproduce your setup later.

::::::::::::::::::::::::::::

::::::::::::::::: checklist

### 3. Run code inside the environment

```bash
uv run python eva_data_analysis.py
```

You can also start a Python REPL safely:

```bash
uv run python
```

> 🪟 **Windows Tip:** Run these commands inside VS Code’s **Git Bash** terminal, not PowerShell.  

::::::::::::::::::::::::::::

::::::::::::::::: checklist

### 4. Inspect and maintain packages

```bash
uv tree            # see dependency tree
uv add seaborn     # add a new package
uv sync --upgrade  # update to latest compatible versions
uv remove pandas   # remove a package
```

::::::::::::::::::::::::::::

::::::::::::::::: checklist

### 5. Share with collaborators

Commit these files to Git:

```bash
git add pyproject.toml uv.lock
git commit -m "Add reproducible environment configuration"
```

Ignore the local environment directory:

```bash
echo ".venv/" >> .gitignore
git add .gitignore
git commit -m "Ignore local environment"
```

::::::::::::::::::::::::::::

Collaborators can now reproduce your setup exactly:

```bash
git clone <your-repo>
cd <your-repo>
uv python install
uv sync
uv run python eva_data_analysis.py
```

::::::::::::::::: challenge

### Try it yourself — recreate your environment

Delete the `.venv` folder and rerun:

```bash
uv sync
```

Then check that your script still runs and gives the same result.  
Congratulations — you’ve reproduced your environment from scratch!

::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::: caution

### Environment variables

If you previously set `PYTHONHOME`, `PYTHONPATH`, or `PYTHONSTARTUP`, unset them:

```bash
unset PYTHONHOME PYTHONPATH PYTHONSTARTUP
```

They can interfere with uv’s isolated environment.

::::::::::::::::::::::::::::::::::::::::::::::::::

## Handling encoding issues (Windows example)

When running your script, you might see this error on Windows:

```bash
UnicodeEncodeError: 'charmap' codec can't encode character ...
```

This happens because Windows uses a different default text encoding.  
Fix it by explicitly setting the encoding when reading and writing files:

```python
data_f = open('./eva-data.json', 'r', encoding='ascii')
data_t = open('./eva-data.csv', 'w', encoding='utf-8')
```

Then commit your fix:

```bash
git add eva_data_analysis.py
git commit -m "Specify data encoding"
git push origin main
```

::::::::::::::::::::::::::::::::::::::: discussion

### Reflection

How might using an environment manager like uv help your **future self** or a **collaborator** reproduce your work?

::::::::::::::::::::::::::::::::::::::::

## Further reading

- [Official Python Packaging: `pyproject.toml`](https://packaging.python.org/en/latest/specifications/declaring-project-metadata/)
- [uv documentation](https://docs.astral.sh/uv)
- [Python Tutorial: Virtual Environments and Packages](https://docs.python.org/3/tutorial/venv.html)

:::::::::::::::::::::: callout

### Other environment managers

You may encounter other tools that manage environments differently:

- [**Pixi**](https://pixi.sh) — Rust-based, cross-language environment manager using Conda’s solver.  
- [**Poetry**](https://python-poetry.org) — established dependency and packaging manager.  
- [**Conda / Mamba**](https://docs.conda.io/) — popular in data science for compiled libraries.  
- [**Pipenv**](https://pipenv.pypa.io/) — older tool combining pip and virtualenv.

Each uses the same core idea: isolate dependencies and record them for reproducibility.  
This lesson uses **uv** for its speed, simplicity, and alignment with current best practices.

::::::::::::::::::::::::::::::

::::::::::::::::: keypoints

- A virtual environment isolates your project’s Python version and dependencies.  
- `uv` replaces older tools like `pip` and `venv` with a faster, simpler workflow.  
- `pyproject.toml` declares what you need; `uv.lock` records exact versions.  
- `uv run` executes code safely inside the environment.  
- Share `pyproject.toml` + `uv.lock`; ignore `.venv/`.  
- Recreate an environment anytime with `uv sync`.

::::::::::::::::::::::::::::::
