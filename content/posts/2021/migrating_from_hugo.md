---
title: "Migrating from a Hugo site to... Hugo?"
date: 2021-09-02T22:29:51-04:00
draft: false
type: "post"
slug: "migrating-from-hugo"
---

I've been meaning to update this blog. _Really_. But well, I've known that it would require a lot of work.

When I first put this together, It was a hugo site - but the content was all written in [RMarkdown](https://rmarkdown.rstudio.com/) and powered by [Blogdown](https://bookdown.org/yihui/blogdown/), an R library for blogging. At the time, I thought this was the coolest thing, that I got to say, "My blog is written in R". It's different, non-traditional, and fun.

But, since the first blog post I wrote for this site, I spend less and less time in R. I work in a python shop, so naturally, I'll end up spending more time in the language I work in; that's also meant that my R skills aren't where they were and the idea of opening up RStudio to write a blog post - when i'm not even using R much anymore - doesn't seem appealing.

That's not to say I haven't _wanted_ to or that i _haven't_ worked on it.

While working on a [website](https://brainstem.chris-s-friedman.com/on_tap) related to my beer making, I found Gatsby, and loved how extensible it is, so i figured "I could write my blog in Gatsby!"

So I [tried](https://github.com/chris-s-friedman/friedman_blog_2), but couldn't get it to work for reasons I no longer remember.

Then, six months later, I [tried again](https://github.com/chris-s-friedman/personal_site_v3). I think I wasn't a fan of the template once i started putting content in there, but I really don't remember.

Then, three months later, I [tried again](https://github.com/chris-s-friedman/personal-blog). I think with this one, I saw just how much of a pain it would be to attempt to re-render all the old `.rmd` files that gatsby would be happy with.

Which brings us to today. What changed? I had time to _want_ to work on the blog again.

But more importantly, i went back to the basic framework of this being a blog built on Hugo.

All it took to migrate to this blog was copying over the rendered html files and static files, changing the config file.... and that's it.

+10 points for trying, and trying, and trying, then trying _something different_.
