# Paris Baguette Yonge & Eglinton — Landing Page

Self-contained, responsive landing page for the bakery café at 2401 Yonge Street, Toronto.

## Preview
Open `index.html` directly in any browser, or serve locally:
```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Files
- `index.html` — entire page. All CSS is inline in `<style>`; no build step, no dependencies except Google Fonts (Montserrat + Inter) loaded via CDN. Bakery imagery is hand-drawn inline SVG (no external/photo assets, no copyright concerns).

## Sections
Hero → offerings (chips + cards) → why visit / local location → hours & contact CTA → footer.

## Design system applied
- Palette: navy `#001E60`, deep ink `#0E1144`, gold `#FFC600` (used sparingly), cream `#F6EFE3`, pastry/croissant tones.
- Type: Montserrat (headings/labels/CTAs), Inter (body).
- Rounded cards/chips, soft editorial navy shadows, mobile-first responsive grid.

## CTAs (all real, no deploy)
- Phone: `tel:+14163223337`
- Official site / menu: https://parisbaguette.ca/locations/on/toronto/2401-yonge-street/
- Map / directions: Google Maps search for the verified address.

## Accessibility
Semantic HTML5 landmarks, alt/`aria-label` on every illustration, keyboard-focus rings (gold), WCAG-AA contrast (white-on-navy, ink-on-cream, ink-on-gold), `prefers-reduced-motion` honored.

## Facts
Only verified facts from the business profile are used. No invented prices, discounts, reviews, awards, dietary claims, or promotions. Hours show "open daily 6 AM–10 PM" with a "call to confirm holidays" note. Verify time-sensitive copy against the official page before publishing.
