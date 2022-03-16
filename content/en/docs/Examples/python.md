---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Python, R and Julia"
linkTitle: "Python, R and Julia"
weight: 2
---

## Python

It is easy for you to run the Python Script with SLURM, here is an example, assumes that we want to run job.py, with conda-based Python environment:

```bash
#!/bin/bash
#SBATCH -J test               # The job's name is test
#SBATCH -N 1                  # allocate 1 node
#SBATCH -p CPU-Compute        # submit the job to cpu partition
#SBATCH --cpus-per-task=4     # allocate 4 cpu cores
#SBATCH -t 1-00:00:00         # runtime: 1 day

module load computing/conda/5.3.1
source activate environment_name

python test.py
```

## R

It is easy for you to run the R Script with SLURM, here is an example, assumes that we want to run job.py, with conda-based Python environment:

```bash
#!/bin/bash
#SBATCH -J test               # The job's name is test
#SBATCH -N 1                  # allocate 1 node
#SBATCH -p CPU-Compute        # submit the job to cpu partition
#SBATCH --cpus-per-task=4     # allocate 4 cpu cores
#SBATCH -t 1-00:00:00         # runtime: 1 day

module load computing/conda/5.3.1
source activate environment_name

Rscript --vanilla test.R
```

## Julia

It is easy for you to run the Julia Script with SLURM, here is an example, assumes that we want to run job.py, with conda-based Python environment:

```bash
#!/bin/bash
#SBATCH -J test               # The job's name is test
#SBATCH -N 1                  # allocate 1 node
#SBATCH -p CPU-Compute        # submit the job to cpu partition
#SBATCH --cpus-per-task=4     # allocate 4 cpu cores
#SBATCH -t 1-00:00:00         # runtime: 1 day

module load computing/conda/5.3.1
source activate environment_name

julia test.jl
```

