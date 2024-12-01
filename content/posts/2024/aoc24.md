---
title: "Advent of Code 2024 - What I've Learned"
date: 2024-12-01T10:41:23-05:00
draft: true
type: "post"
slug: "aoc24"
tags:
    - python
    - coding
    - advent_of_code
---

It's once again December which, as a developer can mean only one thing: it's time for the Advent of Code! Not to give too much away, this year, I'll be using my development skills to help find the Chief Historian in time for this year's big Christmas Sleigh Launch!

My goal with this blog post is to update it after completing an Advent of Code puzzle with what I've learned while completing the puzzle. I'll update this post each day with something new, so make sure to check back!

Just a note, I primarily develop in python, so my discussions will likely revolve around writing python code.

## Table of Contents

- [Day 1: `collections.Counter`](#day-1-collectionscounter)

## Day 1: `collections.Counter`

Today, one of my tasks was to take two lists, count how many times each item in the first list appears in the second list, and then do some math on those counts. To accomplish this, I used `collections.Counter`.

A `Counter` object is a subclass of a `dict`. What the counter does is, for every item in an input list, a count of how many times that item appears is recorded. So for a given list:

```python
my_list = ["X", "X", "X", "Y", "Z", "Z"]
```
A counter object (`Counter(my_list)`) will return:

```python
Counter({
    "X": 3,
    "Z": 2,
    "Y": 1
})
```

What makes `Counter()`'s particularly helpful for this task is that they don't return a `KeyError` if you subset the `Counter` with an item not in its input list. Instead, a `0` value is returned. For example:

```python
my_list = ["X", "X", "X", "Y", "Z", "Z"]
my_counter = Counter(my_list)
print(my_counter["A"])
# 0
```

So, to complete my task, I did something _like_ this:

```python
from collections import Counter

list1 = ["X", "A", "B", "Y", "Z", "Z"]
list2 = ["X", "Y", "Y", "Y", "Z", "Z"]

list2_counter = Counter(list2)

counts = [item * list2_counter[item] for item in list1]
```