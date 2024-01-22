---
layout: default
title: File systems
parent: Alpine overview
nav_order: 1.5
---

## File systems

The file system consists of four major systems: `/home`, `/scratch`, `/projects`, and `/pl`. Each file system has a designated purpose and we will be exploring each space.

The file system is best described directly from Alpine [documentation](https://curc.readthedocs.io/en/latest/compute/filesystems.html), but key excerpts obtained from the source are provided below.

> ### The Home Filesystem
Every user is allocated 2 GB of space on the `/home` filesystem in a subdirectory corresponding to their user name (e.g., `/home/janedoe`). Home directories are backed up frequently and are intended for the use of their owner only; sharing the contents of home directories with other users is strongly discouraged. Your `/home` directory is a good place to store source code, small compiled programs, and job scripts.

>### The Projects Filesystem
Each user has access to a 250 GB of space in their subdirectory of `/projects` (e.g., `/projects/janedoe`). As with the `/home` system, these directories are visible from all Research Computing nodes and are regularly backed up. The projects directory is intended to store software builds and smaller data sets.

>### Scratch Filesystems
Alpine users are provided a subdirectory on `/scratch/alpine`, the high-performance parallel scratch filesystem meant for I/O from jobs running on that system (e.g., `/scratch/alpine/janedoe`). By default, each user is limited to a quota of 10 TB worth of storage space and 20M files and directories.  
Scratch space should be used for all compute jobs run on Alpine. These high-performance scratch directories are **not backed up**, and are not appropriate for long-term storage. Data may be purged at any time subject to overall system needs. Files are automatically removed 90 days after their initial creation.

While the documentation provides an explanation of what to expect in each location within Alpine file systems, I will now go over additional comments and usage based on my personal experience.

### home
The `home` directory is your landing point whenever you connect to the server. The directory contains start up files which contain personal preference specifications for your terminal among other applications that you use on the server. 

If you still have a new terminal session open, we will now explore the directory.  

First, to the path to your `home` directory is `/home/$USER`. This can be confirmed by typing:
```sh
echo $HOME
``` 

{: .note }
`$USER` is a global variable that contains your Alpine username

{: .note }
`echo` is a base linux command that prints the contents of a variable

Second, if you are in a newly launched terminal, you can type the following command to print your current location:
```sh
#use print working directory (pwd) base command
pwd
```

OR

```sh
#use echo to print the global variable PWD which contains current directory path
echo $PWD
```

You should now see that the output of `pwd` or `echo $PWD` is equivalent to `echo $HOME`. This confirms we are indeed in our `home` directory.

If you ever get lost in the file system you can return to `home` by running `cd` with no arguments or with `~` as the argument:
```sh
#go home
cd
cd ~
```

{: .important }
The concept of a `home` directory is conserved across all linux operating systems. Because of this, many programs will automatically be designed to store information (cache data, etc.) in `home`. On Alpine the storage space in `home` is very limited (only 2 GB), so be aware that you can accidentally fill up your `home` which will inadvertently cause downstream complications.

{: .important }
Your `home` directory is backed up using `ZFS` snapshots, so if you ever make a mistake you can roll back the directory to an earlier version from a few days prior (I know this because I have had to do it... more on this later in file backups section).

### scratch
We will now shift to explore usage of your `scratch` space. This file system is designed to store raw data and pipeline outputs that you will be processing/generating as you work on the supercomputer. There is a generous amount of space for storing data (10 TB), but the data is purged periodically and is not backed up using `.zfs` snapshots, so this is not a long term storage solution and any data on `scratch` should be adequately backed up elsewhere.

{: .warning }
Files in `scratch` will be purged every 90 days. Make sure your data on `scratch` is adequately backed up elsewhere.

To navigate to `scratch` you can use `cd` (base linux command change directory) followed by the path to your `scratch` allocation.
```sh
cd /scratch/alpine/$USER
```

{: .note }
By using the `$USER` variable in the above command the `cd` call will work universally for anyone using the command on Alpine.


Once in `scratch` you can print the directory contents with `ls` and if you have worked on the server before you may see files, but if this is your first time you will likely see no output from the `ls` command.

There is not much was can do in `scratch` at the moment, so here a couple of notes:

{: .note }
When `scratch` is purged the directories in your `scratch` space are retained, but any files are deleted. 

{: .note }
Although set up of your `scratch` space is personal preference. I recommend setting it up such that the files are structured by project and each directory is labeled with a meaningful name. 

### projects
The `projects` space is a long term storage location that is accessible from compute nodes and allows Users to store up to 250 GB of data.

You can navigate to your projects space with:
```sh
cd /projects/$USER
```

You can use this directory however you see fit, but I recommend having the following core directories: `software`, `references`, `d`. I would not recommend storing raw data in `projects` due to the relatively limited storage space.

If you would like to do this, you can run the following code:
```sh
mkdir /projects/$USER/software /projects/$USER/references
```

You can check that the directories were made by running `ls`.

### pl
The `pl` (PetaLibrary) is a pay-for storage solution that is offered on Alpine. Currently, CSU Users are able to request an `active pl` allocation, but the `archive pl` storage solution is not offered to CSU Users.

`active pl` allocation are long-term storage options for data that you intend to actively use (read/write) from compute nodes. Each allocation will be structured differently and you will need to talk with your PI to determine if your lab has an allocation and how they use their `pl` allocation.

