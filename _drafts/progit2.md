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

Git doesn't store data as changesets or differences, but instead as a series of *snapshots*. A snapshot of content is a checksum of the current version of files (including directories). The computation of checksums uses the [SHA-1 algorithm](https://en.wikipedia.org/wiki/SHA-1) (*Secure Hash Algorithm 1*), and the result of a checksum is a *40 digits long* hexadecimal number. When you command `git add`, Git takes a snapshot and stores it into the staging area. When you command `git commit`, Git makes an object which has a pointer to the staged snapshot. So the commit history forms a chain.

```
+------------+     +------------+     +------------+
|commit 98ca8+<----+commit 72fd6+<----+commit 12b3d|
+-----+------+     +-----+------+     +-----+------+
      |                  |                  |
      |                  |                  |
      v                  v                  v
+-----+------+     +-----+------+     +-----+------+
| snapshot A |     | snapshot B |     | snapshot C |
+------------+     +------------+     +------------+
```

When you command `git branch test`, Git creates a new branch named `test`. A branch is simply a pointer to a commit object (or saying that a file containing 40 characters), so the cost of its creation is very cheap. The default branch is named `master`.

```
                                      +------------+   +--------+
                                      |   master   |   |  test  |
                                      +-----+------+   +---+----+
                                            |              |
                                            |   +----------+
                                            |   |
                                            v   v
+------------+     +------------+     +-----+---+--+
|commit 98ca8+<----+commit 72fd6+<----+commit 12b3d|
+-----+------+     +-----+------+     +-----+------+
      |                  |                  |
      |                  |                  |
      v                  v                  v
+-----+------+     +-----+------+     +-----+------+
| snapshot A |     | snapshot B |     | snapshot C |
+------------+     +------------+     +------------+
```

Git holds a special pointer named `HEAD` to mark the current branch. In default, the `HEAD` points to `master`. When you command `git checkout test`, the `HEAD` points to `test`. It is also very cheap. You can make a new commit in the `test` branch.

```
                                                            +--------+
                                                            |  HEAD  |
                                                            +---+----+
                                                                |
                                                                v
                                       +------------+       +---+----+
                                       |   master   |       |  test  |
                                       +-----+------+       +---+----+
                                             |                  |
                                             v                  v
+--------------+   +--------------+   +------+-------+   +------+-------+
| commit 98ca8 +<--+ commit 72fd6 +<--+ commit 12b3d +<--+ commit 2e38a |
+--------------+   +--------------+   +--------------+   +--------------+
```

If you switch back to the `master` branch and continue to modify your contents, the commit history will diverge. You can command `git log --oneline --decorate --graph --all` to see the branch graph.

Now, we can answer why Git's branching model is its "killer feature". Its creation and switching of branches both are lightweight.

### Remote Branches