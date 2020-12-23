---
title: Looking back at linkblog.io
description: Outlines the high level technical goals, deployment architecture and interesting application level features of linkblog.io, the minimalist link curation tool, a SaaS product I built as a solo-developer
published: true
layout: post
date: 2020-11-26 13:30:00:00 +0700
tags:
- linkblog 
- architecture
- infrastructure
- cloud
- web development
- portfolio
- automation
---
I recently [announced the end of linkblog.io](https://blog.markjgsmith.com/2020/11/25/linkblogdotio-is-dead-long-live-linkblogging.html). I go into a bit of detail in this short [indie hackers discussion thread](https://www.indiehackers.com/post/declaring-the-death-of-your-site-da5cbfed34). I wanted to do a quick retrospective to have something to refer to in future.

I’ve been running a linkblog for close to 10 years. In a lot of ways all the links I’ve posted chronicle my web development journey, but also just life in general. I found it a very useful tool and still do to this day. Somewhere along the way I decided to build a linkblogging SaaS product.

These were the high level goals of the system that emerged over time:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Robust implemenation that does what it was designed to do and does it well
- Have a minimalist user interface, emphasis on text content
- Easily scalable to handle growth
- Deployable to standard VPS hosting
- Fault tolerant and able to have zero downtime deploys
- Resilient so that any server could be easily rebuilt from scratch using backups where necessary 
{: refdef}

From a technical standpoint I achieved all of these goals.

I wrote about [Robust NodeJS Architectures](https://blog.markjgsmith.com/2020/11/13/robust-nodejs-deployment-architecture.html) earlier in the month, and this describes very closely what the linkblog.io infrastructure looked like.

Some other application level features and capabilities that are worth mentioning:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- MongoDB sessions support
- Redis sessions support
- Rate limiting using Redis
- JWT API authentication
- API Caching using Redis
- Backend job scheduling using Agenda
- Backend message queues using MongoDB
- Custom domains
- SCA compliant billing system (Stripe + webhooks)
- Production and staging environments
{: refdef}

Implemented using bash scripts:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Repeatable server provisioning system
- Application build and deploy system
- Backup and restore of certificates and databases
- Log file backup and cleanup
- Certificate renewal
{: refdef}

Most of these features were added as a necessity in response to real world events that happened during development.

Though the UI is quite minimalist and mostly text based, there was quite a lot going on underneath. The system could have been quite easily and safely extended.

Finally here are some screenshots of the UI:

![Landing Page - Header]({{site.baseurl}}/assets/images/linkblog/01_landing-page_header.png)

Landing Page - Header

![Landing Page - Description]({{site.baseurl}}/assets/images/linkblog/02_landing-page_description.png)

Landing Page - Description

![Landing Page - Features]({{site.baseurl}}/assets/images/linkblog/03_landing-page_features.png)

Landing Page - Features

![Landing Page Latest News]({{site.baseurl}}/assets/images/linkblog/04_landing-page_latest-news.png)

Landing Page Latest News

![User Linkblog Page]({{site.baseurl}}/assets/images/linkblog/05_user-linkblog-page.png)

User Linkblog Page

![User Post Message Page]({{site.baseurl}}/assets/images/linkblog/06_user-post-message-page.png)

User Post Message Page

![User Archives Page]({{site.baseurl}}/assets/images/linkblog/07_user_archives_page.png)

User Archives Page

![User Search Page]({{site.baseurl}}/assets/images/linkblog/08_user_search_page.png)

User Search Page

![User Edit Mode Page]({{site.baseurl}}/assets/images/linkblog/09_user-edit-mode-page.png)

User Edit Mode Page

![FAQ Page]({{site.baseurl}}/assets/images/linkblog/10_faq-page.png)

FAQ Page

![User Billing Page - Fresh Load]({{site.baseurl}}/assets/images/linkblog/11_user-billing-page_fresh-load.png)

User Billing Page - Fresh Load

![User Billing Page - Add or Update Card Extended]({{site.baseurl}}/assets/images/linkblog/12_user_billing-page_addorupdate-card-extended.png)

User Billing Page - Add or Update Card Extended

![User Profile Page]({{site.baseurl}}/assets/images/linkblog/13_user-profile-page.png)

User Profile Page

![User RSS Feed]({{site.baseurl}}/assets/images/linkblog/14_user-rss-feed.png)

User RSS Feed

That was linkblog.io!
