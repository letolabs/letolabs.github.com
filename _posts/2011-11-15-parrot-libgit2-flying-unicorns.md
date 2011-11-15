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

Winxed is a new Javascript-ish language that comes with Parrot Virtual
Machine. You can basically think of it as a scripting language on top of
Parrot, which is good for writing system scripts and/or new languages.

Many new projects on Parrot use Winxed for their build system, instead of
Makefiles, Configure.pl or setup.pir. Here is the
[setup.winxed](https://github.com/letolabs/parrot-libgit2/blob/master/setup.winxed)
file which is used to build, test and install parrot-libgit2. This
setup.winxed file is very similar to how [distutils](http://wiki.python.org/moin/Distutils) works in the Python world.
In fact, setup.pir was the old, [PIR](http://docs.parrot.org/parrot/latest/html/docs/user/pir/intro.pod.html) way to do distutils-style build systems
in Parrot, but now we have ported distutils to Winxed.

Maintaining a build script written in higher-level language is a lot
friendlier. PIR is still a useful language, but core Parrot developers mostly
consider it a language that is a target for code generation. We don't really
expect humans to write much PIR, except when there is no other choice.

## parrot-libgit2

Enough about Winxed and build systems! We all know libgit2 is the new shiny
and we want access to those beautiful, glistening DAGs via a [delicious API](http://libgit2.github.com/libgit2/#HEAD).

That is why parrot-libgit2 exists. It provides access to libgit2 *to every
language built on top of Parrot*. Let that sink in for a moment. Usually,
when you write a binding from a dynamic language to some kind of C/C++
library, every single language needs a different binding. This is a huge
amount of work, and most people only ever have the gumption to write a
binding in one or maybe a few languages. If you are really masochistic,
you might even use [SWIG](http://swig.org).

Even still, every one of these bindings needs to be maintained. And that is
*a lot* of code. parrot-libgit2 routes around this problem by giving Parrot
access to libgit2, so any other Parrot language can load some bytecode and
then start calling libgit2 functions. Currently there are tests for using
parrot-libgit2 from PIR and Winxed, but examples of using it from other
Parrot-derived languages such as NQP and Rakudo Perl 6 are on the way.

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

