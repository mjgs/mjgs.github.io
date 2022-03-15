---
title: "Offline Pull Requests"
description: Some thoughts on Pull Requests, which become very central to modern development
published: true
layout: post
date: 2022-03-15 08:41:00:00 +0700
tags:
- programming
- workflows
--- 
Aside from being a phenomenal version control tool, git’s ability to work offline is one of it’s best features. This is especially true if you move around a lot, but even if you don’t, sometimes you just need to disconnect from the network, avoid distractions from things like social media and email, and do some heads down focussed development.

Once you’ve made some progress, it’s trivial to sync back up with the repository remotes. Pull in the changes since you were last online, merge with your code, resolve any conflicts, and push your changes back up to the remote. This is possible because when you clone a repository, you have an entire copy of the repository on your local machine.

This way of working is standard with the command line git tool. It’s how it was designed to work. Each developer has a complete copy and can work entirely independently. This worked really well for many open source projects, but as git hosting platforms emerged, they added new features. One of the most praised has been the [Pull Request (PR)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests). It’s become so central to modern development, that most developer workflows in some way revolve around them.

They are essentially a way to co-ordinate ongoing feature work. They take the form of a web page that has a discussion thread where contributors can talk about the changes they are making to the code. They make many code commits to a feature branch on their local machine, push those commits to the remote, and at some stage a PR is created. Discussions then happen, more code commits can be added, and when the feature is deemed to be complete, it can be merged into the main branch and the PR is closed. At that point all the commits that were pushed to the feature branch will be in the main branch.

The PR has become more that just a discussion area. Many integrations with 3rd party tools enable running of test suites, with results displayed in the PR page along side discussions. There are other neat features like bots that can scan code, and post results to the discussion, code reviews, analysis of comments to see mentions of other PRs, and for example to trigger workflows. The automation features can help speed up development, and maintenance of the project. Overtime PRs become a key place where knowledge about how the code was developed is stored. It’s very usual to spend some time browsing through closed PRs to get a sense for how things are moving along, or how a particular bug was fixed. The PR has been very much a successful feature and has been adopted by most git hosting services.

It’s not to say that PRs don’t have their downsides. Some of these were highlighted in a [recent episode of the Changelog podcast](https://changelog.com/podcast/483)(~20:00). They speak about many of the pros and cons. It’s an interesting discussion. There has also been a “PRs are bad” meme making the rounds the past few weeks (but I can’t find it right now), and much has been written about [the pain of PRs](https://infrastructure-as-code.com/book/2021/01/02/pull-requests.html). We love PRs, but some of us, at times, find them an impediment to progress.

In my personal work I often want to be able to work entirely offline, but I miss the ability to write notes as I develop a feature. There isn’t much point in using PRs since they aren’t accessible offline. PRs are entirely provided by the platform, standard git has no such feature. Making PRs available offline would be an incredible feature, but it probably doesn’t make that much sense, because the threaded discussions would get all out of sync. I’d be happy to be proved wrong on this though.

Offline PRs would make moving between providers feasible. If you have ever tried to do that you’ll know that it’s not at all straight forward. Moving the repo is easy, moving the PRs and all the accumulated knowledge within them, not at all easy.

However with PRs acting more and more as a place to combine the results of many tools, I wonder if there couldn’t be some form of independent notes that couldn’t be written offline that could then be automatically attached to a PR along with the pushed code commits.

If I were developing git based tools, enhancing the offline experience would be something I would spend some time on. Working async is becoming the norm for remote teams, and though it’s great to work together and essential at times, the ability to drop off and work offline is something that is very important in order to be able to keep a healthy work/life balance, but also so that when you do get together with the team, that time is even more beneficial because you’ve been able to make much progress offline, without all stepping on each other’s toes.