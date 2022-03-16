
---
title: "System Information"
linkTitle: "System Information"
date: 2018-01-04
description: >
  A brief introduction on our system and Architecture
categories: ["System"]
tags: ["system", "introduction", "docs"]
---

## Overview

The Bayes cluster is intended for running smaller jobs, as well as developing, debugging, and testing codes. It is a self-built and hosted  beowulf cluster. Each compute node has 20 cores 2.20 GHz Intel Skylake CPU-cores and 256 GB RAM. There are also two nodes with GPUs (NVIDIA-P100). For more details see the Hardware Configuration section below.

| NodeName          | CPU      | Memory | GPU             | Storage |
|-------------------|----------|--------|-----------------|---------|
| Control           | 20 cores | 128GB  | NA              | 240GB   |
| Compute2030005000 | 20 cores | 128GB  | NA              | 600GB   |
| Compute2030005001 | 20 cores | 128GB  | NA              | 3.0 TB  |
| Compute2030005002 | 20 cores | 128GB  | Tesla P100 12GB | 4.8TB   |
| Compute2030005003 | 20 cores | 128GB  | Tesla P100 12GB | 4.8TB   |


## How to Access the Bayes Cluster

You have to request an account before using the Bayes cluster, and then log in through SSH.

1. Requesting Access to Bayes: if you would like an account on Bayes, please fill out the <a href="https://baidu.com" style="text-decoration: none;">Application</a> for to request an account
2. Logging into Bayes: <code style="color: gray">ssh <user_name>@hpc.uicstat.com</code>

## How to work on the Bayes Cluster

Since Bayes Cluster is runing a Linux system, knowing some basic Linux commands is hightly recommended. For an introduction to navigating a Linux system, here are some reference:
* <a href="https://training.linuxfoundation.org/training/introduction-to-linux/">Introduction to Linux</a> | by Linux Foundatation
* <a href="https://github.com/uschpc/workshop-intro-linux">Introduction to Linux and Command Line</a> | by USC-HPC 

Then, please read our <a href="/document/introduction/">guideline of the Bayes cluster</a> to know more about the file systems, module system, and scheduling system running on Bayes cluster.

## Notice

The control node on Bayes should be used for the basic usage (log in, submit your job, file transfer, and etc.) only. **No jobs should be run on the control node**, other than brief tests that last no more than a few minutes.
