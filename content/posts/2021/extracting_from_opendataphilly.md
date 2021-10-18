---
title: "Extracting Data from Open Data Philly"
date: 2021-10-17T18:45:35-04:00
draft: true
type: "post"
slug: "extracting-from-opendataphilly"
---

A little over a year ago, I moved into a new neighborhood in my city. I was really excited about the space and am glad to say I love it even more now after living here a while.

One of the things I was most excited about was trying to be a more active member of my block. While it's been fun getting to know my neighbors, one of the things I've also ended up doing is filing requests with [Philly311](https://www.phila.gov/departments/philly311/) - a service where I can ask questions and request non-emergency municipal services.

In addition to 311, I've also known about and have been a fan of [OpenDataPhilly](https://www.opendataphilly.org/) (ODP) - a portal to access publicly available data produced by the city. In this post, I'll talk about what i've put together to pull data out of ODP - [odphilly-tools](https://github.com/chris-s-friedman/opendataphilly-python)

{{% note %}}
This post coincides with V0.0.1 of these tools. The tools I'm talking about are a work in progress in their very infant stage. Things may change, not work, break, need documentation - all in good time.

Instead of waiting for things to be perfect, I want to get something minimal out into the world so that I can work on it more.
{{% /note %}}

Right now, my tool for querying ODP is built around querying 311 data from their cartoDB instance. [CartoDB](https://carto.com/developers/sql-api/) allows for querying the PostgreSQL behind the data using html API queries. So instead of needing special permision to query postgres, I can just query in the url, like `https://phl.carto.com/api/v2/sql?q=SELECT * FROM public_cases_fc WHERE service_code = 'SR-IR01'`.

Powerful yes, but it'd be helpful to have some functions to make this easier. So I wrote a script with some functions that allow for extracting from their api, one part at a time, to build a dataset of data that I am intersted in.

In my next post, I'll talk about how I'll use those data and some changes i'm already workong on with the odphilly-tools.
