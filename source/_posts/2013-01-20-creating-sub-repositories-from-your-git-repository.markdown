---
layout: post
title: "Creating sub-repositories from your git repository"
date: 2013-01-20 00:27
comments: false
categories: notes
tags: [git, git-subtree]
published: true
---

So you have a nice big project that you've been working on for a while and you
are at a state where you think it will be nice to split a part of the project.
This can be to either create it as a library to use it with other projects or
just maintain it independantly.

There are two steps involved:

* Splitting out the subpath from the repository and creating a new repository
  from it.
* Using this new git repository we've created in the main repository so that we
  can continue working.

Let's tackle them one at a time.

## Splitting a subpath into a new repository

I'm assuming that we're interested in keeping the git history - else, you can
simply just copy out the directory into a new folder and init it as a new
repository.

#### Using `git filter-branch`

```
git filter-branch --prune=empty --subdirectory-filter my-api -- --all
```

The `-- --all` is to ensure that we filter all the branches in the repository.

Next, you simply add new remotes and push your repository there.

```
git remote add my-new-remote git@github.com:adhipg/new-remote.git
git push --all
```

Side note: You'll have to clone the original repository again.

#### Using `git subtree`

[`git subtree`](https://github.com/gitster/git/blob/634392b26275fe5436c0ea131bc89b46476aa4ae/contrib/subtree/git-subtree.txt)
is a new git command that recently was added into git. Using it to create the
new repository is simple enough:

```
git subtree split --prefix my-api --branch my-api-repo
```

Now the `my-api-repo` branch consists of just the contents from my-api and all
the relevant commits. This can now be used to push to a new remote:

```
git push git@github.com:adhipg/new-remote.git split:master
```

## Merging the subpath back into the original repository

We use `git subtree` from earlier for this.

```
git subtree add --prefix my-api --squash git@github.com:adhipg/new-remote.git master
```

The `--squash` here implies that we just want to create a merge commit - else,
we'll end up with  duplicate commits in the history.


