---
title: Automating my blog with hugo, Github, CircleCI and Docker
type: post
date: 2019-01-05T16:12:07-05:00
draft: false
---
{{< figure src="/internet.jpg" alt="This is how it works" >}}

If you're going to host a simple blog on the internet[^1] - especially one that
deals with scaling and security - there's a lot of things that it should be:

[^1]: the footnote text.

  * **durable** - Unless you're doing something fancy and require a full blown
  CMS like Wordpress, using a static site generator is a good idea. Not having
  database or a server to maintain or scale will ensure that your blog will stay
  up pretty much no matter what.

  * **secure** - If you're only hosting a bunch of static files, the surface
  for malicious actors is greatly reduced. You should also have TLS at the bare
  minimum. There's really no excuse not to because of the
  [Let's Encrypt](https://letsencrypt.org)<sup>:heart_eyes:</sup> project.

  * **cheap to host** - Hosting your own blogging platform shouldn't be a drain
  on funds, especially if you aren't being paid to do it. Thankfully static
  hosting is extremely cheap or even free in some cases. If the host doesn't
  have some sort of CDN with HTTPS in front of it, you can always set it up on
  [Cloudflare](https://www.cloudflare.com)<sup>:heart:</sup> which is offers both for free.

  * **easy to use** - Markdown is easy to write and read, even in an unrendered
  form. By relying on file/folder structures and annotated markdown files, the
  content of the site will always

  * **easy to maintain** - The major downside to static site generators is that
  you inevitably have to setup a workflow that will compile your site and deploy
  your files to your host. The upside is that you really don't have to worry
  something going wrong after that point.

Beyond those things that you'd want for any blog, I wanted to go a little
further for when I built this site:

  * **"open source"** - Reading (and sometimes wholesale copying) how other
  people have solved technical problems is a great way to learn. I'd actually
  be really jazzed if somebody went as far as to open a pull request against a
  typo or misinformation posted on my website.

  * **reproduceable** - All the dependencies to build, edit and test this site
  are self contained within this repo. You get started pretty quickly before
  ever needing to publish to the web before you're ready.

## Getting started with `hugo` and setting up your repository

I don't want to go too deep on why I settled on `hugo` over something like
`jekyll`, which has a deeper integration with Github Pages and has probably has
a lot more extensibility. There's been a shift toward using statically linked
`go` binaries and I tend to prefer them over having to install Ruby.
