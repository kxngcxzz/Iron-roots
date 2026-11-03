# Rebuild brief — two variations

Owner wants a clean, premium landing page for the Iron & Roots online coaching brand. Manga page scrapped. Logo = **D3** (barbell over brush 根, Anton wordmark).

## Deliverables
- `index.html` — **Dark premium** variation (main).
- `light.html` — **Brand palette** variation (off-white / forest / rust / charcoal).
Both: single self-contained HTML file, inline `<style>`, tiny vanilla JS only. No frameworks, no build.

## Logo files (already built, use them, don't redraw)
`brand/logo-mark-{dark,light}.svg` (barbell + 根, square), `brand/logo-lockup-{dark,light}.svg` (stacked with wordmark), `brand/logo-horizontal-{dark,light}.svg` (mark + wordmark in a row — use for the header). `dark` = for dark backgrounds.

## References (layout/feel only — never copy their copy, photos, names or branding)
- **MARCHON** (online.marchon.co.uk) — dark premium: full-bleed photo hero with huge uppercase condensed headline centred, one bright pill CTA; a "trusted" strip; asymmetric bento grid of feature tiles mixing photo tiles and UI-ish tiles; horizontal row of tall programme cards with photo + label; a "Why" section of stacked uppercase statements with small bracketed eyebrow labels like `[ STRUCTURE ]`; two-column FAQ (title left, +/- list right); multi-column footer.
- **David Kingsbury** — split hero (photo left, headline + CTA right on white), a row of coloured pillar cards with icons and small buttons, about section where a text card overlaps a big photo, testimonials as solid dark blocks.

## Content (from the existing index.html — keep copy, prices, sections)
Hero, How it works (3 steps), What's inside (4 items), About (coach placeholder), Pricing (Foundation $25 / Builder $49 Most popular / Elite $115 Limited spots, each own checkout link), Results/testimonials (placeholders), FAQ (5, first open), Final CTA, Footer, sticky Join bar on phones (<900px).

## Hard rules (from CLAUDE.md)
- Mobile first at 390px, then 1440px. Phone ad traffic on mobile data → keep it light; photos `loading="lazy"` except hero; width/height attrs to stop layout shift.
- **Don't invent**: no fake stats (no "91% hit their goal"), no fake testimonials, no press logos, no member counts, no star ratings. Keep bracketed placeholders. Keep `#checkout-*`, `#instagram` etc. placeholders.
- Only photos available: `assets/coach-park.jpg` (1290×1497), `assets/coach-gym.jpg` (978×1560, low-res — don't show it large). Don't use stock/hotlinked images. Where a reference uses lots of photos, use typography, colour blocks, the logo mark, or simple UI-style tiles built in HTML/CSS instead.
- Animations: CSS + IntersectionObserver, transform/opacity only, `prefers-reduced-motion` fallback, content visible if JS fails (add a `.js` class on <html> before hiding anything), CTA + sticky bar never delayed.
- Accessibility: real buttons/links, 44px targets, 4.5:1 text contrast, visible focus, FAQ as `<details>` or aria-expanded buttons.

## No AI slop — specifically avoid
Gradient washes/blobs, glassmorphism, glowing orbs, emoji, left-border accent cards, generic icon-in-circle grids for everything, "Unlock your potential" style filler, centred-everything sameness, every section the same card grid, random sparkles. Make deliberate typographic choices, real hierarchy, varied section rhythm, tight spacing system.
