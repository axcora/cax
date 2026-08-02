---
title: About CAX
description: Why CAX was created - Blazing fast Static Site Generator in pure C for everyone
layout: starter/info.cax
---

## About CAX

CAX was created for one simple reason: **make static site generation easy, fast, and accessible for everyone.**

No Node.js. No npm install. No waiting.

Just C.

### Why CAX Was Created

Most static site generators today require heavy dependencies, complex setup, and slow builds.

CAX solves that:

- You want to build a blog, fast?
- You want zero dependencies?
- You want 0.4s builds, not 40s?
- You want Eleventy experience but in C?

That is why CAX exists.

We built CAX for developers, bloggers, creators, and anyone who wants simplicity without sacrificing power.

### Advantages of CAX

**1. Blazing Fast**
Built in pure C. Builds 100+ pages in under 0.4s.

**2. Zero Dependencies**
No Node.js, no npm, no Python required for build. Just one binary: cax.exe.

**3. Eleventy Compatible Experience**
- Frontmatter YAML
- _data/ global data - JSON, YAML, YML
- Layouts and partials
- Collections and pagination
- Includes, if else, for loops

**4. Clean Production Build**
- cax build = 100% clean, no dev scripts
- cax serve = production preview
- cax start = dev only with live reload

**5. Live Reload**
Auto watch content/, templates/, _data/, public/ and rebuild instantly.

**6. Production Ready**
- Auto minified CSS
- Sitemap.xml, RSS, JSON Feed, robots.txt auto generated
- SEO friendly
- Deploy anywhere: Netlify, Vercel, Cloudflare Pages

**7. Simple Templating**
Easy to learn:

```html
{{ title }}
{% for post in posts %}{{ post.title }}{% endfor %}
{% include header.cax %}
```

**8. Lightweight**
Binary size under 1MB. Output is pure static HTML.


#### Installation

```bash
git clone https://github.com/mesinkasir/cax
cd cax
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

## Goal

Our goal is to make CAX the fastest and simplest SSG in the world, while keeping it powerful and extensible.

## Support This Project

CAX is open source and free forever. If you find it useful, please consider supporting:

**GitHub Sponsors:**
[https://github.com/sponsors/mesinkasir](https://github.com/sponsors/mesinkasir)

**PayPal:**
[https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=JVZVXBC4N9DAN](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=JVZVXBC4N9DAN)

**Gumroad:**
[https://creativitaz.gumroad.com/coffee](https://creativitaz.gumroad.com/coffee)

Your support helps us maintain, improve, and add more features to CAX.

Every dollar keeps CAX fast, free, and alive.

## Author

Built with love by Axcora

- Website: https://www.axcora.com
- GitHub: https://github.com/mesinkasir

## License

MIT License - Free for personal and commercial use.
