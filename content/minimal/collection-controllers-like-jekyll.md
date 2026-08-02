---
title: Collection Controllers: The Missing Piece in C SSG
description: How content/posts.md acts as a controller for the whole collection, bringing hero, pagination, and layout in one file.
layout: post.cax
image: /img/minima/c-ssg-built-site-with-c.webp
tags: [c, collections, jekyll]
author: Axcora
date: 2026-05-14
---

## What is Collection Controller?

In Jekyll you have `_posts`. In CAX we have `content/posts.md`:

```yaml
---
layout: posts-list.cax
hero:
  title: Blog
  description: All articles
collection: posts
pagination: 6
---
Welcome text here.
```

This file is NOT a post. It's the **controller**:

- `collection: posts` tells builder to collect `content/posts/*.md`
- `hero` is injected to list template
- `content` body becomes welcome text
- `pagination` sets per_page

One file to rule them all. Clean separation of list vs single.
