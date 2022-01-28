# CSE 15L Week 4 Lab: Testing and Debugging
[Home](index.html)

This report shows the process of testing and debugging `MarkdownParse.java`.

## Error 1
Github diff for the code change that fixed the error:
![Image](week4_files/error1_gitdiff.png)

Test file that contains the failure-inducing input: [test-incorrect.md](week4_files/test-incorrect.md)

Symptom of the failure-inducing input:
![Image](week4_files/error1_symptoms.png)

The failure-inducing input caused the code to enter an infinite loop (note that the program is printing the value of `currentIndex`, which never reaches the value necessary to break out of the while loop). This is because the code searches for an open parenthese following a close bracket, and when it can't find one in the failure-inducing input, it does not increment `currentIndex`. The loop then runs forever as the code searches the same part of the input for an open parenthese which is not there.

## Error 2
