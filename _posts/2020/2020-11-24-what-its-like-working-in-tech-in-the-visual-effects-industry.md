---
title: What it’s like working in tech in the visual effects industry
published: true
layout: post
date: 2020-11-24 16:25:00:00 +0700
tags:
- vfx
- programming
- tech
- jobs
- automation
- workflow
---
I’ve built and supported many workflows for visual effects productions on big blockbuster movies. 

Movies such as

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- [Mirrormask](https://m.imdb.com/title/tt0366780/?ref_=fn_al_tt_0)
- [Are we there yet?](https://m.imdb.com/title/tt0368578/?ref_=fn_al_tt_0)
- [Charlie and the Chocolate Factory](https://m.imdb.com/title/tt0367594/?ref_=fn_al_tt_0)
- [Children of Men](https://m.imdb.com/title/tt0206634/?ref_=fn_al_tt_0)
- [Harry Potter and the Goblet of Fire](https://m.imdb.com/title/tt0330373/?ref_=m_ttls_tt_4)
- [The Golden Compass](https://m.imdb.com/title/tt0385752/?ref_=fn_al_tt_1)
{: refdef}

And hundreds more like those, working alongside digital artists and producers to build novel ways of collaborating. It’s been a few years now, I’ve since moved into enterprise software and now web development, but I thought it would be interesting to write a piece about my experiences in the visual effects (vfx) industry.

The landscape of the vfx industry is made up of a wide variety of companies, big and small, that work together to perform the post production on motion pictures. Ultimately they have the same goal - get the film finished on time for a theatrical release. There are often big budgets involved, and lots and lots of people doing a huge variety of jobs. 

If you’re curious about how things are structured watch the credits of any film right until the very end. You can figure out a lot just from how the names are grouped together. Usually it’s the actors first then production staff, then all the post-production staff. But there’s a lot of nuance, with people being divided up into units based around certain pieces of the movie, say if it was filmed in different main locations. 

It’s often surprising how many different visual effects companies are listed, each with their own teams of artists, engineers and producers. Of course animation based movies like the stuff that Pixar makes are nearly all post-production people, also huge amounts of post staff for all the superhero movies, but often films that don’t appear to have many visual effects shots, actually have loads of them.

The film credits of a movie is an art form in itself, with companies specialising in creating both the front and end rollers. If you stay right until the end of the credits in a movie theatre, a lot of the people remaining at the end, work in post. They want to see how things are structured at other companies, but they also just want to see their names or the names of their friends appear on the big screen. It’s quite a big thrill to see your name rise up across the screen when you’ve spent many months working on something.

I’ve worked in two different areas of the overall post-production movie pipeline. 

First was as part of the engineering team in a reasonably classic vfx house, where we would work on a handful of movies in parallel, typically working on lots of individual shots, adding effects, then delivering these to companies upstream, who assemble all the vfx shots with the regular shots to create the full length movie. The work tended to happen right after production, or in some cases, at the same time as the movie is being filmed. There were often long days, and weekends, with some people working night shifts. These projects felt big, taking many months, with great wrap parties on completion. They also had a whole department that built old school physical visual effects, robotic monsters and weird creatures. Very cool but a bit scary when you are on the night shift.

There was a rather big render farm to render the effects onto the images. Hundreds of pizza box style nodes in racks, all managed by [Pixar’s Renderman](https://renderman.pixar.com/product) software. Organising the farm in an optimum way was complicated by the fact that 2D and 3D artists had very different types of jobs running. The 2D jobs were generally rather quick taking minutes, whereas some 3D jobs could take hours. You never wanted the 3D jobs clogging up the farm, but you also didn’t want the farm to be empty, and of course everyone’s job is very important. After a long time analysing the software and use cases we came up with a pretty effective configuration for the system.

There was a heavy focus towards Linux based systems, because it was easier to create multi-machine complex workflows using scripts written mostly in shell (bash/csh/tcsh) and Python. We would setup artists machines using shell environments in a neat way that enabled them to quickly switch between projects, with shot information pulled from a database, so they didn’t have to think about where the data was being stored, that was all automatic as long as they knew which shot they were working on, and everything was versioned. There were lots of cli system tools that for example did things with long sequences of image files.

For quite lot of the time I was there we had free toast, jams, Nutella, tea and coffee. That was nice. There was also a table football table and we held a yearly World Cup style competition, engineers vs 2D artists vs 3D artist. Good times.

The second vfx shop I worked for was further downstream, I was also part of the engineering team, receiving the finished shots from all the classic vfx houses. The work happened right at the start of post-production with film scanning and then right at the very end, after all the vfx shots had been completed by the classic vfx shops. We received all the shots and did various tasks such as colour correction, colour grading, beginning and end rollers, language versioning, subtitling, recording back to film, and creation of digital cinema distribution masters. The film scanning / recording and colour management tasks are often referred to as digital intermediate (DI), with the correction and grading being done by artists working with the directors and producers in specially constructed completely blacked out theatres.

We often had to meet impossible deadlines compounded by the fact that we were right at the end of the post-production process, impacted by any delays that happened at the other vfx houses. Missing our deadlines was just not an option, the penalties for which were in the order of millions of dollars per day, since the release date of the film would have to be moved.

This happened quite a lot:

>Boss: How long will X take to do?
>
>Engineers: 3 months
>
>Boss: Ok we need you to do it in 3 weeks

Amazingly we always figured out a  way to meet the impossible deadlines.

In this second place there was a much bigger volume of films passing through and typically the work on each film was on the order of weeks, the parties were mostly just for the producers interacting directly with the clients.

I mention the parties because I think it helps to illustrate that the overall vibe at different vfx shops can be very different depending on the type of work that is done. One isn’t necessarily better or worse, it’s just different. In broadcast media, where I’ve also had some experience, it’s yet another kind of different, more corporate in a way.

As far as tech goes there was a lot of cool hardware. Super specialist colour management boxes with unbelievably fast [infiniband](https://en.m.wikipedia.org/wiki/InfiniBand) network connected storage, amazing 2D & 3D projectors, top of the line audio setups. The DI part of the facility could be hired out directly to clients, but our in-house artists also used it for the jobs we were working on.

Finished feature films took up terabytes (12TB for a full length 4k resolution film) of storage space, and the artists often worked on multiple versions of shots. Lots and lots of storage. Anytime new storage was added it got gobbled up pretty quickly. Problems with the storage had a big impact and cost a lot of money because no one could work. Stressful at times but generally there was a good camaraderie between everyone.

When I was there much of the movement of finished shots was done via USB drives, we had hundreds of them moving around town at any one time. I bet they still use drives quite a bit. Very manual but effective. You do what’s necessary to get the job done. I’ve been in situations where we had to send someone transatlantic on a plane just to hand carry some drives.

These days a lot of the finished shots are moved between companies digitally. There are high bandwidth networks between a lot of the post facilities. At the time, we were already experimenting with some very involved transatlantic workflows on some big films.where the director was in LA and the colourist was where we were in London. Making sure that the colour science equipment in both grading theatres was setup correctly was crucial. It was also quite fun because we got to work with the US team that was flown in for the duration of the project.

The film scanners which were about the size of two fridges side by side, were able to scan reels of film at around 8 frames per second, and they had a suite of Perl scripts used for automating the post processing of the all images created, so you could trigger custom scripts to process the scanned images on the render farm or other specialised hardware. Some of the reels of film would come in quite badly scratched, so we setup workflows to automatically digitally remove the scratches using specialised software. The only other way was to do it by hand frame by frame. The render farm there was smaller and ran on very fast blade servers. It was managed by a piece of software called [Rush](http://seriss.com/rush) which is written in Perl.

There was always lots of things happening in parallel, so it was a little tricky not to step on each other’s toes. We were all trying to do this complex thing of creating digital effects all at the same time as constantly rebuilding and upgrading everything around us. If you went away on holiday it was quite usual for your desk to have moved by the time you got back. There were lots of emergencies, the business people were always trying to land new contracts with important clients visiting to see the latest version of their project, a sort of organised chaos. But we sure did make a lot of films.

The other thing that was happening at the time I was there, on top of the general day to day internal tech chaos, was that the whole wider industry was freaking out about the introduction of digital cinema. Every part of the ecosystem was being written and re-written all at the same time.

Was it cool? Yeah it was pretty cool. 

I gained a solid foundation in using cool technologies, building infrastructure and workflows, figuring out new ways of collaborating, streamlining existing processes using both off-the-shelf / open source tools, and writing our own when necessary.
