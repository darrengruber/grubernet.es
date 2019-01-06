---
title: Automating this blog with hugo, Github, CircleCI and Docker
type: post
date: 2019-01-05T16:12:07-05:00
draft: false
---
![alt text](/internet.jpg "This is how it works")

If you're going to post a simple blog on the internet - especially one that
deals with scaling and security, there's a lot of things that it should be:

  * **durable** - Unless you're doing something fancy and require a full blown
  CMS like Wordpress, using a static blog generator is a good idea. Not having
  database or a server to maintain or scale will ensure that your blog will stay
  up pretty much no matter what.

  * **secure** - If you're only hosting a bunch of static files, the surface
  for malicious actors is greatly reduced.  
  Also - it's 2019.
  TLS at the bare minimum. There's really no excuse because of
  the awesome [Let's Encrypt](https://letsencrypt.org) project.

  * **cheap to host** - Free is

  * **easy to update** - The major downside to static site generators is that
  you inevitably have to setup a workflow

  * **easy to deploy** - The major downside to static site generators is that
  you inevitably have to setup a workflow

### Setting up Github
