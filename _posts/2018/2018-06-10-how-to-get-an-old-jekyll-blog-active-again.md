---
title: How to get an old jekyll blog active again
published: true
layout: post
date: '2018-06-10 17:27:00 +0700'
tags:
- blogging
- static site generators
- jamstack
---

It was actually pretty straight forward. Check that the git remote is still configured, install the jekyll software, follow the instructions in the error messages. I had the dev version of the site back up within a few minutes.

{% highlight bash %}
$ cd $WEBSITES_DIR/blog.markjgsmith.com
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
$ cat .git/config | grep -A 2 remote\ \"origin\"
[remote "origin"]
	url = https://github.com/mjgs/mjgs.github.io.git
	fetch = +refs/heads/*:refs/remotes/origin/*
$ which jekyl
$ gem install jekyll bundler
$ bundle exec jekyll serve
Could not find RedCloth-4.2.9 in any of the sources
Run `bundle install` to install missing gems.
$ bundle install
$ bundle exec jekyll serve
Configuration file: [WEBSITES_DIR]/blog.markjgsmith.com/_config.yml
No post given to analyze. Try with -h
            Source: [WEBSITES_DIR]/blog.markjgsmith.com
       Destination: [WEBSITES_DIR]/blog.markjgsmith.com/_site
      Generating...
                    done.
 Auto-regeneration: enabled for '[WEBSITES_DIR]/blog.markjgsmith.com'
Configuration file: [WEBSITES_DIR]/blog.markjgsmith.com/_config.yml
    Server address: http://0.0.0.0:4000/
  Server running... press ctrl-c to stop.
{% endhighlight %}

I'm still a little fuzy on how to add posts. I tried to login to prose.io but the site wanted full access to all my repos on Github...a little excessive. Oh well editing in vim is good enough.

Last but not least push the changes to github...

{% highlight bash %}
git add *
git commit -m "New post: How to get an old jekyll blog active again"
git push
{% endhighlight %}