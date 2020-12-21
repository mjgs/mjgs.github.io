---
title: Mozilla MDN Docs are going full Jamstack
description: These are exciting times for web development, new architectures are being developed to foster collaboration on content sites. This article discusses the recent announcement that MDN Docs, the biggest and most popular documentation site for web development is being updated to have a modern Jamstack architecture
published: true
layout: post
date: 2020-11-19 18:24:00:00 +0700
tags:
- jamstack
- web development
- content
- programming
- architecture
---
Earlier in the year [MDN Web Docs turned 15 years old](https://hacks.mozilla.org/2020/07/mdn-web-docs-15-years-young). They have been around since the early days of the web and made huge contributions to it’s evolution. More info on their [Wikipedia page](https://en.m.wikipedia.org/wiki/MDN_Web_Docs).

But how big are they? 

Let’s look at a few stats:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- 15 million views per month
- 3,000 new articles in the last 3 years, 260,000 article edits
- Grown in double-digit percentages, year over year, every year since 2015
- Serving more than 15 million web developers on a monthly basis
{: refdef}

They are big! 

They’re also doing a phenomenal job of organising the web’s developer documentation, adding new site features to make learning easier, while building a vibrant community.

So it’s big news when they decide to re-architect their platform, especially when it happens just after they announced 250 layoffs (1/4 of it's workforce).

I posted [on my linkblog](https://links.markjgsmith.com/archives/html/2020/11/#2November2020 ) a few weeks ago:

> MDN Web Docs evolves! - the folks at Mozilla are going Jamstack + GitHub for their new MDN docs content contribution workflows, great writeup of the planned architecture, this is definitely an interesting space to keep an eye on, it will be really cool to see the collaboration workflows they build

Here is a link to the original article on [hacks.mozilla.org](https://hacks.mozilla.org/2020/10/mdn-web-docs-evolves-lowdown-on-the-upcoming-new-platform).

Their writeup does a really good job of explaining the architecture changes they are making. 

Essentially it boils down to this:

> We are updating the platform to move the content from a MySQL database to being hosted in a GitHub repository (codename: Project Yari)

And the key takeway:

> We are replacing the current MDN Wiki platform with a JAMStack approach, which publishes the content managed in a GitHub repo

In the piece they list many reasons including:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Making it much easier to add new features to the platform
- Better contribution workflow, moving from a Wiki model to a pull request (PR) model
- Better community building by adding discussions, feedback, review and approve steps
- Simplified frontend architecture improving accessibility
{: refdef}

And they go on to describe the planned architecture in a lot of detail with some illustrative diagrams. [Jamstack](https://jamstack.org) website architectures are officially where new [custom content workflows](https://blog.markjgsmith.com/2020/10/30/github-actions-for-custom-content-workflows.html ) are being built. 

I think this is perhaps a sign that there are some big shifts happening in web development, where the architectures that have powered the web for the past 10 years are being rewritten, enabling new ways of collaborating together to make digital things. 

Which other large websites will make similar moves?
