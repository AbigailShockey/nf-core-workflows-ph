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

In the example below we are pulling the nf-core/demo pipeline version 1.2.0.

```bash
$ nextflow pull nf-core/demo -revision 1.2.0
```

```output
Checking nf-core/demo:1.2.0 ...
 done - revision: 32893afef8 [1.2.0]
```

### Usage instructions and documentation

As we discussed in the last episode, you can find general documentation and instructions for Nextflow and nf-core on the [nf-core website](https://nf-co.re/).
Pipeline-specific documentation is bundled with each pipeline in the /docs folder. This can be read either locally, on GitHub, or on the nf-core website.

Each pipeline has its own webpage at [https://nf-co.re/](https://nf-co.re/)\<pipeline\_name> e.g. [nf-co.re/rnaseq](https://nf-co.re/rnaseq/usage)

In addition to this documentation, each pipeline comes with basic command-line reference. This can be seen by running the pipeline with the parameter `--help`, for example. The `--help` option is a quick way to find out what a pipeline needs and where its results go.

```bash
nextflow run -r 1.2.0 nf-core/demo --help
```

The help output groups parameters by topic. Look for the **Input/output options** group, which lists:

```
  N E X T F L O W   ~  version 26.04.6

Launching `https://github.com/nf-core/demo` [hopeful_mendel] revision: 32893afef8 [1.2.0]


------------------------------------------------------
                                        ,--./,-.
        ___     __   __   __   ___     /,-._.--~'
  |\ | |__  __ /  ` /  \ |__) |__         }  {
  | \| |       \__, \__/ |  \ |___     \`-._,-`-,
                                        `._,._,'
  nf-core/demo 1.2.0
------------------------------------------------------
Typical pipeline command:

  nextflow run nf-core/demo -profile <docker/singularity/.../institute> --input samplesheet.csv --outdir <OUTDIR>


Input/output options
  --input                       [string] Path to a metadata file containing information about the samples in the experiment. 
  --outdir                      [string] The output directory where the results will be saved. You have to use absolute paths to storage on Cloud infrastructure. 
  --email                       [string] Email address for completion summary. 
  --multiqc_title               [string] MultiQC report title. Printed as page header, used for filename if not otherwise specified. 

Reference genome options
  --genome                      [string] Name of iGenomes reference. 
  --fasta                       [string] Path to FASTA genome file. 

Process skipping options
  --skip_trim                   [boolean] Skip trimming fastq files with seqtk 

Generic options
  --multiqc_methods_description [string]          Custom MultiQC yaml file containing HTML including a methods description. 
  --help                        [boolean, string] Display the help message. 
  --help_full                   [boolean]         Display the full detailed help message. 
  --show_hidden                 [boolean]         Display hidden parameters in the help message (only works when --help or --help_full are provided). 
 !! Hiding 19 param(s), use the `--showHidden` parameter to show them !!
------------------------------------------------------

```

Looking at the output from the `--help` command we can see which parameters important for inputs and outputs and a description of what they are and what the pipeline expects. 

Other parameter groups in the output detail specific parameters that can be used for different parts of the pipeline, for example they can be used for reference genome or tool analysis options.


:::::::::::::::::::::::::::::::::::::: challenge

### Running an nf-core pipeline: Exercise 1
1. What command would you use to download the 'nf-core/bacass' pipeline using nextflow? 
2. What additional flags would you add to your command that would download the specific version of 2.6.0?
3. What `nextflow` command would you run that would provide the inputs and outputs of the pipeline?

:::::::::::::: solution

### Answers 
1. `nextflow pull nf-core/bacass`
2. `nextflow pull nf-core/bacass -revision 2.6.0`
3. `nextflow run nf-core/bacass --help`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- The nf-core tools (`nf-core`) is a suite of helper tools that aims to help people run and develop nf-core pipelines.
- nf-core pipelines can be downloaded with `nextflow pull nf-core/<pipeline>`, and a specific version can be downloaded with `-revision`/`-r` flag.
- You can use the `nextflow run nf-core/<pipeline> --help` syntax to view the input an outputs of a nf-core workflow.

::::::::::::::::::::::::::::::::::::::::::::::::
