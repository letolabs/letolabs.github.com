---
layout: post
title: Opening a Can of Disruption on the Music Industry
---

# {{ page.title }}

Free and Open Source software has been disrupting various markets
for almost 40 years, sometimes in a small way, other times with a big splash.
Most of these events have been in extremely technical niches, such as
[operating](https://secure.wikimedia.org/wikipedia/en/wiki/Linux)
[systems](http://rtems.com), [compilers](http://gcc.gnu.org),
[text](http://vim.org) [editors](http://www.gnu.org/software/emacs), [version
control systems](http://git-scm.com/) and the like. All of these technologies
are "close to the metal" of hardcore geekery. Average users rarely interact
with them or even know what they are, even though they have a huge impact
on how software is made, delivered and run.

Each year we see our ["hacker spirit"](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html#catbmain)
travel farther into mainstream culture. We
are seeing our ideals starting to transform industries that were once just a glimmer in an
idealistic hackers eye, such as [electronic medical records](http://openmrs.org) or
[disaster relief management software](https://secure.wikimedia.org/wikipedia/en/wiki/Sahana_FOSS_Disaster_Management_System).

But so many industries still await transformation. One is the music industry,
and in particular, music distribution, sales and promotion. This industry is
currently dominated by proprietary software, usually sold as a hosted service.
These services cost between 15% to 40% of artist sales, usually on
top of any payment processing fees, for very little return. This cost is in addition
to exorbitant fees, such as charging 50 cents for a "download code". This
means it costs an artist (or their label) potentially hundreds of dollars just
to send out a digital demo to a select group of people in hopes of getting a
few reviews.

This outrageous behavior of exploiting artists will soon come to an end, thanks
to [CASH Music](http://cashmusic.org). CASH Music is a [non-profit](http://cashmusic.org/about/) that puts artists first, and has high
hopes to change the tech landscape available to all artists, from the local
garage band to international chart-toppers and everyone in between. There is code being hacked on
currently called [CASH Music DIY](https://github.com/cashmusic/DIY), originally started by the infamous 
[Jesse Von Doom](https://twitter.com/#!/jessevondoom), and increasingly by [yours truly](http://leto.github.com). It aims to greatly change the power
differential between artists and the industry that thrives on their existence.

Through [freely available code](http://cashmusic.org/about/faq/), that anybody is free to modify, tinker with, and
learn from, artists will be able to manage and interact with their fans, sell
and distribute digital and physical representations of their music and have
full control about how to promote their creations.

This code has the moniker DIY (Do It Yourself) because we are first building a
version that runs on your own server, as opposed to being a hosted service.  It
is still in the "developer alpha stage", which means we are actively seeking
out developers to take it out for a spin, give us feedback, and hopefully
contribute back new and exciting features. Our aim is to make it run on just
about any web hosting service with a recent-ish version of PHP, with no
external dependencies, other than some kind of database access. Once we get
stuff nailed down and provide a baseline of functionality, we will look into
hosted solutions. Our other major goal is to make it easy to integrate CASH
Music into an already existing website infrastructure, like Wordpress or
other blogging systems. To add CASH Music to any of these systems, all you need
to do is add this single line of PHP:

{% highlight php %}
    <?php require_once("$CASHMUSIC/framework/php/cashmusic.php"); ?>
{% endhighlight %}

where $CASHMUSIC is the directory where the CASH Music DIY software lives on your server.

All that is necessary is to get a [single PHP file](https://github.com/cashmusic/DIY/blob/master/installers/php/install.php) onto your server, Everything
else is controlled via a pretty web interface that downloads, installs and
configures everything you need and even includes custom art by Audrey Nieh of [Squid You Not](http://www.squidyounot.com)!
Jesse has a sweet tooth for eye candy, and it shows.

We are working, slowly but surely, to make this software a game-changer. And
slowly but surely is on purpose, because we are in it for the long haul, and
the organization and code is evolving together. CASH Music is a non-profit, so
we don't have millions of VC dollars to throw at this, but what we *do* have is
the knowledge that this is important and it contains the seed of greatly
improving the lives of many people, by allowing them more control over their
own creations and allowing them to make a reasonable living by selling their
art without all the middlemen.

If this sounds fun to you, then we would love your help. Check out our code on
[https://github.com/cashmusic/DIY](Github), take a look at our [pretty developer docs](http://cashmusic.github.com/DIY/), let us know what you would like to see it
do, and [definitely tell us if you find a bug or something wonky](http://help.cashmusic.org/).  Join our IRC channel at #cashmusic on irc.freenode.net,
follow CASH Music on the [service](http://twitter.com/cashmusic) [of](http://github.com/cashmusic) [your](http://www.facebook.com/cashmusic.org) choice.
If you are feeling really generous, a [donation](http://cashmusic.org/donate/) will go a long way.
And, of course, we aren't just looking for developers! If you have an eye for
design or the knack for documentation, we could greatly use your help as well.

The current plan is have a [developer release every Thursday](http://blog.cashmusic.org/2011/08/11/the-cash-platform-a-peek-at-what-weve-been-up-to/). You can see a recent
one [here](https://github.com/cashmusic/DIY/commits/dev_release_2). We are all about small, iterative improvements. If each dev
release has one more feature, or better docs, or one less bug than the
previous, then it is a success.

We cordially invite you to join us in refactoring the music industry, because
it surely has needed it for a long time and it sure is going to be a metric shit
ton of fun.
