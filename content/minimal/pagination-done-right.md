---
title: Pagination Done Right: Fixing the /page/1 404 Trap
description: The classic pagination bug that breaks prev_url on page 2 and how we fixed it in CAX SSG.
layout: post.cax
image: /img/minima/cax-c-static-site-generator.webp
tags: [c, pagination, webdev]
author: Axcora
date: 2026-05-13
---

## The Bug

Page 2 had:

```html
<a href="/posts/page/1/">Prev</a> // 404!
```

### The Fix

Jekyll Way:

- Page 1 = `/posts/index.html`
- Page 2 prev = `/posts/` NOT `/posts/page/1/`
- Page 3 prev = `/posts/page/2/`

```c
if(p==1) prev="/%s/";
else if(p>1) prev="/%s/page/%d/";
```

One if-else, 404 gone. UX matters even in C.
