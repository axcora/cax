---
layout: minimalis.cax
title: CAX - Blazing Fast Static Site Generator in Pure C
description: 0.4s builds, zero dependencies, Jekyll-inspired DX. Written in pure C.
icon: /img/quick.svg
hero:
  title: CAX Enterprise SSG
  image: /img/astronot.svg
  description: Blazing fast static site generator written in pure C. Jekyll-inspired frontmatter, Liquid-like templating, 0.4s for 1000 pages.
  text: No Node, No Go, No Rust. Just pure C, zero dependencies, and raw speed. Built for developers who love control and performance.
  button1:
    text: Download
    url: "https://creativitaz.gumroad.com/l/cax-minimalis"
  button2:
    text: Github
    url: "https://github.com/mesinkasir/cax-minimalis"

intro:
  title: Why CAX?
  image: /img/c-ssg.svg
  description: Modern DX with 1972 Power
  text: We combined Jekyll's and ELeventy 11ty elegant frontmatter experience with C's raw performance. No GC pauses, no heavy runtime, just a single 400KB binary that builds your entire site in milliseconds.

card_info:
    - title: 0.4s Builds
      image: /img/rocket.svg
      description: Blazing Fast
      text: Built with pure C, direct memory allocation and mmap file reading. 1000 pages in 0.4s. Hugo is 0.8s, Eleventy is 12s. CAX wins.

    - title: Jekyll Way
      image: /img/build.svg
      description: Familiar DX
      text: Supports hero.title nested frontmatter, collection controllers like content/posts.md, pagination with prev/next fix, tags, and Liquid-like {% for %} {% if %} templates.

    - title: Zero Deps
      image: /img/satelit.svg
      description: Single Binary
      text: No Node_modules, no Go mod, no libyaml. Just gcc and make. Binary <500KB, runs anywhere from Raspberry Pi to your server.

footer:
  title: Ready to Go Blazing Fast?
  image: /img/alien.svg
  description: Join developers who switched to C for static sites.
  text: MIT Licensed. Built with passion by Axcora ecosystem. Free forever.

update: 
  title: Article Update
  image: /img/satelite.svg
  button: 
    text: Explore All Artcile
    url: /minimal/

---

### Quick Start

```bash
git clone https://github.com/mesinkasir/cax-minimalis
cd cax-minimalis
mingw32-make clean
mingw32-make
cax build
cax start
open http://localhost:8080
```

Visit http://localhost:8080 - LiveReload in 100 lines of C.


### Features at a Glance

- **Nested Frontmatter**: `hero.title`, `button.text` auto-parsed
- **Collection Controllers**: `content/posts.md` controls `/posts/`
- **Smart Pagination**: No more `/page/1/` 404
- **Axcora CSS**: Modern UI with 12KB CSS
