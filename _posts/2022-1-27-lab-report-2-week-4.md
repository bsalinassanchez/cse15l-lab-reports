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

#### Link to Test File:
* [links.md](https://github.com/bsalinassanchez/markdown-parse/blob/ba30c2bc957654b5eff12946f7f033e99f9f26f5/links.md)

#### Symptom of Failure-Inducing Input: 
* ![multipleLinesSymptom](https://bsalinassanchez.github.io/cse15l-lab-reports/images/multiplelinessymptom.png)
>This image shows the symptom as a result of the program not being able to print multiple links found in a single line.

#### Description:

The bug in our program was caused by a fix to another bug! After we changed the implementation of `getLinks`, we ran into a symptom where if a line had multiple links then only the first would be printed. The failure-inducing file, `links.md`, had multiple links per line which cuased the symptom.

### Code Change 3: Empty Link ([]())

One bug we encountered was the program adding an empty string to the array whenever it encountered an empty array. For example: `[www.youtube.com, , www.twitter.com]`. Notice the empty spot

#### Screenshot of Fix:

* ![emptyLinkFix](https://bsalinassanchez.github.io/cse15l-lab-reports/images/emptylinkfix.png)
>This image shows our fix to the empty link bug. We added an if-conditional statement to check that the space between the parenthesis is not empty.

#### Link to Test File:

* [Link to test file `emptyLinkTest.md`](https://github.com/bsalinassanchez/markdown-parse/blob/main/emptyLinkTest.md)

#### Symptom of Failure-Inducing Input

* ![emptyLinkSymptom](https://bsalinassanchez.github.io/cse15l-lab-reports/images/emptylinksymptom.png)
>This images shows the symptom as a result of the program adding an empty space into the `toReturn` array if it encounters an empty link.

#### Description: 

The bug in our program was cuased by the programm adding an empty space, " ", to the `toReturn` ArrayList. The symptom as a result of this bug was an ArrayList printed that had empty spots in the middle. For example: `[www.youtube.com, , www.twitter.com]`. Notice the empty space. The file, `emptyLinkTest.md`, brought about this symptom becuase it contained an empty link: \[\]\(\)





