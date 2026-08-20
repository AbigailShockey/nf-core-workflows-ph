---
title: "An Introduction to nf-core"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is nf-core?
- Why should I use the nf-core framework?
- How can I list and filter nf-core pipelines on the command line?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Define nf-core and explain its connection to Nextflow
- List and explain the six main benefits of using the nf-core framework
- Find nf-core community-made pipelines and modules on the nf-core website
- List nf-core community-made pipelines on the command line using nf-core tools

::::::::::::::::::::::::::::::::::::::::::::::::

## What is nf-core?

The instructor should describe that nf-core is both a framework and a community built around creating standardized Nextflow workflows according to a specific set of guidelines. There are six main benefits to the nf-core framework outlined in nf-core's main publication that the instructor should define (community, guidelines, portability, reproducibility, standardization, and research impact).

:::::::::::::::::::::::::::::::::::::::::: instructor

Remember to explain how the six main benefits of using nf-core are featured in the main figure for this episode.

:::::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::: discussion

### How might the nf-core framework benefit you?

Take a moment to reflect on the Nextflow workflows you've written or worked on. How might the nf-core framework improve the scripting of your workflow(s)? After reflecting, discuss with the people (or person) next to you.

:::::::::::::::::::::::::::::::::::::::::::::::::::::

## Finding community workflows on the command line with nf-core tools

The instructor should demonstrate the usage of the `nf-core` starting with `nf-core --help`. They should then describe the most important subcommands for the lesson (`pipelines` and `modules`) and demonstrate the usage of `nf-core pipelines --help` and `nf-core pipelines list`. This section should close with an explanation of filtering pipelines with keywords using `nf-core pipelines list`.

::::::::::::::::::::::::::::: challenge

### Finding genome assembly pipelines

1. What `nf-core` command would you use to list any bacterial genome assembly pipelines?
2. How many genome assembly pipelines are there?

::::: hint

nf-core tool's subcommands can be listed using `nf-core --help`

::::::::::

:::: solution

1. `nf-core pipelines list bacterial genome assembly`
2. One, bacass

:::::::::::::

:::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- nf-core is a community-led project to develop a set of best-practice pipelines built using the Nextflow workflow management system.
- nf-core is portable, reproducible, and standardized, making it an ideal framework for workflow design
- The nf-core tool (nf-core) is a suite of helper tools that aims to help people run and develop nf-core pipelines.
- nf-core pipelines can be found using nf-core pipelines list, or by checking the nf-core website.

::::::::::::::::::::::::::::::::::::::::::::::::
