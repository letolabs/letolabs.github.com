---
layout: post
title: Parrot + libgit2 = Winxed Unicorns
status: unpublished
---

# {{ page.title }}

What happens when you tie together [Parrot Virtual Machine](http://parrot.org) and the shiny new
[libgit2](http://libgit2.github.com) which is rumored to be a ["magical world of ponies, fluffy clouds and unicorns"](https://twitter.com/#!/dukeleto/status/128607267061895168) ? [Winxed](http://winxed.org) unicorns.


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

