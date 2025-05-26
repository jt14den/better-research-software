---
title: "Course introduction"
teaching: 30
exercises: 0
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is open and reproducible research?
- Why are these practices important, in particular in the context of software used to support such research?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

After completing this episode, participants should be able to:

- Understand the concept of open and reproducible research
- Understand why these principles are of value in the research community 
- Setup their machine with software and data used to teach this course

::::::::::::::::::::::::::::::::::::::::::::::::

Software is [fundamental to modern research][ssi-survey-2014] - some of it would even be impossible without software. 
From short, thrown-together temporary scripts written to help with day-to-day research tasks, through an abundance of complex data analysis spreadsheets, to the hundreds of software engineers and millions of lines of code behind international efforts such as the Large Hadron Collider, there are few areas of research where software does not have a fundamental role.

This course teaches good practices and reproducible working methods that are agnostic of a programming language (although we will use Python code in our examples).
It aims to provide researchers with the tools and knowledge to feel confident when writing **good quality and sustainable software** to support their research.
Although the discussion will often focus on software developed in the context of research, most of the good practices introduced here are beneficial to software development more generally.

The lesson is particularly focused on one aspect of good (scientific) software development practice: improving software to enhance reproducibility.
That is, enabling others to run our code and obtain the same results we did.


:::::::::::::::::::::: callout

## Why should I care about reproducibility?
Scientific transparency and rigor are key factors in research. 
Scientific methodology and results need to be published openly and replicated and confirmed by several independent parties.
However, research papers often lack the full details required for independent reproduction or replication. 
Many attempts at reproducing or replicating the results of scientific studies have failed in a variety of disciplines ranging from psychology ([The Open Science Collaboration (2015)][replication-crisis-osc]) to cancer sciences ([Errington et al (2021)][replication-crisis-errington]).
These are called [**the reproducibility and replicability crises**][reproducibility-crisis] - ongoing methodological crises in which the results of many scientific studies are difficult or impossible to repeat.

Reproducible research is a practice that ensures that researchers can repeat the same analysis multiple times with the same results. 
It offers many benefits to those who practice it:

* Reproducible research helps researchers remember how and why they performed specific tasks and analyses; this enables easier explanation of work to collaborators and reviewers. 
* Reproducible research enables researchers to quickly modify analyses and figures - this is often required at all stages of research and automating this process saves loads of time. 
* Reproducible research enables reusability of previously conducted tasks so that new projects that require the same or similar tasks become much easier and efficient by reusing or reconfiguring previous work. 
* Reproducible research supports researchers' career development by facilitating the reuse and citation of all research outputs - including both code and data.
* Reproducible research is a strong indicator of rigor, trustworthiness, and transparency in scientific research. 
  This can increase the quality and speed of peer review, because reviewers can directly access the analytical process described in a manuscript. 
  It increases the probability that errors are caught early on - by collaborators or during the peer-review process, helping alleviate the reproducibility crisis.  

However, reproducible research often requires that researchers implement new practices and learn new tools.
This course aims to teach some of these practices and tools pertaining to the use of software to conduct reproducible research.

[The extra page on Reproducible Research](./learners/reproducible-research-discussion.md) provides a more in-depth discussion of this topic.

::::::::::::::::::::::::::::::

## Practices for Building Better Research Software
The practices we will cover for building better research software fall into three areas.

### 1. Things you can do with your own computing environment to enhance the software

* Using virtual development environments ensures your software can be developed and run consistently across different systems, making it easier for you and others to run, reuse, and extend your code.

### 2. Things you can do to improve the source code of the software itself

* Organising and structuring your code keeps your software clean, modular, and reusable, enhancing its readability, extensibility, and reusability.
* Following coding conventions and guides for your programming language ensures that others find it easy to read your code, reuse or extend it in their own examples and applications.
* Testing can save time spent on debugging and ensures that your code is correct and does what it is set out to do, giving you and others confidence in your code and the results it produces.

### 3. Things you can do to make the software easier for other people to use

* Using version control and collaboration platforms like [GitHub](https://github.com), [GitLab](https://gitlab.com), and [CodeBerg](https://codeberg.org/) makes it easier to share code and work on it together.
* Fostering a community around your software and promoting collaboration helps to grow a use base for your software and contributes to its long-term sustainability. 
* Providing clear and comprehensive documentation, including code comments, API specifications, setup guides, and usage instructions, ensures your software is easy to understand, use, and extend (by you and others).
* Accompanying your software with clear information about its licensing terms and how it should be cited ensures that others can reuse and adapt your code with confidence and that you receive credit when they do so.

:::::::::::::::::: challenge

Individually,

- reflect on what practices (and tools) you are already using in your software development workflow,
- list at least 3 new practices or tools that you would like to start employing or using.

Write your reflections in the shared collaborative document.

::::::::::::::::::

## Further reading

We recommend the following resources for some additional reading on reproducible research:

* [The Turing Way's "Guide for Reproducible Research"][ttw-guide-reproducible-research]
* [A Beginner's Guide to Conducting Reproducible Research][beginner-guide-reproducible-research], Jesse M. Alston, Jessica A. Rick, Bulletin of The Ecological Society of America 102 (2) (2021), https://doi.org/10.1002/bes2.1801
* ["Ten reproducible research things" tutorial][10-reproducible-research-things]
* [FORCE11's FAIR 4 Research Software (FAIR4RS) Working Group][fair4rs-working-group]
* ["Good Enough Practices in Scientific Computing" course][good-enough-practices]
* [Reproducibility for Everyone's (R4E) resources][repro4everyone], community-led education initiative to increase adoption of open research practices at scale
* [Training materials on different aspects of research software engineering][intersect-rse-training] (including open source, reproducibility, research software testing, engineering, design, continuous integration, collaboration, version control, packaging,  etc.), compiled by the [INTERSECT project](https://intersect-training.org/) 
* [Curated resources][forrt-resources] by the [Framework for Open and Reproducible Research Training](https://forrt.org/) (FORRT)

## Acknowledgements and references
The content of this course borrows from or references [various work](learners/reference.md#litref).
