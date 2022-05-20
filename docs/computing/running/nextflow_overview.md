# Nextflow

Running and managing workflows for bioinformatics applications can be challenging
as the workflows usually are fragile eco-systems of several software tools and their
dependencies. We therefore need a workflow manager like [Nextflow](https://www.nextflow.io/) 
to manage our scientific workflow. Nextflow is a groovy-based language for expressing the entire 
workflow in a single script and flexibly deployed in different computing environments including 
on CSC HPC systems like Puhti/Mahti.


## Strengths:

* Easy installation and can be used with different executors including local/slurm/flux in CSC environment
* No persistent database setup is needed
* Good for complex workflows with several dependencies
* Support for HPC-friendly containers (singularity)

## Weaknesses:

* Understanding of configuration settings is needed when working in multi-user environment 
  like Puhti/Mahti
* Nextflow makes a lot of duplicate and intermediate file copies as it operates;
  processing large amounts of data can easily exhaust storage quotas
* Create many jobs & job steps as number of tasks and complexity of workflows increases.

## Supported with caveats

* When using Slurm executor, pay attention to number of jobs/job steps a workflow creates.
  This can lead to long queue waiting times for tasks besides causing overhead on slurm accounting DB.


## How to use Nextflow at CSC (WIP)
   
