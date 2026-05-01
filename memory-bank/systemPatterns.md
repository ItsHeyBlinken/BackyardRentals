# System Patterns

## Architecture
Static site. No build step, no bundler, no framework.

```
BackyardRentals/
├── index.html       # Markup + a single embedded <script> at the bottom
├── styles.css       # All styles for the site
├── logo.png         # Provided brand logo (only real image asset)
└── memory-bank/     # Project memory / docs
```

CSS lives in `styles.css` and is linked via `<link rel="stylesheet" href="styles.css">`
in the `<head>`. JS is still embedded as a single IIFE at the end of `<body>` —
it's small enough that splitting it out has no real benefit yet.

## Code conventions
- Section structure: each major section is a `<section id="...">` so the
  nav links and hero CTA can scroll-anchor to them.
- CSS is organized top-down by concern, separated by clear banner comments:
  Design tokens → Reset/base → Buttons → Header → Hero → Section base →
  About → Services → Service Area → Waitlist → Footer → Reveal.
- Color, radius, shadow, and motion are driven by CSS custom properties
  on `:root` so the palette can be tuned in one place.
- All inline imagery (icons, decorative shapes, "photos") is generated
  with CSS — gradients, `::before/::after` pseudo-elements, `clip-path`,
  and `border-radius`. Only `logo.png` is a real image.
- JavaScript is one IIFE at the end of `<body>`, with these
  responsibilities only:
  1. Stamp the current year in the footer.
  2. Add a `.scrolled` class to the header for the soft-shadow state.
  3. Toggle the mobile nav.
  4. `IntersectionObserver`-driven `.reveal` animations.
  5. Waitlist form: live validation, gentle phone formatting, today-or-later
     date `min`, swap to success state on valid submit.

## Responsive breakpoints
The layout is fluid (driven by `clamp()` for fonts, padding, and gaps).
Discrete media-query breakpoints kick in at:

| Width    | What changes                                                      |
|----------|-------------------------------------------------------------------|
| ≤ 900 px | Hero stacks (copy above visual). Hero visual shrinks.             |
| ≤ 880 px | About & waitlist grids stack to 1 column. About collage moves up. |
| ≤ 820 px | Header collapses to hamburger menu; nav CTA hides.                |
| ≤ 760 px | Footer collapses to 1 column.                                     |
| ≤ 600 px | Confetti shapes shrink; one is hidden.                            |
| ≤ 560 px | Stats grid → 2 columns (3rd tile spans full width).               |
| ≤ 520 px | Form `field-grid` (Email + Phone) stacks to 1 column.             |
| ≤ 480 px | Hero CTA goes full width. Hero visual shrinks again. Pills shrink.|
| ≤ 420 px | Header tagline hides; brand mark shrinks.                         |
| ≤ 380 px | Stats grid → 1 column. Services grid → 1 column.                  |

Form inputs use `font-size: 16px` to prevent iOS Safari's auto-zoom on focus.

## Patterns / decisions worth keeping
- **Single funnel.** Every CTA points at `#waitlist`. Don't add new CTAs
  that pull traffic elsewhere unless there's a clear reason.
- **Brand display rule.** The logo *is* the business name. The string
  "Backyard Party Rentals" appears in text alongside it. "DFW Yard Games"
  is referenced only as the domain.
- **Front-end-only form.** Submitting valid input swaps the form for a
  success state but does *not* persist the data anywhere. Wire to a real
  endpoint before launch.
- **Reduced motion respected.** All animations are gated on
  `prefers-reduced-motion`.
- **No external network requests.** Self-contained. Don't introduce
  Google Fonts, CDN libs, or 3rd-party scripts without explicit approval.

## Accessibility patterns
- Semantic landmarks (`header`, `section`, `footer`, `nav`).
- Form inputs are paired with real `<label for="...">` elements and have
  visible required indicators + accessible error text.
- Decorative elements use `aria-hidden="true"`.
- Focus styles use a visible gold outline (`:focus-visible`).
- Color choices target WCAG AA on body text.
