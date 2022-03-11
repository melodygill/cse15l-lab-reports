# CSE 15L Week 8 Lab: Large Amounts of Tests
[Home](index.html)

I found the tests with different results by using the `diff` command. I saved the results of running the two versions of `MarkdownParse` into two files (both called `results.txt`), and then ran `diff` on them to find the differences in output.


## Test 194
Test file:
```[Foo*bar\]]:my_(url) 'title (with parens) \n[Foo*bar\]]```

Output of my group's implementation:
```[]```

Output of the provided implementation:
```[url]```

Expected output according to VSCode markdown preview:
```[]```

I believe that my group's implementation is correct. The provided implementation does not check to make sure that there are no characters between the `]` and `(` of a link, which would break the link syntax. Here is the section of code that should be fixed in the provided implementation:

![Image](week10_files/code_snip1.png)


For each test:

    Describe which implementation is correct, or if you think neither is correct, by showing both actual outputs and indicating what the expected output is.

    For the implementation that’s not correct (or choose one if both are incorrect), describe the _bug (the problem in the code). You don’t have to provide a fix, but you should be specific about what is wrong with the program, and show the code that should be fixed.