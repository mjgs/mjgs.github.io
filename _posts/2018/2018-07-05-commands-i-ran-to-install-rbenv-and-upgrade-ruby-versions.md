---
title: Commands I ran to install rbenv and upgrade ruby versions
published: true
layout: post
date: '2018-07-05 18:03:58 +0700'
tags:
- ruby
- programming
---

I was able to upgrade ruby versions. These are the commands I had to run. I will spare you the error messages and detours.

{% highlight bash %}
~ $ ruby -v
ruby 2.3.0p0 (2015-12-25 revision 53290) [x86_64-darwin14]

# Commands to install rbenv and latest ruby
brew doctor
brew update
brew install rbenv
echo export PATH=$HOME/.rbenv/shims:$PATH >> $HOME/.bashrc
brew upgrade ruby-build
rbenv install --list
rbenv install 2.5.1
echo 2.5.1 > ~/.rbenv/version
rbenv rehash
rbenv versions
gem env
gem install bundler

~ $ ruby -v
ruby 2.5.1p57 (2018-03-29 revision 63029) [x86_64-darwin15]

# Re-install the gems in the blog installation directory
bundle install
bundle show jekyll
bundle exec jekyll serve
{% endhighlight %}

These are essentially the commands I ran, roughly in that order but it got a bit confusing somewhere in the middle. 

I decided not to run `rbenv init`, the only [mandatory thing](https://github.com/rbenv/rbenv#how-rbenv-hooks-into-your-shell) it does is add the shims folder to the PATH. So I just did that myself.
