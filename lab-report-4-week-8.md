# CSE 15L Week 8 Lab: More Testing
[Home](index.html)

This report shows the process of testing and debugging `MarkdownParse.java`.

Link to my `markdown-parse` repository: 

Link to the repository I reviewed:

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

For your implementation, the corresponding output when running the tests; if it passed, say so. If it didn’t pass, show the specific part of the JUnit output that shows the test failure.
For the implementation you reviewed, the corresponding output when running the tests; if it passed, say so. If it didn’t pass, show the specific part of the JUnit output that shows the test failure.

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

## Snippet 3
The test in `MarkdownParseTest.java` that corresponds to this snippet, which is copied into `snippet3.md`:
```
@Test
    public void snippet3() throws IOException {
        Path fileName = Path.of("./snippet3.md");
	    String contents = Files.readString(fileName);
        List<String> expected = List.of("https://www.twitter.com", "https://ucsd-cse15l-w22.github.io/", "(https://cse.ucsd.edu/");
        assertEquals(expected, MarkdownParse.getLinks(contents));
    }
```

q&a :^)