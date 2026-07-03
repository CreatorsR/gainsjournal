# GainsJournal.com

Single-page landing site for the free **3-Day Goals & Meditation Challenge**.
One job: email signups. Built with Astro 5, deployed on Vercel.

## Develop

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # static output in dist/
```

## Config

Build-time flags live in [`src/config.ts`](src/config.ts):

- `GUMLET_VIDEO_ID` — **placeholder**; swap for the final video ID before launch
- `VIDEO_AUTOPLAY` — appended to the Gumlet embed src
- `SHOW_DAY_BREAKDOWN` — renders/hides the Day 1–3 band
- `SOCIAL_PROOF` — quote + attribution above the signup form. **PLACEHOLDER
  copy — swap in a real member quote before launch** (set to `null` to hide)

Design tokens (colors, fonts, the −12° brand skew) live in
[`src/styles/tokens.css`](src/styles/tokens.css) — never hardcode design values
in components.

## Signup form

The form is **placeholder-wired**: it validates, fires the `optin_submitted`
analytics event, and shows the success state, but only logs the email to the
console. Real ESP wiring goes in the `TODO(ESP)` block in
[`src/pages/index.astro`](src/pages/index.astro).

## Analytics

Named events pushed to `window.dataLayer` (GTM/GA-ready):
`optin_submitted`, `cta_click`, `sticky_cta_click`.
Vercel Web Analytics script is included in production builds — enable
Analytics for the project in the Vercel dashboard to activate it.

## Motion contract

The page is deliberately still except: hero headline reveal on load, slow hero
glow drift, gold line draw on the day band, success-message pulse. Everything
is gated behind `prefers-reduced-motion: no-preference`.
