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

Core parts: `objects/`, `refs/`, `HEAD`, `index`.

### 10.2 Git Objects

Git stores all the content as *tree* and *blob* objects, with trees corresponding directories and blobs corresponding file contents. All objects are atored in the `.git/objects/` directory. For each object, Git calculates its SHA-1 hash value, a 40 characters long hexadecimal number. The first two characters would be a directory name, and the rest 38 characters would be a file name.

```
find .git/objects -type f
```

may ouput

```
.git/objects/f9/9464bc09d8a9ebe7eb82e09c7508e621469b75
.git/objects/f0/6a80f1b2da6ed65c2816c39632e8189830ff5b
.git/objects/f0/85f447537f451c88e544936486f01e12b1b6ea
.git/objects/fa/7399fe2509e97ea171829de5b361d057567609
.git/objects/ff/5f2475cc0c8dc4c74493df316a3a4ed26a6a71
.git/objects/e9/afb2093b557daa1149cd21306cd82c94dce056
.git/objects/e9/31a10281a2499ad719042f251da72d30915afe
.git/objects/f1/4ae37410e6e188d0adac9d33b6b522b71b1084
```