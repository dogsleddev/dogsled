# How to not look AI-generated

dogsled.dev's value proposition partly depends on **not looking like it was AI-generated**, even though much of it is built with AI assistance. The brand reads as *thoughtful builder*, not *generated template*. Protecting that means avoiding specific tells.

This document covers the visual and copy patterns that mark output as AI-generated. Avoid them.

---

## Visual tells

### 1. Warm-cream-and-terracotta hover

The most common AI-design pattern in 2025-2026 is a warm off-white background (~`#F6EFE5`) with a terracotta or orange accent (~`#D87A4E`). Every Cursor/v0/ChatGPT-generated landing page lives in this zone.

**Counter-move:** dogsled commits to a *more saturated* parchment (`#F2EAD8`) and a *hotter* ember (`#E66A3C`). The slight extra commitment in both directions reads as a brand decision, not a template default.

### 2. Generic sans-serif everywhere

AI tools default to Inter, Manrope, or DM Sans for everything. Functional but indistinct.

**Counter-move:** dogsled uses three families with deliberate roles — **Fraunces** (display), **Geist Sans** (body), **Geist Mono** (technical). Mixing serif display with mono captions is rare in AI output. It signals editorial care.

### 3. Tasteful card grids with subtle shadows

The AI-default layout is a hero + features grid + testimonial + CTA. Cards with `border-radius: 12px` and `box-shadow: 0 4px 12px rgba(0,0,0,0.08)`.

**Counter-move:** dogsled prefers *flat surfaces with hairline borders* (`border: 1px solid var(--hair)`), section-numbered structure (`01 ——`, `02 ——`), and inset highlights instead of drop shadows on dark cards. The result reads like print typesetting, not Bootstrap.

### 4. Smooth uniform motion

AI tools tend to apply the same 300ms ease to every transition. Looks polished but anonymous.

**Counter-move:** dogsled uses three named speeds (150ms / 200ms / 320ms) and a single cubic-bezier easing. Use the right speed for the right action — hover state is 150ms, click feedback 200ms, theme switch 320ms. The varied rhythm reads as intentional.

### 5. Emoji peppered through headings

AI loves to add 🚀 ✨ 💡 to section headings.

**Counter-move:** dogsled uses *typographic glyphs* with semantic weight: `★` (Star, future), `▲` (Lead, present), `◣` (Trail, past). These are the mark's three elements, not decoration. Used sparingly, only in editorial contexts where they carry meaning.

### 6. Linear-style gradient blobs

AI design loves big radial blobs in primary brand color, often pink/purple/blue, behind hero text.

**Counter-move:** dogsled uses *much lower-opacity* atmospheric tints (`rgba(230,106,60,0.10)`) plus a topographic-line overlay and grain. The atmosphere is *felt*, not seen. If you can clearly see the glow, it's too strong.

---

## Copy tells

### 1. "In today's fast-paced world..."

Or any opening that contextualizes "the present moment" in vague global terms. AI defaults to this.

**Counter-move:** Drop the cold open. Start with the specific subject. "Forecasts, dashboards, and small fast tools — built in public" beats "In today's fast-paced finance landscape, builders are creating..."

### 2. The "It's not just X — it's Y" framing

> *"It's not just a brand kit — it's an operating system."*
> *"It's not just code — it's craft."*

AI churns these out endlessly. They sound profound and say nothing.

**Counter-move:** State the thing. *"A brand kit that doubles as an operating system."* Or just: *"An operating system."* Cut the negation.

### 3. Three-item parallel-verb lists

Every AI-generated marketing page has at least one of these:

> - *Empower your team*
> - *Streamline your workflow*
> - *Accelerate your growth*

**Counter-move:** dogsled uses lists rarely. When it does, the items are *specific and concrete* — actual project names, actual topics, actual numbers. Or the list is intentionally short (just two items) so it doesn't feel like a template.

### 4. Em-dash overuse

AI loves em-dashes — *every* — sentence — has — one. They make copy feel breathless and overwrought.

**Counter-move:** Use periods. The brand line is three periods. Trust the period.

### 5. Closing rhetorical flourishes

> *"The future of X is here."*
> *"Welcome to the next era of Y."*
> *"This changes everything."*

**Counter-move:** dogsled closes with *a small concrete moment* — a CTA back to the journal, a quiet brand line, a footer that says only what's necessary. Never with a flourish.

### 6. "Powered by", "Driven by", "Fueled by"

AI applies these to feature lists or brand promises.

**Counter-move:** Drop the verb entirely or use a precise one. *"Built on Next.js + Supabase"* beats *"Powered by cutting-edge technology."*

---

## Structural tells

### 1. About / Features / Pricing / Contact

The default SaaS site IA. AI tools generate this without thinking.

**Counter-move:** dogsled's IA is editorial — Featured / Field areas / On the bench / Latest notes / About. The structure tells the reader this is *a publication*, not a product page.

### 2. Identical section padding

Every section gets the same top/bottom padding. Looks regular but rhythmless.

**Counter-move:** dogsled varies section padding per section's content density. Hero sections get more breathing room (`clamp(64px, 12vw, 160px)`), list-heavy sections get less. The result reads like a magazine layout.

### 3. Hero → CTA above the fold

AI assumes everyone wants to convert the visitor in 3 seconds.

**Counter-move:** dogsled's hero is *quiet*. The actual CTAs come well below the fold. The brand trusts that a reader who scrolls is more valuable than one who clicks.

---

## The fundamental anti-AI move: *commitment*

The thing AI-generated work lacks most is **commitment to a particular choice.** Defaults are safe; commitments are recognizable. Every dogsled decision is more committed than the obvious option:

- More yellow parchment (not generic warm-white)
- Hotter ember (not safe terracotta)
- Editorial structure (not SaaS template)
- Real italic Fraunces with the proper SOFT axis (not Google Fonts default italic)
- Sled metaphor carried through every word (not generic builder cliché)

That commitment is what makes the brand readable as *intentional* even when AI helped produce it. **Preserve the commitments. Resist the urge to soften them toward defaults.**

---

## Self-check before shipping anything dogsled

Run this mental checklist:

1. **Is the parchment the right shade?** (`#F2EAD8`, not `#F6EFE5`)
2. **Is the ember saturated, not muted?** (`#E66A3C`, not `#D87A4E`)
3. **Is the wordmark italic at SOFT 60, not SOFT 100?**
4. **Are small text instances using `--ember-text`, not `--ember`?**
5. **Does the copy avoid all six "say" anti-patterns above?**
6. **Is there exactly one italic phrase per heading, on the idea word?**
7. **Does the structure feel editorial (numbered sections, hairline rules) rather than SaaS-template (cards with shadows)?**
8. **Are the periods doing the work the brand line does — short, declarative, particular?**

If yes to all → ship. If no to any → fix before shipping.
