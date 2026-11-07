# FoodBridge — Zero Waste. Zero Hunger.

A single-page landing site for **FoodBridge**, a concept platform that connects surplus food donors (restaurants, caterers, hostels, events, households) with verified local NGOs and community kitchens.

Built for the **OSCode AI Prompt Battle — FoodBridge track**. Zero build step, zero dependencies, deployed as a static site on **Vercel**.

---

## What's inside

| File | Purpose |
| --- | --- |
| `index.html` | The entire site — markup, Tailwind config, custom CSS and vanilla JS in one file |
| `README.md` | This file |
| `vercel.json` | Optional static config (clean URLs, security headers) |

No `package.json`, no bundler, no `node_modules`. Tailwind is loaded from the CDN and configured inline, so the page renders identically on any static host.

---

## Sections

1. **Hero** — badge, headline, dual CTAs, live "pickup request" glass card visual
2. **Impact stats** — animated counters that trigger on scroll
3. **The Problem** — sourced food-waste and hunger statistics + "broken loop" breakdown
4. **Our Solution** — before/after comparison grid + three trust pillars
5. **How It Works** — 3-step donor → NGO → delivery pipeline with UI mocks
6. **Key Features** — pickup coordination, live tracker, NGO verification, impact metrics, recurring schedules, food-safety guardrails
7. **Community Stories** — auto-playing testimonial slider with dots, arrows and keyboard nav
8. **CTA Banner** — donor / NGO / volunteer conversion block with a demo post form
9. **Footer** — quick links, social icons, contact details, developer credit

Also included: sticky nav that condenses on scroll, scroll-progress bar, mobile drawer menu, scroll-reveal animations, back-to-top button, and `prefers-reduced-motion` support.

---

## Run locally

The site is a single static file, so any of these works:

```bash
# 1. Just open it
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows

# 2. Or serve it (recommended — matches production behaviour)
npx serve .
# or
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## Deploy to Vercel

### Option A — Vercel CLI (fastest)

```bash
npm i -g vercel     # once
cd foodbridge
vercel              # follow prompts, accept defaults
vercel --prod       # promote to production
```

You'll get a `https://<project>.vercel.app` URL. No build command and no output directory are needed — Vercel auto-detects a static site. If it asks, set **Framework Preset: Other**, **Build Command: (empty)**, **Output Directory: `.`**.

### Option B — Git + Vercel dashboard

```bash
cd foodbridge
git init
git add .
git commit -m "feat: FoodBridge landing page"
git branch -M main
git remote add origin https://github.com/<your-username>/foodbridge.git
git push -u origin main
```

Then:

1. Go to [vercel.com/new](https://vercel.com/new) and sign in with GitHub.
2. **Import** the `foodbridge` repository.
3. Framework Preset → **Other**. Build Command → leave empty. Output Directory → `.`
4. Click **Deploy**. First build finishes in roughly 10–20 seconds.
5. Copy the production URL — that's your submission link.

Every push to `main` redeploys automatically.

### Custom domain (optional)

Vercel dashboard → your project → **Settings → Domains → Add**. Point a `CNAME` at `cname.vercel-dns.com`.

---

## Deploy to Render (alternative)

Vercel is the primary target, but Render works too:

1. Push the repo to GitHub.
2. Render dashboard → **New → Static Site** → connect the repo.
3. **Build Command:** leave empty. **Publish Directory:** `.`
4. **Create Static Site**, then redeem any credit coupon under **Billing → Credit Balance** first.

---

## Customising

| What | Where |
| --- | --- |
| Brand colours | `tailwind.config` block in `<head>` — `leaf` (green) and `ember` (orange) scales |
| Fonts | Google Fonts `<link>` — Sora (display) + Inter (body) |
| Headline / copy | Search the section `<h2>` text directly in `index.html` |
| Stat counters | `data-target="..."` on each `.counter` span |
| Testimonials | Duplicate a `.slide` div inside `#sliderTrack` — dots rebuild automatically |
| Contact details | Footer `Contact` column (email, phone, location) |
| Developer credit | Footer bottom line — replace `Team FoodBridge` |

---

## Data & sourcing notes

Every external statistic on the page is linked to its source in a small caption beneath it:

- **1.05 billion tonnes** wasted in 2022, **19%** of food available to consumers, ~**1 billion meals/day**, **132 kg per capita**, **60%** household share — [UNEP Food Waste Index Report 2024](https://www.unep.org/en/news-and-stories/press-release/world-squanders-over-1-billion-meals-day-un-report)
- **733 million** people facing hunger in 2023 (1 in 11 globally, 1 in 5 in Africa) — [FAO/WHO, SOFI 2024](https://www.who.int/news/item/24-07-2024-hunger-numbers-stubbornly-high-for-three-consecutive-years-as-global-crises-deepen--un-report)
- **78.2 million tonnes** of household food waste per year in India (~55 kg/person) — [WRI India](https://wri-india.org/perspectives/india-must-reduce-food-waste-source)
- India ranked **105 of 127**, GHI score **27.3** — [Global Hunger Index 2024](https://www.globalhungerindex.org/pdf/en/2024.pdf)

**Intentionally labelled as illustrative, not real data:**

- The impact counters (14,820 kg rescued / 41,200 meals / 186 partners / 42 min) are pilot placeholders for a concept build.
- The three community stories are composite narratives written for this build, not real testimonials.
- The "post surplus food" form in the CTA banner is a non-functional visual mock.

---

## Accessibility & performance

- Semantic landmarks (`header`, `section`, `article`, `figure`, `footer`) and a visible heading hierarchy
- Keyboard-operable slider with `ArrowLeft` / `ArrowRight`, `aria-label`s on all icon-only buttons
- `aria-expanded` state on the mobile menu toggle
- Full `prefers-reduced-motion` fallback that disables animations and reveals all content
- Scroll listeners are `passive` and throttled through `requestAnimationFrame`

---

## Credits

Design and build: **Team FoodBridge** · Concept for the OSCode AI Prompt Battle.
