---
layout: post
title: "Notes on Pro Git, 2nd Edition"
tags: git
toc: true
---

Notes on [*Pro Git*, 2nd Edition](https://git-scm.com/book/en/v2) by Scott Chacon and Ben Straub (2014).

## About Authors

- [Scott Chacon](https://scottchacon.com/), a software developer working on GitHub.com, as well as the maintainer of the [Git homepage](https://git-scm.com/) and the Git Community Book.

## 2. Git Basics
### 2.1 Getting a Git Repository

Initializing a repository in an existing directory:

```shell
git init
```

This creates a subdirectory named `.git`.

Cloning an existing repository:

```
git clone <url>
```

### 2.2 Recording Changes to the Repository

The `git add <file>` command has two semantics: Tracking a new file and staging a modified file.

The `git status` or `git status --short` can see the current status of working directory.

`git diff` compares what is in your working directory with what is in your staging area. `git diff --staged` compares your staged changes with the last commit. We can also use `git difftool` to call external diff viewing program.

### 2.3 Viewing the Commit History
### 2.4 Undoing Things
### 2.5 Working with Remotes
### 2.6 Tagging
### 2.7 Git Aliases