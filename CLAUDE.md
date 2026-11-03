# Iron & Roots — landing page

Iron & Roots is an online fitness membership for a US and worldwide audience, sold through Whop. This repo holds its landing page. Most visitors arrive from ads (Meta: Facebook/Instagram, and Whop) on a phone, so **design and test mobile first** (390px wide), then desktop (1440px).

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
| `sitemap.xml` | Lists the main page for search engines. Update `<lastmod>` when the page changes. |
| `robots.txt` | Allows everything except `light.html`; points to the sitemap. Only takes effect at a domain root (custom domain). |

No build step. Open the HTML files directly or serve the folder (`npx serve .`).

## Brand

- **Tagline:** Strong habits. Real results.
- **Personality:** grounded, strong, no-nonsense, encouraging. Not flashy gym-bro, not soft wellness.
- **Currency:** US dollars ($25 / $49 / $115 a month), because the audience is US/worldwide and checkout runs on Whop in USD.
- **Spelling:** US English on the page (programs, etc.). Exception: "chilli" in the example meal plan stays as the owner wrote it..
- **Audience:** everyday people who want to get fit without an expensive gym, confusing programmes or crash diets.
- **Colours:** charcoal `#1C1C1A` (base), forest `#2F4A3A` (primary), rust `#C8642E` (CTAs), off-white `#F4F1EA` (backgrounds). Small rust text uses `#A34D1F` on light and `#E07A43` on dark for contrast.
- **Type:** Anton (headlines, uppercase), Oswald (labels, buttons), Inter (body).
- **Logo (option D3):** a barbell with double rust plates over a brush-written 根 (*ne*, roots), IRON & ROOTS wordmark in Anton below. On dark: off-white + `#E07A43`; on light: charcoal + `#C8642E`.

## Page structure (`index.html`, top to bottom)

1. **Hero** — header (logo centred; on desktop the nav is split either side: How it works / What's inside / About on the left, Pricing / FAQ on the right), big "Strong habits. Real results." headline, short body line, "Cancel anytime, no lock-in", coach photo. No button in the hero: the sticky Join is the call to action.
2. **How it works** (`#how`) — 3 steps: Pick your level → Get your plan → Progress with support.
3. **What's inside** (`#inside`) — 4 cards: workouts, meal guides, community (Builder + Elite only), progress tracking.
4. **About** (`#about`) — two staggered coach photos (park in colour "Founder", gym in black and white "Training"), "Hi, I'm [Coach name]", story placeholder, 3 beliefs.
5. **Pricing** (`#pricing`) — Foundation $25, Builder $49 ("Recommended"), Elite $115 ("Limited spots": only keep if spots really are capped). Each has its own Join button, which will link to its Whop product.
6. **Member stories** (`#results`) — 3 testimonial cards + before/after strip. **Hidden** (`hidden` attribute) until real stories with permission arrive; when shown again, renumber FAQ to 06.
7. **FAQ** (`#faq`, label 05 while Results is hidden, heading "Before you join") — 5-question accordion, first one open.
8. **Final CTA** — logo, "Start building your roots today.", short line, "Cancel anytime, no lock-in" (no button; the sticky Join covers it).
9. **Footer** — logo, tagline, one line explaining 根 (*ne*) = roots, socials, contact, Terms, Privacy.
10. **Sticky Join** — the one general Join button, on every screen size: full-width bar on phones, floating pill bottom-centre on desktop. The only other Join buttons are the three plan buttons in Pricing. Don't add more.

`light.html` follows the same order.

### Animations in place

- Hero photo eases in and headline lines rise on load; sections fade up on scroll (`.rv` → `.in` via IntersectionObserver).
- Header logo: the barbell (`.lift` group in the inline SVG) drops onto the 根 once on load.
- How it works: outlined step numbers fill in one by one (`.step-n::after`).
- What's inside: the example chart line draws left to right (clip rect `.draw` scales open).
- Pricing: Builder card glows once and its "Most popular" badge pops in.
- All of it only runs when `html.js` is set (JS on and reduced motion off); otherwise the page shows the finished state.

### Responsive helpers

- `.only-wide` shows at ≥ 900px (desktop nav); `.only-narrow` shows below 900px.
- Layout is mostly intrinsic (flex-wrap, `auto-fit` grids, `clamp()` type), so few media queries are needed.

## Copy style

- Plain and specific. No rule-of-three filler, no stock headings ("Questions, answered", "Real people. Real results."), no em dashes in body copy or buttons.
- Section labels are plain (`01 / How it works`). Square brackets are reserved for real placeholders like `[Coach name]` so they are easy to spot.

## Placeholders still to fill (don't invent these)

- Checkout links: `#checkout-foundation`, `#checkout-builder`, `#checkout-elite` → the client's Whop product URLs.
- Coach name and story in About; contact email; social profile URLs (`#instagram`, `#facebook`, `#tiktok`); Terms and Privacy pages (should match Whop's cancellation and refund handling).
- Testimonials and before/after: bracketed placeholders until real member stories with permission arrive. Never write fake testimonials or results.

## Ground rules for animation work

- **Mobile performance first.** Ad traffic is on phones over mobile data. Prefer CSS transitions/animations and `IntersectionObserver`; animate `transform` and `opacity` only. Keep any added library small (no heavy frameworks for this).
- **Respect `prefers-reduced-motion`.** Every animation needs a reduced-motion fallback (no motion, content fully visible).
- **Never hide content behind animation.** If JS fails or is slow, all text, prices and Join buttons must still be visible and clickable. The CTA and the sticky Join bar must never be delayed or obscured.
- **Don't move the layout around** (no layout shift that pushes the Join button as it loads).
- **No unverified claims:** badges like "Most popular" or "Limited spots" only when true.
- **Keep it on-brand:** strong and grounded, not flashy. Keep the existing colours, fonts and copy unless asked.
- **References are for feel only.** Never copy another brand's copy, photos, names or logos.
- Keep both pages working at 390px and 1440px; check both after each change.
