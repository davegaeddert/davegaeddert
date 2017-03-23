---
date: 2015-05-15T00:00:00-00:00
draft: false
title: "Sibbell: A SaaS Pricing Experiment"
---

#### Background

I suppose you could consider [Sibbell](https://sibbell.com) to be a SaaS (Software as a Service). Sibbell started out as a solution to a problem: how do I stay up-to-date with all of the open source projects that I use? 90% of the time when I find a bug (or better yet, a client finds a bug) in an open source library, it's already been fixed and I just don't know it.

GitHub continues to prove to be the "hub" of open source. Almost every open source project worth mentioning now lives on GitHub.

Sibbell does one thing: [notify you whenever the GitHub projects you use get updated](http://davegaeddert.com/2014/10/11/sibbell-emails-for-new-releases-on-github/).

#### What I've learned so far
Running a site like Sibbell costs money (not to mention time). Even though the hosting and other associated costs are still fairly low, it starts to add up. Especially if you want to deliver the experience that users are used to these days.

I love free stuff as much as the next guy, but as I've gotten older and more "experienced", I've learned to appreciate the value of a good product. I've also learned that sometimes you have to pay for a good product. And that's ok. In fact, I almost prefer it.

When I pay for something, I think of it as an acknowledgement of these things:

- it costs less than the time and energy expense of using an inferior product or hand-built solution
- if they're charging for it, they're committed to its future and making improvements

To that end, I'm introducing paid services in Sibbell.

#### A la carte monthly pricing
Like I said, I like free stuff too. I want the core functionality of Sibbell to remain free and still do its job. As far as pricing models, I've toyed around with a few things. An obvious option, which you see in a lot of SaaS's, is to have a few tiers of features with different monthly costs. A variation on this that came to mind, which I can't think of too many examples of, is to break out the set of features (maybe 5 or 6) into small subscribtions that can be individually enabled - a la carte style. By small subscriptions, I really mean small - like $1 or $2 per month. My hope is that at that price, pulling the trigger should almost be a no-brainer for a user. For me, even if a fairly low percentage of users convert with an average of $2 a piece ($2 == 1 feature), Sibbell could pay for itself.

Then again, maybe there's a reason I can't think of many examples of this kind of pricing model...we'll see.

Some potential feature examples:

- batch notifications - instead of receiving emails as-it-happens, get a daily or weekly summary (weekly is already in place)
- a [Sibbell Chrome extension](https://chrome.google.com/webstore/detail/sibbell/focknnclhinffehmdpokckjahcfaldac) (already in place)
- individually choose repos instead of just enabling all "stars" or all repos you're "watching" (already in place)
- webhook notifications - [Slack](https://slack.com/)!
- [IFTTT](https://ifttt.com/) integration?
- choosing if you want major or minor release notifications - per repo?
- anything regarding pre-releases - not used too often though...
- a Sibbell button, via [Chrome extension](https://chrome.google.com/webstore/detail/sibbell/focknnclhinffehmdpokckjahcfaldac), that shows up on GitHub repo pages next to the watch/star/fork buttons and allows you to quickly enable/disable Sibbell notifications
- organize releases by your projects - ex. Sibbell uses [django/django](https://github.com/django/django), [kennethreitz/requests](https://github.com/kennethreitz/requests), and I want to know when to update my requirements
  - various tools that do this already (https://requires.io/, https://david-dm.org/, but are there any that cover multiple languages? https://gemnasium.com/?
- notifications on GitHub status? outages, etc.
