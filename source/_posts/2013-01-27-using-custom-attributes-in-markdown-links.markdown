---
layout: post
title: "Using custom attributes in Markdown links"
date: 2013-01-27 21:58
comments: true
categories: notes
---

This blog runs on Octopress &mdash; which means that I write posts in Markdown.

I'm presently a big fan of [Microformats](http://microformats.org/) and wanted
to include [`rel="me"`](http://microformats.org/wiki/rel-me) links to other
websites that I use.

After searching a little for a clean solution, I realised that Markdown is
[HTML-compatible](http://daringfireball.net/projects/markdown/syntax#html) - I
can simply write in the exact HTML I need for the link within my Markdown file.

### Example:

Instead of writing something like

`[@adhipg](http://twitter.com/adhipg)`

and then trying to add custom attributes; I can simply write

`<a href="http://twitter.com/adhipg" rel="me">@adhipg</a>`.

Obviously you can use this for any other custom attributes/html you want.

Ugly - yes. But it works and does not need JavaScript.
