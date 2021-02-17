---
title: "Hash links for individual linkblog items"
description: The linkblog main page has a new feature, enabling linking to individual linkblog items.
published: true
layout: post
date: 2021-02-17 21:18:00:00 +0700
tags:
- web development
- linkblog
- programming
---
If you read the [linkblog](https://links.markjgsmith.com) you might have noticed a change today.

The [linkblog](https://links.markjgsmith.com), by the way is where I share links I find online, it’s published every day at midnight. 

Sometimes I add a bit of commentary, other times it’s just the link and page title. It’s mostly links to javascript, technology and web development content, but there’s often other stuff in there too. There’s an RSS feed. 

At the end of the week I do a roundup of the best links and send it out in the [newsletter](https://markjgsmith.substack.com).

One of the features that I lost when migrating from the [old linkblog SaaS]({{ site.baseurl }}/2020/11/25/linkblogdotio-is-dead-long-live-linkblogging.html) (which is sadly no more) to the [statically generated serverless linkblog]({{ site.baseurl }}/portfolio#jamstack-architecture-content-sites), was the ability to link directly to an item in a day. I’ve added this feature back, so you should see hash links next to each item in the linkblog. The day hash links remain unchanged.

The item hash links point to the archives rather than on the main page, because the main page only shows the previous 50 days, so it makes more sense to link to the archives, so that the link continues to point to something even after the item drops out of the most recent 50 days.

The feature is a little different to the [SaaS version]({{ site.baseurl }}/2019/12/08/new-linkblog-feature-highlightable-messages.html), it’s less fancy, but since it just uses a standard url [hash fragment](https://en.m.wikipedia.org/wiki/URI_fragment) it works without javascript, which makes it arguably more robust. 

It’s definitely useful, I’ve been experimenting with [inserting linkblog items into blog posts as quotes]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html), and having a direct link to an item will make that a lot easier. 

Hash links are standard these days, quite well understood by users, people are used to seeing them on blogs and social media sites. I’ve also chosen a font size, weight and color that blends quite well with the page without getting in the way of the reading experience.

Though they add quite a lot of extra characters to the UI, I think on balance the page still has the minimalist aesthetic.

That’s the change, it’s nothing earth shattering, but the main linkblog page doesn’t change very often so I wanted to describe the change. I think you’ll find it a useful feature.
