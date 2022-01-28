---
layout: post
title: Week 4 Lab Report
tags: github gitpages
categories: lab reports
---

# Week 4 Lab Report

## Overview

This lab report contains 3 of the many bugs we encountered while working with the `MarkdownParse.java` file from Lab 3 and Lab 4. Our group worked together to fix the bugs and commit/push our solutions to github.

### Code Change 1: No Command-Line Argument

One issue we encountered was the program crashing from a `ArrayIndexOutOfBoundsException`. This error is caused when a user does not include a file name when running the program(ex: `java MarkdownParse test-file.md`). To fix this bug we included a conditional statement that checks for an argument. If no argument is found then the program terminates.

#### Screenshot of Fix:
* ![noArgumentFixImage](https://bsalinassanchez.github.io/cse15l-lab-reports/images/noargumentfix.png)
>This image shows our group fixing the `ArrayIndexOutOfBoundsException` error by adding an if-condition statement that checks for an argument

#### Link to Test File:
* *There is no test file for a failure-inducing input for this specific bug, since the bug arrises when a user DOES NOT pass in a test file argument when running the program.*

#### Symptom of Failure-Inducing Input:
* ![noArgumentSymptomImage](https://bsalinassanchez.github.io/cse15l-lab-reports/images/noargumenterror.png)
>This image shows the symptom as a result of the "no argument" bug

#### Description:

The bug in our program was caused by trying to access `args[0]`. Since NO test file was passed in as a command-line argument, the program could not access `args[0]` and the output resulted in the symptom: `ArrayIndexOutOfBoundsException`.


### Code Change 2: Multiple Links in the Same Line
Another issue we ran into was the program not printing all the links found in a single line. This problem was non-existent in the original implementation of the program and was introduced because of our new implementation.

#### Screenshot of Fix:

* ![multipleLinesFix](https://bsalinassanchez.github.io/cse15l-lab-reports/images/multiplelinesfix.png)
>This image shows fixing the multiple links per line symptom by checking to see if the line after a specific index contains a link

#### Symptom of Failure-Inducing Input: 
* ![multipleLinesSymptom](https://bsalinassanchez.github.io/cse15l-lab-reports/images/multiplelinessymptom.png)
>This image shows the symptom as a result of the program not being able to print multiple links found in a single line.

#### Link to Test File:
*[testFileUsedForMultipleLinesError](https://bsalinassanchez.github.io/markdown-parse/links.md)

#### Description:


