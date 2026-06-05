# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page static personal portfolio site for Khamphay Sialimoua (back-end / IoT developer). Pure HTML + CSS — **no build step, no package manager, no JavaScript, no framework, no tests.** There is nothing to compile or install.

## Running / previewing

Open `index.html` directly in a browser, or serve the folder over HTTP (needed so the absolute-rooted CSS asset paths resolve correctly):

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

There is no lint, build, or test command — those concepts don't apply here.

## Structure

- `index.html` — the entire page. All content (hero, About, Projects, footer links) lives here.
- `assets/styles/index.css` — all styling. Uses **nested CSS** (native, e.g. `.header { .menu { ... } }`) and the `Righteous` font imported via `@import url('/assets/fonts/Righteous.ttf')`.
- `assets/images/`, `assets/fonts/` — local assets.
- `public/` — empty.
- Icons come from the Material Design Icons CDN (`mdi mdi-*` classes), loaded in the `<head>`.
- Tech-stack logos in the hero are hot-linked from **external third-party URLs** (mindrops.com, kinsta.com, licdn.com, etc.), not stored locally — they can break if those hosts change.

## Conventions / gotchas to preserve

- This codebase leans heavily on **inline `style="..."` attributes** in `index.html` alongside the external stylesheet. Match the existing approach rather than refactoring to classes unless asked.
- Nav anchors and section IDs are **mismatched** — e.g. nav links to `#her0` and `#contect`, but the hero section's id is `hero` and there is no `contact`/`contect` section (the footer is the de-facto contact area). Don't assume in-page anchor links currently work; fix IDs as a pair if touching navigation.
- The CSS `@import` points at a `.ttf` file, not a CSS file — fonts are effectively loaded by the browser falling back, not via a proper `@font-face`. Be aware if changing typography.
- The repo root and `assets/` contain committed `.DS_Store` files (macOS); avoid adding more.
