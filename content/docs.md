---
layout: page.cax
title: CAX Documentation
description: Complete guide for CAX - Blazing fast Static Site Generator in pure C
image: /img/minima/cax-opening.webp
---

## CAX Documentation

CAX is a blazing fast Static Site Generator written in pure C. Inspired by [Eleventy 11ty](https://11ty.dev), built for speed.

#### Installation

```bash
git clone https://github.com/mesinkasir/cax-minimalis
cd cax-minimalis
mingw32-make
```

#### Commands

| Command | Description |
|---------|-------------|
| `cax init` | Initialize project structure |
| `cax build` | Build production site to site/ - clean, no live.js |
| `cax serve` | Serve production preview at http://localhost:8080 |
| `cax start` | Dev mode - Serve + Watch + Live Reload |
| `cax watch` | Alias of start |

#### Project Structure

```
.
├── content/          ## Markdown content
│   ├── index.md
│   ├── about.md
│   └── posts/        ## Collection
├── _data/            ## Global data
│   ├── metadata.json
│   ├── nav.json
│   ├── social.yaml   ## YAML supported
│   └── config.yml    ## yml also supported
├── templates/
│   ├── layouts/      ## default.cax, home.cax, posts-list.cax
│   └── partials/     ## header.cax, footer.cax
├── public/           ## Static assets copied to site/
└── site/             ## Output generated
```

#### Frontmatter

Supports YAML nested objects and list of objects:

```yaml
---
title: My Post
layout: default.cax
hero:
  title: Welcome
  subtitle: Fast SSG
features:
  - title: 0.4s Builds
    desc: Blazing fast
    icon: fast
  - title: Zero Deps
    desc: No Node.js needed
tags:
  - c
  - ssg
---
```

#### Data Files

Eleventy-style auto loading. Supports JSON and YAML.

_data/social.yaml:

```yaml
github: https://github.com/mesinkasir
links:
  - title: Docs
    url: /docs/
  - title: Blog
    url: /posts/
```

Usage in template:

```html
{{ social.github }}
{% for link in social.links %}
  <a href="{{ link.url }}">{{ link.title }}</a>
{% endfor %}
```

Supported: _data/*.json, *.yaml, *.yml

#### Templating Engine

Variables:

```html
{{ title }}
{{ site.title }}
{{ social.github }}
{{ hero.title }}
```

If Else:

```html
{% if title %}
  <h1>{{ title }}</h1>
{% endif %}

{% if not description %}
  No description
{% else %}
  {{ description }}
{% endif %}

{% if pagination.prev_url %}
  <a href="{{ pagination.prev_url }}">Prev</a>
{% endif %}
```

For Loops:

```html
{% for post in posts %}
  <h2>{{ post.title }}</h2>
{% endfor %}

{% for link in social.links %}
  {{ link.title }} - {{ link.url }}
{% endfor %}
```

Includes:

```html
{% include header.cax %}
{% include footer.cax %}
```

#### Collections and Pagination

Create controller file content/posts.md:

```yaml
---
collection: posts
layout: posts-list.cax
title: Blog Posts
pagination: 6
---
```

This will scan content/posts/*.md and generate paginated list at /posts/, /posts/2/, etc.

#### Live Reload Development

```bash
cax start
```

- Watches content/, templates/, _data/, public/
- Auto rebuild on change
- Auto inject __cax_live.js - DEV ONLY
- Auto open browser at http://localhost:8080

Production build is always clean:

```bash
cax build
cax serve
```

No live.js in production.

#### Deployment

Upload site/ folder to Netlify, Vercel, Cloudflare Pages, or any static hosting.

```bash
cax build
```

#### Features

- Written in pure C
- 0.4s builds for 100+ pages
- Zero dependencies
- Minified CSS auto
- Sitemap, RSS, JSON Feed auto generated
- YAML and JSON data support
- Nested objects and list of objects


#### Support This Project

CAX is open source and free forever. If you find it useful, please consider supporting:

**GitHub Sponsors:**
[https://github.com/sponsors/mesinkasir](https://github.com/sponsors/mesinkasir)

**PayPal:**
[https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=JVZVXBC4N9DAN](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=JVZVXBC4N9DAN)

**Gumroad:**
[https://creativitaz.gumroad.com/coffee](https://creativitaz.gumroad.com/coffee)

Your support helps us maintain, improve, and add more features to CAX.

#### License

MIT - By Axcora - www.axcora.com
