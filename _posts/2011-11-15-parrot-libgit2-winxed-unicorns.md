---
layout: post
title: Parrot + libgit2 = Winxed Unicorns
status: unpublished
---

# {{ page.title }}

## Background

What happens when you tie together [Parrot Virtual Machine](http://parrot.org) and the shiny new
[libgit2](http://libgit2.github.com) which is rumored to be a ["magical world of ponies, fluffy clouds and unicorns"](https://twitter.com/#!/dukeleto/status/128607267061895168) ? [Winxed](http://winxed.org) unicorns.

<center>
<a href="http://www.flickr.com/photos/29364131@N07/3119439609/sizes/s/in/photostream/">
<img src="/images/winxed_unicorn.jpg">
</a>
</center>

Winxed is a new [Javascript-ish](http://whiteknight.github.com/Rosella/winxed/syntaxandtypes.html) language that comes with Parrot Virtual
Machine. You can basically think of it as a scripting language on top of
Parrot, which is good for writing system scripts and/or new languages.

Many new projects on Parrot use Winxed for their build system, instead of the traditional
[Configure.pl](https://github.com/rakudo/rakudo/blob/master/Configure.pl), [setup.nqp](https://github.com/parrot/tree-optimization/blob/master/setup.nqp), or [setup.pir](https://github.com/fperrad/lua/blob/master/setup.pir) build file. Here is the
[setup.winxed](https://github.com/letolabs/parrot-libgit2/blob/master/setup.winxed)
file which is used to build, test and install parrot-libgit2. This
setup.winxed file is very similar to how [distutils](http://wiki.python.org/moin/Distutils) works in the Python world.
In fact, setup.pir was the old, [PIR](http://docs.parrot.org/parrot/latest/html/docs/user/pir/intro.pod.html) way to do distutils-style build systems
in Parrot, but now we have ported distutils to Winxed.

Many thanks are owed to [Bob Kuo](https://twitter.com/bobkuo), who was a [Google Summer of Code](http://code.google.com/soc/) student that
wrote a [setup.winxed](https://github.com/bubaflub/parrot-gmp/blob/master/setup.winxed) for his [parrot-gmp](https://github.com/bubaflub/parrot-gmp) project. The setup.winxed in
parrot-libgit2 was based on his work and wouldn't exist without it.

Maintaining a build script written in higher-level language is a lot
friendlier, takes less time and is less error-prone. PIR is still a useful
language, but core Parrot developers mostly consider it a language that is a
target for code generation. We don't really expect humans to write much PIR,
except when there is no other choice.

## parrot-libgit2

Enough about Winxed and build systems! We all know libgit2 is the new shiny
and we want access to those beautiful, [glistening DAGs](http://eagain.net/articles/git-for-computer-scientists/) via a [delicious API](http://libgit2.github.com/libgit2/#HEAD).

That is why parrot-libgit2 exists. It provides access to libgit2 *to every
language built on top of Parrot*. Let that sink in for a moment. Usually,
when you write a binding from a dynamic language to some kind of C/C++
library, every single language needs a different binding. This is a huge
amount of work, and most people only ever have the gumption to write a
binding in one or maybe a few languages. If you are really [masochistic](https://github.com/leto/math--gsl),
you might even use [SWIG](http://swig.org).

Even still, every one of these bindings needs to be maintained. And that is
*a lot* of code. parrot-libgit2 routes around this problem by giving Parrot
access to libgit2, so any other Parrot language can load some bytecode and
then start calling libgit2 functions. Currently there are tests for using
parrot-libgit2 from PIR and Winxed, but examples of using it from other
Parrot-derived languages such as [NQP (Not Quite Perl 6)](https://github.com/perl6/nqp] and [Rakudo Perl 6](http://rakudo.org) are on the way.

Example Winxed code using [parrot-libgit2](https://github.com/letolabs/parrot-libgit2):

{% highlight javascript %}
// these are very similar to use Module::Foo in Perl 5
using Git2.Repository;
using Git2.Index;
using cstring;

// create a new repo object
var git_repo = new Git2.Repository();

// actually open the repo in .git
var rc       = git_repository_open(repo.ptr, cstring(".git"));

// check to see if this is a bare repo
var bool     = git_repository_is_bare(repo.ptr);
{% endhighlight %}

<br>

## Why is libgit2 exciting?

libgit2 is a reimplementation of Git as a thread-safe library in pure C. That
is huge. Currently, many libraries cannot integrate with Git properly for
various reasons that are baked into how Git works on the command-line.

libgit2 is not going to replace Git 1.x. Rather, it is a kid sister. But
libgit2 *is* bringing native Git support to new platforms, such as Windows,
since it does not depend on Perl and /bin/sh.

It also allows people to use git repositories via a nice programming API
instead of shelling out to binaries, which often don't exist. Mobile apps will
probably be looking towards libgit2 for their Git-related needs soon.

## What can parrot-libgit2 right now?

It can do very simple things, like open repositories and indexes. It can call
simple functions that don't require complex datatypes. There is [a branch](https://github.com/letolabs/parrot-libgit2/tree/oid) to add
Git2.Oid objects, which are basically how you search for SHA1's in a git object
database.

Not all libgit2 datatypes are currently supported. There are some known bugs
where assumptions about size_t are made where they should be detected. You
can look at the current Winxed tests [here](https://github.com/letolabs/parrot-libgit2/blob/master/t/winxed/001_load.t) .

If learning about libgit2 and Parrot sounds interesting to you, fork
parrot-libgit2 and try it out! You can also find me hanging out in #libgit2 on
irc.freenode.net if you have questions. May the DAG be with you.
