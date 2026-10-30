# scoutaloud site

## Stack

- **Zola** static site generator
- **Sveltia CMS** for writing posts in the browser (`static/admin/`)
- Hosted on **Netlify**: every push to `main` runs `zola build` and deploys `public/`
- Templates are **Tera** in `templates/`, styles are hand-written **CSS** in `static/base.css`, content is **Markdown** in `content/`.

## Set up locally

```sh
brew install zola   # check: zola --version  → should be 0.23.6
zola serve          # http://127.0.0.1:1111
zola serve --drafts # include draft posts
```

## Writing a post

### Via the CMS (usual way)

1. Go to **https://scoutaloud.net/admin/**.
2. **Sign in with GitHub** (the `cybergrrl` account, which owns the repo). Login uses the GitHub OAuth provider configured in Netlify under *Site configuration → Access control → OAuth*. If the button errors, that provider needs re-adding there.
3. Pick a collection (**Blog Posts** or **Home & Away**), write, **Publish**.
4. Publishing commits `content/<collection>/<slug>/index.md` to `main`; Netlify redeploys in a couple of minutes.

### By hand

Create `content/blog/<slug>/index.md`:

```toml
+++
title = "Post title"
date = 2026-09-03
draft = false

[taxonomies]
tags = ["books"]
+++

Body in Markdown.
```

Colocate images in the same folder. Commit and push to `main`.

## Sections

Three, each a folder in `content/` with an `_index.md`. The nav is hardcoded in `templates/base.html`.

- **blog** – flat, all posts in `content/blog/`, sorted by date.
- **home-and-away** – trips and days out. One folder per outing; extra pages go in the same folder and link back with `[Back to itinerary](../)`.
- **projects** – mostly dormant.

## Taxonomies

Declared once in `config.toml`: `tags`, `categories` (both for the blog), and `xmas_genres` (Christmas-movies section only). Each generates term pages at `/tags/<term>/` etc., rendered as pills on post cards and post pages.

In practice: use **tags** freely, keep casing consistent (`books` and `Books` are two different pages). **categories** are wired up but left empty; only start using them if a small fixed set of broad buckets would help.

## Images

Colocate the file with the Markdown, then reference it by its built site path with the `img` component (`templates/components.html`):

```
{{ <img path="/home-and-away/krka/krka-1.jpg"
       alt="Krka waterfalls"
       caption="Krka" /> }}
```

Params: `path`, `alt`, `caption`, `class` (all optional except `path`). Max width is capped at 2500px via `config.toml`. CMS uploads land in `static/uploads/`.

## Zola

The Zola version is pinned in `netlify.toml` for deploys and `mise.toml` for local use.

#### To update Zola:

1. Check the [changelog](https://github.com/getzola/zola/blob/master/CHANGELOG.md) for breaking changes.
2. Change the version in both `mise.toml` and `netlify.toml`.
3. Run `mise install`, then `zola build` to check the site still builds.
4. Commit both files together, along with any template fixes.
