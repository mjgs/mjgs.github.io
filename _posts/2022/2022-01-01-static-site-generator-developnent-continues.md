---
title: "Static site generator development continues..."
description: Some notes about the next phase of development of the static site generator I'm using to build my linkblog
published: true
layout: post
date: 2022-01-01 14:00:00:00 +0700
tags:
- blogging
- web development
- linkblogging
- programming
---
Here are the notes I [mentioned in my previous post]({{ site.baseurl }}/2022/01/01/2022-01-01-static-site-generator-developnent-continues.html). You’ll get some idea of what I’ve been up to in my personal development projects, even if it’s not a nicely crafted piece, I’ve made some progress on my static site generator, and I wanted to blog about it. Still blogging… :)

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Initial version which I wrote as a sort of life raft when the [linkblog.io ship was sinking]({{ site.baseurl }}/2020/11/25/2020-11-25-linkblogdotio-is-dead-long-live-linkblogging.html)
- Jamstack, serverless, Netlify, Github Actions, CI/CD, and git repo powered development were all becoming super popular
- It’s running my current linkblog, it works, it’s all running in the cloud, quite awesome 
- But...the code is kind of fragile
  - quite a lot of duck tape
  - the structure of the code is convoluted in places
  - lots of callback hell
  - hey async/await was new when I wrote it and I hadn’t gotten comfortable with it yet
- It uses plain javascript objects rather than classes, which is mostly fine, but I’ve seen quite a few implementations of tools that use classes
  - it’s much clearer to me now how to think about and mentally manipulate such concepts
  - there’s a lot of flexibility and structural benefits when you have the right abstractions
  - you can more easily get out of the weeds in some places
  - You can more easily build something that can be refactored to suit your current needs
- Classes do present a new set of challenges though, but on balance, I feel like they are the right structure to be using a lot of the time
- I wrote an initial version back before the big lockdown happened, I had been thinking about it for a while and was able to get something working over a few days
- The main ideas were
  - Just render templates, stick to EJS and Markdown, keep it simple
  - Path base page routing
  - Maybe rendering websites using templates could be similarish to how a render farm operates, something I have a lot of experience from [my time in the featute film visual effects (VFX) industry]({{ site.baseurl }}/2020/11/24/2020-11-24-what-its-like-working-in-tech-in-the-visual-effects-industry.html)
  - I had been reading a lot about various more formal data structures, and it was clear to me that a queue would be beneficial to handle all the template rendering 
  - Just get something working that runs locally, but maybe if the architecture was done right it would be easy to get things working in a serverless environment later
  - Initial specific requirements for phase 1 - Implemented these crucial examples very early, and so can easily check that structural changes don’t break these
    - EJS using data files
    - EJS with includes 
    - Markdown
  - Phase 2 implemented after the big lockdown, once again I’d been thinking about the best structure for many weeks and was able to get these changes made over 3-4 days
  - A set of core components have emerged that feel really nice, a structurally sound way to render templates, with possibility to extend functionality
  - Things I have in the back of my mind
    - How to handle config
    - How to handle more advanced template rendering, for instance how to render many different output pages from a single template, with some kind of iteration logic, necessary for rendering the linkblog calendar folder structure
    - Concentrate on EJS, but try to architect a solution where different ways of rendering templates could be accommodated in future, at least try to go in that vague direction even if it’s not a completely working multi-rendering solution at first 
    - Create the right abstractions so that changing template rendering input and output locations is trivial (i.e. local file system, S3 like cloud storage etc)
- Inspiration
  - Jekyll - the ssg I currently use for my blog
  - Eleventy - awesome ssg that uses classes in a really nice way, great community
  - Pixar’s Renderman - the standard for running large scale render farms in the VFX industry
  - Render farms - [memories I have of my time working with VFX render farms, mostly sysadmin/devops stuff, but also some of software development
  - Serverless and Jamstack the shiney future at the end of the tunnel
  - Wordpress, & open source
- Open source
  - Something I’ve wanted to do for many many years
  - There’s been a lot of Linux in all my previous jobs, I feel like I’ve been living and breathing in open source in one way or another all throughout my career
  - But I must mention though that the closer I get to having something that I feel is good enough to ship, the more ham strung and hands tied behind my back the world around me has me feeling, not so great considering the whole point of open source
  - Which license to choose, MIT, GPL or Apache, or something else
  - How to handle the competing, often contradictory aspects of the intersection between developing software in the open, and having a balanced personal life
- Somewhat esoteric, feels like I should mention, without dwelling on them for too long at this point in time 
  - Why does it feel like the choice of open source license somehow impacts the freedoms I experience in my personal life?
  - Why does it always feel like right after I do one of these 3-4 days development sprints on a personal project, that I get absolutely clobbered by the world around me? It’s like clockwork, happens every single time, I’m not particularly religious, but is this the metaverse of the future, appearing in the present? Seriously, it really worries me, and especially that it’s impossible to talk about without sounding like you’ve lost your marbles
- The try to stay alive cascade
    1. survival
    2. self-preservation
    3. try not to negatively affect others
{: refdef}