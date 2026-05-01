# Active Context

## Current focus
v1 coming-soon landing page is shipped. CSS is now its own file and a
mobile-responsive refinement pass has been applied.

## Most recent work
- Extracted all CSS from `index.html` into a new `styles.css`. `index.html`
  now references it via `<link rel="stylesheet" href="styles.css">`.
- Mobile-responsive refinements added in `styles.css`:
  - Form `field-grid` (Email + Phone side-by-side) stacks to 1 column ≤ 520 px.
  - Stats grid steps 3 → 2 → 1 columns at 560 / 380 px.
  - Services grid → 1 column ≤ 380 px.
  - Hero CTA goes full-width ≤ 480 px.
  - Hero visual shrinks at 900 / 480 px breakpoints.
  - Brand tagline hides ≤ 420 px (logo + name only).
  - City pills tighten padding ≤ 480 px; confetti shapes shrink ≤ 600 px.
  - About-collage moves above copy when stacked.
  - Form inputs locked to `font-size: 16px` to prevent iOS Safari focus zoom.
- HTML structure and JS behavior are unchanged.

## Earlier work (this project)
- Built `index.html` originally with embedded CSS + JS, no external libs.
- All sections delivered per spec: Header, Hero (Coming Soon badge + CTA),
  About / Launching Soon, Services (4 cards), Service Area, Waitlist Form,
  Footer.
- Brand decision locked: logo is the visible business name
  ("Backyard Party Rentals"), and "DFW Yard Games" is the **domain only**.
  All visible copy that referenced "DFW Yard Games" was updated to
  "Backyard Party Rentals" accordingly.
- Logo image (`logo.png`) is shown in the header brand mark, hero card,
  and footer.
- Form is validated client-side only (name, email, phone, optional date,
  optional message). On success the form swaps to a success state.
- Memory bank initialized.

## Open decisions / questions
- None blocking. (Domain `dfwyardgames.com` and email
  `info@dfwyardgames.com` are placeholders until the domain is live.)

## Next likely steps (not yet done)
1. Wire the waitlist form to a real capture target
   (Formspree, Netlify Forms, Mailchimp, or a backend endpoint).
2. Replace CSS-generated placeholder graphics with real event photos
   once they exist.
3. Add basic analytics (privacy-friendly) to track waitlist conversion.
4. Add `Open Graph` / Twitter card metadata for link previews.
5. Add a `robots.txt` and basic `sitemap.xml` once a domain is live.
6. Accessibility pass: confirm color contrast on all states, keyboard
   nav, and focus-visible styles in real browsers.

## Constraints to remember
- Static site only — `index.html` + `styles.css` + a small embedded `<script>`.
  **No external libraries / fonts / CDNs.**
- All imagery beyond `logo.png` must be CSS-generated.
- No backend logic. No DB migrations. No deploys without explicit ask.
