---
title: Building a Template Engine: Mustache Meets Liquid in C
description: How CAX template engine supports {{variables}}, {% for %}, {% if %}, and nested layouts.
layout: post.cax
image: /img/minima/cssg.webp
tags: [c, template-engine, liquid]
author: Axcora
date: 2026-05-12
---

## Goals

We needed:

- `{{hero.title}}` nested lookup
- `{% for post in pagination.items %}`
- `{% include header.cax %}`
- `--- layout: base.cax ---` chaining

### Nested Lookup

```c
const char* get_nested_value(ctx, "hero.title"){
  obj = get_pointer(ctx, "hero");
  return get_string(obj, "title");
}
```

### Layout Chaining

`cax_template_render_file` checks if file starts with `---`. If yes, it renders body, then injects as `{{content}}` into parent layout. Just like Jekyll.

Clean, fast, no regex hell.
