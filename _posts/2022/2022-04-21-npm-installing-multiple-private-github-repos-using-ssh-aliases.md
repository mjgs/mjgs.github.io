---
title: "Npm installing multiple private Github repos using ssh aliases"
description: "How to npm install multiple private Github repos from within a Github Action"
published: true
layout: post
date: 2022-04-21 17:10:00:00 +0700
tags:
- blogging
- programming
---
When you are developing in NodeJS it’s often useful to be able to install private modules. 

The main ways to do that are:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
1. Github Packages using Personal Access Token (PAT)
2. Private Github repo using Personal Access Token (PAT)
3. Private Github repo using Deploy Keys
{: refdef}

Apparently (1) is the most popular among developers, however it requires setup and management of additional workflows to create the Github Package.

(2) Only works for a maximum of 1 private repo.

(3) Works for 1 private repo, and can be extended using ssh aliases to work with multiple private repos. 

Deploy keys are also more granular in terms of security than PAT.

This article focuses on method (3).

Github has an [example repo](https://github.com/jcansdale-test/consume-private-npm-package) that demonstrates how to install a private repo using deploy keys. It’s worth testing that out.

If you try the same methodology for installing more than 1 private repo in the same workflow, you’ll run into an issue. The reason being that Github doesn’t allow you to re-use the same deploy key across repos, and by default npm will use the default ssh private key (~/.ssh/idrsa), of which there is only one.

However if you configure ssh to use aliases, you can specify a different private key for each alias, and then use those aliases in your package.json to specify the private module dependency.

Read more details about how to do that in [the  Github docs](https://docs.github.com/en/developers/overview/managing-deploy-keys#using-multiple-repositories-on-one-server).

For example if you had 3 private repos:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- username/repo1
- username/repo2
- username/repo3
{: refdef}

Where repo1 installs both repo2 and repo3, then add an ssh config ($HOME/.ssh/config) as follows:

```
Host github.com-repo2
  Hostname github.com
  IdentityFile=/home/user/.ssh/private_key_repo2

Host github.com-repo3
  Hostname github.com
  IdentityFile=/home/user/.ssh/private_key_repo3
```

Then specify the modules like so in repo1’s package.json:


```
"dependencies": {
  …
  "repo2": "git+ssh://git@github.com-repo2: username/repo2",
  "repo3": "git+ssh://git@github.com-repo3: username/repo3",
  …
}
```

It’s important to specify the protocol correctly. Without ‘git+ssh://‘ the install completes but none of the files actually get installed. Instead some type of symlink gets created. At least that’s what happened in my tests. 

Store your private keys in Github secrets, and before your install step, create the private keys on the filesystem from those secrets:

```
/home/user/.ssh/private_key_repo2
```

and

```
/home/user/.ssh/private_key_repo3
```

Now in your repo1 workflow you should be able to install all repo1 dependencies using:

```
npm install
```

It’s worth having a verify step after install that lists the installed files using ls -l and/or tree.