---
title: "An Introduction to nf-core"
teaching: 10 # teaching time in minutes
exercises: 2 # exercise time in minutes
---

:::::::::::::::::::::::::::::::::::::: questions 

- What is nf-core?
- Why should I use the nf-core framework?
- How can I list and filter nf-core workflows on the command line?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Define nf-core and explain its connection to Nextflow
- List and explain the six main benefits of using the nf-core framework
- Find nf-core community-made workflows and modules on the nf-core website
- List nf-core community-made workflows on the command line using nf-core tools

::::::::::::::::::::::::::::::::::::::::::::::::

## What is nf-core?

Nf-core is a community-led project to develop a set of best-practice workflows scripted using Nextflow workflow management system, as well as a framework for Nextflow workflow development. Nf-core workflows are governed by a set of guidelines, enforced by community code reviews and automatic code testing.

![A diagram showcasing the key aspects of nf-core, a community effort to provide best-practice analysis workflows. The diagram is divided into three sections: Deploy, Participate, and Develop. The Deploy section includes features like Stable workflows, Centralized configs, List and update workflows, and Download for offline use. The Participate section highlights Documentation, Slack workspace, Twitter updates, and Hackathons. The Develop section emphasizes the Starter template, Code guidelines, CI code linting and tests, and Helper tools.](fig/nf-core.png 'nf-core')

## The core features and key benefits of nf-core

There are six core features of nf-core that are beneficial to bioinformaticians and computational biologists, whether they be in a government, private sector, or academic setting:

1. **Community (Participate)**: The developers and users of the nf-core community collaboratively develop best practices, pipelines, and tools. All code is hosted openly on GitHub, and members actively participate in code reviews and discussions on GitHub and Slack.
2. **Guidelines (Develop)**: An established a set of guidelines lists the requirements and recommendations for pipeline development. This ensures consistency and adherence to best practices across all workflows. The requirements and recommendations include thorough documentation, usage examples, results descriptions, and test data sets.
3. **Portability (Deploy)**: All nf-core pipelines allow for execution across local machines and cloud platforms, which surmounts the challenge of creating reproducible analyses across different systems. The nf-core guidelines enforce consistent implementation practices through templates, guidelines, and lint tests that ensure all pipelines fully utilize Nextflow’s portability features. Additionally, nf-core requires all pipelines to bundle dependencies in Docker containers, providing static runtime environments. This minimizes issues related to hardware differences, operating systems, and software versions.
4. **Reproduciblity (Deploy)**: Once stable, nf-core pipelines are given tagged releases on GitHub. Each version is given a number using semantic versioning, and nf-core​ pipelines support the collection of analysis metadata such as pipeline version, software versions, and command and parameter configuration.
5. **Standardization (Develop)**: To help developers get started with new pipelines, nf-core provides a standardized pipeline template that adheres to all nf-core guidelines, as well as command line tools for pipeline creation. This lowers barriers to development and provides consistent structure across all pipelines, making them easier to learn, use, and develop.
7. **Research Impact (Participate)**: The nf-core framework increases reliability and reproduciblity of scientific analyses, and it accelerates scientific discoveries through ready-to-use, validated workflows.

:::::::::::::::::::::::::::::::::::::::::: instructor

Remember to explain how the six main benefits of using nf-core are featured in the main figure for this episode.

:::::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::: discussion

### How might the nf-core framework benefit you?

Take a moment to reflect on the Nextflow workflows you've written or worked on. How might the nf-core framework improve the scripting of your workflow(s)? After reflecting, discuss with the people (or person) next to you.

:::::::::::::::::::::::::::::::::::::::::::::::::::::

## What are nf-core workflows?

nf-core workflows are an organized collection of Nextflow scripts,  other non-nextflow scripts (written in any language), configuration files, software specifications, and documentation hosted on [GitHub](https://github.com/nf-core). There is usually a single pipeline for a given data and analysis type e.g. There is a single pipeline for assembly and variant calling from viral sequence data, Viralrecon. All nf-core workflows are distributed under the [MIT licence](https://en.wikipedia.org/wiki/MIT_License), a highly permissive license that requires the inclusion of a copyright and license notice.

## Finding community workflows

There are two main ways you can find nf-core workflows. You can manually search the workflows page of the nf-core website, found [here](https://nf-co.re/workflows/), or you can use nf-core tools on the command line.

### Finding nf-core workflows online

As an example, we'll look at the webpage for nf-core's [demo pipeline](https://nf-co.re/demo/1.0.1/).

Each nf-core pipeline's webpage contains the following information, organized in tabs:

 1. [Introduction](https://nf-co.re/demo/1.2.0/) - A summary of the pipeline
 2. [Usage](https://nf-co.re/demo/1.2.0/docs/usage/) - Instructions on how to run the pipeline
 3. [Parameters](https://nf-co.re/demo/1.2.0/parameters/) - A list of the pipeline's parameters, which includes a description of the parameter and their default values
 4. [Output](https://nf-co.re/demo/1.2.0/docs/output/) - A description of the pipeline's output
 5. [Results](https://nf-co.re/demo/1.2.0/results/demo/results-32893afef8076a03a2767a020b3f0cab2e0b40b2/) - An example of the pipeline's results
 6. [Releases](https://nf-co.re/demo/releases_stats/) - The pipeline's version history

Other useful information on a pipeline's webpage includes commands to clone the pipeline, and links to ask a question about the pipeline on Slack or open an issue using GitHub. Some workflows also feature Youtube Videos on their webpages, which can also be found on [this playlist](https://youtube.com/playlist?list=PL3xpfTVZLcNh0T2JLJ_hRDqdouS4o8ik7&si=I5-zpScD-HGWas3w).

### Finding nf-core workflows on the command line using nf-core tools

#### What is nf-core tools?

nf-core provides a suite of helper tools aim to help people run and develop workflows.
The [nf-core tools](https://nf-co.re/tools) package is written in Python and can run from the command line or imported and used within other packages.

#### nf-core tools sub-commands

You can use the `--help` option to see the range of nf-core tools sub-commands.

```bash
nf-core --help
```

```output


                                          ,--./,-.
          ___     __   __   __   ___     /,-._.--~\ 
    |\ | |__  __ /  ` /  \ |__) |__         }  {
    | \| |       \__, \__/ |  \ |___     \`-._,-`-,
                                          `._,._,'

    nf-core/tools version 4.0.2 - https://nf-co.re


 Usage: nf-core [OPTIONS] COMMAND [ARGS]...                           
                                                                      
 nf-core/tools provides a set of helper tools for use with nf-core    
 Nextflow workflows.                                                  
 It is designed for both end-users running workflows and also         
 developers creating new workflows.                                   
                                                                      
 ═ Commands ═════════════════════════════════════════════════════════ 
 interface                              Launch the nf-core interface  
 modules        m,module                Commands to manage Nextflow   
                                        DSL2 modules (tool wrappers). 
 pipelines      p,pipeline              Commands to manage nf-core    
                                        workflows.                    
 subworkflows   s,swf,subworkflow       Commands to manage Nextflow   
                                        DSL2 subworkflows (tool       
                                        wrappers).                    
 test-datasets  t,td,tds,test-datasets  Commands to manage nf-core    
                                        test datasets.                
                                                                      
 ═ Options ══════════════════════════════════════════════════════════ 
 --version            Show the version and exit.                      
 --verbose        -v  Print verbose output to the console.            
 --hide-progress      Don't show progress bars.                       
 --log-file       -l  Save a verbose log to a file. [<filename>]      
 --help           -h  Show this message and exit. 
```

#### Listing available nf-core workflows

The simplest sub-command is `nf-core workflows list`, which lists all available nf-core workflows in the nf-core Github repository.

The output shows the latest version number and when that was released.
If the pipeline has been pulled locally using Nextflow, it tells you when that was and whether you have the latest version.

```bash
$ nf-core pipelines list
```

An example of the output from the command is as follows:

```output
                                          ,--./,-.
          ___     __   __   __   ___     /,-._.--~\ 
    |\ | |__  __ /  ` /  \ |__) |__         }  {
    | \| |       \__, \__/ |  \ |___     \`-._,-`-,
                                          `._,._,'

    nf-core/tools version 4.0.2 - https://nf-co.re


┏━━━━━━━━━━━┳━━━━━━━┳━━━━━━━━━━━┳━━━━━━━━━━━┳━━━━━━━━━━━┳━━━━━━━━━━━━┓
┃           ┃       ┃           ┃           ┃           ┃ Have       ┃
┃ Pipeline  ┃       ┃    Latest ┃           ┃      Last ┃ latest     ┃
┃ Name      ┃ Stars ┃   Release ┃  Released ┃    Pulled ┃ release?   ┃
┡━━━━━━━━━━━╇━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━╇━━━━━━━━━━━━┩
│ variantb… │    50 │     1.5.0 │  3 months │         - │ -          │
│           │       │           │       ago │           │            │
│ deepmuts… │     5 │       dev │  11 hours │         - │ -          │
│           │       │           │       ago │           │            │
│ mhcquant  │    49 │     3.2.0 │  2 months │         - │ -          │
│           │       │           │       ago │           │            │
│ proteinf… │   108 │     2.0.0 │  4 months │         - │ -          │
│           │       │           │       ago │           │            │
│ methylseq │   197 │     4.2.0 │  7 months │         - │ -          │
│           │       │           │       ago │           │            │
│ rnastruc… │     1 │       dev │ yesterday │         - │ -          │
│ datasync  │    10 │       dev │    2 days │         - │ -          │
│           │       │           │       ago │           │            │
│ raredise… │   122 │     3.1.2 │   2 weeks │         - │ -          │
│           │       │           │       ago │           │            │
│ rnasplice │    68 │     1.0.4 │   2 years │         - │ -          │
│           │       │           │       ago │           │            │
│ sarek     │   583 │     3.9.0 │   3 weeks │         - │ -          │
[..truncated..]
```

#### Filtering available nf-core workflows

If you supply additional keywords after the `workflows list` sub-command, the listed pipeline will be filtered.
**Note:** that this searches more than just the displayed output, including keywords and description text.

Here we filter on the keywords **genome** and **assembly**.

```bash
$ nf-core pipelines list genome assembly
```

```output
                                          ,--./,-.
          ___     __   __   __   ___     /,-._.--~\ 
    |\ | |__  __ /  ` /  \ |__) |__         }  {
    | \| |       \__, \__/ |  \ |___     \`-._,-`-,
                                          `._,._,'

    nf-core/tools version 4.0.2 - https://nf-co.re


┏━━━━━━━━━━━━━━━━━┳━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━┓
┃ Pipeline Name   ┃ Stars ┃ Latest Release ┃      Released ┃ Last Pulled ┃ Have latest release? ┃
┡━━━━━━━━━━━━━━━━━╇━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━┩
│ mag             │   308 │          5.4.2 │  4 months ago │           - │ -                    │
│ bacass          │    91 │          2.6.0 │  3 months ago │           - │ -                    │
│ genomeqc        │    24 │            dev │   1 weeks ago │           - │ -                    │
│ genomeassembler │    33 │          1.1.0 │ 12 months ago │           - │ -                    │
│ funcscan        │   117 │          4.0.0 │   3 weeks ago │           - │ -                    │
│ genomeskim      │     4 │            dev │   4 years ago │           - │ -                    │
│ genomeannotator │    38 │            dev │   4 years ago │           - │ -                    │
└─────────────────┴───────┴────────────────┴───────────────┴─────────────┴──────────────────────┘
```

::::::::::::::::::::::::::::: challenge

### Finding genome assembly workflows

1. What `nf-core` command would you use to list any bacterial genome assembly workflows?
2. How many genome assembly workflows are there?

::::: hint

nf-core tool's subcommands can be listed using `nf-core --help`

::::::::::

:::: solution

1. `nf-core pipelines list bacterial genome assembly`
2. One, bacass

:::::::::::::

:::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: keypoints 

- nf-core is a community-led project to develop a set of best-practice workflows built using the Nextflow workflow management system.
- nf-core is portable, reproducible, and standardized, making it an ideal framework for workflow design
- The nf-core tool (nf-core) is a suite of helper tools that aims to help people run and develop nf-core workflows.
- nf-core workflows can be found using `nf-core pipelines list`, or by checking the nf-core website.

::::::::::::::::::::::::::::::::::::::::::::::::
