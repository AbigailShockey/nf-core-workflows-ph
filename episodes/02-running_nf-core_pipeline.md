---
title: "Running an nf-core pipeline"
teaching: 20 # teaching time in minutes
exercises: 5 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I download an nf-core pipeline using nf-core tools?
- How do I find out what inputs and outputs a pipeline has?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Download nf-core pipelines on command line utilizing Nextflow
- Find the expected inputs and outputs of a pipeline

::::::::::::::::::::::::::::::::::::::::::::::::

In the last episode, we used nf-core tools to search for pipelines. We will now go through the process of downloading and running an nf-core pipeline. 

### Downloading nf-core pipelines

#### Software requirements for nf-core pipelines

As we work with nf-core pipelines, we should consider their software dependencies. nf-core pipelines specify these dependencies using Docker, Singularity, or Conda, and Nextflow handles downloading the containers and creating the Conda environments for you. In theory it is possible to run the pipelines with software installed by other methods (e.g. environment modules or manual installation), but this is not recommended. You will not need to manage any of this in this training, because the tools used by our pipelines are already downloaded in your environment.


#### Fetching pipeline code with Nextflow

Unless you are actively developing pipeline code, you should use Nextflow's [built-in functionality](https://www.nextflow.io/docs/latest/sharing.html) to fetch nf-core pipelines. You can use the following command to pull the latest version of a remote workflow from the nf-core GitHub site.

```bash
$ nextflow pull nf-core/<PIPELINE>
```

For the best reproducibility, it is good to explicitly reference the pipeline version number that you wish to use with the `-revision`/`-r` flag.

In the example below we are pulling the viralrecon pipeline version 3.0.0. Viralrecon has not yet been updated to support strict config parsing, which was introduced in Nextflow v26 (the version installed in our working environment). We will not cover strict parsing in this training, but we need to set `NXF_SYNTAX_PARSER` variable equal to `v1` so viralrecon runs without errors.

```bash
$ export NXF_SYNTAX_PARSER=v1
$ nextflow pull nf-core/viralrecon -revision 3.0.0
```

```output
Checking nf-core/viralrecon:3.0.0 ...
 downloaded from https://github.com/nf-core/viralrecon.git - revision: 395079f1d2 [3.0.0]
```

### Usage instructions and documentation

As we discussed in the last episode, you can find general documentation and instructions for Nextflow and nf-core on the [nf-core website](https://nf-co.re/).
Pipeline-specific documentation is bundled with each pipeline in the /docs folder. This can be read either locally, on GitHub, or on the nf-core website.

Each pipeline has its own webpage at [https://nf-co.re/](https://nf-co.re/)\<pipeline\_name> e.g. [nf-co.re/rnaseq](https://nf-co.re/rnaseq/usage)

In addition to this documentation, each pipeline comes with basic command-line reference. This can be seen by running the pipeline with the parameter `--help`, for example. The `--help` option is a quick way to find out what a pipeline needs and where its results go.

```bash
nextflow run -r 3.0.0 nf-core/viralrecon --help -profile test
```

**Note:** For some pipelines the `--help` option is sufficient, but viralrecon requires its required parameters be fulfilled in order for the `--help` option to work. This is why we used a special profile called `test`. 

The help output groups parameters by topic. Look for the **Input/output options** group, which lists:

```
 N E X T F L O W   ~  version 26.04.6

Launching `https://github.com/nf-core/viralrecon` [big_stone] revision: 395079f1d2 [3.0.0]


------------------------------------------------------
                                        ,--./,-.
        ___     __   __   __   ___     /,-._.--~'
  |\ | |__  __ /  ` /  \ |__) |__         }  {
  | \| |       \__, \__/ |  \ |___     \`-._,-`-,
                                        `._,._,'
  nf-core/viralrecon 3.0.0
------------------------------------------------------
Typical pipeline command:

  nextflow run nf-core/viralrecon -profile <docker/singularity/.../institute> --input samplesheet.csv --outdir <OUTDIR>

given to `--help`, the full help message of that parameter will be 
printed.  
combination with `--help` or `--help_full`.  

Input/output options
  --input                        [string] Path to comma-separated file containing information about the samples you 
would like to analyse.  
  --platform                     [string] NGS platform used to sequence the samples.  (accepted: illumina, 
nanopore)  
  --protocol                     [string] Specifies the type of protocol used for sequencing.  (accepted: 
metagenomic, amplicon)  
  --outdir                       [string] The output directory where the results will be saved. You have to use 
absolute paths to storage on Cloud infrastructure.  
  --email                        [string] Email address for completion summary. 
  --multiqc_title                [string] MultiQC report title. Printed as page header, used for filename if not 
otherwise specified.  
```

Looking at the output from the `--help` command we can see which parameters important for inputs and outputs and a description of what they are and what the pipeline expects. 

Other parameter groups in the output detail specific parameters that can be used for different parts of the pipeline, for example they can be used for reference genome or tool analysis options.

The `test` profile runs the pipeline on a small dataset to make sure the pipeline works as expected. In this episode we will not be running this command, but it can be a helpful way to verify the pipeline works as expected in your environment.


:::::::::::::::::::::::::::::::::::::: challenge

### Running an nf-core pipeline: Exercise 1
1. What command would you use to download the 'bacass' pipeline using the `nf-core tools`? 
2. What additional flags would you add to your command that would download the specific version of 2.6.0?
3. What `nextflow` command would you run that would provide the inputs and outputs of the pipeline?

:::::::::::::: solution

### Answers 
1. `nf-core pipelines download bacass`
2. `nf-core pipelines download bacass -revision 2.6.0`
3. `nextflow run nf-core/bacass --help`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- The nf-core tools (`nf-core`) is a suite of helper tools that aims to help people run and develop nf-core pipelines.
- nf-core pipelines can be downloaded with `nextflow pull nf-core/<pipeline>`, and a specific version can be downloaded with `-revision`/`-r` flag.
- You can use the `nextflow run nf-core/<pipeline> --help` syntax to view the input an outputs of a nf-core workflow.

::::::::::::::::::::::::::::::::::::::::::::::::
