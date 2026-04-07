# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev      # local dev server at http://localhost:4321
npm run build    # production build → dist/
npm run preview  # preview the built site
```

## Stack

- **Astro 4** – static output (`output: 'static'` in astro.config.mjs), deployed to Cloudflare Pages
- **Tailwind CSS** via `@astrojs/tailwind` – layout/spacing only; design tokens live in CSS variables
- **Satoshi** font family – woff/woff2 files in `public/fonts/`, referenced in `src/styles/global.css`

## Architecture

Single-page site with all content in `src/pages/index.astro`. Sections in order: Hero → Services → Work/Experience → About → Contact → Footer.

Design tokens (colours, typography scale) are CSS custom properties defined in `src/styles/global.css` under `:root`. Component classes (`.card`, `.btn-primary`, `.heading-lg`, etc.) are `@layer components` blocks in the same file — Tailwind is used for utilities inside those classes and for spacing/layout directly in the template.

`src/layouts/Layout.astro` handles `<head>` metadata, font preload, and structured data only.

Public assets: `public/fonts/` (Satoshi), `public/favicon.*`. Placeholder for profile photo: replace the `<div>` blocks labelled "Photo placeholder" in `index.astro` with `<img>` tags.

## Deployment

Cloudflare Pages — connect the GitHub repo and set build command `npm run build`, output directory `dist`. No environment variables required for static build.
