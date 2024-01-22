---
layout: default
title: Personalization
parent: Alpine overview
nav_order: 5.5
---

## Terminal personalization
There are several ways in which you can personalize your terminal which include:
* Creating shorthand commands called `aliases`
* Adding colorization to your terminal
* Making custom scripts accessible from anywhere in the system

We will discuss how to modify these parameters and make your computing environment a place that is more user friendly.

### Start up files
All the aforementioned personalization topics will be specified in start up files. Start up files are a set of hidden files within your `home` directory that get loaded in every time you login to the server or launch a terminal in JupyterLab.

To explore your hidden files navigate to your `home` directory then list all (`-a`) files:
```sh
cd ~
ls -a
```

{: .note}
The inclusion of `-a` shows hidden files, but if you were to omit the flag you would not be able to see the files.

The output should include one file called `.bashrc` and one file called `.bash_profile`. It is possible you will see additional hidden files, including `.profile`.

These are standard start up files that the operating system will look for when a session is started. Different operating systems may source different start up files by default. Oddly enough when you access Alpine using `ssh` or an OnDemand Alpine shell the operating system will look for `.bash_profile`, but when launching a terminal through JuyperLab, the operating system will look for `.profile`. Given the differences in start up procedures, we will now look into the contents of the start files to see how the are working.

TO DO: add soln see ubuntu .test

### Aliases

For sake of organization, we will create a separate hidden file that contains you aliases called, `.bash_aliases`.

To create the file we can open a new file with the name we want using a text editor (`vim` or `nano`). We will use `nano`.
```sh
nano .bash_aliases
```

While in nano we can add contents to the file. You can create aliases to to be shorthand for anything you would like. As you get more familiar with your personal need and instances of repetitive typing you may wish to modify your aliases. To start we will add an alias to easily navigate to your `scratch` space.
```sh
# .bash_aliases

#navigate to scratch
alias scratch='cd /scratch/alpine/$USER/`
```

Here are some additional general use aliases to consider adding:
```sh
#navigate to projects
alias project='cd /projects/$USER/'

#check job status
alias que='squeue -u $USER'

#alias fun
alias hi='Hi, how are you doing today?'
```

We will revisit aliases later on as well.

### PS1

The PS1 is a global variable that specifies what your bash command line prompt will look like. You can make modifications regarding the information contained in the line and/or you can tweak the colorization to spruce up your computing experience.

This personalization is done by modifying a PS1 export statement within one of your start up files. So, we will have to locate the appropriate file, but before doing that, let's see what our current PS1 is set to.
```sh
echo $PS1
```

If your using Ubuntu you might see something like this:
```sh
\[\e]0;\u@\h: \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$
```

Or something like this for git bash:
```sh
\[\033]0;$TITLEPREFIX:$PWD\007\]\n\[\033[32m\]\u@\h \[\033[35m\]$MSYSTEM \[\033[33m\]\w\[\033[36m\]`__git_ps1`\[\033[0m\]\n$
```

But for Alpine you'll likely see:
```sh

``` 

The syntax is quite overwhelming, but hopefully after this they start to make a little more sense.


## Setting up global executables
{:data-toc-text="Global executables"}