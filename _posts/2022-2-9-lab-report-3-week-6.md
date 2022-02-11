---
layout: post
title: Week 6 Lab Report
tags: github gitpages
categories: lab reports
---

# Week 4 Lab Report

## Overview

For Lab Report 6 I decided to choose "Group Choice 1 - Streamline `ssh` Configuration". Essentially, this means optimizing the process of connecting to a remote server, such as `ieng6`.

### Image 1: My `config` File (located on my laptop)

![myconfig](https://bsalinassanchez.github.io/cse15l-lab-reports/images/myconfig.png)
> This file shows the config file on my laptop. I used the command `open ~/.ssh/config` in order to open the config file on my laptop. The second chunk of words, starting from "Host ieng6", is what allows the client to establish a connection to the designated server.

What the lines mean:
1. "Host ieng6"
    - This line establishes the alias the user wants. For example: `ieng6`, `server`, `basement`, etc.
2. "HostName ieng6.ucsd.edu"
    - This line identifies the "host" of the server. In this case the ieng6 computers.
3. "User cs15lwi22ams"
    - This line identifies my specific account.
4. "ForwardAgent yes"
    - This line allows the server to use the clients ssh agent.


### Image 2: Using the alias

![alias](https://bsalinassanchez.github.io/cse15l-lab-reports/images/alias.png)
> This image demonstrates using the new ssh host alias. Instead of having to type out `cs15lwi22xyz@ieng6.ucsd.edu`, the user can simply replace it with `ieng6`. This means less typing which can save you lots of time if you are sshing and logging out of a server frequently. 

### Image 3: Using `scp` with alias

![scpalias](https://bsalinassanchez.github.io/cse15l-lab-reports/images/scpalias.png)
> This image demonstrates me using the `scp` command to copy `example.txt` over to my home directory on ieng6. Afterwards, I log into the ieng6 server and use `ls` in order to confirm that the file was copied over. 