---
title: Self-hosted web based tool to get tasks done efficiently
published: true
layout: post
date: 2020-11-02 15:40:00:00 +0700
tags:
- github
- productivity
- agile
- nodejs
---
A short while ago I was wanting to have a self-hosted tool to manage sets of tasks in an efficient way, so that tasks actually get done. I wanted it to be simple enough not to require much maintenance, with minimal chances of something breaking because of software upgrades. 

I built a simple statically generated web based tool that is based on the [agile software development](https://www.atlassian.com/agile) methodology, which uses a “backlog” of “stories” that you complete during time periods called “sprints” (usually 2 weeks long).

Another key idea is that writing things down is a great way to focus on the task at hand and a way to drive your way as you forge your path.

It uses the [Eleventy](https://www.11ty.dev) static site generator to render all the pages. 

Here is the [Github repo](https://github.com/mjgs/eleventy-agile-blog) and there is a [demo site](https://festive-haibt-b7ead0.netlify.app) with a bit of example data.

How does it work? 

From the repo docs:

> Use blog posts to describe your work, what you did, what you are about to do, then create "stories" that you add to the "backlog". Assign stories to "sprints", these last 1 week. Flesh out the stories, implement them, and then move these to "done" when you complete them.
>
>At the end of the week do a retrospective of what you did, and plan (i.e. create and assign stories to the next sprint) for the upcomming week.
>
>Whenever you are a bit unsure of your path, read the above 2 paragraphs. You probably need to write a blog post.

Benefits:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Self hosted - run it in the cloud or just locally on you machine
- Everything is a file, versioned using git
- Create items written in [markdown](https://www.markdownguide.org/basic-syntax)
- Easily backup your repo using one of the many git hosting providers
- Never have a migration problem, it’s all just text files
- Works offline
{: refdef}

This is aimed at personal use rather than for large projects. I think for big projects, especially where you are collaborating with others, it’s probably better to use more comprehensive tools.
