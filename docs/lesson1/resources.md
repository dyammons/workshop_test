---
layout: default
title: Resources
parent: Alpine overview
nav_order: 2.5
---

## Resources

We have access to 3 different node types on Alpine: `login`, `compile`, and `compute`.  

A node is a set of computers with the same hardware configuration, each with a designated purpose. 

### The `login` node
Landing place when you `ssh` onto Alpine from a terminal or using the OnDemand Alpine shell. These node a virtual machines that have limited processing capabilities. 

{: .important }
__Do not do any computing on these nodes__ or you will negatively impact the computing environment (your own environment as well as others).

Acceptable usage of the a `login` node is to:
* monitor jobs
* submitting jobs
* edit scripts
* launching interactive sessions

If you find yourself on a `login` node but want to do some compiling or computing you will have to launch an [`sinteractive`](#sinteractive) or [`acompile`](#acompile) session.


#### `acompile`

This can be done by simply typing `acompile` while on a login node. This will start a job on an `acompile` node which is able to handle light computing/compiling. Although this command does not require any arguments, the base usage of `acompile` will request a 60 minute job with 1 core (ntasks). Which looks like:

```sh
acompile --time 1 -ntasks 1
```

If you would like to launch a longer session or request more cores you can add arguments rather than just type `acompile`. For instance a 8 hour, 2 core session would look like:

```sh
acompile --time 8 -ntasks 2
```

If you use the `--help` flag you can view the short help menu associated with `acompile`.

```sh
acompile --help

acompile: CURC utility to access a single alpine compute node for compiling software
usage:
       -t | --time=<time-limit>        : set the job's minimum runtime (default 60 minutes/max 12 hours)
       -n | --ntasks=<number-of-cores> : set the number of cores required for the session (default 1/max 4)
       -X | --x11                      : enable x11 support for the session (requires user to login w/ -X or -Y flag)
          | --test-only                : stop job submission and print submit command
       -h | --help                     : print this message
```

#### `sinteractive`

The `acompile` command is actually a wrapper around `sinteractive` which limits the flexibility to reduce the time it takes for users to gain access to resources. The `sinteractive` command is SLURM command that allows you to start a job using the full array of SLURM directives. This is discussed in more detail later on.

### The `compile` node
Under the current Alpine configuration `compile` nodes are actually equivalent to the`amilan compute` node (introduced in next section). They have identical hardware configurations, but are reserved for compiling and light computing, so there are restrictions on the amount of resources you can request to ensure Users get quick access to `compile` nodes.

### The `compute` node
There are several types of `compute` nodes available on Alpine. We have access to all of the nodes and can use them as we see fit. With the being said, each different hardware configuration (called `partition`) has a different purpose.

Below are the partitions available on Alpine. `amilan` is the general use compute node that is amiable for completion of most hpc tasks. The `csu` nodes are also general use node that we have access to. The csu partition has slightly less resources available compared to `amilan`, but also is a viable option for most hpc tasks.

| Partition | Description                   | # of nodes    | cores/node    | RAM/core (GB) | Billing wgt/core  | Default/Max Walltime  |
| --------- | ----------------------------  | ----------    | ----------    | ------------- | ---------------   | ------------------------  |
| amilan    | AMD Milan (default)          | 347        | 32,48,64   |   3.74        | ~1.0            | 24H, 24H                 |
| csu       | Nodes contributed by CSU     | 77         | 32 or 48   |   3.74        | ~1.1            | 24H, 24H          |      
| atesting  | Testing                      | Up to 2    | 16         | 0.25             | 0.5H, 3H                 |
| acompile  | Compile                      | 1          | 4         | 1.0              | 1H, 12H                  |
| ainteractive     | Interactive Jobs      | 1  | 1         | 1.0              | 1H, 12H                  |

Special use partitions available on Alpine.
| Partition | Description   | # of nodes    | cores/node    | RAM/core (GB) | Billing wgt/core  | Default/Max Walltime  |
| --------- | ----------------------------  | ---------- | ----------    | -------------    | ---------------  | ------------------------   |
| amem      | High-memory                  | 22         | 48 or 64  |   16          | ~4.0            |  4H,  7D                 |
| ami100    | GPU-enabled (3x AMD MI100)   | 8          | 64         |   3.74        | ~6.0            | 24H, 24H                 |
| aa100     | GPU-enabled (3x NVIDIA A100) | 12         | 64        |   3.74        | ~6.0            | 24H, 24H                 |


{: .note }
The key difference between `sinteractive` and `acompile` is that `sinteractive` can request to use resources from any `partition` whereas the `acompile` command only allows for use of the `acompile` partition.

Let's take a minute to explore this information in the context of the server.

TO DO:
Add something with `sinfo` and other useful commands.

show `curc-quota` and `du` and `ls` here.

With partitions and Alpine resources introduced we will now move to look at how to request and use the resources through the resource manager `SLURM`.