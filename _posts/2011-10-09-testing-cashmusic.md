---
layout: post
title: Testing CASH Music
status: unpublished
---

# {{ page.title }}

For those that are unfamiliar with the concept of "testing code" or "test
driven development", it is the habit of writing code to ensure that other code
works correctly. It works out to be a very valuable habit.

Imagine you have a pile of code Foo, which is exercised by a different pile of
code Bar. If you wanted to sound fancy, you would call Foo "the implementation"
and Bar your "test suite". The point of the test suite is to ensure that the
implementation works correctly.

Some of the simplest and most useful tests to write are syntax checking test.
Does every file in Foo pass a syntax check? If not, surely bugs are lurking.

So, of course, the first kinds of tests that I wrote for [CASH Music](http://cashmusic.org) were syntax
check tests, which have already proved useful in finding some issues.

The next step in making tests useful are to get them automagically run on each
commit to the [DIY](https://github.com/cashmusic/DIY) repo, also known as 'continuous integration'. CASH Music uses
[Jitterbug](http://jitterbug.pl) to run tests on each commit to [Github](http://github.com/organizations/cashmusic), and it even has a 
[pretty web interface](http://dev.cashmusic.org:3000/project/DIY) to show off the data. This makes it very easy to see exactly which
commit "breaks the test suite", i.e. causing at least one test to fail. Knowing
*exactly* which commit breaks something is invaluable when things are being
changed and fixed rapidly.

Recently I helped to add [SQLite](http://sqlite.org) support to our command-line 
[developer installer](https://github.com/cashmusic/DIY/blob/master/installers/php/dev_installer.php). The primary motive was to make it easy for developers to test out
CASH Music without needing a MySQL database, but the secondary motive was to
deploy the CASH Music schema to SQLite in our test suite so databasey stuff can
be tested. Since CASH Music is predominantly databasey interaction, this is
absolutely necessary to for good test coverage.

After SQLite was working, I created a [test installer](https://github.com/cashmusic/DIY/blob/master/installers/php/test_installer.php) which is really just a
paired down developer installer which sets up a DIY instance specifically to
run test. This has recently allowed us to write some basic tests for
CASHRequest which is a central component of DIY that just about everything else
relies on.

But why do we test? What is the big deal? Doesn't it take extra time? Is it
really worth it?

The difference between tested and untested code is a large chasm. On one side,
you can make a change and have some confidence that it didn't break something,
if your test suite passes. On the other side, any change, possibly only a
single line or character has the possibility to break some other seemingly
unrelated part of your codebase. The only way to be sure is to manually go
through, attempting to exercise a large portion of your code to ensure nothing
broke. As your codebase goes from dozens to thousands of lines of code, this
quickly becomes infeasible. In these cases, developers change stuff and hope
for the best, which is hardly a strategy at all.

Testing does take extra time, but it also measurably increases the code quality
as well as giving developers the agility to quickly change and adapt code.

So is it really worth it to test CASH Music? The way I see it, our lives are
continually being entangled with code. What if that DNA-refactoring-with-Xrays
machine at the airport has a bug in it? What if self-driving robotic cars that
are trying to capture "street views" start mowing down cute innocent
pedestrians or worse, their pets? Bugs in code are now intimately entangled
with the physical meatspace that we live in.

Since artists in the future will depend on our codebase, we are not taking bugs
lightly. The only way CASH Music is going to roll is with a well-tested and
easy-to-use platform that artists and labels can rely on.
