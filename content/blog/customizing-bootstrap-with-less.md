---
date: 2015-04-15T00:00:00-00:00
draft: false
title: Customizing Bootstrap with Less
---

We at [Flint Hills Design](http://flinthillsdesign.com) build a lot of websites. We also use [Bootstrap](http://getbootstrap.com/) to build a lot of those sites. "Why" is a whole 'nother topic on its own, but needless to say, it saves us a ton of time and energy, and allows our small team to accomplish more than we ever could if we started every site from scratch.

The downside of using the same framework for many different projects? They could easily all end up looking exactly the same! And exactly the same as thousands of other sites that are also built on Bootstrap!

### So what do you do? Customize it.

There are many ways that you can customize your Bootstrap setup, most of them deal with modifying the [Less](http://getbootstrap.com/css/#less) or [Sass](http://getbootstrap.com/css/#sass) variables, which makes sense. But there doesn't really seem to be a suggested way to *actually* do that.

We use Less, and here's how we do it.

##### Install Bootstrap
We use [Bower](http://bower.io/) to do this. Something like `bower install bootstrap`...

##### Create bootstrap-custom
The file structure here might be a little bit overkill, but should also be able to handle anything we decide to do in the future. The important thing is that we want a `variables-custom.less` file, which we put in `bootstrap-custom/less/`.

![file structure](/img/blog/Screen-Shot-2015-04-21-at-9-17-37-PM.png)

##### Redefine the variables in variables-custom.less
The idea here is to **only override the variables you need**. This will make it incredibly easy to track down your modifications, and make updating Bootstrap much easier (all you'll need to do is check that the names of variables you are using didn't change).

**Just copy and paste the lines you want to modify, and change them.**
<script src="https://gist.github.com/davegaeddert/dd3f3d1b895bd15e000e.js?file=variables-custom.less"></script>

##### Add your variables to Bootstrap variables.less
This is the only part of the Bootstrap source that you will need to modify. We just tell Bootstrap to override the default `variables.less` with any customizations we made in `variables-custom.less`. Now when it compiles, you'll have all your modifications, safe and as detached as possible from the Bootstrap source code!
<script src="https://gist.github.com/davegaeddert/dd3f3d1b895bd15e000e.js?file=variables.less"></script>

###### Bonus points
You can also use these variables (and Bootstrap mixins and whatever else you'd like) in your own stylesheets. Just `@import` them at the top.
<script src="https://gist.github.com/davegaeddert/dd3f3d1b895bd15e000e.js?file=style.less"></script>
