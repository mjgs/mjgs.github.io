---
title: Looking back at linkblog.io
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

{:refdef: style="text-align:center;margin-top:50px;"}
![Landing Page - Header]({{site.baseurl}}/assets/images/linkblog/01_landing-page_header.png)
Landing Page - Header
{: refdef}

That was linkblog.io!
