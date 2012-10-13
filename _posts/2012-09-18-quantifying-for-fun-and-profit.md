---
layout: post
title: Quantifying for Fun and Profit
status: unpublished
---

# {{ page.title }}


[TLDR](https://en.wiktionary.org/wiki/TLDR): With the help of [Beeminder](http://beeminder.com) and the excellent personal trainer
[Josh Sabraw of Form and Function](http://pdxtraining.com), I've lost 27 pounds and continue on a downward trend.

<img src="https://www.beeminder.com/dukeleto/goals/weight/graph?style=hist">

## What is Beeminder?

Many years ago I read the [Hacker's Diet](http://www.fourmilab.ch/hackdiet/www/hackdiet.html) and learned many
things, but the most important was the concept of a "trend". The corollary of
this is that tracking your daily weight is only important to calculate your
moving average. It is easy to get demotivated if you have a single day spike in
weight, which is why it is much better to gain the perspective from the trend.

## How I use Beeminder

As you can see from the graph above, I started using Beeminder but went off
track. But I saw that Beeminder motivated me to go in the right direction
and I knew that putting some cash money on the line would motivate me even more.
Beeminder tells you how to avoid the impending train wreck.

Being able to enter data via SMS is a killer feature. Beeminder even lets you
tell it what time of day to deliver an SMS, so I set it up to happen early in
the morning. This way, I always get an early morning reminder to weigh in and
record data. I also use Beeminder to track how many good-form [squats](https://www.beeminder.com/dukeleto/goals/squats) that I do,
and I have that SMS reminder come in around 11pm, when I am hopefully heading
to bed and have the total for the day to record.

I remember using the Hacker's Diet first on paper in a folder and
then by maintaining a CSV file and using a custom GNUplot script to generate
graphs in PNG format. It was awesomely nerdy but not very convenient and hence
easy to "forget" to record data.

Also, if you start going above your trend (10 day moving average), Beeminder
warns you and tells you that you *could* lose tomorrow. That is the inflection
point between short-term you and long-term you ([akrasia](http://blog.beeminder.com/akrasia/)) and gives you the right
information at the right time to change your behavior. It will also warn you
that you are off-track and going to *lose today* without corrective measure. That
is the beginning of the trend changing direction and is the time to act or fail.
This is a huge motivator that should not be underestimated.

Beeminder was the tracking side of my goal, the other side was doing the actual
work and changing my eating patterns. Without the help of [Josh Sabraw](https://twitter.com/pdxtraining) of [Form and Function](http://pdxtraining.com).
I would not have been able to "stay on the yellow brick road". 

One of the most important lessons that I learned from Josh was the importance of proper form. There is a
world of a difference between doing planks or squats with proper form and not. There is
really no point in doing this things if you are going to do them incorrectly, because
you are just going to hurt yourself or get frustrated, or both. Josh excels at teaching
proper form and that is a lesson that will be valuable for a lifetime.

## Making things Beemind-able

The key to making Beeminder really useful for *you* is to make it dead simple.
Another thing that I use Beemind to track is [commits](https://www.beeminder.com/dukeleto/goals/github_commits). 
The only way to make this feasible is to make it automatic, so I wrote a silly little [Perl module](https://github.com/letolabs/App-Beeminder-Hook) that
could be added as a Github post-receive hook.

<img src="/images/github_commits_graph.png">

Look at that motivation! I actually forgot that I changed my goal from a flat
line to 10 commits per day. But when the Beeminder bot told me I was going to
lose, I said "Oh no you don't" and started a flurry of commit activity.
