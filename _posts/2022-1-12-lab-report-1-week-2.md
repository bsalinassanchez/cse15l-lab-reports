---
layout: post
title: Week 2 Lab Report
tags: github gitpages
categories: lab reports
---

# Remote Access and Filesystem Tutorial

## Overview

This tutorial will teach you how to:
- Install Visual Studio Code (VSCode)
- Connect remotely to ieng6 (server)
- Perform simple filesystem commands
- Move files with `scp`
- Set an SSH Key
- Optimize remote running

*Note: this tutorial is intended for devices running macOS*
<p>&nbsp;</p>

### Step 1: Install <a href="https://code.visualstudio.com/download" target="_blank">VSCode</a>
Visual Studio Code is the recommended integrated development environment (IDE) for CSE 15L and many other CSE courses. VSCode is available for free for mac and windows devices.
<p>&nbsp;</p>

![vs code download](https://bsalinassanchez.github.io/cse15l-lab-reports/images/vscode-download.png)
>Download and install VSCode for your operating system
<p>&nbsp;</p>

![vscode open](https://bsalinassanchez.github.io/cse15l-lab-reports/images/vscode-open.png)
>When you first open VSCode you should see a window that looks like this
<p>&nbsp;</p>

![java extension](https://bsalinassanchez.github.io/cse15l-lab-reports/images/java-extension.png)
>I also recommend installing the Extension Pack For Java
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 2: Connecting Remotely to ieng6 (server)
ieng6 is a remote server you can connect to remotely using the `ssh` command. Students are given special accounts used to connect remotely to ieng6 (similar to AD accounts).

In order to connect to ieng6 you will first need to find your course-specific account.

1. Go to the <a href="https://sdacs.ucsd.edu/~icc/index.php" target="_blank">Account Lookup Tool</a>
    * Accounts will appear as `cs15lwi22xyz@ieng6.ucsd.edu`, where `xyz` is unique to each student. `wi22` should be changed as appropriate.
2. In the VSCode terminal, type `$ ssh cs15lwi22xyz@ieng6.ucsd.edu`
    * this commands allows the client (your device) to connect to the server (ieng6)
    * if a message pops up stating that the authenticity of host could not be established, just type `yes` and enter your password (your password for the course-specific account)
3. If your connection to the server is successful, your terminal should look like something this:
    * ![sshlogin](https://bsalinassanchez.github.io/cse15l-lab-reports/images/sshlogin.png)
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 3: Simple Filesystem Commands
Commands are a useful way of performing specific operations such as listing all files, changing directories, and copying over files to another location. 

![terminal example](https://bsalinassanchez.github.io/cse15l-lab-reports/images/terminal-examples.png)
>Here is an example of running several commands on the VSCode terminal (on the ieng6 server)

Here are a list of some useful commands you should know and try:

- `cd`
- `cd~`
- `ls`
- `ls -a`
- `pwd`
- `mkdir`

Try these commands from your computer (client) and ieng6 (server).

There are many more very useful commands. Look up some up and try them out!
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 4: Moving Files With `scp`
`scp` stands for secure copy. This command allows us to copy a file from the client to the server.