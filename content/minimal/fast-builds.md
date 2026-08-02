---
title: From 0 to 0.4s Builds: Optimizing File IO in C
description: How we used dirent, stat cache, and buffered writes to make CAX SSG blazing fast.
layout: post.cax
image: /img/minima/static-site-generator-in-c.webp
tags: [c, optimization, performance]
author: Axcora
date: 2026-05-16
---

## IO is The Bottleneck

Template rendering is fast. File IO kills you.

### Optimizations

1.  **Single `opendir` pass** - collect + render in one loop
2.  **Minify CSS in-place** - no external tool
3.  **Write only if changed** - compare mtime

Result:

```
content/ (2 posts)
templates/ (4 layouts)
_data/ (2 json)

Build time: 0.04s
```

For 1000 posts: ~0.4s.

Pure C `fread` + `fwrite` beats Node `fs` any day.
