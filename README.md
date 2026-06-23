# dogsled.dev — Landing Page

The bare-bones landing page for `dogsled.dev`. Wordmark, tagline, the module list with status pills, links to the live tools.

## What this is

A single static HTML file. No framework, no build step. Designed to ship today and evolve from here.

The page does three jobs:

1. **Establishes the brand** — wordmark, tagline, dogsled atmosphere (topo lines, grain, parchment, ember accent).
2. **Lists the modules** — a reverse-chronological builder's log of the kit (newest on top).
3. **Links to the live tools** — `dogfood.cafe` (AI-native FP&A SaaS), `freightclose.dogsled.dev` (Freight Accrual Close), `staff.dogsled.dev` (Resource Staffing), and `artool.dogsled.dev` (AR Forecast).

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

**This list is the builder's log — the tools and products built under dogsled, newest on top.** It is NOT the dogfood.cafe SaaS *nav* (which has 21 modules in 6 groups): dogfood.cafe appears here **once**, as a single product entry (06), not as its 21 internal modules. The landing page shows the builder's log, not the product's sidebar.

**The list is a REVERSE-CHRONOLOGICAL builder's log (newest on top).** ⚠️ Convention changed 2026-06-14 — it used to be a fixed 10-module roadmap in ascending order. Now: the project built *first* gets number 01 and sits at the **bottom**; each new tool gets the next build-sequence number and goes on **top**. The numbers are retained as labels, so they read 05 → 01 down the page.

Current list (top → bottom, as rendered):

```
06  dogfood.cafe           → dogfood.cafe               Active   ← newest
05  Freight Accrual Close  → freightclose.dogsled.dev   Active
04  Resource Staffing      → staff.dogsled.dev          Active
03  AR Forecast            → artool.dogsled.dev         Active
02  Cash Flow                                           Notes
01  Dashboard                                           Notes    ← first built
```

When you ship a new tool: give it the next build-sequence number, add it as the **first** `<li>` (an `<a class="module-item linked" href="...">` with `pill active`), and link its live URL (a `*.dogsled.dev` subdomain or an external domain like `dogfood.cafe`). Unbuilt placeholders use `<div class="module-item notes-only">` + `pill notes`. Leave existing numbers alone — a project's number never changes once assigned.

The old roadmap placeholders (Projects, WIP, Rolling Forecast, Pipeline, Budget, 606 Revenue Rec) were removed on 2026-06-14 — the list grows organically as tools ship, not from a fixed 10-item plan.

Note: dogfood.cafe itself is listed once as entry 06. Its *internal* modules (Month-End Close, PBC, …) live in the dogfood.cafe SaaS nav and do NOT get their own entries here — list the product, not its sidebar.

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
