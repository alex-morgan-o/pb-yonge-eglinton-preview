# Paris Baguette Yonge & Eglinton - landing page (menu update)

Self-contained static landing page for the neighbourhood bakery café.
One file, no build step: open `index.html` in any browser. Internet access is
needed at view time because the product images load from the official Paris
Baguette CDN.

## Design read

Redesign-preserve of an already-published local bakery café preview for
neighbourhood visitors. Premium asymmetrical editorial storefront language kept
intact on the existing Paris Baguette navy / gold / cream tokens. This pass
swaps the generic placeholder photography for official Paris Baguette menu
imagery and adds a richer, category-grounded menu section.

**Dials:** `DESIGN_VARIANCE: 7` · `MOTION_INTENSITY: 4` (CSS-only, reduced-motion safe) · `VISUAL_DENSITY: 4`

## What changed vs the previous version

- **Picsum placeholders replaced with official photography.** Hero, story,
  signature-picks bento, and the neighbourhood panel now use real product image
  URLs from the official Paris Baguette menu scrape (parisbaguette.ca). No more
  seeded `picsum.photos` images anywhere.
- **New "Explore the menu" section.** A curated, category-grounded menu directory:
  a horizontal pill nav strip plus 12 category groups, each with a short
  description and a horizontal scroll-snap row of representative items
  (official name + official photo, linking to the official product page).
- **Signature-picks bento reworked** to use real product photos (cakes, croissant,
  sourdough loaf, croissant donut) plus one navy tile (coffee) and one cream tile
  (grab-and-go), keeping the 6-cell rhythm and background diversity. Decorative
  kickers trimmed.
- **Availability note** added at the top of the menu section: items and
  availability vary by location and season; verify and order through the official
  menu and location links.
- **CTAs unified** around four intents: View menu / View full menu (official menu),
  Order ahead (official location page), Call the café (tel), Get directions (maps),
  plus the hero "Visit us today" anchor. Nav gains a Menu link.
- **Eyebrows recounted for the larger page.** Six main sections (hero, story,
  signature picks, menu, neighbourhood, visit), so at most 2 eyebrows: one in the
  hero, one on the menu section. The old "On the counter" and "Hours & location"
  eyebrows were removed to stay within `ceil(sections / 3)`.

## Menu source

- **Scrape source URL:** `https://parisbaguette.ca/menu/`
- **Item names and image URLs are taken verbatim from that scrape only.** No prices,
  no invented item descriptions. Category blurbs are shortened paraphrases of the
  scraped category descriptions, with all dashes removed.
- **Curated, not dumped.** The official menu has ~176 items across 15 categories.
  This landing page shows a representative 3 to 4 items per category across 12
  categories (cakes, seasonal sweets, sweets & pastries, savouries, shareable
  breads, breakfast sandwiches, salads/sandwiches/wraps, hot/iced/frozen beverages,
  roll cakes & packaged treats, grab & go). Each item links out to its official
  product page for the full list and ordering.
- A few scraped items were skipped because their image URLs were malformed in the
  source data (the `...jpgautoformat2Ccompress...` entries, e.g. some macaron sets,
  Honey Castella, gluten-free loaves, Mr./Ms. Bear). Working image URLs were chosen
  in their place within the same categories.

## Images

All visible imagery is loaded directly from the official Paris Baguette CDN
(`https://parisbaguette.ca/wp-content/uploads/...`) at the URLs given in the menu
scrape. These are official product photos, served remotely:

- Hero: Strawberry Soft Cream Cake (portrait crop)
- Story: Almond Croissant
- Signature bento: Celebration Party Cake (feature), Croissant, Sourdough Loaf
  Bread, Croissant Donut
- Neighbourhood panel: Cafe Latte
- Menu directory: one official product photo per item

The previous build's note about swapping in brand photography no longer applies for
these slots: the page already uses official Paris Baguette assets. If the official
CDN paths change, the `src` URLs in `index.html` need updating. There is no
storefront photo in the scrape, so the storefront/neighbourhood slot uses an
official café (latte) photo rather than an invented or stock storefront shot.

No AI-generated logo or substitute Paris Baguette mark is used; the brand lockup is
a plain Montserrat wordmark.

## Motion (dial 4, no JS)

- Hero copy fades up in sequence on load; hero photo fades in.
- Sections and each menu category group reveal on scroll using native CSS
  scroll-driven animations (`animation-timeline: view()`), guarded by `@supports`
  so unsupported browsers just show content normally. No scroll listeners.
- Hover lifts on buttons, bento tiles, and menu item cards; menu thumbnails scale
  gently on hover. Active-state push on buttons.
- Everything collapses to static under `prefers-reduced-motion: reduce`, and reveal
  opacity is only applied where motion is allowed, so nothing can get stuck invisible.

The only JavaScript is a one-line footer-year stamp.

## Verified facts only

Name (Paris Baguette Yonge & Eglinton), address (2401 Yonge Street, Toronto, ON
M4P 3H1), phone (416) 322-3337, and open daily 6 AM to 10 PM are preserved from the
business profile. No prices, promos, discounts, reviews, awards, dietary claims, or
"best" claims were invented. Menu and ordering links point to the official Paris
Baguette menu and location pages. Verify hours, availability, and catering against
the official page before publishing time-sensitive copy.

## Pre-flight checklist (taste skill, Section 14)

- [x] Design read + dial values declared (above).
- [x] Redesign mode detected (preserve: IA, brand tokens, copy voice intact; images and menu added).
- [x] **Zero em-dashes / en-dashes** anywhere visible (verified, count 0).
- [x] Page theme lock: one light theme; navy blocks are brand devices, no mid-page mode flip.
- [x] Color consistency: gold is the only accent, used the same way throughout.
- [x] Shape consistency: single radius system (pills, 12px buttons, 20px tiles/cards, 28px panels/media).
- [x] Button contrast: navy/white, gold/navy, and navy-text-on-cream all pass WCAG AA.
- [x] No CTA label wraps (`white-space: nowrap`, 2 to 3 word labels).
- [x] No duplicate CTA intent: View menu / Order ahead / Call the café / Get directions / Visit us today, each reused consistently.
- [x] Hero fits viewport: headline 2 lines, subtext under 20 words, CTAs above the fold, top padding under the cap.
- [x] Hero stack: eyebrow + headline + subtext + CTAs + one meta line, no tagline/trust strip.
- [x] Eyebrow count = 2, within `ceil(6 / 3)`.
- [x] No split-header pattern; section headers stack.
- [x] Zigzag cap respected (hero + story are the only consecutive splits, then bento and menu break it).
- [x] Bento has rhythm, exact 6 cells, background diversity (4 photo + 1 navy + 1 cream).
- [x] No three equal feature cards.
- [x] Long menu lists use the right component: pill nav + per-category horizontal scroll-snap rows, item label below the image (not a default bulleted `<ul>`).
- [x] Real photographic images (official PB product photos), no div fake-screenshots, no decorative SVG as main visual.
- [x] No pills/labels overlaid on images; menu item names sit below the thumbnail. No photo-credit captions.
- [x] No version labels, no section-number eyebrows, no scroll cues, no decorative dots, no locale/weather strips, no fake counters.
- [x] No `border-t + border-b` on every row; category groups and hours list use hairline tops only.
- [x] Availability note present and links to official menu + location page.
- [x] Content density sane for dial 4: short headings, category blurbs under ~20 words, curated item counts.
- [x] Motion claimed = motion shown; all motion reduced-motion safe; no scroll listeners.
- [x] Mobile collapse explicit per section (splits and bento go single-column; menu rows scroll horizontally on touch).
- [x] Viewport stability via `aspect-ratio`, never `h-screen`.
- [x] Semantic HTML, skip link, focus-visible rings, labelled regions, alt text on every image.
- [x] Icons limited to functional contact glyphs; brand uses no fabricated mark.

## Notes / known trade-offs

- Fonts load via Google Fonts `<link>` (with `preconnect`) to keep the page
  build-free and single-file. For production, self-host with `@font-face` +
  `font-display: swap`.
- Product images are hotlinked from the official Paris Baguette CDN. This keeps the
  page truthful (official photography) but means the page depends on those URLs
  staying live. For production, mirror the approved assets locally.
- Not deployed or published. Local artifact only.
