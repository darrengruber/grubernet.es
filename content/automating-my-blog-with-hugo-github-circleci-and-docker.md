---
title: Automating my blog with hugo, Github, CircleCI and Docker for $0
type: post
date: 2019-01-05T16:12:07-05:00
draft: false
---
{{< figure src="/internet.jpg" alt="This is how it works" >}}

If you're going to host a simple blog on the internet - especially one that
deals with scaling and security - there's a lot of things that it should be:

  * **durable** - Unless you're doing something fancy and require a full blown
  CMS like Wordpress, using a static site generator is a good idea. Not having
  database or a server to maintain or scale will ensure that your blog will stay
  up even if you're being "hugged to death" by reddit or HN.

  * **secure** - If you're only hosting a bunch of static files, the surface
  for an attack is *greatly* reduced. You should also have TLS at the bare
  minimum. There's really no excuse not to because of the
  [Let's Encrypt](https://letsencrypt.org)<sup>:heart_eyes:</sup> project.

  * **inexpensive** - Hosting your own blogging platform shouldn't be a drain
  on funds, especially if you aren't being paid to do it. Thankfully static
  hosting is extremely cheap or even free in some cases. If the host doesn't
  have some sort of CDN with HTTPS in front of it, you can always set it up on
  [Cloudflare](https://www.cloudflare.com)<sup>:heart:</sup> which is offers both for free.

  * **easy to use** - Markdown[^1] is easy to write and moderately readable,
  [even in an unrendered form](https://raw.githubusercontent.com/darrengruber/grubernet.es/master/content/automating-my-blog-with-hugo-github-circleci-and-docker.md). Having website content as files makes it easy to version control
  and edit/preview directly within Github.

[^1]: Markdown is an overloaded term. Different rendering engines handle different "flavors" of Markdown, the most popular being "Github flavored". `hugo` uses the [`blackfriday`](https://github.com/russross/blackfriday#extensions) rendering engine for Markdown but also has "[shortcodes](https://gohugo.io/content-management/shortcodes/)" which go even further in extending the type of content you can render.

  <!-- * **maintainable** - The major downside to static site generators is that
  you inevitably have to setup a workflow that will compile your site and deploy
  those files to your host. The upside is that you really don't have to worry
  something going wrong after that point. -->

Beyond those things that you'd want for any blog, I wanted to go a little
further for when I built this site:

  * **"open source"** - Reading (and sometimes wholesale copying) how other
  people have solved technical problems is a great way to learn. I'd actually
  be really jazzed if somebody went as far as to open a pull request against a
  typo or misinformation posted on my website.

  * **continuously integrated and deployed** - A good chance to use some of the
  best practices associated with CI/CD. I'm a firm believer things are moving
  toward a [GitOps](https://www.weave.works/blog/gitops-operations-by-pull-request)
  mentality, so why not center everything around

  * **reproduceable** - All the dependencies to build, edit and test this site
  are self contained within this repo. You get started pretty quickly before
  ever needing to publish to the web.

  * **content focused** - Simple, easy to read theme. No distractions, ads, sidebars, etc. Kind of like how medium.com used to be before they clobbered
  visitors with the huge interstitial

If you haven't been scared away yet, let's get started :sweat_smile:

## Picking a static file host

[Github Pages](https://pages.github.com/) was a clear winner for me. They
support [custom domains](https://help.github.com/articles/using-a-custom-domain-with-github-pages/) and [automatically add Let's Encrypt certificates for you](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/).

In the past, I'd opt for using S3 & Cloudfront.


## Getting started with `hugo` and setting up your repository

I don't want to go too deep on why I settled on `hugo` over something like
`jekyll`, which has a deeper integration with Github Pages and has probably has
a lot more extensibility through plugins. There's been a shift toward using
statically linked `go` binaries and I tend to prefer them over having to install
Ruby.
