---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Quick Start"
linkTitle: "Quick Start"
weight: 2
---
## Quick Start

After reading the introduction of USBC, you may have interest in running your first program on it. Steps are as follows: Apply for an account. Log in the Cluster (set up <a href="https://itsc.uic.edu.cn/">campus VPN service</a> connection if you are off-campus). Upload your program source code. Prepare a SLURM script to run your program. Submit your program running task to the Cluster.

## Request for an Account

Usually, only authorized user (faculty and students in Statistics of BNU-HKBU UIC) are allowed to log in the Bayes cluster. You have to request an account before using the Bayes cluster, please fill out the <a href="https://shimo.im/forms/JcWGhwvdGVvHtpRd/fill?channel=UICSTAT"> Application Form </a> to request an account.

## Runtime 

In order to optimize computing resources on the Bayes cluster, the defualt storage for each account is limited to 50GB. The submitted computing tasks will also be queued to be processed by specified compute nodes, and the maximum running time for each task is limited as follows,

| Node Name          | Maximum runtime | 
|--------------------|-----------------|
| Compute2030005000 | 24 Hours  |
| Compute2030005001 | 7 Days  | 
| Compute2030005002 | 24 Hours  |
| Compute2030005003 | 7 Days  |

## Access to the System

The Bayes cluster can only be accessed from UIC campus by an authorized user. If you are off-campus, you need to use <a href="https://itsc.uic.edu.cn/en/info/1030/1119.htm">UIC-VPN Service</a> to connect the cluster.

{{% alert title="" color="warning" %}}
The following instructions, we assume you:

1. You have an USBC account (username: `user_name`, password: `passwd`)
2. Are connecting:
    1. (if on-campus) from the campus wired/wireless network
    2. (if off-campus) with UIC-VPN Service 
{{% /alert %}}

### SSH

In order to connect to the university computing clusters, you will need an SSH (secure shell) client, a piece of software for establishing secure connections to remote machines. On **macOS and Linux**, the default Termina application has such a client built-in. No download is necessary. On **Windows** machines, there is also an SSH-enable client (Windows CMD and Windows Powershell). You can also try [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and [MobaXterm](http://mobaxterm.mobatek.net/).

1. Access a command-line tool on your machine:
    * **Linux** open a Terminal window
    * **macOS** open a Terminal window
    * **Windows** open a CMD/Powershell window
2. SSH into the cluster: 
    * type: `ssh user_name@hpc.uicstat.com`
    * If you are first time connecting to the cluster, you will see a comment about the fingerprint along with the question: `Are you sure you want to continue connecting (yes/no/[fingerprint])?`, please answer **yes**
    * Enter your password [^1] 
3. End the SSH connect to the cluster:
    * To close the SSH connection, simply type `exit`

[^1]: There are no asterisks or dots to indicate how many characters you've typed, so if you think you've made a typo, hit Backspace many times and enter the password from scratch.

## Before using it

Every user have a default folder: `~/user_name/`. Please use the `~/user_name/` folder to store your data, codes and etc.. As the default home path has very limited storage (100MB) and the `~/user_name/` has 50GB. If you need external storage, please connect the maintainer.

## File Transfer

After obtaining an account one of the things that you may wish to do is get data transferred to or from the Bayes cluster. Two of the most widely available tools for secure file transfer are [SCP (Secure Copy)](https://en.wikipedia.org/wiki/Secure_copy_protocol) and [SFTP (Secure File Transfer Protocol)](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol) which utilize the SSH protocol to implement security. While SCP is a simple, non-interactive command line tool, it is often a more suitable choice when setting up unattended file transfers using scripts. Alternatively, SFTP is an interactive tool which offers features like remote file listing, copying, deleting, directory creation, etc.

For using the SCP:

* Copy file (`name.file`) from local to the cluster: `scp /path_of_local/name.file user_name@hpc.uicstat.com:/path_of_remote/name.file`
* Get file (`name.file`) from the cluster to local: `scp user_name@hpc.uicstat.com:/path_of_remote/name.file /path_of_local/name.file`

For using the SFTP:

* Copy file (`fname.file`) from local to the cluster: 
  ```bash
  sftp user_name@hpc.uicstat.com
  put /path_of_remote/name.file
  ```
* Get file (`name.file`) from the cluster to local: 
  ```bash
  sftp user_name@hpc.uicstat.com
  get /path_of_remote/name.file
  ```
