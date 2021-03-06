---
layout: post
title: Week 2 Lab Report
tags: github gitpages
categories: lab reports
---

# Remote Access and Filesystem Tutorial

## Overview

This tutorial will teach you how to:
- [Install Visual Studio Code (VSCode)](#step-1-install-vscode)
- [Connect remotely to ieng6 (server)](#step-2-connecting-remotely-to-ieng6-server)
- [Perform simple filesystem commands](#step-3-simple-filesystem-commands)
- [Move files with `scp`](#step-4-moving-files-with-scp)
- [Set an SSH Key](#step-5-setting-an-ssh-key)
- [Optimize remote running](#step-6-optimize-remote-running)


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
3. If your connection to the server is successful, your terminal should look something like this:
![sshlogin](https://bsalinassanchez.github.io/cse15l-lab-reports/images/sshlogin.png)

4. You can disconnect from the server by typing `exit` or `logout` in the terminal

*Note: you will need to enter your password everytime you `ssh` to the server or `scp` to copy a file over to the server. This may not seem like such an inconvinience, after all it only adds a few seconds. Now imagine working on a PA where you have to do this hundreds of times.*
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 3: Simple Filesystem Commands
Commands are a useful way of performing specific operations such as listing all files, changing directories, and copying over files to another location. 

![terminal example](https://bsalinassanchez.github.io/cse15l-lab-reports/images/terminal-examples.png)
>Here is an example of running several commands on the VSCode terminal (on the ieng6 server)

Here are a list of some useful commands you should know and try, can you figure out what they do?:

- `cd`
- `cd~`
- `ls`
- `ls -a`
- `pwd`
- `mkdir`

Try these commands from your computer (client) and/or the ieng6 (server).

There are dozens more useful commands. The best way to learn most of them is through experience. Look up some up and try them out for yourself!
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 4: Moving Files With `scp`
`scp` stands for secure copy. This command allows us to copy a file from the client (your computer) to the server (ieng6). This command can only be run from the client.
<p>&nbsp;</p>

1. First create a java file on your computer. You can use this file as an example, `WhereAmI.java`:
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```
2. Now, try running `javac` and `java` on ***your*** computer. Make note of the output.
3. Next, run the command `$ scp WhereAmI.java cs15lwi22xyz@ieng6.ucsd.edu:~/`
4. Similar to connecting to the server with `ssh`, you will be asked for a password.
5. Now, `ssh` into ieng6 and use `ls` to list the files. If you successfully copied the file from the client to the server, `ls` should print this out to the terminal:

![successful scp](https://bsalinassanchez.github.io/cse15l-lab-reports/images/scp.png)
>Notice how after running `ls` we can see the file we copied over, `WhereAmI.java`


6. Now, try running `javac` and `java` on the server. What is the output? How is it different than running `java` on your computer?

![server](https://bsalinassanchez.github.io/cse15l-lab-reports/images/server.png)

![client](https://bsalinassanchez.github.io/cse15l-lab-reports/images/client.png)
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 5: Setting an SSH Key

Remember having to enter your password everytime you `ssh` or `scp`? How long does that take. Only a few seconds right? Now imagine working on a PA the night before its due. Everytime you want to run a file on the ieng6 server or copy a file over to the server you need to enter your password. Its reasonable that you will need to enter your password dozens or even hundreds of times. By the time you are finished, this will have actually amounted to several minutes!

How can we decrease the amount of time we take having to enter our password? 

SSH Keys allow the client to establish a connection to the server without having to enter your password everytime! This is through a public and private key, stored in the server and client respectively.

1. In order to generate an ssh key run `$ ssh-keygen` on your computer (the client)
2. Next, choose a file location to save the key. It will give you a recommendation in parenthesis.
3. Afterwords, enter a passphrase/password. You will be asked to enter it a second time.
4. The public/private key pair will be created and located in the indicated location.
5. The entire interaction should look something like this:

![keygen](https://bsalinassanchez.github.io/cse15l-lab-reports/images/keygen.png)
>I already had a ssh key generated which is why it prompted me to "Overwrite". You won't need to overwrite.

6. Now, `ssh` into the server. Once connected to the server run `$ mkdir .ssh` in order to create a "hidden" folder. Run `ls -a` in order to view the hidden folder.
7. `logout` or `exit` from the server.
8. finally, run `$ scp /Users/username/.ssh/id_rsa.pub cs15lwi22xyz@ieng6.ucsd.edu:~/.ssh/authorized_keys` on the client (your computer). This will copy your public key to the `.ssh` file in the server.
9. If everything was succesfull you should be able to `ssh` into the server without entering your password. You can verify that your public key was succesfully copied over to the server by running `$ cd .ssh` and `ls` on the server:

![authorized-key](https://bsalinassanchez.github.io/cse15l-lab-reports/images/authorized-key.png)
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>

### Step 6: Optimize Remote Running

Now that you have finished setting up VSCode and SSH connection, how can we continue to optimize running remotely on a server?

As it turns out, there are many useful tricks you can do in the command line in order to optimize remote running. 

For example, you can `ssh`, `ls`, and `logout` in a single command!

![optimize](https://bsalinassanchez.github.io/cse15l-lab-reports/images/optimize.png)

You can also execute multiple commands by seperating them with a semicolon (`;`) in a single line

`$ ssh cs15lwi22xyz@ieng6.ucsd.edu "ls"; java WhereAmI`

Is there a long command you repeat often in a short time? Tired of typing it out or having to copy-paste? You can simply press the up arrow-key on your keyboard to switch through recently used commands!

There are many more useful command line running tricks, look some up!

#### Impact of Remote Running

How many keystrokes would it take to copy a file to a remote server, ssh into remote server, and run a file on the ieng6 server without any optimization?

Let's try copying and running `example.java` on the remote server:
```
public class example {
	public static void main(String[] args) {
		System.out.println("How many keystrokes did it take to run this file?");
	}
}
```


Lets Count!

Running Without Optimization:
1. `scp example.java cs15lwi22xyz@ieng6.ucsd.edu:~/` + `enter` + `password` - 48 keystrokes + password length
2. `ssh cs15lwi22xyz@ieng6.ucsd.edu` + `enter` + `password` - 32 keystrokes + password length
2. `javac example.java` + `enter` + `java example` + `enter` - 32 keystrokes
3. Total of 112 keystrokes + (3 * password length)!

Now let's try running with optimization

*It is important to note that we are assuming the user has ran the code before without optimization and that the commands are stored in the terminal and accessible through the up-arrow key. We also assume user has setup ssh key requiring no password to `scp` or `ssh`. We also assume the user has used the command `ssh cs15lwi22xyz@ieng6.ucsd.edu "javac example.java; java example;"`*

Running With Optimization: updating `example.java` and running it on server

Make local change to `example.java`: add print statements
```
System.out.println(System.getProperty("os.name"));
System.out.println(System.getProperty("user.name"));
System.out.println(System.getProperty("user.home"));
System.out.println(System.getProperty("user.dir"));
```

1. `up-arrow key`(scp command) + `enter` - 2 keystrokes
2. `up-arrow key`(ssh,javac,java) + `enter` - 2 keystrokes
3. Total of 4 keystrokes + (x * up-arrow key) if arrow key was pressed more than once.
4. Wow! There is a HUGE difference between running without optimization and running with optimization. This can save you a lot of time! There is no need to type your password everytime you use `scp` or `ssh`. There is also no need to run many different commands. Only two are needed!

* ![optimizedRunning](https://bsalinassanchez.github.io/cse15l-lab-reports/images/optimizedrunning.png)
>this image demonstrates copying an updated file to the remote server, ssh into a remote server, and compiling and running a file in a remote server all in only 2 commands!




