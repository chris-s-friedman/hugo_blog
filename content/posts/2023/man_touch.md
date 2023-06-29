---
title: "man touch"
date: 2023-06-28T11:29:02-04:00
draft: false
type: "post"
slug: "man_touch"
tags:
  - bash
  - man
---
<!-- markdownlint-disable-next-line MD026 -->
## `man touch`...

... is the silly thing i've typed into my terminal today. Why? As a result of
business needs, one of the common tasks in my office is to copy data between
cloud storage buckets across multiple accounts.

Recently, our devops team found a bug in our copy scripts that copied files into
directories named after themselves. So, for example a file at
`~/Documents/my_doc.md` that is to be copied to the root of a bucket would be
copied to `/Documents/my_doc.md/my_doc.md`.

I wanted to recreate this issue locally using tools that i'm familiar with. I
wanted to try to create a file when the directory exists where both the file and
directory have the same name:

```sh
> mkdir deleteme.md
> touch deleteme.md
```

If you try to do this, the directory `deleteme.md` gets created but no file is
created. I was expecting that `touch deleteme.md` would produce an error but it
did not.

Conversely, creating the file first and then the directory, results in an error:

```sh
> touch deleteme.csv
> mkdir deleteme.csv
mkdir: deleteme.csv: File exists
```

At this point, I'm confused. Why doesn't `touch` fail the first time around?
I've been consistently taught to use `touch` to create files. That advice seems
misguided though if `touch` doesn't give an error when a file isn't created when
the command is given to create the file.

I bring this to one of my coworkers and he has one piece of advice:

`man touch`

Although the specific language changes by the specifics of the machine, the
purpose of `touch` is to change access and modification times of files.

Creating files happens as a side-effect of `touch`.

At the end of the day, I think that all of this is fine and I've learned a lot.
I learned that tools I commonly use may not have the purpose I expect. I learned
that it's important to consult the manual. And I learned that sometimes with
shell scripting, we use tools in a certain way because we figured that the tool
works *just* fine.
