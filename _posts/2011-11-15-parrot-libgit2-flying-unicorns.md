---
layout: post
title: Parrot + libgit2 = Winxed Unicorns
status: unpublished
---

# {{ page.title }}

What happens when you tie together Parrot Virtual Machine and the shiny new
[libgit2](http://libgit2.github.com) which is rumored to be a ["magical world of ponies, fluffy clouds and unicorns"](https://twitter.com/#!/dukeleto/status/128607267061895168) ? Winxed unicorns.


Example Winxed code using parrot-libgit2:

{% highlight javascript %}
using Git2.Repository;
using Git2.Index;
using cstring;

var git_repo = new Git2.Repository();
var rc       = git_repository_open(repo.ptr, cstring(".git"));
var bool     = git_repository_is_bare(repo.ptr);
{% endhighlight %}

