---
layout: post
title: "Notes on Pro Git, 2nd Edition"
tags: git
toc: true
---

[*Pro Git*, 2nd Edition](https://git-scm.com/book/en/v2). Scott Chacon and Ben Straub. 2014.

## Chapter 10. Git Internals

Humans use models to study things. Models are abstraction of objects. So if you want to learn how to use Git, you only need to know the commands of Git. But I'm a programmer, I should explore the internals of Git and it's beneficial to me.

### 10.1 Plumbing (水管管道) and Porcelain (瓷器)

- Git's "plumbing" commands: low-level commands
- Git's "porcelain" commands: user-friendly commands

Directory structure of `.git`:

```
-- hook/                           # client- or server-side hook scripts (See #8.3)
-- info/                           # containing a global exclude file
-- objects/                        # stores all the content 
-- refs/                           # stores pointers into commit objects 
-- description                     # only used by the GitWeb program (See #4.7)
-- config                          # project-specific configuration
-- HEAD                            # points to the current branch
-- index                           # stores staging area information
```

Core parts: `objects/`, `refs/`, `HEAD`, `index`