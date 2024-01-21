---
layout: default
title: Accessing Alpine
parent: Alpine overview
nav_order: 0.5
---

## Accessing the computer

There are a few different ways to access the supercomputer. No approach is inherently better than another, so the choice is up to the User to decide what works best for them. 

In this section we will go over various methods of interacting with the server to enable Users to better choose the approach that best fits their needs.

There are two main methods of accessing the supercomputer (1) use a [local terminal](#1-terminal) or (2) use [OnDemand](#2-ondemand). We will go over how to use a linux terminal then demonstrate how to use the OnDemand portal.  

### 1. Terminal

To access the server via a terminal you will need a linux terminal (Mac) or a third party application to launch a terminal through a __subprocess__ (Windows; typically Ubuntu, git bash, putty). Check out the installation section of resources for more details on how to get these programs running.

<br>

#### Connect via `ssh`  

Once a terminal is installed access is fairly straight forward. Simply launch a terminal then `ssh` onto the server. 

{: .note }
`ssh` stand for Secure Shell protocol and is a secure method to connect your personal laptop (or desktop) to a remote server

The `ssh` command looks like:
```sh
ssh username@login.rc.colorado.edu
```
where "username" will be whatever UC Boulder has on record. For CSU Users this is typically your NetID followed by "@colostate.edu".

For example mine would look like:
```sh
ssh dyammons\@colostate.edu@login.rc.colorado.edu
```

{: .note }
Because CSU Users have a special character in their usernames (`@`) the addition of a backslash (`\`) is required to cancel out the special effect of the `@` and allow the computer to read it as part of the username. The second `@` needs to register as a special character, hence the lack of preceding backslash in that instance.

Once the above command is run (be sure to modify it with your username), you will initiate an interaction with the supercomputer and be prompted with (see [tangent](#important-tangent) below if this is not what you see):  

`(NetID@colostate.edu@login.rc.colorado.edu) Password:`  

<br>

##### Important tangent

{: .note }
If this is your first time connecting to the server via a terminal you will be asked to verify the host key fingerprint. This is a unique string of characters that gives you the opportunity to confirm you are connecting to the computer you intend to interact with. You will instead be prompted with:

```sh
The authenticity of host 'login.rc.colorado.edu (198.59.51.7)' can't be established. 
ED25519 key fingerprint is SHA256:uNn+9REKipRZ59VZQEKlBzB8xjOCe/9yII8uBgEFOGY. 
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? y 
Please type 'yes', 'no' or the fingerprint: 
```

{: .note }
(Cont.) You can review the host keys listed on in the CURC [host key documentation](https://curc.readthedocs.io/en/latest/access/logging-in.html#ssh-host-keys) at which point you can cross reference the fingerprint listed above `SHA256:uNn+9REKipRZ59VZQEKlBzB8xjOCe/9yII8uBgEFOGY` to make sure it matches with the provided keys. If they match you can answer with `yes` if they do not match you can say `no` and it will cancel the connection. A more secure approach is to use the `fingerprint` option where you can copy the code that you think matches the from the CURC documentation and the ssh client will only proceed is they match. In this case we will type the key (obtained from to [CURC documentation](https://curc.readthedocs.io/en/latest/access/logging-in.html#ssh-host-keys) to ensure everything looks correct.

```sh
Please type 'yes', 'no' or the fingerprint: SHA256:uNn+9REKipRZ59VZQEKlBzB8xjOCe/9yII8uBgEFOGY
Warning: Permanently added 'login.rc.colorado.edu' (ED25519) to the list of known hosts. (output)
```

{: .note }
(Cont.) The statement "Warning: Permanently added 'login.rc.colorado.edu' (ED25519) to the list of known hosts" indicates the host key is saved and you will not need verify it again in the future. FYI: any ssh keys should be stored in `$HOME/.ssh/known_hosts`

<br>

You will now need to enter in your CSU login password and verify the login using 2-factor authentication. There are two options to accomplish this...

{: .note }
When entering in a password in a terminal you will typically not be able to see what you are typing, this is for security purposes.

* __Option 1:__  
(Send a push to duo that you can then accept)
```sh
(NetID@colostate.edu@login.rc.colorado.edu) Password: password,push
```

* __Option 2:__  
(Enter in your 6 digit authentication key that can be retrieved from the duo app)
```sh
(NetID@colostate.edu@login.rc.colorado.edu) Password: password,push
```
If you only enter in you password you will be prompted with:
```sh
(NetID@colostate.edu@login.rc.colorado.edu) Enter passcode:
```

<br>

Once the connection is established a welcome message will appear, with some useful information and state that you are on a login node (more on this later).

```sh
Last login: Sat Nov 11 11:42:17 2023 from 129.82.95.71
Welcome to CU-Boulder Research Computing.

  * Website http://colorado.edu/rc
  * Questions? rc-help@colorado.edu
  * Subscribe to system announcements: https://curc.statuspage.io/
  * Please type rc-help for the Acceptable Use Policy and a short help page.

You are using login node: login11
(base) login11 ~ $
```

For anyone following along, we will now close our connection to the server and switch to connecting via OnDemand. To do this all you need to do is type `exit` and you will be be prompted with:
```sh
(base) login11 ~ $ exit
logout
Connection to login.rc.colorado.edu closed.
```

While I typically prefer to use OnDemand (introduced below) to interact with Alpine, it is important to understand this more "primitive" approach (especially if OnDemand is down) and to better understand how User-supercomputer interactions work (which will come into play with data transfer).  

### 2. OnDemand

This is my favorite method of connecting to the server. It is versatile web browser based application that allows for interaction via a variety of approaches.

* OnDemand can be accessed [here](https://ondemand-rmacc.rc.colorado.edu/).

For first time login you will have to choose your institution, but if you select "remember my selection" you will not have to do this step again.  

![ondemand1](/docs/assests/images/ondemand1.png){:width="70%" height="70%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

Use your CSU credentials to login via CILogon...  

![ondemand2](/docs/assests/images/ondemand2.png){:width="30%" height="30%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

...and authenticate using Duo  

![ondemand3](/docs/assests/images/ondemand3.png){:width="30%" height="30%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

Once you have completed those steps you will now be on OnDemand and the home page should look something like this:  

![ondemand4](/docs/assests/images/ondemand4.png){:width="70%" height="70%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

Once logged in you can gain access to the supercomputer using the "Clusters" tab or launching an interactive session through the "My Interactive Sessions" tab.

#### Cluster terminal
Navigate the page to launch a terminal through Alpine shell:  

![ondemand5](/docs/assests/images/ondemand5.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

Once clicked, a terminal will open in a new window and you will be placed on a login node (same as if you had `ssh`ed in via a terminal).  

![ondemand6](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

This approach is a quick and easy way to connect to the server to make minor modifications to scripts, to submit jobs, and to check the status of your active jobs. An additional benefit of using this approach is that you do not submit a job to gain access which provides immediate access and does not impact you fair share priority level (discussed later).

We will discuss how to compute using this approach in more detail later on, but for now close the connection to the server by running `exit`, then close the browser tab.  

#### Interactive session

Navigate page to start an interactive session by selecting an interactive app. I frequently use the `JuypterLab (custom)` option, but the other options are worth exploring if you are more interested in using `VS code` or `Rstudio`. All of the options provide an integrated development environment (IDE) like experience which is highly conducive to efficiently writing and testing code.  

![ondemand7](/docs/assests/images/ondemand7.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

<br>

Once you click on the application, `JuypterLab (custom)` in this case, you can specify the parameters for the session. Here we will change the account to `csu-general` the Partition to `acompile` and QoS Name to `compile`.  

The time and number of core can be set as you see fit. If I know I am going to be working on the computer all day I often launch 12 hour sessions with anywhere from 1-8 cores. To being, lets launch a session with 1 core and 4 hours.

![ondemand8](/docs/assests/images/ondemand8.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

After clicking `Launch` you will see a new session appear in the `My Interactive Sessions` tab. The status of the session (indicated in the top right of the session card) will progress from __`queued` to `starting` to `running`. Once the session is terminated the status will change to `completed`.__  

![ondemand9](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

![ondemand10](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

![ondemand11](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

Once the status changes to `running` __a blue button labeled `Connect to Juypter` will appear__. Click this button to open a JuypterLab session in a new tab. This is the IDE-like application that we will be using to work on Alpine in most sessions associated with this workshop.  

![ondemand12](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

The starting layout should have one tab open within JuypterLab called `Launcher` this can be used to open up python environments (kernals), Juypter Notebooks, and to launch linux terminals. We will use the launcher to open a Linux terminal by clicking the `Terminal` button.  

![ondemand13](/docs/assests/images/holder.png){:width="50%" style="display:block; margin-left:auto; margin-right:auto"}

You are now connected to the supercomputer through a linux terminal similar to the above two approaches. __A key difference using the interactive session approach that you are not on login node, but rather you are on the node that was specified when you launched the session (in this case `acompile`).__ Being on an `acompile` node allows users to complete more resource intense tasks than a `login` node. Differences between nodes, discussion of available resource, and an overview of Alpine file systems will be covered in the next two pages.

