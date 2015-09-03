---
layout: default
title: CIS 121 Testing Guide
active_tab: homework
---

Context
=======

Why do we care so much about testing? After all, we write tests for homework
assignments, and you aren’t likely to come back to a homework assignment in six
months and add breaking features to it. However, we are in the business of
teaching good habits and practices. There are several benefits of writing tests
properly:

1. **Unit tests help you determine code correctness.** How else would you know
    if your assignment is ready to submit unless you had written a full unit
    test suite?

2. **Unit tests provide a mental framework for code design.** After writing out
    your test suite, you should have a better understanding of the flows of data
    within your program, as well as the outputs that your program should emit in
    response to certain inputs.

3. **Unit tests are an easy way of letting other people jump into a codebase.**
    While this does not apply to CIS 121, in real life, code bases are shared
    between people. Not everyone can have a complete understanding of a software
    project; even Linus Torvalds, inventor of Linux, doesn’t fully understand
    the entire operating system and its ecosystem at this point. It is
    ostensible that someone can add a new feature or make a change to the code
    base that accidentally breaks existing functionality. A full test suite
    would catch this. What if an engineer came to work on a project years after
    you left that project? She wouldn’t be able to call you and ask you for your
    knowledge of the code base. Therefore, unit tests are therefore an artifact
    of your knowledge.

4. **Unit testing saves your organization money.** While this also does not
    apply to CIS 121, this is probably the most important point, and definitely
    the most overlooked point. People write software to accomplish some business
    goal, whether that is creating a product, consulting for a client,
    performing academic research, or automating a manual process. If you write
    code that breaks something, you cost your organization money. For example,
    your customers might not be able to buy an item, you could lose a consulting
    client and damage your firm’s reputation, you could waste grant money, or
    you could perform some task incorrectly. Unit and integration tests are
    incorporated into all modern build systems; put simply, you will not be
    physically able to deploy code to production servers if any automated tests
    fail. Therefore, you are hedged against a large cause of performance
    regressions, and you save your organization money.


Bottom-Up vs. Top-Down
======================

We require that you use **bottom-up** testing in CIS 121. Put simply, bottom-up
testing means testing simple things before testing harder things. This is
because of the compositional nature of software engineering. Methods and
abstractions build on top of each other. It is best to make sure that code at a
lower level of abstraction is tested before code at a higher level of
abstraction.

Why? Let us consider a motivating example. Imagine a 2D rendering engine in Java
that had a `Point` class, a `Shape` class, and a `Scene` class. A `Shape` is a
collection of `Point`s, and a `Scene` is a collection of `Shape`s. You would
want to fully test the `Point` class first, then the `Shape` class, and then the
`Scene` class. This makes it much easier to determine the source of an error. If
some bug comes up in the rendering engine, you can be reasonably certain that
the issue is not with the `Point` class (the lowest of the abstractions), since
you already fully tested it! If we had done **top-down** testing, we would have
not known if the issue were in the `Scene` class, the `Shape` class, or the
`Point` class.

Bottom-up testing also applies to methods within a class. Imagine that you wrote
a method that used three helper methods. Bottom-up testing mandates that you
test the helper methods first, make sure that they work, and *then* test the
larger method. The reasoning is similar as above.

Finally, bottom-up testing applies to the size of test cases for a specific
method. You should order "small" test cases (edge cases and base cases) before
large test cases. This way, if your code has a bug, you can reasonably determine
characteristics of the bug.

We will be manually grading your test cases based on this philosophy. For a
given method, we might expect to see all edge cases unit tested, followed by
degenerate cases and base cases, followed by a small test case demonstrating
more complex functionality. For example, imagine a method of the signature
`public static int max(int[] arr)`, which attempts to find the maximum of an
array of integers. Here is one potential strategy for the test cases we would
write:

1.  A null array, which is an edge case.

2.  An empty array, which is a degenerate case.

3.  A size-one array, which is a base case.

4.  A size-two array with the maximum at index 0.

5.  A size-two array with the maximum at index 1.

6.  A size-two array with a tie for the maximum (edge case).

7.  A size-three array with the maximum at index 0.

8.  A size-three array with the maximum at index 2.

9.  A size-three array with a tie for the maximum (edge case).

10. A size-four array.

One should be reasonably convinced after passing this test suite that the `max`
function is correct. It returns some reasonable output for edge and degenerate
cases, and it appears to iterate over the array and track the maximum properly.
There is no magical answer that says that a size-four array is the right one to
stop testing at, but we can imagine that we have already captured all of the
method’s complexity in the above test cases.


Edge Cases
==========

At some point during this class, you are probably going to ask yourself or your
friends what the big deal with edge cases are. Why do we insist that you throw
so many `IllegalArgumentException`s and test all of those cases? There are two
answers: **security and reliability**. First of all, recognize that public
methods can take in any input that typechecks. We don’t have a choice but to
consider ugly inputs; public methods can be called by any client of our code.
There are edge cases that, if left unhandled, can return a stack trace or memory
dump to the user, leaking sensitive information about the internals of your
application. This can cost your organization money (not to mention cause a very
poor user experience). Second of all, if every possible input and output is
documented, a client of your code can write reliable code on top of your API.
While these concerns are not huge for the scope of CIS 121, again, it is
important to build strong and correct habits.


Test Before Coding
==================

As taught in CIS 120, you should write unit tests before actually implementing
code. This is useful because it allows you to get into a good workflow of adding
code, running your test suite, and making fixes. Second, it encourages you to
think more about the problem before solving it. Finally, some of the programming
homeworks in this course will be very long; if you write tests first, you will
get some points for your work, even if you don’t get a chance to implement that
part of the homework itself. (:


Annotated Methods
=================

It is oftentimes useful to re-initialize data structures before every unit test
is run, particularly if you are testing a method that mutates the data
structure. Imagine that you wanted to run dozens of unit tests over the same
graph, for example. You should use the `@Before` annotation to invoke a method
that is run before every unit test. For example:

{% highlight java %}

Graph g;
@Before
public void setUp() {
    g = Graph.parseFromFile("directory.json");
}

{% endhighlight java %}

There is a corresponding `@After` annotation that should be used for routine
clean-up. Since Java is garbage-collected, you generally would only need to use
this to close files, close network connections, etc. (You would also use this to
clean up your test database if running these tests as part of a deployment
infrastructure, but that’s beyond the scope of CIS 121.)

Analogously, methods with the `@BeforeClass` annotation are run once (before
*any* unit test is run), and methods with the `@AfterClass` annotation are run
once (after the entire test suite is finished).


Testing for Exceptions
======================

It is easy to test for an exception to be thrown. Simply do the following:

{% highlight java %}

@Test(expected=NullPointerException.class)
public void testMaxNullArray {
    OurMathClass.max(null);
}

{% endhighlight %}

Obviously, you can change the `expected` field to look for any exception you
care about. For more fine-grained control over where the exception should be
thrown, do the following:

{% highlight java %}

public class ExceptionThrowingTest {
    @Rule
    public ExpectedException expectedException = ExpectedException.none();

    @Test
    public void testThrowAnException() {
        ExceptionThrower thrower = ExceptionThrowers.getDefaultThrower();

        expectedException.expect(MyException.class)
        thrower.throwMyException();
    }
}

{% endhighlight %}