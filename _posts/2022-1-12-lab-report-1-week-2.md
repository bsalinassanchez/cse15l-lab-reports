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
    * Accounts will appear as `cse15lwi22xyz@ieng6.ucsd.edu`, where `xyz` is unique to each student
2. In the VSCode terminal, type `$ ssh cse15lwi22xyz@ieng6.ucsd.edu`
    * this commands allows the client (your device) to connect to the server (ieng6)
    * if a message pops up stating that the authenticity of host could not be established, just type `yes` to continue
3. 




A bullet list is created using `*`, `+`, or `-`, like:

- dog
- cat
- muffin

A numbered list is created using a number + `.`, like:

1. one
2. two
6. three
2. four
