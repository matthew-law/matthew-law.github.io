---
layout: post
title:  "How I Made This Website"
date:   2020-05-15 18:24:07 +0100
tags: [thing a week, web design]
permalink: /blog/:title.html
---

This post has a bit more technical information about how I went about making this site, but it is definitely not a how-to guide – I made the site by piecing together information and trying things to see what worked and what did not, so I am by no means an authority on this.

The basis of the site is [Jekyll](https://jekyllrb.com/), a static site generator which can take documents written in Markdown (like this very post) and spit out the html necessary to display it as a webpage.

The site is based on the [Klisé](https://github.com/piharpi) theme for Jekyll by Mahendrata Harpi, from which the structure/layout is adapted. The minimalistic theme works well because a) I don't actually have much content as of now and b) I'm not really aiming for a site that looks like [cameronsworld.net](https://www.cameronsworld.net/). Bonus points for night mode too (top left).

Everything is hosted for free on [GitHub pages](http://pages.github.com/), which integrates nicely with Jekyll.

The favicon is just the Ⓜ️ emoji (for Matthew ofc) from Twitter's open source [Twemoji](http://pages.github.com/) emojis, and I used [realfavicongenerator.net](https://realfavicongenerator.net/) to quickly generate the necessary files from the [original svg](https://raw.githubusercontent.com/twitter/twemoji/master/assets/svg/24c2.svg).

At the moment I'm using [Visual Studio Code](https://code.visualstudio.com/) as my IDE, but I'm still in the early experimentation stage of things, so can't say whether or not I'll stick with this or start using a WYSIWYG Markdown editor instead.
