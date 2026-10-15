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


### What are nf-core pipelines?

nf-core pipelines are an organised collection of Nextflow scripts,  other non-nextflow scripts (written in any language), configuration files, software specifications, and documentation hosted on [GitHub](https://github.com/nf-core). There is usually a single pipeline for a given data and analysis type e.g. There is a single pipeline for bulk RNA-Seq. All nf-core pipelines are distributed under the [MIT licence](https://en.wikipedia.org/wiki/MIT_License).

### What is nf-core tools?

nf-core provides a suite of helper tools aim to help people run and develop pipelines.
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
 Nextflow pipelines.                                                  
 It is designed for both end-users running pipelines and also         
 developers creating new pipelines.                                   
                                                                      
 ═ Commands ═════════════════════════════════════════════════════════ 
 interface                              Launch the nf-core interface  
 modules        m,module                Commands to manage Nextflow   
                                        DSL2 modules (tool wrappers). 
 pipelines      p,pipeline              Commands to manage nf-core    
                                        pipelines.                    
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

### Listing available nf-core pipelines

The simplest sub-command is `nf-core pipelines list`, which lists all available nf-core pipelines in the nf-core Github repository.

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

#### Filtering available nf-core pipelines

If you supply additional keywords after the `pipelines list` sub-command, the listed pipeline will be filtered.
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
