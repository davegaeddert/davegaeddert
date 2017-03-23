---
date: 2014-12-01T00:00:00-00:00
draft: false
title: Xcode exception breakpoints
---

Having trouble tracking down where your exceptions are coming from in iOS development? If you're not using exception breakpoints, you should be.

Just go to breakpoints:
![](/img/blog/2fb922f8d8119a7830d18e452069ed11.png)

Add an exception breakpoint:
![](/img/blog/ae2894f2f3d826dd75b1ab45c2349ec0.png)
![](/img/blog/a9c3e2970d2d6427d4c330331f87131a.png)

That's it. Now when an exception is thrown, Xcode will take you straight to the line where it originated.
![](/img/blog/7878ebf6d2898abc5ddba44edcabe8da.png)
