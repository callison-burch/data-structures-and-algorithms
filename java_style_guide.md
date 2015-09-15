---
layout: default
title: CIS 121 Java Coding Style
active_tab: java-style-guide
---

Style Guidelines
================
{:.no_toc}

* Will be replaced with the ToC
{:toc}

You only write code once, but read it many times. Having clean, organized,
legible, intuitive, and understandable code is important for those who read it:
whether it be for debugging purposes (yourself, a peer, or a TA), for style
grades (a TA), or even for judging your coding abilities and organization (a
potential employer/co-worker). Yes, your code may run and solve a given problem
whether it is organized or not. But, writing your code in a clean and organized
way *from the start* will benefit you in the long run.


The Basics
----------

### Code must compile

Any code you submit *must* compile. If it does not compile, we won't grade the
assignment and you will lose all the points for the assignment.

### 80 column limit

No line of code should have more than 80 columns. Using more than 80 columns
causes your code to wrap around to the next line, which adversely impacts
readability. You can set a visible margin in Eclipse by going to Preferences \>
Editors \> Text Editors \> Show print margin.

### Proper indentation

Fortunately, Eclipse makes this really easy for you! Simply press `Ctrl-Shift-F`
(`Cmd-Shift-F` for Macs) to auto-format tabs and whitespaces.

### Don't repeat yourself (DRY)

If you find yourself writing the same or similar code two or more times,
consider whether it could be put in a separate method.

### Always use braces for if-statements and loops

Although curly braces aren't required for one statement, it's good style to
always include them. Doing so can help you avoid easily prevented bugs.

Commenting
----------

### Comments go above the code they reference

Consider the following:

    // BAD:
    double magnitude = Math.pow(x, 2) * Math.pow(y, 2);
    // Computes the magnitude of a vector

    // GOOD:
    // Computes the magnitude of a vector
    double magnitude = Math.pow(x, 2) * Math.pow(y, 2);


The latter is the better style.

### Avoid useless comments

Your code should be readable in many cases without comments. This is called
self-documenting code. Comments that merely repeat the code they reference or
that state the obvious are a travesty to programmers. Comments should state the
invariants, the non-obvious, or any references that have more information about
the code.

### Avoid over-commenting

Incredibly long comments are not very useful. Long comments should only appear
at the top of a file---here you should explain the overall design
of the code and reference any sources that have more information about the
algorithms or data structures. Rarely should you need to comment within a
function---variable naming should be enough.

### Comment multi-line blocks properly

When comments are printed on paper, the reader lacks the advantage of color
highlighting performed by an editor such as Emacs. This makes it important for
you to distinguish comments from code. When a comment extends beyond one line,
it should be preceded with a \* similar to the following:

    /*
    * This is one of those rare but long comments that need
    * to span multiple lines because the code is unusually
    * complex and requires extra explanation.
    */


### Write Javadoc

Ever wonder how the thousands of Java API web pages
are generated? Using javadoc, an Oracle tool that generates API
documentation in HTML format! Comment blocks that pertain to an
entire method or class should be marked as javadoc by beginning the
block with a double \*:

    /**
    * A class of linear algebra utility methods.
    */


Naming and Declarations
-----------------------

### Use meaningful names

Variable names should describe what they are for. Distinguishing what a variable
references is best done by following a particular naming convention (see Item
10). Variable names should be words or combinations of words.

### Follow naming conventions

By convention, Java uses [camelCase](http://en.wikipedia.org/wiki/CamelCase).

1.  **Variables** and **functions** are usually verbs, and are written in
    `camelCase`. The first letter is lowercase.

    1.  Getter and setter methods should begin with the verbs `get`
        and `set`. Examples: `getName()`, `setName(String name)`.

    2.  Methods that return a `boolean` generally begin with the verbs
        `is` or `has`. Examples: `isSeventeen()`, `hasMiddleName()`.

2.  **Classes** names are usually nouns, and are given in `PascalCase`. Follow
    the `camelCase` rule as above, and capitalize the first letter. Examples:
    `Ticket`, `DormRoom`.

3.  **Constants** (variables marked `static final`) and **enumeration members**
    are usually written in `ANGRY_CASE`. Capitalize all letters, with
    underscores between multiple words. Examples: `PI`, `MAXIMUM_SIZE`.


Code Factoring
--------------

### Break up large methods into small methods

In _Clean Code_, Bob Martin asserts that methods should hardly ever be more than
20 lines long. While this guideline may be hard to always adhere to, if your
method starts to look bloated, consider breaking it into smaller,
logically-separated helper methods.


Verbosity
---------

### Don't rewrite existing code

The Java standard libraries provide implementations of a great number of methods
and data structures---use them! The
[java.util](https://docs.oracle.com/javase/8/docs/api/java/util/package-summary.html)
package will prove especially useful in this course.


Testing
-------

### Write tests first

Follow test-driven development! Set up test cases *before you write your code.*
Doing so will help you better understand the behavior of the algorithm or
solution you are implementing.


OO (Object-Oriented) Concerns
-----------------------------

### Avoid public fields

Use getters and setters instead. If a class `Point` has an instance variable `x`
and you are working with a `Point` point, you should not find yourself writing
`point.x`. Instead, declare `x` as a (package-)private variable, and write a
getter method, `point.getX()`. One exception in which this rule may be waived is
if the variable `x` is marked as final, and only if `x` is immutable.

### Use appropriate modifiers for all types

In general, restrict visibility as much as possible. If need a refresher on
modifiers (like `protected`, `final`, `static`), refer to the Oracle pages on
[access-level
modifiers](http://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html)
and [instance/class
members.](http://docs.oracle.com/javase/tutorial/java/javaOO/classvars.html)


Additional Style Resources
--------------------------

-   [General Penn Coding
    Guidelines](http://www.cis.upenn.edu/~cis1xx/resources/codingStyleGuidelines.html)
-   [Swarthmore
    CS](http://www.cs.swarthmore.edu/~newhall/unixhelp/javacodestyle.html)
-   [Clean
    Code](http://www.e-reading-lib.com/bookreader.php/134601/Martin_-_Clean_Code_-_A_Handbook_of_Agile_Software_Craftsmanship.pdf)
    (free book!)
-   The Elements of Java Style
-   _Effective Java_, by Joshua Bloch: It’s not free, but… _Effective Java_
    is the go-to book on the Java language and is practically required
    reading at many major tech companies, such as Google and Palantir.
    It covers some advanced topics that are more relevant to production
    code, but is nonetheless an invaluable resource with respect to
    class design and general programming. In particular, Chapter 4
    ("Classes and Interfaces"), and Chapter 8 ("General Programming") are relevant
    to 121.
