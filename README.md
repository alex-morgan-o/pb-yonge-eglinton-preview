# Paris Baguette Yonge & Eglinton - landing page redesign

Self-contained static redesign of the neighbourhood bakery café landing page.
One file, no build step: open `index.html` in any browser.

## Design read

Redesign-overhaul of a local bakery café landing page for neighbourhood visitors,
premium consumer bakery language, leaning toward a polished asymmetrical editorial
storefront on the existing Paris Baguette navy / gold / cream tokens.

**Dials:** `DESIGN_VARIANCE: 7` · `MOTION_INTENSITY: 4` (CSS-only, reduced-motion safe) · `VISUAL_DENSITY: 3`

## What changed vs the original

- **Hand-rolled decorative SVG illustrations removed.** The old hero, product cards, and
  storefront were drawn with custom SVG (an AI-design tell). Replaced with real photographic
  placeholders under a navy duotone so they read as one branded set.
- **Asymmetrical hero** (text left `1.05fr`, tall photo right `0.95fr`), not a centered hero.
- **Editorial story section** ("Baked through the day") as a photo + text split.
- **Offerings as a bento with rhythm**: one 2x2 feature tile plus five varied tiles
  (3 photo, 1 navy, 1 cream, 1 croissant). Exactly 6 cells for 6 offerings, no empty cells,
  no three-equal-card row.
- **Neighbourhood panel**: navy gradient block with storefront photo and a hairline list
  (not three equal feature cards).
- **Clean hours/contact CTA** in a cream card, then footer.
- **Eyebrows cut to 2** total (hero + offerings) across the page, per the skill's
  `ceil(sections / 3)` rule. Old page had one above almost every section.
- Removed decorative dots, the "Baked fresh every morning" badge, and the en-dash hours
  separator.

## Tokens

Straight from `DESIGN.md`: navy `#001E60`, deep ink `#0E1144`, gold `#FFC600` (accent, used
sparingly), cream `#F6EFE3`, white, pastry `#E8B778`, croissant `#F6DCAE`. Montserrat for
headings/labels/CTAs, Inter for body. One radius system: chips = pill, buttons = 12px,
tiles/cards = 20px, large panels/media = 28px.

## Motion (dial 4, no JS)

- Hero copy fades up in sequence on load; hero photo fades in.
- Sections reveal on scroll using native CSS scroll-driven animations
  (`animation-timeline: view()`), guarded by `@supports` so unsupported browsers just show
  content normally. No `window` scroll listeners, no animation library.
- Hover lifts on buttons and tiles; active-state push on buttons.
- Everything collapses to static under `prefers-reduced-motion: reduce`, and reveal opacity
  is only applied where motion is allowed, so nothing can get stuck invisible.

The only JavaScript is a one-line footer-year stamp.

## Images

Placeholders use `picsum.photos` seeded URLs (the skill's sanctioned fallback when no
image-gen tool is available). They are generic photography, not Paris Baguette product shots.
**Before publishing, swap them for official or client-approved brand photography** at:

- Hero, `1100x1320` (portrait) - counter / café moment
- Story, `1100x880` - baking in progress
- Bento feature, `900x900` - handcrafted cake
- Bento pastries, `800x600`
- Bento catering, `800x600`
- Neighbourhood, `1000x900` - storefront on Yonge

No AI-generated logo or substitute Paris Baguette mark is used; the brand lockup is a plain
Montserrat wordmark.

## Verified facts only

Name, address (2401 Yonge Street, Toronto, ON M4P 3H1), phone (416) 322-3337, open daily
6 AM to 10 PM, and the official offerings list. No prices, promos, discounts, reviews,
awards, dietary claims, or "best" claims were invented. Menu / catering links point to the
official Paris Baguette location page. Verify hours and catering against the official page
before publishing time-sensitive copy.

## Pre-flight checklist (taste skill, Section 14)

- [x] Design read + dial values declared (above).
- [x] Redesign mode detected (overhaul, content/IA preserved).
- [x] **Zero em-dashes / en-dashes** anywhere visible (grep-verified, count 0).
- [x] Page theme lock: one light theme; navy blocks are brand devices, no mid-page mode flip.
- [x] Color consistency: gold is the only accent, used the same way throughout.
- [x] Shape consistency: single radius system, applied everywhere.
- [x] Button contrast: navy/white and gold/navy and navy-text-on-cream all pass WCAG AA.
- [x] No CTA label wraps (`white-space: nowrap`, 2-3 word labels).
- [x] No duplicate CTA intent: one label per intent (Visit us today / View the menu /
      Call the café / Get directions), reused consistently.
- [x] Hero fits viewport: headline 2 lines, subtext 17 words, CTAs above the fold,
      top padding under the cap.
- [x] Hero stack: eyebrow + headline + subtext + CTAs + one meta line, no tagline/trust strip.
- [x] Eyebrow count = 2, within `ceil(5 / 3)`.
- [x] No split-header pattern; section headers stack.
- [x] Zigzag cap respected (hero + story are the only consecutive splits, then bento breaks it).
- [x] Bento has rhythm, exact 6 cells, and background diversity (photo + navy + cream + croissant).
- [x] No three equal feature cards.
- [x] Real photographic images (no div fake-screenshots, no decorative SVG as main visual).
- [x] No pills/captions overlaid on images as decoration; no photo-credit captions.
- [x] No version labels, no section-number eyebrows, no scroll cues, no decorative dots,
      no locale/weather strips, no fake live counters.
- [x] No `border-t + border-b` on every row; lists use hairline tops only.
- [x] Content density sane: short headings, sub-paragraphs under ~25 words.
- [x] Motion claimed = motion shown; all motion reduced-motion safe; no scroll listeners.
- [x] Mobile collapse explicit per section (bento and all splits go single-column < 760-940px).
- [x] Viewport stability via `aspect-ratio`/`min-h`, never `h-screen`.
- [x] Semantic HTML, skip link, focus-visible rings, labelled regions, alt text.
- [x] Icons limited to functional contact glyphs; brand uses no fabricated mark.

## Notes / known trade-offs

- Fonts load via Google Fonts `<link>` (with `preconnect`) to keep the page build-free and
  single-file. For production, self-host with `@font-face` + `font-display: swap`.
- `picsum` images are placeholders, not bakery-specific; replace before launch (see above).
- Not deployed or published. Local redesign only.
