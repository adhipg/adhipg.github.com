---
layout: post
title: "Tracking your Toggl timer with tmux-powerline"
date: 2013-02-11 18:22
comments: false
categories: notes
tags: [tmux-powerline, toggl, node.js]
---

I've recently started using [Toggl](http://toggl.com) to track time spent on
various things. But I usually forget to turn it on when I'm actually working.

I wrote a little script that uses [Node.JS](http://node.js) to get my active 
running timer on Toggl and display it on my
[tmux-powerline](https://github.com/erikw/tmux-powerline). It displays nothing
if no timer is running.

The script can be found here:
{% gist 4749181 %}

Do remember to `chmod +x` the JS file and include it as a segment in your status
bar.

A screenshot for completeness:

{% img /images/tmux-powerline-toggl.jpg %}
