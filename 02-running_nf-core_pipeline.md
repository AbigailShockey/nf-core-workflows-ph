---
title: "Running an nf-core pipeline"
teaching: 20 # teaching time in minutes
exercises: 5 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- How do I download an nf-core pipeline using nf-core tools?
- How do I find out what inputs and outputs a pipeline has?
- How do I run an nf-core pipeline using its built-in test profile?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

_By the end of this episode, learners will be able to..._

- Utilize nf-core tools to download a pipeline on command line
- Find the expected inputs and outputs of a pipeline
- Run the demo nf-core pipeline on the command line using the built-in test profile

::::::::::::::::::::::::::::::::::::::::::::::::

We have started to use the nf-core tool by searching for piplines. We will now go through the process of downloading and running a nf-core pipeline. 

### Downloading nf-core pipelines

#### Software requirements for nf-core pipelines

Something to consider as we work with nf-core pipelines are their softer depencides. nf-core pipeline software dependencies are specified using either Docker, Singularity or Conda. It is Nextflow that handles the downloading of containers and creation of conda environments. In theory it is possible to run the pipelines with software installed by other methods (e.g. environment modules, or manual installation), but this is not recommended. This something you will not need to worry about in this training, since the tools used by the pipelines are already downloaded in our environments.

#### Fetching pipeline code with nextflow

Unless you are actively developing pipeline code, you should use Nextflow's [built-in functionality](https://www.nextflow.io/docs/latest/sharing.html) to fetch nf-core pipelines. You can use the following command to pull the latest version of a remote workflow from the nf-core github site.;

```bash
$ nextflow pull nf-core/<PIPELINE>
```

For the best reproducibility, it is good to explicitly reference the pipeline version number that you wish to use with the `-revision`/`-r` flag.

In the example below we are pulling the viralrecon pipeline version 3.0.0. Viralrecon is not yet upated to strict config parsing, a change implemented in v26 of Nextflow (the version installed in the working environment) that we will not discuss as part of this training. We need to export the `NXF_SYNTAX_PARSER` param equal to `v1` to run viralrecon without an error.

```bash
$ export NXF_SYNTAX_PARSER=v1
$ nextflow pull nf-core/viralrecon -revision 3.0.0
```

```output
Checking nf-core/viralrecon:3.0.0 ...
 downloaded from https://github.com/nf-core/viralrecon.git - revision: 395079f1d2 [3.0.0]
```
## Usage instructions and documentation

You can find general documentation and instructions for Nextflow and nf-core on the [nf-core website](https://nf-co.re/) .
Pipeline-specific documentation is bundled with each pipeline in the /docs folder. This can be read either locally, on GitHub, or on the nf-core website.

Each pipeline has its own webpage at [https://nf-co.re/](https://nf-co.re/)\<pipeline\_name> e.g. [nf-co.re/rnaseq](https://nf-co.re/rnaseq/usage)

In addition to this documentation, each pipeline comes with basic command line reference. This can be seen by running the pipeline with the parameter `--help` , for example. The `--help` options is the quickest way to find out what a pipeline needs and where its results go. :

```bash
nextflow run -r 3.0.0 nf-core/viralrecon --help -profile test
```

**Note:** For some pipelines the `--help` option is sufficient, but viralrecon requires its required parameters be fulfilled in order for the `--help` option to work. This is why we used a special profile called `test`. 

The help ouput groups parameters by topic. Look for the **Input/output options** group, which lists:

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

  nextflow run nf-core/viralrecon -profile <docker/singularity/.../institute> --input samplesheet.csv --outdir<OUTDIR>

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

Looking at the ouptut from the `--help` command we can see what parameters important for inputs and outputs and a descriptions of what they are and what the pipeline expects. 

Other parameter groups in the ouput detail specific parameters that can be used for reference genome or tool analysis options.

The `test` profile runs the pipeline on a small dataset to make sure the pipeline works as expected. When downloading a new pipeline it may be good to look at the documentation and run the test profile to make sure the pipeline works as expected in your environment.

:::::::::::::::::::::::::::::::::::::::  challenge

### Running an nf-core pipeline: Exercise 1
1. What command would you use to download the 'bacass' pipeline using the `nf-core tools`? 
2. What additional flags would you add to your command that would download the specific version of 2.6.0?
3. What `nextflow` command would you run that would provide the inputs and outputs of the pipeline?
4. What `nextflow` command would you run to to run the 'bacass' pipeline version 2.6.0 using the test profile with docker, saving results to a folder called 'results'?
   
:::::::::::::::  solution

### Answers 
1. `nf-core pipelines download bacass`
2. `nf-core pipelines download bacass --revision 2.6.0`
3. `nextflow run nf-core/bacass --help`
4. `nextflow run nf-core/bacass -r 2.6.0 -profile test --outdir results`

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


::::::::::::::::::::::::::::::::::::: keypoints

- The nf-core tool (`nf-core`) is a suite of helper tools that aims to help people run and develop nf-core pipelines.
- nf-core pipelines can be downloaded with `nextflow pull nf-core/<pipeline>`, and a specific version can be downloaed with `-revision`/`-r` flag.
- An nf-core workflow is run using `nextflow run nf-core/<pipeline>` syntax.
- The `test` profile runs a pipeline on a small built-in dataset to check that everything works.

::::::::::::::::::::::::::::::::::::::::::::::::
