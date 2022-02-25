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

q&a :^)