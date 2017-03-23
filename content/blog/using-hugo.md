+++
title = "Using Hugo"
date = "2017-03-23T16:31:07-05:00"

+++

Once again, I'm changing how my site is hosted. A while back, I set things up using [Ghost](https://ghost.org/). It was fine. Fairly simple, generally speaking, but
after a while it felt like even that required too much work to run and update. Truthfully, I've always wanted a no-fuss static
site with a simple design and as few files as possible. I'd tried Hugo once before (for [pullapprove](https://about.pullapprove.com/) documentation?)
but it didn't work out (honestly can't remember why). Since then I've used [Pelican](http://docs.getpelican.com/en/stable/), which is also ok but looking at those projects now, there's just way too many files and scripts involved to make it work.

Today I had to shuffle some shit around due to the hosting provider transitioning servers, and I decided it was time to simplify yet again.
I've deployed static sites to AWS before using S3, which is cool but even that takes configuration that I just don't have the patience for, especially for
"side-projects". So, now I've got a [Hugo](https://gohugo.io/) site in a [public repo on GitHub](https://github.com/davegaeddert/davegaeddert) published via [Netlify](https://www.netlify.com/). There's basically a file for each post and page, and that's about it. I can now use Netlify for free, including HTTPS via LetsEncrypt,
and there is almost nothing to mess with.

![](/img/blog/hugo-site-structure.png)

My old posts (and stupidly named screenshot images) have been copied over to this new site. Most of them are largely irrelevant but...history, right?

Hopefully I'll get a chance to post more than I've been able to lately. Most likely some of those will be cross-posted to Medium as well.
