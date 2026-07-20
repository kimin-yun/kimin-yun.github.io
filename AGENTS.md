# Repository Guidelines

## Project Structure & Module Organization

This repository contains Kimin Yun's static academic website, published from the repository root through GitHub Pages.

- `index.html` contains the page structure, content, inline styles, and the small JavaScript video-lightbox implementation.
- `data/` stores publication thumbnails, profile images, and the linked CV PDF. Use relative paths such as `data/26-icpr.png`.
- `bibtex/` contains downloadable citation text files.
- `stylesheet.css` is a separate style artifact, but the current page styling is primarily defined in `index.html`; confirm a stylesheet is linked before changing it.
- `CV_kmyun.tex` and the root PDF are CV source/output artifacts.

## Build, Test, and Development Commands

Always synchronize the personal website before editing:

```sh
git pull --ff-only origin master
```

Resolve any synchronization issue before changing files. There are no dependencies, build step, automated tests, or lint tasks. Preview changes from the repository root:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/`. A direct browser open of `index.html` is also suitable. Before submitting, inspect both desktop and narrow mobile layouts, click internal navigation, and verify new image, PDF, publication, and video links.

## Coding Style & Naming Conventions

Preserve the existing compact HTML/CSS style and semantic grouping. Use two-space indentation for newly expanded HTML and JavaScript; keep CSS declarations consistent with the surrounding block. Reuse existing classes and CSS custom properties (`--ink`, `--muted`, `--link`) instead of introducing near-duplicates. Give images useful `alt` text and add `loading="lazy"` to non-hero images.

Name publication images `data/YY-short-name.ext`, for example `data/26-icpr.png`. Keep publications newest-first, grouped by year. Bold Kimin Yun in author lists, retain contribution markers, and use relative repository paths for local assets.

## Testing Guidelines

Validation is manual. Check the browser console for errors, resize below the `680px` responsive breakpoint, and confirm that embedded YouTube lightboxes close via button, backdrop, and Escape key. Ensure every newly referenced local file is tracked and matches path capitalization.

## Commit & Pull Request Guidelines

Recent commits use short, imperative summaries such as `Update banner-understanding demo video link` and `Optimize images: resize thumbnails + lazy-load`. Keep commits focused on one content or presentation change. Pull requests should explain the visible change, list manual checks, link relevant issues or publication sources, and include before/after screenshots for layout or styling updates. Do not commit or publish sensitive contact or configuration data.
