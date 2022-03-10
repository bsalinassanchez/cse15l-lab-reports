---
layout: post
title: Week 8 Lab Report
tags: github gitpages
categories: lab reports
---

# Week 10 Lab Report

## Overview

For this lab I compared my implementation of `markdown-parse` vs the implementation given to us during lab 9.

## How I found the tests

In order to find tests that differed in outputs between my program and the one given to me, I decided to use a bash script.

`script.sh`:
```
#!/bin/bash
for file in test-files/*.md;
do
  java MarkdownParse $file
  java my-MarkdownParse $file
  echo $file
done
```
> This script runs both implementations of markdown-parse and compares them. It prints out the output of the control file, my file, and the file name

Example output:
![example output](https://bsalinassanchez.github.io/cse15l-lab-reports/images/compare.png)

Afterwards, I just looked at the output for all files and found ones where the outputs differed.


### Test 1: `test-files/573.md`
Actual Outputs:
![test 1 actual outputs](https://bsalinassanchez.github.io/cse15l-lab-reports/images/test1actual.png)

Expected output:
![test 1 expected](https://bsalinassanchez.github.io/cse15l-lab-reports/images/test1expectedoutput.png)
> Actual expected output from commonmark.org

I believe that my implementation is correct. In the actual output, my implementation of markdown-parse resulted in no links printed which is supported by the actual output. However, the implementation given to us has one link. 


#### Test 1 Possible Fix:
![test 1 fix](https://bsalinassanchez.github.io/cse15l-lab-reports/images/test1fix.png)

The reason why the provided implementation failed this test is because it doesn't check for image files. It searches for the index of `[` but failed to check if there is an `!` right before it. Also, it fails to check for more nexted brackets. This could be fixed easily by refactoring `findCloseParen` to `findCloseBracket`.


### Test 2: `test-files/567.md`
Actual Outputs:
![test 2 actual outputs](https://bsalinassanchez.github.io/cse15l-lab-reports/images/test2actual.png)

Expected output:
![test 2 expected](https://bsalinassanchez.github.io/cse15l-lab-reports/images/test2expectedoutput.png)
> Actual expected output from commonmark.org

I believe that my implementation for markdown-parse is wrong. However, I don't think its because of a bug but rather my implementation does not account for reference links. Reference links are another feature of markdown. 

#### Test 2 Possible Fix:
A possible fix for my bug/issue would be to add a helper method to my implementation that accounts for reference links. Reference Links are not one of the possible issues we could run into that we accounted for.

Reference Links example:
![reference links](https://bsalinassanchez.github.io/cse15l-lab-reports/images/referencelinks.png)
