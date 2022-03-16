---
title: What it’s like working for an enterprise software startup
description: I look back at some of my experiences working for an enterprise software startup, both in the global operations team working in technical roles alongside sales executives, and as a developer in the an agile software engineering team building an enterprise grade SaaS
published: true
layout: post
date: 2020-11-30 08:00:00:00 +0700
tags:
- web development
- programming
- automation
- workflows
- services
- travel
---
I wrote recently about my time [working in the VFX industry](https://blog.markjgsmith.com/2020/11/24/what-its-like-working-in-tech-in-the-visual-effects-industry.html ) during the height of the analogue to digital transition. I wanted to write another similar piece remembering my time working for an enterprise software startup in the file delivery space, so that I have something to refer to in future, but also because it might be useful to others to get a picture of what it’s like working in an enterprise software company startup.

First I worked as a Technical Consultant, and then as a Solutions Architect as part of the Global Operations team. I then joined the engineering team as a Software Developer, contributing to the development of a hybrid cloud file delivery SaaS. Having worked with many software vendors as a client in my time working for visual effects companies, it was eye opening being on the other side of the fence, with the folks building, marketing and selling vendor software.

When I joined they had a head office in Boston (US) and the engineering team in Ottawa, (Canada). Europe, Middle East & Africa (EMEA) was a new region for them, so there was no office. I worked from home in London (UK), or onsite at client locations, everything was done remotely. Initially we had to build the customer base, so there was a lot of travel throughout the EMEA region. There were times where I was travelling to several different countries every other week. I got a taste for being on the road and I liked it.

The company was pivoting from making source code replication software, to more generalised file movement software and they were focusing on the Media & Entertainment sector because the analogue to digital conversion was resulting in a need to move very large files. I was brought in to help grow the EMEA region and I worked closely with the regional Sales Director and Sales Engineer, meeting with clients, doing technical pre-sales, and later post-sales integration work, architecting and implementing a variety of media workflows.

I met with people from all levels, from engineers, developers, producers, journalists, managing directors, CEOs, CTOs to name a few. This was within visual effects companies but also broadcasters, channel aggregators, playout centres, network carriers, news organisations, radio stations, advertising agencies, system integrators, other software vendors, cloud providers, and occasionally clients in other sectors like oil and gas and automotive. Having exposure to a much wider section of the media landscape was incredibly interesting. I learnt first hand how these companies moved and transformed files, how they structured their organisations so that people could collaborate effectively, and the challenges  they faced in moving to digital.

Another side that was super interesting was working closely with sales and marketing. 

We had weekly sales calls at the end of the week, everyone in Global Ops would dial into the conference call no matter where we were. This was mostly the sales reps sharing how we were getting on with prospects, if they were on target to hit their number for the quarter, as well as any roadblocks they were up against. Occasionally the Technical Consultants / Solution Architects would be called upon. Us techies also had our own separate weekly conference call for more involved technical discussions. Although there was some competition between regions, we all collaborated together really effectively because we all wanted the entire company to do well.

At the time it blew my mind that we were all separately moving around while dialled into the sales call on our Blackberrys (and later iPhones). People transiting between clients in cabs, waiting for planes in airports, snacking in hotel lounges, zipping around on trains, or just in their home office, all across the globe, every continent. The first few years our phone bills were pretty insane.

The language in sales and marketing focussed companies is completely different to what I had experienced before. Everything revolves around the year being divided up into quarters, with Q1 starting in beginning of January and Q4 finishing end of December. It makes it easier to talk quickly about approximate timelines.

There are a lot of 3 letter acronyms, POCs (proof of concept), SOWs (statement of work), NDAs (non-disclosure agreements), RFPs (Request for proposal), QBRs (quarterly business review), ROI (return on investment), and many more.  They make communication more efficient. The other thing there was a lot of was conferences, attending IBC in Amsterdam and BVE in London every year, hosting a booth where we did demos and presentations throughout the day.

As can be expected, there was a big focus on numbers, on your team hitting it’s quarterly quotas, with extensive use of [Salesforce](https://en.m.wikipedia.org/wiki/Salesforce) to track and forecast the sales process. It was noticeable to me the motivating effect of having a commission component to my compensation package. 

I was often really impressed with how very complex customer relationships were navigated, with creative ways to move the sales process along, and the formation of strategic partnerships with people and companies with whom we had synergies. It was enlightening to see how much effort was put into pricing, and into relaying customer feedback to the product and engineering teams, and then to later see changes in the product that had been added in response.

As the EMEA region customer base grew, there was a lot more post-sales integration work. This is where I would work closely with the customer to architect the deployment of the software they had purchased. There was a lot of variety but generally they wanted a robust, secure and highly available infrastructure, and they often wanted to integrate our file movement software with their existing internal systems. 

I wrote custom components in Perl that connected our software to existing systems using APIs or hot folder + XML file integrations. I then used these and pre-existing components in the product's workflow engine to build multi step workflows to automate the processing of inbound and outbound files, sending them to 3rd party tools or to operators and digital artists for manual steps. Sometimes replacing old manual workflows, other times creating entirely new workflows that had never existed or been possible before. I would then install the software and custom workflows, test everything was working, get the customer to sign-off on the deployment and train the users on how to use the system.

These were some of the workflows I designed and/or built:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- ProsiebenSat – Ingest via Mx/Agent/Smartjog/Ftp, automated validation then manual validation, checking into MAM, export via Mx/Agent/Smartjog/Ftp
- Canal Plus - Ingest via FTP Pull/MX, media check, Agility transcoding, import into Sonaps and Avid editors
- Chellomedia - Ingest via Agent, movement of file bundles, Antivirus check, splitting of bundle on arrive in Lan, delivery of each piece to the right place
- TPC – Swiss Television - Avid export, transcoding, Sound recording, manual steps offered via Mx GUI, delivery to Playout
- Media City UK - Avid Gateway - easy ingest and outgest of avid projects
- Discovery UK - VOD preparation with automatic adding of bumpers, logos and subtitles, and automated quality assurance check
{: refdef}

It was at times very chaotic. I remember completing a pre-sales demo workflow that used AWS SQS to receive files in the back of the taxi on the way to the client demo. I got it working on my laptop over 3G just as we pulled into the carpark. The live demo worked without a hitch. The total number of hours worked per week was very high, it was difficult to separate work and personal life, and the constant travel, though fun, did start to take it's toll on me after several years.

Overtime we introduced processes, training programs, new staff, we started using a concierge to organise our travel and hotel bookings, we built cloud infrastructure to host many concurrent client POCs on VMs. Things got very streamlined and we were bringing in about a 1/3 of the company revenue.

I then moved over to Ottawa and joined the engineering team as a Software Developer, working on the team that was building a new SaaS file movement product. It was a nice change of pace to have an office again, and to be on a team of developers. 

We followed an agile software development methodology, working on features in 2 week sprints, with daily standups, spikes, retrospectives and sprint planning. I worked closely with QA engineers and devops to ensure the features were thoroughly tested and deployed without issues, and with the support team to identify and fix bugs. The team was very well organised, and we shipped a lot of features. The product was adopted rapidly with the user base growing to 400000 users, made up of both existing and new clients. During that period I learned a lot about web development, it was a fantastic experience.

Aside from the occasional merge conflict, things ran pretty smoothly, there weren’t that many emergencies. We had weekly meetings where all the teams across engineering shared what they were working on. It was fascinating to be a part of the development process of enterprise grade software. It was a great foundation in developing web based software as part of an agile team.

I also experienced what it’s like to live in a very cold climate, with winter temperatures often down to -20 Celsius, having to use special snow tires, and learn how to drive in snow storms and ice rain. We had a team outing to go ice skating on a nearby lake, that was a lot of fun. I went over the provincial border to Quebec, met and spoke with french Canadians. They have a very different accent to people from France. I got to go snowboarding quite a bit and can now board pretty well in either direction.
