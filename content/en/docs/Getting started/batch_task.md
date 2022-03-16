---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Batch Tasks"
linkTitle: "Batch Tasks"
weight: 5
---

To submit a batch task on the cluster, it requires a SLURM script to clarify the requested resources and the programs to run.

### Check Available Resource

Before the submission, please check the compute nodes’ status to insure itthey hashave enough resource to run the upcoming jobs.

```bash
user_name@Control:~$ sinfo
PARTITION      AVAIL  TIMELIMIT  NODES  STATE NODELIST
CPU-Compute-1*    up 1-00:00:00      1   idle Compute2030005000
CPU-Compute-2     up 7-00:00:00      1   idle Compute2030005001
GPU-Compute-1     up 7-00:00:00      1    mix Compute2030005002
GPU-Compute-2     up   infinite      1  alloc Compute2030005003
```

As the example shown, sinfo can roughly shows the information of all the partitions.

* If the STATE column is “idle”, it means the node is in an idle state
* If the STATE column is “alloc”, it means the node is full
* If the STATE column is “mix”, it means that the node is occupied by someone, but it still has remaining resources

You can also use the pestat to chekc hte detail of each node:

```bash
user_name@Control:~$ pestat
Hostname       Partition     Node Num_CPU  CPUload  Memsize  Freemem  Joblist
                            State Use/Tot              (MB)     (MB)  JobId User ...
Compute2030005000  CPU-Compute-1*     idle   0  40    1.11*   128000    35643
Compute2030005001   CPU-Compute-2     idle   0  40    0.11    128000    34578
Compute2030005002   GPU-Compute-1      mix   2  40   16.30    128000    37085	 1422 user_2
Compute2030005003   GPU-Compute-2    alloc  40  40   35.50*   128000    29748  1454 user_1
```
### Submit a Batch Task

After you have generate a proper SLURM script, you can eaily submit your job by using `sbatch`:

```bash
user_name@Control:~$ sbatch run.slurm
Summited batch job 4100
```

### Check Task's Status

After the submission, you can use `squeue` to check the status of your task:

```bash
user_name@Control:~$ squeue
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
              1454 GPU-Compu 		 test   user_1  R 22-17:04:56      1 Compute2030005003
              1422 GPU-Compu 		debug   user_2  R       01:30      1 Compute2030005002
```

* `squeue -l`: can show detailed information
* `squeue -u user_name`: only show user_name's task
* `squeue -t state`: only shows the task with “state” status

To cancel task:

* `scancel jobid`: cancel the task with JobID = jobid
* `scancel -u user_name`: cancel all the tasks belong to user_name
* `scancel -s state`: Delete all the tasks with “state” status

{{% alert title="Notice" color="warning" %}}
User can only cancel its only task, not others!
{{% /alert %}}