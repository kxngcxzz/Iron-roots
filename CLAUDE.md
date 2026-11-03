# Iron & Roots — landing page

Iron & Roots is a UK online fitness membership. This repo holds its landing page. Most visitors arrive from Meta (Facebook/Instagram) ads on a phone, so **design and test mobile first** (390px wide), then desktop (1440px).

The next job is adding animations. The owner will describe the animations they want; follow those. The ground rules at the bottom apply to whatever gets built.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | **Main landing page**: dark premium variation. Self-contained HTML + inline styles, small vanilla JS. |
| `light.html` | Alternative variation in the brand palette (off-white / forest / rust). Same copy, sections and prices. |
| `BRIEF.md` | Design brief for the two variations (references, rules, what to avoid). |
| `assets/coach-park.jpg` | Coach photo, outdoors (About intro, in colour). |
| `assets/coach-gym.jpg` | Coach photo, gym mirror shot (hero, and the "Training" photo in About; always shown black and white). Low-res; will be replaced. |
| `brand/logo-mark-{light,dark}.svg` | D3 logo mark (barbell over brush 根), square. `dark` = for dark backgrounds. |
| `brand/logo-lockup-{light,dark}.svg` | D3 stacked lockup with IRON & ROOTS wordmark. |
| `brand/logo-horizontal-{light,dark}.svg` | Mark + wordmark in a row (headers). All text is outlined; no fonts needed. |
| `brand/tokens.css` | Colours, fonts, radii. |

No build step. Open the HTML files directly or serve the folder (`npx serve .`).

## Brand

- **Tagline:** Strong habits. Real results.
- **Personality:** grounded, strong, no-nonsense, encouraging. Not flashy gym-bro, not soft wellness.
- **Currency:** prices are shown in US dollars ($25 / $49 / $115 a month, converted from the original £19 / £39 / £89). Checkout must charge in USD to match.
- **Audience:** everyday people who want to get fit without an expensive gym, confusing programmes or crash diets.
- **Colours:** charcoal `#1C1C1A` (base), forest `#2F4A3A` (primary), rust `#C8642E` (CTAs), off-white `#F4F1EA` (backgrounds). Small rust text uses `#A34D1F` on light and `#E07A43` on dark for contrast.
- **Type:** Anton (headlines, uppercase), Oswald (labels, buttons), Inter (body).
- **Logo (option D3):** a barbell with double rust plates over a brush-written 根 (*ne*, roots), IRON & ROOTS wordmark in Anton below. On dark: off-white + `#E07A43`; on light: charcoal + `#C8642E`.

## Page structure (`index.html`, top to bottom)

1. **Hero** — header (inline SVG logo; desktop nav), big "Strong habits. Real results." headline, tagline, body, 4 benefits, `Join Now — From $25/mo` button, "Cancel anytime, no lock-in", coach photo.
2. **How it works** (`#how`) — 3 steps: Pick your level → Get your plan → Progress with support.
3. **What's inside** (`#inside`) — 4 cards: workouts, meal guides, community (Builder + Elite only), progress tracking.
4. **About** (`#about`) — two staggered coach photos (park in colour "Founder", gym in black and white "Training"), "Hi, I'm [Coach name]", story placeholder, 3 beliefs.
5. **Pricing** (`#pricing`) — Foundation $25, Builder $49 (Most popular), Elite $115 (Limited spots). Each has its own Join button.
6. **Social proof** (`#results`) — 3 testimonial cards + before/after strip (placeholders).
7. **FAQ** (`#faq`) — 5-question accordion, first one open.
8. **Final CTA** — "Start building your roots today." + Join button.
9. **Footer** — logo, socials, contact, Terms, Privacy.
10. **Sticky Join bar** — phones only (`.only-narrow`, hidden ≥ 900px).

`light.html` follows the same order.

### Animations in place

- Hero photo eases in and headline lines rise on load; sections fade up on scroll (`.rv` → `.in` via IntersectionObserver).
- Header logo: the barbell (`.lift` group in the inline SVG) drops onto the 根 once on load.
- How it works: outlined step numbers fill in one by one (`.step-n::after`).
- What's inside: the example chart line draws left to right (clip rect `.draw` scales open).
- Pricing: Builder card glows once and its "Most popular" badge pops in.
- All of it only runs when `html.js` is set (JS on and reduced motion off); otherwise the page shows the finished state.

### Responsive helpers

- `.only-wide` shows at ≥ 900px (desktop nav); `.only-narrow` shows below 900px (sticky bar and its footer spacer).
- Layout is mostly intrinsic (flex-wrap, `auto-fit` grids, `clamp()` type), so few media queries are needed.

## Placeholders still to fill (don't invent these)

- Checkout links: `#checkout-foundation`, `#checkout-builder`, `#checkout-elite` → real checkout URLs from the client.
- Coach name and story in About; contact email; social profile URLs (`#instagram`, `#facebook`, `#tiktok`); Terms and Privacy pages.
- Testimonials and before/after: bracketed placeholders until real member stories with permission arrive. Never write fake testimonials or results.

## Ground rules for animation work

- **Mobile performance first.** Ad traffic is on phones over mobile data. Prefer CSS transitions/animations and `IntersectionObserver`; animate `transform` and `opacity` only. Keep any added library small (no heavy frameworks for this).
- **Respect `prefers-reduced-motion`.** Every animation needs a reduced-motion fallback (no motion, content fully visible).
- **Never hide content behind animation.** If JS fails or is slow, all text, prices and Join buttons must still be visible and clickable. The CTA and the sticky Join bar must never be delayed or obscured.
- **Don't move the layout around** (no layout shift that pushes the Join button as it loads).
- **Keep it on-brand:** strong and grounded, not flashy. Keep the existing colours, fonts and copy unless asked.
- **References are for feel only.** Never copy another brand's copy, photos, names or logos.
- Keep both pages working at 390px and 1440px; check both after each change.
