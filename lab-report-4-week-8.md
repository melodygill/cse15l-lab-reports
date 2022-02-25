# CSE 15L Week 8 Lab: More Testing
[Home](index.html)

This report shows the process of testing and debugging `MarkdownParse.java`.

Link to my `markdown-parse` repository: [CSE15L-Panther](https://github.com/melodygill/CSE15L-Panther)

Link to the repository I reviewed: [markdown-parse](https://github.com/ShashankVenkatramani/markdown-parse/)

## Snippet 1
The test in `MarkdownParseTest.java` that corresponds to this snippet, which is copied into `snippet1.md`:
```
@Test
    public void snippet1() throws IOException {
        Path fileName = Path.of("./snippet1.md");
	    String contents = Files.readString(fileName);
        List<String> expected = List.of("`google.com", "google.com", "ucsd.edu");
        assertEquals(expected, MarkdownParse.getLinks(contents));
    }
```


My implementation: test failed with the following output.
```
1) snippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[`google.com, google.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet1(MarkdownParseTest.java:100)
```

The implementation I reviewed: test failed with the following output.
```
3) snippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[`google.com, google.com, ucsd.edu]> but was:<[url.com, `google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet1(MarkdownParseTest.java:83)
```

## Snippet 2
The test in `MarkdownParseTest.java` that corresponds to this snippet, which is copied into `snippet2.md`:
```
@Test
    public void snippet2() throws IOException {
        Path fileName = Path.of("./snippet2.md");
	    String contents = Files.readString(fileName);
        List<String> expected = List.of("a.com", "a.com(())", "example.com");
        assertEquals(expected, MarkdownParse.getLinks(contents));
    }
```
My implementation: test failed with the following output.
```
2) snippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, a.com((]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet2(MarkdownParseTest.java:108)
```
The implementation I reviewed: test failed with the following output.
```
4) snippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com(()), example.com]> but was:<[a.com, b.com, a.com, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet2(MarkdownParseTest.java:91)
```

## Snippet 3
The test in `MarkdownParseTest.java` that corresponds to this snippet, which is copied into `snippet3.md`:
```
@Test
    public void snippet3() throws IOException {
        Path fileName = Path.of("./snippet3.md");
	    String contents = Files.readString(fileName);
        List<String> expected = List.of("https://www.twitter.com", "https://ucsd-cse15l-w22.github.io/", "https://cse.ucsd.edu/");
        assertEquals(expected, MarkdownParse.getLinks(contents));
    }
```
My implementation: test failed with the following output.
```
3) snippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet3(MarkdownParseTest.java:116)
```
The implementation I reviewed: test failed with the following output.
```
5) snippet3(MarkdownParseTest)
]>https://cse.ucsd.edu/22.github.io/[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]> but was:<[https://www.twitter.com
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.snippet3(MarkdownParseTest.java:99)
```

## Questions
Answer the following questions with 2-3 sentences each:

1. Do you think there is a small (<10 lines) code change that will make your program work for snippet 1 and all related cases that use inline code with backticks? If yes, describe the code change. If not, describe why it would be a more involved change.

Yes, I think I could fix the backticks problem easily. 2 out of the 3 links in snippet 1 were processed correctly by my program. I would just rearrange some of the lines of code so that it ignores close brackets within backtick segments (which was the problem that caused failure with the 3rd link).


2. Do you think there is a small (<10 lines) code change that will make your program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets? If yes, describe the code change. If not, describe why it would be a more involved change.

I think it would be a more involved change, like changing the structure of my program, to make my program work for snippet 2. I would have to add code to ignore escape characters, and also change the way that the program parses parentheses and brackets for it to process nested parentheses properly. Most likely I would use a stack to match parentheses and brackets before I decided if they were valid parts of the link syntax, which I think would take more than 10 lines.

    
3. Do you think there is a small (<10 lines) code change that will make your program work for snippet 3 and all related cases that have newlines in brackets and parentheses? If yes, describe the code change. If not, describe why it would be a more involved change.

I believe that markdown displays 2 out of the 3 links in snippet 3 as links because they start with `https://`, not because of the `[text](link)` format. If I were to code it so that my program displays `https://` links, it would probably take less than 10 lines of code. I don't know why my program is failing with the other link that involves newlines in the parentheses portion of the markdown link syntax, but I'm guessing it would take less than 10 lines of code to make my program ignore whitespace characters surrounding links.