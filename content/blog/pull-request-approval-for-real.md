---
date: 2015-11-15T00:00:00-00:00
draft: false
aliases:
- /2015/11/05/a-pull-request-approval-workflow/
title: Pull request approval, for real

---

At [Flint Hills Design](http://flinthillsdesign.com/), we use GitHub. We haven't always, and we still host a lot of repos elsewhere on our own servers, but there are just too many benefits to using a service like GitHub. Especially when it comes to collaboration.

It's no secret that one of the best features of GitHub is the fork and pull request workflow. With public projects, forking a repository and asking for your changes to be merged back in to the main codebase makes a lot of sense. People can easily clone the code, fiddle around with it, and when they're ready, present it to the project maintainers to get their approval and hopefully get it merged into the public project.

This formal, request and approval workflow is the same way that we handle internal projects. We have a spoken rule that an "admin" needs to review things before they get put into production. Unfortunately there's no way to actually implement this, other than to say "don't click the merge button, even though you can"

Sure, the fork-flow accomplishes exactly this, but for us, the fork / multiple repo structure is unnecessarily complicated. We like to keep our tooling as simple as it needs to be. One way we like to keep it simple is to keep a project to one repository. Ideally, all of our developers could work on branches on the main repo, but nothing could be merged into master without approval. "Limited write-access" in a sense.

With the new [GitHub protected branches](https://github.com/blog/2051-protected-branches-and-required-status-checks), we can actually have the best of both worlds. Protected branches, in short, let you choose specific tests that all code needs to pass, before it can be merged in to the master branch. The most common form that these status checks take is in continuous integration services, like Travis CI or Circle CI. But the cool thing about these status checks is that *anything can be a status check!* Code goes in, something happens, and a pass or fail comes out. It could be signing a CLA, checking commit message syntax, running traditional tests...anything. In addition, the "merge" button on pull requests can actually be disabled until these status checks pass!

With that in mind, we created [PullApprove](https://pullapprove.com/). PullApprove is a dead simple service, utilizing webhooks and status checks to say whether or not a pull request has been approved (clever name, I know). Just decide who needs to approve things. The rules for who needs to be approve what can be as simple, or as complicated as you like. Do all of the developers need to review a PR? Maybe 2 of 3 admins need to give the ok? Or just one person needs to approve everything?

There's a lot more to say, and maybe there will need to be some additional posts on this topic. The gist:
## You can have a truly formalized approval process for deciding what can be merged and what can't.

#### https://pullapprove.com

---

![PullApprove with a comment](/img/blog/approve-by-comment.gif)
