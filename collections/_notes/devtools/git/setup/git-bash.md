---
layout: post
title: Setup Using git bash
permalink: /:collection/git/setup/git-bash
---

- [Adding an existing project to GitHub using the command line](https://docs.github.com/en/github/importing-your-projects-to-github/adding-an-existing-project-to-github-using-the-command-line)

```cmd
git init
git add .
git commit -m "init commit"
git remote add origin https://github.com/[username]/[reponame].git
git remote -v
git push origin master
git branch --set-upstream-to=origin/master

<!-- if unrelated history error -->
git pull origin master
git pull --allow-unrelated-histories
```
