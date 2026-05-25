# Blog — Claude Code Guide

## Stack

- **Astro 6** — static site generator
- **Sveltia CMS** — browser-based content editor at `/admin`
- **GitHub Pages** — hosting via GitHub Actions
- **Lora** (Google Fonts) — serif typography

## Development

```bash
npm run dev       # start dev server at http://localhost:4321
npm run build     # build to dist/
npm run preview   # preview the built site locally
```

## Project structure

```
src/
  content.config.ts       # content collection schema
  content/posts/          # Markdown post files
  layouts/
    Base.astro            # HTML shell + header
    Post.astro            # single-post layout
  pages/
    index.astro           # homepage (post list)
    posts/[id].astro      # individual post page
  styles/global.css       # all CSS

public/
  admin/
    index.html            # Sveltia CMS loader
    config.yml            # CMS collection config
```

## Writing posts

Posts live in `src/content/posts/` as Markdown files.

Frontmatter fields:
```yaml
---
title: My Post Title       # required
date: 2026-05-25           # required, YYYY-MM-DD
description: A summary.    # optional, shown in post list
lang: en                   # optional, "en" or "sv"
---
```

The filename becomes the URL slug: `hello-world.md` → `/posts/hello-world`.

## CMS setup (Sveltia CMS + GitHub Pages)

1. Create a GitHub OAuth App at https://github.com/settings/developers
   - Application name: Blog CMS (or anything)
   - Homepage URL: `https://martinleino.github.io`
   - Authorization callback URL: `https://martinleino.github.io/blogg/admin/`

3. Open `https://YOUR_USERNAME.github.io/admin/` in a browser and authenticate with GitHub.

## Deploying to GitHub Pages

1. `astro.config.mjs` is already configured:
   ```js
   site: 'https://martinleino.github.io',
   base: '/blogg',
   ```

2. In the GitHub repo settings:
   - Go to Settings → Pages
   - Set source to "GitHub Actions"

3. Push to `main` — the workflow in `.github/workflows/deploy.yml` builds and deploys automatically.

## Changing the blog title

The site title is set in `src/layouts/Base.astro`:
```astro
const siteTitle = 'My Blog';
```

Change that string and rebuild.
