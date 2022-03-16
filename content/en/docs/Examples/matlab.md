---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "MATLAB"
linkTitle: "MATLAB"
weight: 1
---

For now, MATLAB is no supported via the web portal, thus, user can only submit their MATLAB jobs via the terminal.Here is an example:

```bash
#!/bin/bash
#SBATCH -J test               # The job's name is test
#SBATCH -N 1                  # allocate 1 node
#SBATCH -p CPU-Compute        # submit the job to cpu partition
#SBATCH --cpus-per-task=4     # allocate 4 cpu cores
#SBATCH -t 1-00:00:00         # runtime: 1 day

module load computing/MATLAB/2021b # load matlab module

# use MATLAB to run the "Test.m" file
matlab -nodesktop -nosplash -nodisplay -r "Test"
```

`matlab -nodesktop -nosplash -nodisplay` means <u>disable the MATLAB GUI and welcome page</u>, `-r` means excecute the MATLAB command. The file name is “Test.m”, however, in the script, <u>we need to remove the “.m”</u>