---
title: "Running an nf-core pipeline"
teaching: 20 # teaching time in minutes
exercises: 5 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- Questions for episode

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

_By the end of this episode, learners will be able to..._

- Utilize nf-core tools to download a pipeline on command line
- Describe the inputs and outputs of pipeline
- Run the demo nf-core pipeline on the command line using the built-in test profile

::::::::::::::::::::::::::::::::::::::::::::::::

Episode content will go here...

:::::::::::::::::::::::::::::::::::::: challenge

### Running an nf-core pipeline: Exercise 1
1. What command would you use to download the 'bacass' pipeline using the `nf-core tools`? 
2. What additional flags would you add to your command that would download the specific version of 2.6.0?
3. What `nextflow` command would you run that would provide the inputs and outputs of the pipeline?
:::::::::::::: solution

### Answers 
1. `nf-core pipelines download bacass`
2. `nf-core pipelines download bacass --revision 2.6.0`
3.  `nextflow run nf-core/bacass --help`


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: Keypoints

- Keypoints for episode

::::::::::::::::::::::::::::::::::::::::::::::::
