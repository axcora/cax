---
title: Implementing Jekyll-Inspired Frontmatter Parser in Pure C
description: How we built a YAML frontmatter parser that supports nested objects like hero.title without libyaml.
layout: post.cax
image: /img/minima/jekyll-11ty-astro.webp
tags: [c, yaml, frontmatter, jekyll]
author: Axcora
date: 2026-05-11
---

## The Challenge

We wanted Jekyll DX:

```yaml
hero:
  title: Blog - CAX SSG
  info: Editorial
```

But in C. No `libyaml`, no dependencies.

### Solution: Indent Stack

We implemented a stack-based parser:

- Track indent level
- `hero:` -> push new CAXObject
- `  title:` -> set string in top object

```c
CAXObject *stack[16];
int indent_stack[16];
while(line){ if(indent>stack[top]) push(); }
```

Now `{{hero.title}}` works in `*.cax` templates. Zero dependency, 200 lines.
