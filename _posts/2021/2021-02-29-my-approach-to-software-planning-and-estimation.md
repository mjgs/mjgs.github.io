---
title: "My approach to software planning and estimation"
description: A brief description of how I approach project planning and estimation, with some useful articles and resources.
published: true
layout: post
date: 2021-02-29 12:22:00:00 +0700
tags:
- web development
- services
- programming
---
## Introduction

While there isn’t a single approach that works for all projects, doing some planning and estimation goes a long way to increasing the chances of a successful project. I wanted to give my general approach and share some useful resources on the subject.

For smaller projects, a high level overview and a few diagrams might suffice, but for longer projects with more unknowns, it’s important to take more time, filling out a more detailed plan before commencing. At the same time you want to avoid getting stuck in endless details or a plan that isn’t flexible to changing conditions.

Identifying problematic areas, and finding an appropriate balance between planning and implementation is key, with good communication between the people involved in the project.

## Create a high level system design

- Overview
- Project parts
- Architecture
- Issues / items that need to be discussed and solved

See the Facebook architecture planning videos for some good examples of high level system design:

[Top Facebook System Design Interview Questions (Part 1)](https://hackernoon.com/a-look-at-the-top-questions-for-a-system-design-interview-at-facebook-va15311j)

[Top Facebook System Design Interview Questions (Part 2)](https://www.indiehackers.com/post/top-facebook-system-design-interview-questions-part-2-3409d78139)

## Create a sprint plan 

General approach is agile scrum methodology. Break down the project parts into subtasks (called stories), add time to each, gather all these into a backlog. These will be completed during time blocks called sprints, which last a set amount of time (typically 1 or 2 weeks). 

During sprint planning assign stories to be completed in each sprint:

- high level sprint planning for several months at a time, and
- more detailed sprint plan each week for the next sprint

Take each project part

- Create stories
- Add story estimates
    - amount
    - confidence
    - measured
    - accuracy 
- Add stories to backlog
- Total all the estimate amounts
- Update measured & accuracy throughout project

Project planning article goes into a lot of depth in this subject.

[Definite guide to estimating software projects](https://maximzubarev.com/estimating-software-definite-guide)

## Useful tools

There are lots of great agile development tools available, many of which have excellent collaboration features. You should probably use the best available at the time your project is happening.

Planning is such an important aspect of web development that I have build an agile blog tool that you can use just in case there’s nothing else available.

It’s open source, uses text files as storage, very unlikely to break, and will enable you to manage a backlog of tasks.

http://blog.markjgsmith.com/portfolio/#eleventy-agile-blog
