# Progress Log

> Append-only log of completed work. Newest entries on top.

---

## 2026-05-01 — Fulfillment model messaging updated (pickup/return default)

**Status:** Complete.

**Done:**
- Updated public-facing copy in `index.html` to reflect a **pickup & return** default model.
- Clarified that **delivery & pickup is available for an additional fee**.
- Updated `memory-bank/projectbrief.md` to match the new messaging.

**Notes:**
- Hero positioning kept neutral (no delivery-first headline).

---

## 2026-04-30 — CSS extracted to its own file + mobile-responsive pass

**Status:** Complete.

**Done:**
- Moved all CSS out of the inline `<style>` block in `index.html` into a
  new `styles.css`. `index.html` now links it from the `<head>`.
- Applied a mobile-responsive refinement pass in `styles.css`:
  - Form `field-grid` (Email + Phone side-by-side) stacks to 1 column
    ≤ 520 px so neither field gets cramped on a phone.
  - Stats grid steps 3 → 2 → 1 columns at 560 / 380 px.
  - Services grid collapses to a single column ≤ 380 px.
  - Hero CTA goes full-width below 480 px (thumb-friendly).
  - Hero visual scales down at 900 / 480 px so the logo card doesn't
    dominate small screens.
  - Header brand tagline hides ≤ 420 px; brand mark shrinks slightly.
  - City pills tighten padding & icon size ≤ 480 px.
  - Confetti decoration shrinks ≤ 600 px and one piece is hidden.
  - About-collage reorders above the copy when stacked.
  - Form inputs use `font-size: 16px` to prevent iOS Safari's
    auto-zoom on focus.

**Verified:**
- Linter: clean across the project.
- File layout: `index.html` (markup + JS), `styles.css` (all styles),
  `logo.png`, `memory-bank/`.

---

## 2026-04-30 — v1 coming-soon landing page shipped

**Status:** Complete (front-end only, no backend wiring yet).

**Done:**
- Created `index.html` — single self-contained file with embedded CSS + JS,
  no external libraries, no CDN requests.
- Implemented all sections from spec:
  - Sticky glass-effect header with logo, nav links, and primary CTA.
  - Hero with "Coming Soon" badge, headline + gold accent word, subheadline,
    primary CTA, promo note, animated confetti shapes, and a logo card.
  - About / "Launching Soon Across DFW" with 3 stat tiles and a
    CSS-only collage visual.
  - Services grid — 4 rounded cards with hover lift, soft shadows, and
    pure-CSS icons (cornhole, NERF dart, gift package, delivery truck).
  - Service Area — deep-navy section with 9 city pills.
  - Waitlist form — Full Name, Email, Phone, Planned Event Date,
    Message; live client-side validation; phone auto-formatting;
    today-or-later date enforcement; success state on valid submit.
  - Footer — brand mark, contact email, Facebook + Instagram CSS
    glyphs, copyright, domain reference.
- Mobile responsive (hamburger nav < 820px, single-column stacks
  < 880–900px).
- `prefers-reduced-motion` honored for all animations.
- Smooth scroll, IntersectionObserver reveal-on-scroll, sticky-header
  shadow on scroll.
- Brand decision applied: visible name = "Backyard Party Rentals";
  "DFW Yard Games" appears only as the domain reference.
- Initialized `memory-bank/` with all 6 required files.

**Verified:**
- Linter: clean (no errors reported on `index.html`).
- File size: single ~30KB HTML + the existing logo.png.

**Not yet done / explicit non-goals for v1:**
- Form does not submit anywhere — it's purely client-side. Needs to be
  wired to Formspree, Netlify Forms, or similar before real launch.
- No analytics, no Open Graph metadata, no sitemap/robots.
- No real photography — all decorative graphics are CSS only.
