---
title: "Don't Forget to Rebase"
date: 2024-11-26T11:42:09-05:00
draft: false
type: "post"
slug: "dont_forget_to_rebase"
tags:
  - git
  - github
  - development
---

[Git is hard](https://duckduckgo.com/?t=ffab&q=git+is+hard&atb=v342-1&ia=web). It used to be harder for me to understand how to use it. Moving from using Github Desktop to the Git CLI was an adjustment, but it made me better at using Git for version control.

For small, single developer projects that I work on alone, after hours, I don't put much thought into my Git history.

When I work collaboratively on more complex projects, where a pull request may be reviewed with multiple changes through the review process, the commit history of the project may quickly become a mess of attempts to fix issues as well as commits made by bots updating metadata tags in code. To clean up this messy commit history, the tool I use is `git rebase`. `git rebase` provides a way to re-write a git history, useful for cleaning up a commit history with many changes that are works in progress or made and then removed.

## Why I'm writing this post

Recently, I had a pull request with over 100 commits that I was responsible for, with multiple authors and a bot contributing changes. Many of these changes were testing out different ideas to fix deployment issues. To conform to my team's standards, all of these commits need to be condensed into a single commit, for the change in this pull request.

So, while working on this pull request, I go to rebase my branch and find that rebasing and squashing every commit results in every commit having a merge conflic.

Every.

Single.

Commit.

Over the course of a few hours, I ended up fixing these merge conflicts (and then fixing those fixes when I accepted the wrong change when resolving the conflicts). It was messy and it took time, but eventually, the commit history was cleaned up.

So this is my reminder to myself: don't just commit often, but rebase often too.
