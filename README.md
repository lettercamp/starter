# Lettercamp starter

A small content-only starter for a Lettercamp publication. **Fieldnotes** is the sample publication, with a homepage, three original sample posts, and original cover artwork.

The starter is organized around readable content files and a simple editorial publication format. All sample articles and cover artwork are original.

## Files

```text
site.json                 Publication name, description, author, and navigation
pages/index.mdx            Homepage with an introduction and three story cards
pages/posts/*.mdx          Individual posts and their metadata
public/favicon.svg        Publication icon
public/images/*.png       Cover and Open Graph images (1200 × 630)
assets/covers/*.svg        Editable originals for the cover artwork
```

This repository intentionally contains no application dependencies, renderer, or deployment configuration. It is not a runnable Astro project yet. The shared Lettercamp renderer will be added separately; there is no preview command at this stage.

## Customize it

1. Update the publication details in `site.json`.
2. Edit the introduction and story list in `pages/index.mdx`.
3. Replace the sample posts and images with your own content.

The homepage is ordinary Markdown inside an MDX file, including image links and story summaries. For now, maintain its list manually when adding or changing posts. It does not depend on an unimplemented custom component or automatic feed.

## Content conventions

These are the starter's conventions for the future renderer, not built-in Astro behavior:

- `pages/index.mdx` maps to `/`.
- `pages/posts/example.mdx` maps to `/posts/example/`.
- `public/` files are served from the site root: `public/images/example.png` becomes `/images/example.png`.
- `layout: home` identifies the publication homepage; `layout: post` identifies an article.
- The renderer should use the frontmatter `title` as the page heading and `description` for metadata. Post bodies start below that heading.
- Post `date` values are quoted `YYYY-MM-DD` strings, representing calendar dates without timezone conversion. Sort posts newest first when adding an automatic feed.
- `image` and `imageAlt` describe the article cover; `ogImage` specifies the social sharing image. The samples reuse the same PNG for both.
- The renderer should resolve image paths to absolute URLs using the deployed site's origin when generating Open Graph metadata. The template does not hard-code a deployment domain.
- `site.json` supplies publication defaults, including the fallback author and OG image.

Example post frontmatter:

```yaml
---
title: "Your next story"
description: "A short introduction for the homepage and search results."
layout: "post"
date: "2026-10-14"
author: "Your name"
image: "/images/your-next-story.png"
imageAlt: "A useful description of the cover image."
ogImage: "/images/your-next-story.png"
---
```

All sample MDX uses plain Markdown. There are no JavaScript imports, executable expressions, custom components, or external image dependencies. Search, subscriptions, comments, and chat are not wired up.
