---
published: true
layout: post
title: Minimal Setup for Blogging with Jekyll
date: 2015-10-25T11:40:00.000Z
categories: jekyll
---



This initial post is to document how to configure the base [Jekyll](http://jekyllrb.com/) installation so that it's ready for blogging, with posts displaying on the main page, an archives page that lists all the posts, an about page for a personal description and social media info in the footer.

![Jekyll customized for blogging]({{site.baseurl}}/assets/images/customized-jekyll-for-blogging.png)


The actual Jekyll installation is covered in the [docs](http://jekyllrb.com/docs/quickstart/). It's pretty straight forward. Setting up free hosting with Github is covered [here](https://help.github.com/articles/using-jekyll-with-pages/).

For details of the modifications I made to the vanilla install have a look through the commits in the Github repo up to [this commit](https://github.com/mjgs/mjgs.github.io/commit/adf2a56ddf5427029ae0c65fe300e6e2a4366117).

![Jekyll new install git commits]({{site.baseurl}}/assets/images/github-jekyll-new-install-commits.png)

I'm using [Prose.io](http://prose.io/) to edit posts in my web browser. Prose knows about Jekyll so you can create drafts and publish posts, it's also [open source](https://github.com/prose/prose).