# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

The personal academic website of Kimin Yun (senior researcher at ETRI / associate professor at UST), served via GitHub Pages at `kimin-yun.github.io`. It is a fully static site — no build step, no framework, no dependencies. Adapted from Jon Barron's / Sangdoo Yun's academic website template.

## Workflow

- **No build, no tests, no lint.** Edit files directly and open `index.html` in a browser to preview, or `python3 -m http.server` from the repo root.
- **Deploy = push to `master`.** GitHub Pages serves the repo root, so any commit to `master` publishes immediately. There is no staging branch.
- Fonts (Lato) load from Google Fonts CDN at runtime; everything else is committed locally.

## Structure

- `index.html` (~1300 lines) — the entire site. A nested-`<table>` layout with these sections in order: bio/profile header, Research blurb, **publications list**, Awards/Activities lists, Links footer.
- `stylesheet.css` — custom element styles. Note the **non-standard HTML tags** used as styling hooks: `<name>`, `<heading>`, `<papertitle>`. When adding content, reuse these tags rather than inventing classes.
- `data/` — all images (paper thumbnails, profile photos), plus `CV_kmyun.pdf`. Not tracked individually in normal edits beyond `git add`.
- `bibtex/` — citation `.txt` files linked from publication entries.

## Editing publications

Publications dominate the site. Each is one `<tr>` block inside the publications `<table>`, preceded by an HTML comment marking the venue (e.g. `<!-- AVSS'25 -->`). Newest papers go at the **top** of the list.

A publication entry follows this exact shape — copy an existing `<tr>` and adapt:

```html
<!-- VENUE'YY -->
<tr>
  <td style="padding:20px;width:25%;vertical-align:middle">
    <img src="data/YY-shortname.jpg" alt="..." width="160">
  </td>
  <td style="padding:20px;width:75%;vertical-align:middle">
    <a href="PAPER_URL" id="shortname">
    <papertitle>Paper Title</papertitle>
    </a>
    <br>
    Author One, <strong>Kimin Yun</strong>, Author Three
    <br>
    <em>Full Venue Name (ABBREV)</em>, YYYY
    <br>
    <a href="...">arXiv</a> / <a href="bibtex/...txt">bibtex</a>
  </td>
</tr>
```

Conventions to preserve:
- **Image naming:** `data/YY-shortname.ext` where `YY` is the 2-digit year (e.g. `25-TSA.jpeg`, `24-PLM.jpg`). Thumbnails are 160px wide.
- Wrap **Kimin Yun** in `<strong>` in every author list.
- Use `*` for equal contribution and `†` for corresponding author, with an explanatory `<p>` note inside the entry when used.
- The `id` on the anchor is a short slug used as a deep-link target; keep it unique.

## Notes

- This repo is non-code content; OMC's heavier agent/test/verification machinery is overkill here. Direct edits with a browser preview are the right altitude. Only commit/push when the user explicitly asks.
