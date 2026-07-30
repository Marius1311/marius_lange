# Marius Lange

Source for [mariuslange.com](https://mariuslange.com). Built with [Hugo](https://gohugo.io) and the
[Blowfish](https://blowfish.page) theme, deployed by Netlify from `main`.

## Building locally

Prerequisites — Hugo must be the **extended** build, and Go is needed because the theme is consumed
as a Hugo module:

```bash
brew install hugo go
```

Then, from the repo root:

```bash
hugo server
```

That's it — <http://localhost:1313>, with live reload. The first run downloads the theme (~65 MB)
and takes a minute; afterwards it starts in well under a second.

To reproduce exactly what Netlify publishes, into `public/`:

```bash
hugo --gc --minify --cleanDestinationDir
```

If something looks stale, delete the build state and retry:

```bash
rm -rf public resources .hugo_build.lock
```

## Adding a post

One directory per post under `content/post/`, with the body in `index.md`:

```
content/post/my_new_post/
├── index.md
└── featured.png    # optional; any file starting with `feature` is picked up
```

Front matter — only `title` and `date` are required:

```yaml
---
title: "Post title"
description: "One-line summary, used for the meta description"
date: 2026-07-30T12:00:00Z
draft: false
tags:
  - CellRank
  - single-cell
categories:
  - News
---
```

Tags and categories render exactly as written, so keep the stylised lowercase of tool names
(`moscot`, `moslin`, `cell-annotator`). `hugo server -D` also renders drafts.

## Where things live

| What | Where |
|---|---|
| Homepage bio, Interests, Education & Experience | `content/_index.md` |
| Name, headline, avatar, social links | `config/_default/languages.en.toml` |
| Theme options (colour scheme, search, homepage layout) | `config/_default/params.toml` |
| Nav bar | `config/_default/menus.en.toml` |
| Core Hugo settings (URLs, taxonomies, pagination) | `config/_default/hugo.toml` |
| Custom CSS | `assets/css/custom.css` |
| Redirects | `netlify.toml` |

No theme template is overridden anywhere — content is plain Markdown and the only styling is three
rules in `custom.css`. Keep it that way: it is what makes a future theme change cheap.

## Upgrading the theme

Deliberately, with an explicit version:

```bash
hugo mod get github.com/nunocoracao/blowfish/v2@v2.106.0
```

Never `hugo mod get -u` — it silently ignores the pin in `go.mod`. Blowfish also declares a maximum
supported Hugo version, so if a build breaks right after `brew upgrade hugo`, check that first.
