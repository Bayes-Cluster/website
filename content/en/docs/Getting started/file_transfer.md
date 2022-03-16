---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "File Transfer"
linkTitle: "File Transfer"
weight: 7
---

After obtaining an account one of the things that you may wish to do is get data transferred to or from the Bayes cluster. Two of the most widely available tools for secure file transfer are [SCP (Secure Copy)](https://en.wikipedia.org/wiki/Secure_copy_protocol) and [SFTP (Secure File Transfer Protocol)](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol) which utilize the SSH protocol to implement security. While SCP is a simple, non-interactive command line tool, it is often a more suitable choice when setting up unattended file transfers using scripts. Alternatively, SFTP is an interactive tool which offers features like remote file listing, copying, deleting, directory creation, etc.

* For using the SCP:
  * Copy file (`file_name.file`) from local to the cluster: `scp /path_of_local/file_name.file user_name@hpc.uicstat.com:/path_of_remote/file_name.file`
  * Get file (`file_name.file`) from the cluster to local: `scp user_name@hpc.uicstat.com:/path_of_remote/file_name.file /path_of_local/file_name.file`
* For using the SFTP:
  * Copy file (`file_name.file`) from local to the cluster: 
  ```{r, engine='bash', eval=FALSE, indent="\t"}
  sftp user_name@hpc.uicstat.com
  put /path_of_remote/file_name.file
  ```
  * Get file (`file_name.file`) from the cluster to local: 
  ```{r, engine='bash', eval=FALSE, indent="\t"}
  sftp user_name@hpc.uicstat.com
  get /path_of_remote/file_name.file
  ```
