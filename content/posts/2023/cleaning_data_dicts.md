---
title: "Cleaning Data (Dictionaries)"
date: 2023-06-16T13:57:00-04:00
draft: false
type: "post"
slug: "cleaning_data_dicts"
tags:
  - data cleaning
---

I'm slowly working through a new program to formalize and fill-in blanks in my
knowledge in working with data. To help me with that, I've been searching for
a toy data set to use to practice the things I'm learning. I think that I've
found my data set.

And oh my gosh, this data has depth.

I've decided to spend some time playing with Pennsylvania crash data, with data
from 2007-2021. The data portal to access the data can be found
[here](https://crashinfo.penndot.gov/PCIT/welcome.html#).

After downloading a subset of data and the data dictionary, I found what may be
one of the most annoying things I've found as a data professional:

The data dictionary is a
[PDF](https://pennshare.maps.arcgis.com/sharing/rest/content/items/fd0412e19feb45419da49eb7a759060d/data).

PDF's are hard to parse. This one is particularly hard to parse. It's hard to
parse because it includes a mish-mash of all different formatting. For example,
here's a section that has codes for where a person is in a vehicle. Note a
code-value pair split over multiple rows and note how some code-values are
separated with a `-`while others are not. Also note how some values have dashes
in the value. 

What all of this means is that the codes and dictionary values are hard to
parse into a tabular format that can then be plugged into analyses and
visualizations later on in analyses.

I've converted the pdf data dictionary to a tabular format [here](https://github.com/chris-s-friedman/pa_crash_data/tree/main/source_data).

![seat position code dictionary](/post/2023-06-16-cleaning_data_dicts/seat_position.png)

