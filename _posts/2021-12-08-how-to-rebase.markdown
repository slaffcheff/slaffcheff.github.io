---
layout: post
title:  "How to rebase"
date:   2022-12-08 14:35:00 +0200
categories: git
---
Developers, I am pissed at you. A big chunk of your everyday duties involves source control. Not knowing how it works is unacceptable on many levels. FFS, this is developing 101. Learning GIT is in the core of every good training.

So, what is rebase? This will not be an essay, there is plenty of info on the net. I will just show you the sources:
1. [Merging vs Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)
2. [Git rebase explained](https://dev.to/jacobherrington/git-rebase-explained-simply-k0a)

Let’s input some commands in order to understand the most common case when rebase is needed and used. You have a remote branch (master, trunk, develop, etc). You create a working/feature/hotfix/etc local branch from the remote branch and start working. We all know that sometimes you work in a team with other developers, sysadmins, QAs and so on. They all do commits and merge them eventually. Some tasks take more time than couple of minutes, sometimes days. During this time, there are changes applied on the remote branch. When you finally push your changes, DANG. You see in your GIT provider (github, bitbucket, gitlab) that there is a conflict. And then .. you need to rebase. Please, don’t close your MR/PR, delete the branch and re-do the whole thing. Just learn how to use rebase. It’s not rocket science, I promise. 

For the following git commands we will use master branch as an example but of course you can adjust it to your needs, I am sure 🙂 

While you are on your local branch and hit a conflict the party starts. First we need to visit master branch (remote).

`git checkout master`


And pull the new remote changes that cause the conflict.

`git pull origin master`


When the changes are pulled, you can go back to your branch.

```
git checkout local-branch
git rebase master
```

In some cases you will need to clear some lines from the code but git will inform you for that. If this occurs, you need to clean whatever git wants and then do:

```
git add/rm file1 file2
git rebase --continue
```


When the work is done and you finally rebased properly, you can push. Because of the rebase, you will need to force push them.
`git push --force origin local-branch`

That’s all. Please rebase. Thanks.