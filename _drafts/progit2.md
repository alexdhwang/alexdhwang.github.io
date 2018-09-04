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

You can use `git rm --cached <file>` to remove accidentally staged files.

### 2.3 Viewing the Commit History

Common options for `git log`:

| `-p` | Show the patch introduced with each commit. |
| `--stat` | Show statistics for files modified in each commit. |
| `--shortstat` | Display only the changed/insertions/deletions line from the `--stat` command. |
| `--name-only` | Show the list of files modified after the commit information. |
| `--name-status` | Show the list of files affected with added/modified/deleted information as well. |
| `--abbrev-commit` | Show only the first few characters of the SHA-1 checksum instead of all 40. |
| `--relative-date` | Display the date in a relative format (for example, “2 weeks ago”) instead of using the full date format. |
| `--graph` | Display an ASCII graph of the branch and merge history beside the log output. |
| `--pretty` | Show commits in an alternate format. Options include oneline, short, full, fuller, and format (where you specify your own format). |
| `--oneline` | Shorthand for `--pretty=oneline` `--abbrev-commit` used together. |

### 2.4 Undoing Things

Adding forgotten files:

```
git commit -m "bla bla bla"
git add fogotten_files
git commit --amend
```

Unstaging a staged file:

```
git reset HEAD <file>
```

Unmodifying a modified file:

```
git checkout -- <file>
```

### 2.5 Working with Remotes
### 2.6 Tagging
### 2.7 Git Aliases