---
layout: default
title: Accessing Alpine
parent: Alpine overview
nav_order: 0.5
---

### Accessing the computer

There are a few different ways to access the supercomputer. No approach is inherently better than another, so the choice is up to the User to decide what works best for them. 

In this section we will go over various methods of interacting with the server.

#### 1. Terminal

To access the server via a terminal you will need a linux terminal (Mac) or a third party application to launch a terminal through a subprocess (Windows; typically Ubuntu, git bash, putty).

Once a terminal is installed access is fairly straight forward. Simply launch a terminal then `ssh` onto the server. 

<br>

{: .note }
`ssh` stand for Secure Shell protocol and is a secure method to connect your personal laptop (or desktop) to the remote server.

<br>

The command to `ssh` onto the server looks like:
```sh
ssh username@login.rc.colorado.edu
```
where "username" will be whatever UC Boulder has on record. For CSU Users this is typical your NetID followed by "@colostate.edu".

For example mine would look like:
```sh
ssh dyammons\@colostate.edu@login.rc.colorado.edu
```

<br>

> **_NOTE:_** Because CSU Users have a special character in their usernames (`@`) the addition of a backslash (`\`) is required to cancel out the special effect of the `@` and allow the computer to read it as part of the username.

<br>

Once the above command is run you will initiate an interaction with the computer and be prompted with:
```sh
(NetID@colostate.edu@login.rc.colorado.edu) Password:
```

You will now need to enter in your CSU login password and verify the login using 2-factor authentication. There are two options to accomplish this...
```sh
#option 1:
(NetID@colostate.edu@login.rc.colorado.edu) Password: password,push
```

This will send a push to duo that you can then accept.


```sh
#option 2:
(NetID@colostate.edu@login.rc.colorado.edu) Password: password
```

If you only enter in you password you will be prompted with:
```sh
(NetID@colostate.edu@login.rc.colorado.edu) Enter passcode:
```
The computer is asking for your 6 digit authentication key that can be retrieved from the duo app

<br>

> **_NOTE:_** When entering in a password in a terminal you will typically not be able to see what you are typing, this is for security purposes.

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

While I typically prefer to use OnDemand (introduced below) to interact with Alpine, it is important to understand this more "primitive" approach (especially if OnDemand is down) and to better understand how User-computer interactions work (which will come in play with data transfer).


#### 2. OnDemand

This is personally my favorite method of connecting to the server. It is versatile web browser based application that allows for interaction via a variety of approaches.

OnDemand can be accessed at: https://ondemand-rmacc.rc.colorado.edu/

For first time login you will have to select your institution, but if you select remember my selection you will not have to do this step again.

IMG
IMG
