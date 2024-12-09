---
title: "Advent of Code 2024 - What I've Learned"
date: 2024-12-01T10:41:23-05:00
draft: false
type: "post"
slug: "aoc24"
tags:
    - python
    - coding
    - advent_of_code
---

It's once again December which, as a developer can mean only one thing: it's time for the Advent of Code! Not to give too much away, this year, I'll be using my development skills to help find the Chief Historian in time for this year's big Christmas Sleigh Launch!

My goal with this blog post is to update it after completing an Advent of Code puzzle with what I've learned while completing the puzzle. I'll update this post each day with something new, so make sure to check back!

Just a note, I primarily develop in python, so my discussions will likely revolve around writing python code. I am tracking the work I'm doing for advent of code [here](https://github.com/chris-s-friedman/advent-of-code-2024)

## Table of Contents

- [Day 1: `collections.Counter`](#day-1-collectionscounter)
- [Day 2: naivete is OK](#day-2-naivete-is-ok)
- [Day 3: Regex Time!](#day-3-regex-time)

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

## Day 2: Naivete is OK

Going to _try_ to keep this short. Today's advent was a reminder that sometimes it makes sense to accept the more naive, less clever, less thinks-through-every-case-possible-in-the-universe solution in favor of just looping through your list and getting your job done.

Today's advent challenged me to find sets of numbers in a list of sets where rules were violated and then, in part two of the challenge, allowed up to one item to be removed from each set if removing that item will make the set not violate the rules. This second part of the task had me thinking for most of my morning. I ended up writing a 100+ line function with multiple sub-functions called within it, with a complicated returned tuple that provided information about where and how a set failed or didn't fail to follow the rules.

I would run my script, submit an answer, be told it was wrong, write code to handle _some_ edge case, resubmit, make changes, run, resubmit, change, run, resubmit... and on and on.

All of this was to avoid what I thought would be the slower, more naive, simple solution: loop through each item in every failing set and see if removing an item makes the set not fail. This solution is probably slower but it's much easier to understand, essentially self-documenting and.... works. Also, how much does speed really matter on a list of 1000 sets (answer: not much)?

So, today's lesson learned: just write the damn solution if the "clever" solution is not much of a solution.

## Day 3: Regex Time

Today is time for some regex-fu. Today I learned two things... and I don't have much to say about them except for they are technical eccentricities of the regex:

1. The `.` character doesn't select _everything_. It selects everything except newline characters.
2. To select text between two sets of characters, don't dorget to put the text you're looking to extract in parentheses!

That's it! Easy day and looking forward to tomorrow!

## Day 4: It's kind of a matrix

Ok it's not a matrix today but it was a fun puzzle of trying to find words in a cross-word style matrix of letters. I will say, the vast majority of this solution is cribbed from [Geeks for Geeks](https://www.geeksforgeeks.org/search-a-word-in-a-2d-grid-of-characters/).

The thing I've learned today - besides to not be afraid of matrices, because this one wasn't bad - was that you don't learn as much when you just re-use someone else's code.
