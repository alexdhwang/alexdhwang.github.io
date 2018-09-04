---
layout: post
title: "Reading Log of Pro Git, 2nd Edition"
tags: git
toc: true
---

[*Pro Git*, 2nd Edition](https://git-scm.com/book/en/v2). Scott Chacon and Ben Straub. 2014.

## About Authors

- [Scott Chacon](https://scottchacon.com/), a software developer working on GitHub.com, as well as the maintainer of the [Git homepage](https://git-scm.com/) and the Git Community Book.

## Chapter 3. Git Branching

Why is Git's branching model the "killer feature"?

### Git Braching Model

Git doesn't store data as changesets or differences, but instead as a series of *snapshots*. A snapshot of content is a checksum of the current version of files (including directories). The computation of checksums uses the [SHA-1 algorithm](https://en.wikipedia.org/wiki/SHA-1) (*Secure Hash Algorithm 1*), and the result of a checksum is a *40 digits long* hexadecimal number. When you command `git add`, Git takes a snapshot and stores it into the staging area.