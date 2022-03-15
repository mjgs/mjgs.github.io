---
title: 'New Linkblog feature: highlightable messages'
published: true
layout: post
date: '2019-12-08 16:32:00'
tags:
- linkblog
---

A big part of linkblog is the ability to see the context around a link, to see the other links that were posted on that day. It’s been possible to link directly to a day in your linkblog since the beginning. But until now, it hasn’t been possible to link directly to a specific message in a day.

For example here is the link to [yesterday in my linkblog](https://linkblog.io/users/mark?date=7December2019). These day urls are copyable from the hash link (#) next to each day.

The latest feature is the ability to link directly to a specific message in a day. When the page loads from a highlightable message url, the message that is specified in the url will momentarily be highlighted. After a few seconds the highlight will fade back to the regular linkblog page. This strikes a good balance between being able to point directly at a specific message while also keeping the context around the message focussed.

{:refdef: style="text-align: center;"}
![Linkblog Redesign - Landing page 1]({{site.baseurl}}/assets/images/highlightable-messages1.png)
{: refdef}

After loading a linkblog using a [highlightable message url](https://linkblog.io/users/mark?date=7December2019&id=be8b2a88-7147-4ad8-82a8-7313c743d692) you will know which message was being referenced but also be able to see clearly the context of that message. Note that you have to have javascript enabled in your browser for the feature to work.

One challenge implementing this feature was how to do it while minimising the effects on the linkblog page. Adding a clickable element next to each message on the page to copy the url to the clipboard would negatively impact the minimalism and readability of the page. For the moment the way to get a highlightable message url is from the search page. 

Each message in the search page results has a highlightable message url as the hash link. Since most often users will probably be searching for the most recent messages, I’ve updated the search page so that performing a search with an empty search box returns all the messages with latest listed first.

{:refdef: style="text-align: center;"}
![Linkblog Redesign - Landing page 1]({{site.baseurl}}/assets/images/highlightable-messages2.png)
{: refdef}

I hope you enjoy the new feature!