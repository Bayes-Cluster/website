---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Software Installation"
linkTitle: "Software Installation"
weight: 6
---

{{% pageinfo %}}
In default situation, you cannot install software via `sudo` as normal user are not authorized. However, user can install their needed software under their own home directory. Here are some example:
{{% /pageinfo %}}

## Install Python via Anaconda

Conda can create a virtual python environment, and it easily install packages. This created virtual individual environment can solve the python's version and requirement problem and it is fully controlled by the user you can install packages without root permission

1. Activate Anaconda environment
2. Create an environment with conda

```bash
# connect to the Compute Node
salloc && slink

# activate anaconda PATH
module load computing/conda/5.3.1

# using conda
proxychains4 conda create -name=py_env python=3.7

# activate py_env environment
source activate py_env 

# use Beigjing Foreign Studies Univerisy's  Mirrors (https://mirrors.bfsu.edu.cn)
proxychains4 python -m pip config set global.index-url https://mirrors.bfsu.edu.cn/pypi/web/simple

## run program
python main.py
```

## Install R via Anaconda

Conda can create a virtual R environment, and it easily install packages. This created virtual individual environment can solve the R's version and requirement problem and it is fully controlled by the user you can install packages without root permission

1. Activate Anaconda environment
2. Create an environment with conda

```bash
# activate anaconda PATH
module load computing/conda/5.3.1

# using conda
proxychains4 conda create -n r_env

# activate r_env
source activate r_env
proxychains4 conda install -c conda-forge r-base #or proxychains4 conda install -c conda-forge/label/gcc7 r-base
# or proxychains4 conda install r-base
## run program
R
```

**Tips**: sometimes we may use devtools::install_github() to install R pacakge directly from GitHub, however, the connection between the school intranet and GitHub server is not robust enough. Here is a solution:

* install package via the github proxy
* use BFSU CRAN Mirrors: `install.packages("{package_name}", repos="https://mirrors.bfsu.edu.cn/CRAN/")`

## Install Julia via Anaconda

Conda can create a virtual Julia environment, and it easily install packages.

1. Activate Anaconda environment
2. Create an environment with conda

```bash
# activate anaconda PATH
module load computing/conda/5.3.1

# using conda
proxychains4 conda create -name=julia_env julia

# activate py_env environment
source activate py_env 

## run program
julia test.jl
```

## Install packages wihout sudo privileges

User withou sudo priviledges need to compile the package from source, for example:

```bash
install from source
apt-get source PACKAGE
./configure --prefix=$HOME/{package-PATH}
make
make install
```