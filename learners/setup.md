---
title: Setup
---

## Software Setup

To go through the course material on your own or at a workshop, 
you will need the following software installed and working correctly on your system:

- [Command line terminal (shell)](installation-instructions.html#command-line-tool) (such as **Bash**, **Zsh** or **Git Bash**)  
- [Git version control tool](installation-instructions.html#git-version-control-tool)
- [GitHub account](installation-instructions.html#github-account)
- [Python 3](installation-instructions.html#python-3-distribution)
- [Visual Studio Code (VS Code)](installation-instructions.html#visual-studio-code) integrated development environment (IDE)
- [Astronaut data and analysis code](installation-instructions.html#astronaut-data-and-analysis-code) which we will be used for exercises in the course

Please follow the [installation instructions](installation-instructions.md) to install the above tools and set up for the course.

## Example Data & Research Software

We are going to follow a fairly typical experience of a new PhD or postdoc joining a research group.
They were emailed some data and analysis code bundled in a `.zip` archive and written by another group member who worked on similar things but has since left the group.
They need to be able to install and run this code on their machine, check they can understand it and then adapt it to their own project.

As part of the [setup for this course](./installation-instructions.html#astronaut-data-and-analysis-code), you should have downloaded a `.zip` archive containing the software project the new research team member was given.
Let's unzip this archive and inspect its content in VS Code.
The software project contains:

1. A JSON file (`data.json`) - a snippet of which is shown below - with data on extra-vehicular activities (EVAs or spacewalks) undertaken by astronauts and cosmonauts from 1965 to 2013 (data provided by NASA via its [Open Data Portal](https://data.nasa.gov/Raw-Data/Extra-vehicular-Activity-EVA-US-and-Russia/9kcy-zwvn/about_data))

   ![JSON data file snippet showing EVA/spacewalk data including EVA id, country, crew members, vehicle type, date of the spacewalk, duration, and purpose)](episodes/fig/astronaut-data-json-snippet.png){alt='JSON data file snippet showing EVA/spacewalk data including EVA id, country, crew members, vehicle type, date of the spacewalk, duration, and purpose'}
2. A Python script (`my code v2.py`) containing some analysis.

   ![A first few lines of a Python script](episodes/fig/astronaut-analysis-bad-code-screenshot.png){alt='A first few lines of a Python script used as example code for the episode'}

   The code in the Python script does some common research tasks:

    * Read in the data from the JSON file
    * Change the data from one data format to another and save to a file in the new format (CSV)
    * Perform some calculations to generate summary statistics about the data
    * Make a plot to visualise the data

Let's check your setup now to make sure you are ready for the rest of this course.

::::::  challenge

### Check your setup

Open a command line terminal and look at the prompt.
Compare what you see in the terminal with your neighbour, does it look the same or different?
What information is it telling you and why might this be useful?
What other information might you want?

Run the following commands in a terminal to check you have installed the tools listed in the Setup page.
Compare the output with your neighbour and see if you can see any differences.

Checking the command line terminal:

1. `$ date`
2. `$ echo $SHELL`
3. `$ pwd`
4. `$ whoami`

Checking Python:

5. `$ python --version`
6. `$ python3 --version`
7. `$ which python`
8. `$ which python3`

Checking Git and GitHub:

9. `$ git --help`
10. `$ git config --list`
11. `$ ssh -T git@github.com`

Checking VS Code:

12. `$ code`
13. `$ code --list-extensions`

::: hint

The prompt is the `$` character and any text that comes before it, that is shown on every new line before you type in
commands.
Type each of the commands one at a time and press enter.
They should give you a result by printing some text in the terminal.

:::

::: solution

The expected out put of each command is:

1. Today's date
2. `bash` or `zsh` - this tells you what shell language you are using. In this course we show examples in Bash.
3. Your "present working directory" or the folder where your shell is running
4. Your username
5. In this course we are using Python 3. If `python --version` gives you Python 2.x you may have two versions of Python installed on your computer and need to be careful which one you are using.
6. Use this command to be certain you are using Python version 3, not 2, if you have both installed.
7. The file path to where the Python version you are calling is installed.
8. If you have more than one version these should be different paths, if both 5. and 6. gave the same result then 7. and 8. should match as well.
9. The help message explaining how to use the `git` command.
10. You should have `user.name`, `user.email` and `core.editor` set in your Git configuration. Check that the editor listed is one you know how to use.
11. This checks if you have set up your connection to GitHub correctly. If is says `permission denied` you may need to look at the instructions for setting up SSH keys again on the Setup page.
12. This should open VSCode in your current working directory. macOS users may need to first open VS Code and [add it to the PATH](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
13. You should have the extensions GitLens, Git Graph, Python, JSON and Excel Viewer installed to use in this course.

:::

::::::


You may have noticed that our researcher has received the software project they are meant to be working as a `.zip` archive via email. 
This is not very good practice for several reasons - email does not track changes, does not allow for multiple people to work on the same file, code reviews or issue tracking, attachments can be mistakenly sent with outdated versions and may have storage and scalability limitations. 
In the rest of the course, we will learn some better practices for developing, sharing, tracking changes and collaborating on a software project. 