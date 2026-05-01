# Tech Context

## Stack
- **HTML5** — `index.html`, semantic landmarks.
- **CSS3** — external stylesheet `styles.css`, linked from `<head>`.
  Custom properties, grid, flexbox, `clamp()` fluid typography,
  `aspect-ratio`, `backdrop-filter`, `mask-image`, `clip-path`,
  `prefers-reduced-motion`.
- **Vanilla JS (ES5-friendly)** — embedded `<script>` at end of `<body>`,
  single IIFE. Uses `IntersectionObserver` (with a no-JS fallback that
  simply shows all `.reveal` elements).

## What's intentionally NOT used
- No frameworks (React, Vue, Svelte, etc.).
- No CSS frameworks (Tailwind, Bootstrap, etc.).
- No CDN-loaded fonts (only system font stacks).
- No icon libraries — icons are CSS-only.
- No backend, no database, no build step, no package manager.

## Browser support target
Modern evergreen browsers (Chrome, Edge, Firefox, Safari, mobile Safari,
Android Chrome). Layout uses widely supported features; `backdrop-filter`
on the sticky header degrades gracefully (just looks slightly less glassy
on older Safari/Firefox without the prefix).

## Fonts
- Display: native serif stack — `"Iowan Old Style", "Palatino Linotype",
  Palatino, "Book Antiqua", Georgia, serif`.
- UI / body: native sans stack — `-apple-system, BlinkMacSystemFont,
  "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`.

## Color palette
- Navy `#1B3A5C`, deep navy `#112944`
- Brand blue `#3F7CB8`, soft blue `#6FA0D0`, pale blue `#E6EFF8`
- Sun gold `#F4B942` (primary accent / CTA)
- Coral `#FF7A6B` (alert / playful accent)
- Grass green `#5BA85B` (success / checkmarks)
- Cream `#FFF8EC`, page bg `#FAFBFD`, alt bg `#F1F5FA`

## How to run / preview
Just open `index.html` in any modern browser. Double-click on Windows,
or `start index.html` from the directory. There is no dev server.

## File assets
- `logo.png` is the only real image. The hero card, header brand mark,
  and footer brand mark all reference it via relative path `logo.png`.
- If the logo file is moved or renamed, update:
  - `.brand-mark` background URL in `styles.css`
  - The hero `<img src="logo.png">` in `index.html`
  - The `<link rel="icon" href="logo.png">` in `index.html`
