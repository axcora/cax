---
title: Future of CAX: What’s Next for C Static Site Generator
description: Roadmap for CAX SSG: image optimization, shortcodes, and WebAssembly build.
layout: post.cax
image: /img/minima/cax-opening.webp
tags: [c, roadmap, ssg]
author: Axcora
date: 2026-05-19
---

## Where We Are

- [x] Frontmatter nested objects
- [x] Liquid-like templates
- [x] Collections + Pagination
- [x] Tags + Sitemap

## What’s Next

### v0.2
- Image resize with `stb_image.h`
- Shortcodes: `{{< youtube id >}}`

### v0.3
- Incremental builds (only changed files)
- WASM build: `cax.wasm` runs in browser

### v1.0
- Plugin system with `dlopen`
- `cax deploy` to Cloudflare Pages

**Philosophy:** Keep binary <500KB, zero deps, <1s builds forever.

Want to contribute? PR at github.com/axcora/cax
