## Episode: "Course introduction"

### Exercise: 
### Motivation
Think about the questions below. Your instructors may ask you to share your answers in a shared notes document and/or
discuss them with other participants.

- What motivated you to attend this course? Did you come by choice or were you advised to attend?
- What do you hope to learn or change in your current research software practice? Describe how your knowledge,
  work or attitude may be different afterwards.


### Exercise: 
### What does open and reproducible research mean to you?
Think about the questions below. Your instructors may ask you to share your answers in a shared notes document and/or
discuss them with other participants.

- What do you understand by the words "open" and "reproducible" in the context of research?
- How many people or groups can you list that might benefit from your work being open and reproducible?
- How many times did you wish that someone else's work you came across was more open or accessible to you?
  Can you provide some examples?


### Exercise: 
## Checking your setup

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

5. `$ python3 --version`
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

## Episode: "FAIR research software"

### Exercise: 
Think of a piece of software you use in your research - any computational tool used for data gathering, modelling & simulation, processing & visualising results or others. 
If you have a bit of code or software you wrote yourself, in any language, feel free to use that.

Think where on the FAIR spectrum it fits, using the following scale as a guide for each principle:

- 1 - requires loads of improvement
- 2 - on a good path, but improvements still needed
- 3 - decent, a few things could still be improved
- 4 - very good, only tiny things to improve upon
- 5 - excellent


### Exercise: 
Look at our software project compare its data and code to the software you chose earlier (or assess 
it on its own).
Do you think it is Findable, Accessible, Interoperable and Reusable? 
Give it a score from 1 to 5 in each category, as in the previous exercise, and then we will discuss it together.

## Episode: "Tools and good practices for research software"

### Exercise: 
Individually,

- reflect on what practices (and tools) you are already using in your software development workflow,
- list at least 3 new practices or tools that you would like to start employing or using.

Write your reflections in the shared collaborative document.

## Episode: Version control

### Exercise: 
### Add and commit the changed file

Using the Git commands demonstrated so far, save the change you just made to the Python script.

Remember, commit messages should be descriptive and complete the sentence "If applied, this commit will...".
You can also use `git status` to check the status of your project at any time.


### Exercise: 
### Good commit messages

Read the two commit messages below.
In pairs or small groups,
discuss which messages help you understand more about what the commit author did.
What about the commit messages do you find helpful or not?

1. ```output
   [main 7cf85f6] Change variable
     1 file changed, 1 insertion(+), 1 deletion(-)
   ```
2. ```output
   [main 8baf69d] Change variable name from columns to column_headers
    1 file changed, 1 insertion(+), 1 deletion(-)
   ```


### Exercise: 
### Understanding commit contents

Below are the `diffs` of two commits.
A `diff` shows what changed in one or more file(s) between two commits.
Lines starting with `+`s are additions, while lines starting with `-`s are deletions.
Compare the two `diff`s - can you understand what the commit author was trying to achieve in each commit?
How many changes have they tried to make in each commit?
Discuss in pairs or small groups.

1. ![Example Diff 1](fig/ex-diff-1.png)
2. ![Example Diff 2](fig/ex-diff-2.png)


To find out more about how to generate `diffs`,
you can read the [Git documentation](git-diff-docs) or the [Tracking Changes episode][swc-git-lesson-track] from the [Software Carpentry Version control with Git lesson][swc-git-lesson].


### Exercise: 
### Terminology

In pairs or small groups, discuss the difference between the terms `remote`
and `origin`. What is the definition of each term?

## Episode: Reproducible software environments
## Episode: Code readability

### Exercise: 
### Give a descriptive name to a variable

Below we have a variable called `var` being set the value of 9.81.
`var` is not a very descriptive name here as it doesn't tell us what 9.81 means, yet it is a very common constant in physics!
Go online and find out which constant 9.81 relates to and suggest a new name for this variable.

Hint: the units are *metres per second squared*!

```python
var = 9.81
```


### Exercise: 
### Rename our variables to be more descriptive

Let's apply this to `eva_data_analysis.py`.

a. Edit the code as follows to use descriptive variable names:

    - Change data_f to input_file
    - Change data_t to output_file
    - Change g_file to graph_file
    
b. What other variable names in our code would benefit from renaming? 
c. Commit your changes to your repository. Remember to use an informative commit message.



### Exercise: 
### Add comments to our code

a. Examine `eva_data_analysis.py`.
Add as many comments as you think is required to help yourself and others understand what that code is doing.
b. Commit your changes to your repository. Remember to use an informative commit message.


### Exercise: 
### Writing docstrings

Write a docstring for the function `write_dataframe_to_csv` we introduced earlier.

## Episode: Code structure

### Exercise: 
Refactor your software project so that input data is stored in `data/` directory and results (the graph and CSV 
data files) saved in `results/` directory. 
Remember to create the `results/` directory or your code will fail.

## Episode: "Code correctness & testing"

### Exercise: ### Types of software tests

Fill in the blanks in the sentences below:

-   \_\_\_\_\_\_\_\_\_\_ tests compare the \_\_\_\_\_\_ output of a
    program to its \_\_\_\_\_\_\_\_ output to demonstrate correctness.
-   Unit tests compare the actual output of a \_\_\_\_\_\_
    \_\_\_\_\_\_\_\_ to the expected output to demonstrate correctness.
-   \_\_\_\_\_\_\_\_\_\_ tests check that results have not changed since
    the previous test run.
-   \_\_\_\_\_\_\_\_\_\_ tests check that two or more parts of a program
    are working together correctly.


### Exercise: 
### What are the limitations of informally testing code? (5 minutes)

Think about the questions below. Your instructors may ask you to share
your answers in a shared notes document and/or discuss them with other
participants.

-   Why might we choose to test our code informally?
-   What are the limitations of relying solely on informal tests to
    verify that a piece of code is behaving as expected?


### Exercise: 
### Interpreting pytest output

A colleague has asked you to conduct a pre-publication review of their code which analyses time spent in 
space by various individual astronauts.

You tested their code using `pytest`, and got the following output.
Inspect it and answer the questions below.

#### Example `pytest` output

``` output
============================================================ test session starts 
platform darwin -- Python 3.12.3, pytest-8.2.2, pluggy-1.5.0
rootdir: /Users/Desktop/AnneResearcher/projects/Spacetravel
collected 9 items                                                                                                                                                              

tests/test_analyse.py FF....                                              [ 66%]
tests/test_prepare.py s..                                                 [100%]

====================================================================== FAILURES 
____________________________________________________________ test_total_duration

    def test_total_duration():
    
      durations = [10, 15, 20, 5]
      expected  = 50/60
      actual  = calculate_total_duration(durations)
>     assert actual == pytest.approx(expected)
E     assert 8.333333333333334 == 0.8333333333333334 ± 8.3e-07
E       
E       comparison failed
E       Obtained: 8.333333333333334
E       Expected: 0.8333333333333334 ± 8.3e-07

tests/test_analyse.py:9: AssertionError
______________________________________________________________________________ test_mean_duration 

    def test_mean_duration():
       durations = [10, 15, 20, 5]
    
       expected = 12.5/60
>      actual  = calculate_mean_duration(durations)

tests/test_analyse.py:15: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ 

durations = [10, 15, 20, 5]

    def calculate_mean_duration(durations):
        """
        Calculate the mean of a list of durations.
        """
        total_duration = sum(durations)/60
>       mean_duration = total_duration / length(durations)
E       NameError: name 'length' is not defined

Spacetravel.py:45: NameError
=========================================================================== short test summary info 
FAILED tests/test_analyse.py::test_total_duration - assert 8.333333333333334 == 0.8333333333333334 ± 8.3e-07
FAILED tests/test_analyse.py::test_mean_duration - NameError: name 'length' is not defined
============================================================== 2 failed, 6 passed, 1 skipped in 0.02s 
```

a.  How many tests has our colleague included in the test suite?
b.  The first test in test_prepare.py has a status of s; what does this
    mean?
c.  How many tests failed?
d.  Why did "test_total_duration" fail?
e.  Why did "test_mean_duration" fail?


### Exercise: 
### Unit tests for calculate_crew_size

Implement unit tests for the `calculate_crew_size` function. 
Cover typical cases and edge cases.

Hint - use the following template when writing tests:
```         
def test_MYFUNCTION (): # FIXME
    """
    Test that ...   #FIXME
    """
    
    # Typical value 1
    actual_result =  _______________ #FIXME
    expected_result = ______________ #FIXME
    assert actual_result == expected_result
    
    # Typical value 2
    actual_result =  _______________ #FIXME
    expected_result = ______________ #FIXME
    assert actual_result == expected_result
    
```


### Exercise: 
### Evaluating code coverage

Generate the code coverage report for your software using the `python3 -m pytest --cov --cov-report=html` command.

Inspect the `htmlcov` folder created by the above command in the root directory of your propject, then open the 
`htmlcov/index.html` file in a Web browser and extract the following information:

a.  What proportion of the code base is currently "not" exercised by the test suite?
b.  Which functions in our code base are currently untested?

## Episode: Software documentation

### Exercise: 
### README and the FAIR principles

Think about the question below. Your instructors may ask you to share your answer in a shared notes document and/or 
discuss them with other participants.

Here are some of the major sections you might find in a typical README. 
Which are **essential** to support the FAIR principles? Which are optional?

+ Purpose of the code
+ Audience (who the code is intended for)
+ Installation instructions
+ Contribution guide
+ How to get help
+ License
+ Software citation
+ Usage example
+ Dependencies and their versions
+ FAQs
+ Code of Conduct


### Exercise: 
### Spacewalks README

Extend the README for Spacewalks by adding:

1. Installation instructions
2. A simple usage example


### Exercise: 
### Select a licence

Choose a license for your code. 
Discuss with your neighbour or the group your choice of license and reason for choosing it.


### Exercise: 
### Add a license to your code

Add a LICENSE file containing the full text of your chosen license to your code repository.

## Episode: My Software
## Episode: Spacewalks

### Exercise: 
### Spacewalks software citation

Add the citation file for our Spacewalks software to the root folder of our repository on GitHub.
You can either do it directly on GitHub or creating the file locally and the committing and pushing to GitHub from the 
command line.

### Exercise: ### Explore your documentation

Explore documentation in `site/` folder built with MkDocs for your project, starting from the `index.html` file.

Open `index.html` file in a Web browser to see how it renders. 

Check `site/reference.html` to see how docstrings from your functions are 
provided here as a reference manual.

### Exercise: 
### Spacewalks how-to guide

a. Review the Diataxis guidance page on writing a How-to guide. Identify
three features of an effective how-to guide.

b. Following the Diataxis guidelines, add a how-to guide to the `docs/how-to-guides.md` file
in your documentation folder to show users how to change the destination filename for the output 
CSV dataset generated by the Spacewalks software.

::: spoiler
### Discussion hints & solution

An effective how-to guide should:

+ be goal oriented and focus on action.
+ avoid teaching or explanation
+ use appropriate language e.g. conditional imperatives
+ have an informative title

An example how-to guide for our project to the file `docs/how-to-guides.md`:

```
# How to change the file path of Spacewalk's output dataset

This guide shows you how to set the file path for Spacewalk's output
data set to a location of your choice.

By default, the cleaned data set in CSV format, generated by the Spacewalk software, is saved to the `results/`
folder within the working directory with file name `eva-data.csv`.

If you would like to modify the name or location of the output dataset, set the
second command line argument to your chosen file path. 
For example, if you want to save the output data set to the subfolder `data/clean/` you can 
invoke the script as:

`(venv_spacewalks) $ python3 eva_data_analysis.py eva-data.json data/clean/eva-data-clean.csv`

The specified destination folder `data/clean/` must exist before running spacewalks analysis script.
```

Remember to rebuild your documentation:

```bash
(venv_spacewalks) $ mkdocs build
```

### Exercise: ### Spacewalks tutorial
Let's adapt the how-to guide from the previous challenge into a tutorial that explains 
how to change the file path for the output dataset when running the analysis script.

::: spoiler 
### Solution

Here is what an example tutorial may look like. 

#### Introduction

In this tutorial, we will learn how to change the file path for the output dataset generated by the Spacewalk software.
By the end of this tutorial, you will be able to specify a custom file path for the cleaned dataset.

#### Prerequisites

Before you start, ensure you have the following:

- Python installed on your system
- The Spacewalk script (`eva_data_analysis.py`)
- An input dataset (`eva-data.json`)

####  Prepare the destination directory

First, let us decide where we want to save the cleaned dataset and make sure the directory exists.

For this tutorial, we will use `data/clean/` as the destination folder.

Let's create the directory if it does not exist - e.g. from the command line do:

```bash
(venv_spacewalks) $ mkdir -p data/clean
```

#### Run the analysis script with a custom path

Next, execute the Spacewalk script and specify the custom file path for the output dataset:
```bash
(venv_spacewalks) $ python3 eva_data_analysis.py <input-file> <output-file>
```

Replace <input-file> with your input dataset (`data/eva-data.json`) and <output-file> with your desired output path 
(`data/clean/eva-data-clean.csv`).

Here is the complete command:
```bash
(venv_spacewalks) $ python3 eva_data_analysis.py data/eva-data.json data/clean/eva-data-clean.csv
```

Notice how the output to the command line clearly indicates that we are using a custom output file path.

```output
Using custom input and output filenames
Reading JSON file data/eva-data.json
Saving to CSV file data/clean/eva-data-clean.csv
Adding crew size variable (crew_size) to dataset
Saving to CSV file data/clean/eva-data-clean.csv
Plotting cumulative spacewalk duration and saving to results/cumulative_eva_graph.png
```

After running the script, let us check the `data/clean` directory to ensure the
cleaned dataset has been saved correctly.

```bash
(venv_spacewalks) $ ls data/clean
```
You should see `eva-data-clean.csv` file listed in the `data/clean` folder.

#### Exercise: custom output path

+ Create a new directory named `output/data` in your working directory.
+ Run the Spacewalk script to save the cleaned dataset in the newly created `output/data` directory with the filename `cleaned-eva-data.csv`.
+ Verify that the dataset has been saved correctly.

##### Solution

```bash
# Create the directory:
(venv_spacewalks) $ mkdir -p output/data

# Run the script:
(venv_spacewalks) $ python3 eva_data_analysis.py data/eva-data.json output/data/cleaned-eva-data.csv

# Verify the output:
(venv_spacewalks) $ ls output/data

# You should see cleaned-eva-data.csv listed
```

Congratulations! You have successfully changed the file path for Spacewalks output dataset
and completed an exercise to practice the process. You can now customize the output location
and filename according to your needs.


### Exercise: 
### Tutorial vs. how-to guide

How does the content and language of our example tutorial differ from our example how-to guide?

:::::::::::::::::::::::: spoiler
### Discussion hints

#### Content

- The tutorial clearly signposts what will be covered
- The tutorial includes a narrative of each step and the expected output
- The tutorial highlights important behaviour the learner should notice
- The tutorial includes an exercise to practice skills

#### Language

- The tutorial uses the "we" language
- The tutorial uses imperative to provide clear instructions, e.g. "First do x, then do y"

## Episode: Open software management & collaboration

### Exercise: 
### Archive your repository to Zenodo (Sandbox)

Note: for this exercise, as demonstrated earlier, you should use the [Sandbox Zenodo](https://sandbox.zenodo.org/) (a version of 
Zenodo for testing and playing with before minting a real DOI).
For real software releases, you should use Zenodo.

 * Create an account on Zenodo Sandbox that is linked to your GitHub account.
 * Use Zenodo Sandbox to create a release for your repository and obtain a DOI for it.
 * Get the link to the DOI badge for your repository and add a link to this image to your README file in 
Markdown format. Check that this is the DOI for the latest version and not the DOI for a specific version, 
if not you will be updating this every time you make a release.

### Exercise: 
### Add a DOI to your citation file

Add the DOI you were allocated in the previous exercise to your `CITATION.cff` file and then commit and 
push the updated version to your GitHub repository. 
If you used the `commit` field in your `CITATION.cff` file before to point to a given version of the code - you can 
now remove it as using the DOI field is better for this job.


### Exercise: 
### Write an issue to describe our bug

Create a new issue in your repository's issue tracker by doing the following:

 - Go to the GitHub webpage for your code
 - Click on the Issues tab
 - Click on the "New issue" button
 - Enter a title and description for the issue
 - Click the "Submit Issue" button to create the issue.

### Exercise: 
### Practice pull requests

Q: Work in pairs for this exercise. Share the GitHub link of your repository with your partner. 
If you have set your repository to private, you will need to add them as a collaborator. Go to the settings page on your GitHub repository's webpage, click on Collaborators from 
the left hand menu and then click the green "Add People" button and enter the GitHub username or email address of your partner. 
They will get an email and an alert within GitHub to accept your invitation to work on this repository, without doing this they won't be able to access it.

 - Now make a fork of your partners repository. 
 - Edit the `CITATION.cff` file and add your name to it.
 - Commit these changes to your fork
 - Create a pull request back to the original repository
 - Your partner will now receive your pull request and can review 
## Episode: Wrap-up
