---
title: Memory Safety in C SSG Without Rust
description: Patterns we use to avoid leaks and segfaults in CAX: arenas, object pools, and strict free ownership.
layout: post.cax
image: /img/minima/fast-ssg-c.webp
tags: [c, memory-safety, systems]
author: Axcora
date: 2026-05-15
---

## Is C Unsafe? Only If You Code Unsafe.

Our rules:

1.  **Every `cax_object_new()` has `cax_object_free()` in same scope**
2.  **No global state** - pass `CAXObject *ctx`
3.  **Copy, don't reference** - `copy_all()` for context

```c
CAXObject *ctx = cax_object_new();
copy_all(global_data, ctx);
copy_all(ctrl, ctx);
// use
cax_object_free(ctx);
```

We run `valgrind` on every build:

```
==123== All heap blocks were freed -- no leaks are possible
```

C can be safe. You just need discipline.
