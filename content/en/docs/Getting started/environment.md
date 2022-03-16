---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Environment Module"
linkTitle: "Environment Module"
weight: 3
---

## Overview 

“Environment Modules” are the mechaism by which much of the software is made available to the users of USBC. The Modules package is a tool that simplifies shell initialization and lets users easily modify theire environment during a session using modulefiles.

## Check the Avaiable Module and Loaded Module

Before running the code, you can list all (loaded and unlabled modules) on Bayes cluster using:

```bash
user_name@Compute2030005000:~$ module avail
------------------------------------------ /usr/share/modules/modulefiles ------------------------------------------
compiler/cuda/10.2          computing/conda/5.3.1  computing/MATLAB/2021b
compiler/mpi/openmpi/4.1.1  computing/gap/4.11.1   computing/SageMath/9.3
```

## Load and Unload Module

You can then load a module by using `module load ` and use `module list` to check loaded module: 

```bash
user_name@Compute2030005000:~$ module load computing/MATLAB/2021b
user_name@Compute2030005000:~$ module list
Currently Loaded Modulefiles:
 1) computing/MATLAB/2021b
```

If you want to stoping using a module (by undoing the changes that loading that module made to your environment):

```bash
user_name@Compute2030005000:~$ module unload computing/MATLAB/2021b
user_name@Compute2030005000:~$ module list
No Modulefiles Currently Loaded.
user_name@Compute2030005000:~$
```

{{% alert title="Notice" color="warning" %}}
`module` can be only used in the Compute Node.
{{% /alert %}}