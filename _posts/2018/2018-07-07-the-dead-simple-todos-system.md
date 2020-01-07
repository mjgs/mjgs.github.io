---
title: The dead simple todos system
published: true
layout: post
date: '2018-07-07 20:51:06 +0700'
tags:
- todos
- scripting
- shell
- bash
---

Over the years I've tried a variety of sofware solutions to todo lists but I always find that eventually I end up just opening a empty file and typing a text list. It's just so straight forward. Almost as if writing a list in a notebook, which of course is the ultimate todo list solution.

Anyhow I've been adding quite a lot of aliases to my dotfiles recently and I wondered if I could add just a few that would make the bare essentials of a todo list system. These are the aliases that I came up with:

{% highlight bash %}
alias 'slugd=date +%Y-%m-%d'
alias 'todos=cd $TODOS_DIR'
alias 'tdf=echo $TODOS_DIR/$(ls $TODOS_DIR | tail -n 1)'
alias 'tdt=echo $TODOS_DIR/$(slugd).txt'
alias 'tde=e $(tdf)'
alias 'tdd=echo "### $(date "+%A %d %B, %Y") ###"'
alias 'tda=cat $(tdf); echo'
alias 'tdc=cat $(tdf) | grep "[x]"'
alias 'tdi=cat $(tdf) | grep "\[ ]"'
alias 'tdn=TODOS=$(tdi); ! test -f $(tdt) && tdd > $TODOS_DIR/$(slugd).txt && echo >> $(tdf) && echo "$TODOS" >> $(tdf) && tda'
{% endhighlight %}

It's all very standard shell scripting, the aliases get loaded from `.bash_aliases` or similar. The only complicated one is `tdn` which only creates the new todos file if one doesn't already exist for the current day to avoid accidentally overwritting an existing list.

{:refdef: style="list-style-type:none; margin-bottom: 14px;"}
- slugd - create slug using date
- todos - fast navigation to $TODO_DIR
- tdf   - (file) prints latest existing todo file path
- tdt   - (today) prints file path using todays date
- tde   - (edit) opens latest todo file in editor
- tdd   - (date) prints todays date nicely formated
- tda   - (all) prints all todos from latest todo file
- tdc   - (complete) prints all completed todos from latest todo file
- tdi   - (incomplete) prints all incomplete todos from latest todo file
- tdn   - (new) new todo file extracting all incomplete from previous
{: refdef}

In practive the only aliases you actually use are `tdn`, `tda` and `tde`. 
That's it just 3 aliases to remember and it's pretty close to using a notebook. The only configuration necessary is to set `TODOS_DIR` environment variable somewhere that gets loaded by the shell automically like your shell's `.bashrc` file.

Here is what a todo list file looks like:

{% highlight bash %}
~ $ tda
### Saturday 07 July, 2018 ###

[ ] Install new theme on blog
[ ] Deploy live keys to payments pages
[ ] Troubleshoot failed mail deliveries
[ ] Add links to freelancer github repo on payment pages
[x] Troubleshoot github remotes issue on markjgsmith.com
[x] Troubleshoot freelancer left pane image centering issue
[ ] Re-organise dotfiles and dotfiles local
[x] Add todo aliases to dotfiles
[ ] New blog post: The dead simple todos system

~ $
{% endhighlight %}

The real test of course is tomorrow morning when I create a new todo list.