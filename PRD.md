# Product Requirements — Personal Blog

## Purpose

A personal blog for publishing essays and reflections in English and Swedish, aimed at a general audience. The site should feel like a place for considered writing — not a portfolio, not a news feed. Emphasis on reading comfort and simplicity.

## Goals

- Make it easy to write and publish posts without touching code
- Deliver a clean, typographically focused reading experience
- Deploy reliably via GitHub Pages at no cost
- Keep the codebase small and maintainable

## Non-goals

- Comments or social features
- Search
- Tags or categories (can be added later if needed)
- Analytics (can be added later)
- A separate About page (can be added later)

## User stories

| As... | I want to... | So that... |
|---|---|---|
| Author | Write a new post in a web editor | I don't need to edit files or use git directly |
| Author | Set a title, date, and optional description per post | Posts are well-organized and previewable |
| Author | Indicate the language of each post (en/sv) | Readers know what to expect |
| Reader | See a clean list of posts sorted newest first | I can find what's new quickly |
| Reader | Read a post in a comfortable, distraction-free layout | Long-form reading is pleasant |
| Reader | Visit the blog on mobile | The site adapts to small screens |

## Features

### MVP (this project)

- Post list homepage: title, date, optional description; sorted newest first
- Individual post pages with serif typography
- Bilingual support: posts can be written in English or Swedish
- Browser-based CMS at `/admin` (Sveltia CMS + GitHub backend)
- GitHub Actions deployment to GitHub Pages
- Responsive layout (mobile-friendly)

### Deferred / future

- RSS feed
- About page
- Tags / categories
- Open Graph meta tags for social sharing
- Dark mode
- Syntax highlighting for code blocks

## Design decisions

| Decision | Choice | Rationale |
|---|---|---|
| Framework | Astro | Static output, great Markdown support, deploys anywhere |
| CMS | Sveltia CMS | Works with GitHub Pages without a server-side OAuth proxy |
| Fonts | Lora (Google Fonts) | Elegant serif, designed for screen reading |
| Max content width | 680px | Comfortable line length for reading |
| Color scheme | White background, near-black text | Maximum readability |
| Navigation | None (just a title link) | Fewer pages = no need for nav |

## Open questions

- **Blog name**: Not yet decided. Currently using placeholder "My Blog" in `src/layouts/Base.astro`.
- **GitHub repo name**: Needed to configure the CMS backend (`public/admin/config.yml`) and the Astro site URL (`astro.config.mjs`).
- **Custom domain**: User may want a custom domain instead of a GitHub Pages subdomain — no decision yet.
