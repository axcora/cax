---
title: JSON Data Files — Centralize Your Configuration
description: How to use JSON files for site-wide data in CAX SSG.
layout: starter/detil.cax
image: /img/minima/jekyll-11ty-astro.webp
tags: ["json", "data", "configuration"]
date: 2026-06-23
author: CAX Team
---
CAX SSG loads any `.json` file from the `_data/` directory and makes it available in templates. Access data with `{{ filename.key }}` syntax. Use JSON for navigation, metadata, site settings, and any reusable data.

JSON files keep your content clean and your configuration centralized.