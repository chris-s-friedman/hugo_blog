---
title: "Scraping a Wiki"
date: 2021-11-11T21:19:38-05:00
draft: false
type: "post"
slug: "wiki-scraping"
tags:
  - wiki
  - omnipedia
  - python
  - scraping
  - beautifulsoup
---

A few months ago, I discovered and started exploring an interactive game called [Neurocracy](https://neurocracy.site/). The basic premise is to explore and investigate a major world event in a not-so-far-off sci-fi future... through a wikipedia-style rabbit hole.

The game takes place over ten days of edits and additions in this wiki, [Omnipedia](https://omnipedia.app/). The first full day, Otober 1st, 2049, is freely available. After exploring the wiki, I'm sure you'll want to support the developers and writers of Neurocracy by [purchasing the full game](https://omnipedia.app/join).

Considering the nature of this game is going down the rabbit hole - and past work has found me supporting network and graph analysis - I decided I wanted to map the networks of connections between each page in the wiki.

Now I _could_ go through, page by page, and manually record what pages each page links to. But why do that when I could scrape those links out of the wiki?

So, today I announce the very beginning work on my tools for scraping and analyzing data from Omnipedia.

Feel free to visit the repository [here](https://github.com/chris-s-friedman/omnipedia) and explore the code.

Right now, i've got code written for two purposes: scraping pages and parsing data that can be found in each page. I'm currently working on the scripts to further analyze the data from Omnipedia.

That said, if you want to scrape the feely-availbale page of Omnipedia:

Install the repository with:

```bash
pip install -U git+https://github.com/chris-s-friedman/omnipedia.git@latest-release
```

And then in your python script:

```python
import requests
from ompedia_tools.scrape.parse import parse_wiki

url = "https://omnipedia.app"

client = requests.Session()

wiki_data = parse_wiki(client, url)
```

wiki_data will have a list of dicts of information about each unique wiki page in the wiki.
