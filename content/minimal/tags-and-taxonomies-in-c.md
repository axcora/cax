---
title: Tags and Taxonomies Without Database in C
description: Generating /tags/c.html automatically from frontmatter tags: [c, blog] using hash maps in C.
layout: post.cax
image: /img/minima/ssg-with-c.webp
tags: [c, taxonomy, tags]
author: Axcora
date: 2026-05-17
---

## How Tags Work

In post:

```yaml
tags: [c, blog]
```

Builder:

1.  Scan all `master_array`
2.  `tags_map[tag] -> array of posts`
3.  For each tag, render `templates/layouts/tag.cax`

```c
CAXObject *tags_map = cax_object_new();
for each post:
  for each tag in post.tags:
    add post to tags_map[tag]
```

Now `/tags/c/index.html` exists with 5 posts. No DB, just C arrays. Jekyll would be proud.
