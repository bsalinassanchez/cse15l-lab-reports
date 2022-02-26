---
layout: post
title: Week 8 Lab Report
tags: github gitpages
categories: lab reports
---

# Week 8 Lab Report

## Overview

For this lab I tested three provided md snippets on both my implementation of `MarkdownParse.java` and another person's implementation of `MarkdownParse.java`.


## My Implementation

My repository: <a href="https://github.com/bsalinassanchez/markdown-parse" target="_blank">markdown-parse</a>

### Snippet 1

Expected Outcome: ``["`google.com", "google.com", "ucsd.edu"]``

JUnit Test:
![snippet one test](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetOneTest.png)

JUnit Output:
![snippet one output](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetOneOutput.png)


### Snippet 2

Expected Outcome: ``["a.com", "a.com(()), "example.com"]``

JUnit Test:
![snippet two test](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetTwoTest.png)

JUnit Output:
![snippet two output](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetTwoOutput.png)

### Snippet 3

Expected Outcome: ``["https://ucsd-cse15l-w22.github.io/"]``

JUnit Test:
![snippet three test](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetThreeTest.png)

JUnit Output:
![snippet three output](https://bsalinassanchez.github.io/cse15l-lab-reports/images/snippetThreeOutput.png)


## Other Team Implementation

Their repository: <a href="https://github.com/Stocktocon/markdown-parse" target="_blank">markdown-parse-other-team</a>

### Snippet 1

Expected Outcome: ``["`google.com", "google.com", "ucsd.edu"]``

JUnit Test:
![snippet one test other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetOneTest.png)

JUnit Output:
![snippet one output other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetOneOutput.png)


### Snippet 2

Expected Outcome: ``["a.com", "a.com(()), "example.com"]``

JUnit Test:
![snippet two test other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetTwoTest.png)

JUnit Output:
![snippet two output other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetTwoOutput.png)

### Snippet 3

Expected Outcome: ``["https://ucsd-cse15l-w22.github.io/"]``

JUnit Test:
![snippet three test other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetThreeTest.png)

JUnit Output:
![snippet three output other](https://bsalinassanchez.github.io/cse15l-lab-reports/images/othersnippetThreeOutput.png)




## Questions

1. For snippet 1, I think there is a bit over 10 lines of code that could possibly fix the issue. The first thing I would do is look for a single backtick. If the index is -1 then don't do anything. Else, if the index is greater than -1, then look for a second backtick. If the second backtick is found then skip any text between the index of both backticks. Do this by checking that currentIndex is not in between the indexes of the two backticks. The implementation would look something like this:
```
int firstBacktick = markdown.indexOf("`");
int secondBacktick = -1;
Boolean between = false;
if(firstBacktick != -1) {
    secondBacktick = markdown.indexOf("`", firstBacktick);
}

if(firstBacktick != -1 && secondBacktick != -1) {
    if(currentIndex >= firstBacktick && currentIndex <= secondBacktick) {
        between = true;
    }
}

//some different checks

if(between == true) {
    currentIndex = closeParen + 1;
}
```

2. I don't think there is a solution that is less-than 10 lines of codes that would fix the problem with nested parenthesis. In lecture we went over a similar solution and it was longer than 10 lines. I think this solution would take longer than 10 lines of code becuase we would need to implement a stack and several loops and if-statements. We would need to push/pop to the stack, check that each open parenthesis has a closing parenthesis, and increment the currentIndex.

3. I think there is a less-than 10 line solution for the third snippet problem. The solution would be somewhat similar to the solution for the backtick problem. First you would look for the index of a new line escape character(`\n`). Then you would need to check if the index of the new-line character is between the open/close parenthesis or the open/close brackets. If so, update the current index to be after the closing parenthesis. If not, then don't do anything. 







