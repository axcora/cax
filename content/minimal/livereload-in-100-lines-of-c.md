---
title: LiveReload in 100 Lines of C and JS
description: How we added dev server with live reload using pure C file watcher and 10 lines of JS.
layout: post.cax
image: /img/minima/ssg-in-c.webp
tags: [c, dev-experience, livereload]
author: Axcora
date: 2026-05-18
---

## Dev UX Matters

`cax serve --watch` should reload.

### Implementation

**C watcher:**

```c
time_t last = scan_dir("content");
while(1){
  sleep(1);
  if(scan_dir("content") != last) rebuild();
}
```

**JS injection:**

```js
(function(){let h=null;setInterval(async()=>{
  let t=await fetch(location.href).then(r=>r.text());
  if(h===null) h=t.length; else if(h!=t.length) location.reload();
},1000)})();
```

No WebSocket. Just content-length compare. 100 lines total, works on Windows + Linux. Simple > fancy.
