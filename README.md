# dogsled.dev — Landing Page

The bare-bones landing page for `dogsled.dev`. Wordmark, tagline, ten modules with status pills, links to the two live tools.

## What this is

A single static HTML file. No framework, no build step. Designed to ship today and evolve from here.

The page does three jobs:

1. **Establishes the brand** — wordmark, tagline, dogsled atmosphere (topo lines, grain, parchment, ember accent).
2. **Lists the ten modules** — current scope of the kit, ordered roughly by build sequence.
3. **Links to the two live tools** — `staff.dogsled.dev` (Resource Staffing) and `artool.dogsled.dev` (AR Forecast).

Everything else is a Notes pill — "not yet shipped, but on the trail."

## Folder structure

```
dogsled-landing/
├── README.md              ← you are here
├── KICKOFF_PROMPT.md      ← paste at the start of an Antigravity / Claude Code session
├── index.html             ← the landing page (single file)
├── vercel.json            ← Vercel deploy config
└── dogsled-brand/         ← the brand skill, extracted
    ├── SKILL.md
    └── references/
        ├── tokens.css
        ├── components.md
        ├── lockup-svg.md
        ├── voice.md
        ├── anti-ai-tells.md
        └── starter.html
```

## How to ship this

### Option A — straight Vercel CLI

```bash
cd dogsled-landing
vercel --prod
```

Then set the custom domain `dogsled.dev` in the Vercel dashboard.

### Option B — Antigravity / Claude Code

1. Open this folder in Antigravity or Claude Code
2. Paste the contents of `KICKOFF_PROMPT.md` (or say "Read KICKOFF_PROMPT.md")
3. Tell Claude what you want to change/add
4. When ready: deploy to Vercel from inside the agent

## How to update the modules

Open `index.html`. Find the `<ol class="module-list">` section. Each module is an `<li>` with a known structure:

- **For linked modules** (have a live URL): use `<a class="module-item linked" href="...">`. Use the `pill active` status.
- **For unshipped modules**: use `<div class="module-item notes-only">`. Use the `pill notes` status.

**This list is the 10 dogsled WORKSHOP modules — the standalone tutorials. Not the same as the dogfood.cafe SaaS nav (which has 21 modules in 6 groups).** The landing page shows the content roadmap, not the product's sidebar.

**The order is the BUILD SEQUENCE, locked:**

```
01  Dashboard          02  Cash Flow           03  AR Forecast
04  Resource Staffing  05  Projects            06  WIP
07  Rolling Forecast   08  Pipeline            09  Budget
10  606 Revenue Rec
```

AR Forecast and Resource Staffing are *currently live* (old versions, slated for a rebuild) so they're `linked` + `active` — but they sit at positions 03 and 04 because that's their place in the sequence. Do NOT float live tools to the top just because they're deployed. The numbering tells the story of the plan; a visitor should see the intended arc, not the accident of what shipped first.

When a module ships: change its `<div>` to an `<a>`, add the href, swap `notes-only` → `linked` and `pill notes` → `pill active`. Leave its number alone — the position never changes.

Note: Month-End Close and PBC live in the dogfood.cafe SaaS nav but are NOT among the 10 workshop tutorials. Don't add them to this list.

## What's deliberately NOT here yet

- No Substack link (intentional — we'll add it when content goes live)
- No "About" page (the tagline is the about)
- No newsletter signup (premature; add when there's something to subscribe to)
- No detail pages per module (each module's microsite is its own subdomain)
- No analytics (add when worth measuring)

The page is intentionally a one-pager. Resist the urge to add sections that don't earn their place.

## Brand fidelity

This page is built with the `dogsled-brand` skill (v1.3) in the `dogsled-brand/` folder. Any future edits in Antigravity or Claude Code will pull from that skill — colors, type, motion, voice, the mark, the pill vocabulary.

If the agent ever produces output that drifts from the brand (wrong colors, wrong type, generic AI voice), point it at `dogsled-brand/SKILL.md` and `dogsled-brand/references/anti-ai-tells.md`. Those two files are designed to keep output on-brand.

---

Pulls weight. Doesn't bark.
