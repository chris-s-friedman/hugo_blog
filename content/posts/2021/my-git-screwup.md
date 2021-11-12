---
title: "My Git Screwup"
date: 2021-10-24T10:31:33-04:00
draft: false
type: "post"
slug: "my-git-screwup"
tags:
  - git
---

{{% warning %}}
**Warning**: There are code snippets below that may have unexpected consequences that can break things. Use caution when copying code snippets, make sure you know what you are copying and double check your commands before hitting `return`.
{{% /warning %}}

This morning I deleted a bunch of configuration files from my [Home Assistant](https://www.home-assistant.io/) instance.

I've made some changes to my configurations over the past month or so and have neglected backing up those config changes. This morning, I figured now was as good a time as any to commit those chagnes and upload them to my personal home assistant config repo.

After logging into my machine and taking a look at the changes, I see a bunch of files that should be ignored

```
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   config/home-assistant.log

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	config/home-assistant_v2.db-shm
	config/home-assistant_v2.db-wal
	config/home-assistant_v2.db.corrupt.2021-10-24T13:51:45.805151+00:00
```

Ok, so I add some stuff to my `.gitignore` but there's still that `config/home-assistant.log` sitting there, being tracked.

I then do what any dev would do: I look it up:

# How do I remove untracked files from git?

I find the stackoverflow link:

[how to remove untracked files in Git?](https://stackoverflow.com/questions/8200622/how-to-remove-untracked-files-in-git)

I see the [top answer](https://stackoverflow.com/a/8200645/5975765) and I copy & paste ™️

{{% warning %}}
Remember that warning above? Don't run this code unless you know what you're doing. This code is why I spent this morning fixing a mistake and writing a blog post instead of _literally_ anything else.
{{% /warning %}}

```
git clean -fdx
```

And that's when I got a message that much of my configuration - my secrets, local storage (including authentication, dashboards), etc - was deleted. permenently.

I went to the stackoverflow answer to find that there's a note after the asnwer (and a bunch of comments with warnings about using this code):

> To remove untracked files / directories do:
>
> `git clean -fdx`
>
> -f - force
>
> -d - directories too
>
> -x - remove ignored files too ( don't use this if you don't want to remove ignored files)
>
> ---
>
> **Use with Caution!**
>
> These commands can permanently delete arbitrary files, that you havn't thought of at first. Please double check and read all the comments below this answer and the --help section, etc., so to know all details to fine-tune your commands and surely get the expected result.

After about an hour of work, i've got my Home Assistant instance back up and running. I still have to rebuild all of my lovelace dashboards, but at least I can now control things.

# Why did this happen?

So then, why did I delete a bunch of things using a command I was unfamiliar with? I've come up with a few reasons below that are all connected to each other in some way.

## I didn't know what I was doing

Clearly - and as I just said - I didn't know what that command would do. I was looking for something to remove a file that should be ignored because of a `.gitignore` from the git repository **but not from the file system.** Turns out that `git clean` removes the file from the file system - not from being tracked.

## I just wanted to do a thing and move on

I was looking for a quick answer to something so that I could do it and then move on to what I really wanted to do with my morning. Rushing to do things is never a good idea.

This would have been prevented if I read the **entire** answer first.

Running Commands that I don't understand - and rushing while doing so - is careless. This is certainly something I will try to avoid doing in the future.

## I used the wrong ~~answer~~ question

As I mentioned above, the answer I used wouldn't even get me where I want to be.

The command I wanted was (taken from [another blog](https://renatello.com/git-untrack-single-file/)):

```sh
git rm --cached 'config/home-assistant.log'
```

Really, the question in stack overflow was the incorrect one for my case.

Wrong question -> Wrong answer -> Wrong result

## The stack overflow answer put the warning after the answer.

First - I don't fault the writer of the stack overflow answer as a reason why I deleted a bunch of configuration files. I believe it's my responsibility to know what I'm doing on my machine.

That said, if I would have read the warning before running the command, i wouldn't have run it. I would have likely read the warning if the warning was before the code. To repeat though, I'm not obsolving myself from not reading the enter answer before running the code in it.

# What did I learn?

## Not everything in my config is actually in git.

There are a bunch of key files - like authentication stuff, and the layouts of my lovelace dashboards - that i lost. that's not good.

## I need to be more careful before running commands I'm unfamiliar with,

Seriously. If I don't know what something does, I should look it up before using it.

## `git clear -fdx` wil delete things - even things you wouldn't think of.

I was expecting one log file to be untracked. Instead a bunch of configuration files were sent into oblivion.

## Use `git rm --cached filename` to untrack files

This is the way.

## Git is not some black box that keeps everything backed up

There's no way to undo a `git clear`. Git isn't some magic black box of safety and rolling back changes. Git only does _exactly_ what it's told.

# What will I do in the future?

## Be more careful

This means a few things:

- Read all of a stack overflow comment before running code in it.
- If I don't know what code will do, look it up.
- Don't treat git like some magic black box of safety

## Be mindful of how I write

If i write about something that can have devestating or undo-able consequences, I must put my warnings first. In big bold letters that do everything I can to warn my readers to not make the same mistakes I did.

# Making mistakes is a great way to learn

Thankfully i've never `rm -rf`ed my entire machine or most of a [pixar movie](https://thenextweb.com/news/how-pixars-toy-story-2-was-deleted-twice-once-by-technology-and-again-for-its-own-good). Breaking things is a [great way](https://www.edsurge.com/news/2015-05-21-making-by-breaking-why-taking-things-apart-is-essential-to-making-them-work) to learn how they work though. As long as we can look back on our mistakes and learn from them, then i consider it a good mistake.
