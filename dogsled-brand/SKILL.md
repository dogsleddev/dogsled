---
name: dogsled-brand
description: Apply the dogsled.dev v1.3 brand system to any frontend code — websites, landing pages, components, dashboards, emails, social cards, or any visual surface. Use this skill whenever the user mentions dogsled, dogsled.dev, "the brand", "the kit", "our colors", "our type", "our mark", or "Aim high / Pull hard / Leave tracks". ALSO use when the user asks to make something "look like dogsled" or "match the brand". ALWAYS pull from this skill when generating CSS, Tailwind config, React components, Next.js pages, or HTML for any dogsled-related project — even if the user does not explicitly ask. Encodes the colors, type scale, motion tokens, the connected-trail mark with three semantic elements (Star, Lead, Trail), the status-pill vocabulary (SHIPPING, ACTIVE, NOTES, GRADUATED), the dark/light theme system, accessibility decisions (ember-text variant for WCAG AA), and the voice guidelines for any dogsled.dev surface.
---

# dogsled.dev Brand System

A complete design system for dogsled.dev — a builder's log for modern finance. Use this whenever you're writing code, styling, or generating UI for any dogsled.dev surface.

The brand line is **Aim high. Pull hard. Leave tracks.** Three actions, three time horizons. Everything in this system serves that philosophy.

---

## When to apply this skill

Apply this skill aggressively. It triggers in these situations:

- Any frontend code for dogsled.dev or any dogsled subdomain (`staff.dogsled.dev`, etc.)
- Any landing page, blog post layout, OG image, email template, social card, or marketing surface for dogsled
- Any time the user says "the brand", "our brand", "the kit", "our colors", "our type"
- Any time the user mentions the mark, the wordmark, the status pills, or the philosophy
- Any time the user is building something *adjacent* to dogsled (a tool that links from it, a project page) — pull the tokens in and stay consistent

When in doubt, apply the system. Consistency compounds.

---

## The Mark

Connected-trail chevron with three semantic elements:

- **★ The North Star** — a small filled circle above the climb. The destination/waypoint. The future you're aimed at.
- **▲ The Lead** — the front chevron in V-formation. Forward motion. The present, the work happening right now.
- **◣ The Trail** — a second chevron offset behind the Lead (+8x, +4y), drawn at 0.55 opacity. The portfolio, the work behind, the past.

**The story:** Aim high. Pull hard. Leave tracks.

**SVG source** (use this exactly — do not redraw):

```html
<symbol id="mark" viewBox="0 0 64 64">
  <g class="m-trail" fill="none" stroke="currentColor" stroke-width="5"
     stroke-linecap="square" stroke-linejoin="miter">
    <path d="M 16 50 L 36 26 L 56 50" opacity="0.55"/>
  </g>
  <g class="m-lead" fill="none" stroke="currentColor" stroke-width="5"
     stroke-linecap="square" stroke-linejoin="miter">
    <path d="M 8 46 L 28 22 L 48 46"/>
  </g>
  <g class="m-star">
    <circle cx="28" cy="14" r="3.2" fill="currentColor"/>
  </g>
</symbol>
```

**Small mark variant** (for usage under 24px — favicon, tiny avatars):

```html
<symbol id="mark-sm" viewBox="0 0 64 64">
  <g fill="none" stroke="currentColor" stroke-width="6"
     stroke-linecap="square" stroke-linejoin="miter">
    <path d="M 12 48 L 32 22 L 52 48"/>
  </g>
  <circle cx="32" cy="13" r="3.6" fill="currentColor"/>
</symbol>
```

The small variant drops the Trail. At sub-24px sizes, the Trail blurs into the Lead and reads as mush. Use `#mark-sm` for: 16px and 24px favicons, in-line author avatars under 24px, and any spot where stroke clarity matters more than the three-element story.

**Use `currentColor`** for both. Never hardcode the mark's color. The mark picks up whatever `color` is set on its container.

---

## The Wordmark

`dogsled.dev` set in Fraunces. Three rules:

1. **`dogsled`** — upright Fraunces, SOFT axis 40, weight 400, letter-spacing -2px (at 56px)
2. **`.`** (the dot) — ember-colored, upright, normal style
3. **`.dev`** — italic Fraunces, **SOFT axis 60, weight 400, italic** — *not* SOFT 100 weight 300

The big italic SOFT 100 / weight 300 cursive look is for **display-only contexts** (hero headlines, big editorial moments, the card back). For *wordmarks at any size*, use SOFT 60 weight 400. The cursive version is too dramatic at small sizes and starts reading as decorative script instead of a brand mark.

**HTML wordmark pattern:**

```html
<span class="wordmark">
  dogsled<span class="dot">.</span><span class="dev">dev</span>
</span>
```

**CSS:**

```css
.wordmark {
  font-family: var(--serif);
  font-variation-settings: "SOFT" 40, "opsz" 144;
  font-weight: 400;
  letter-spacing: -0.025em;
}
.wordmark .dot { color: var(--ember); }
.wordmark .dev {
  color: var(--ember);
  font-style: italic;
  font-weight: 400;
  font-variation-settings: "SOFT" 60, "opsz" 144;
}
```

For SVG lockups, use a single `<text>` element with `<tspan>` children — never three separate text elements with hardcoded x-positions. Hardcoded positions create gaps. See `references/lockup-svg.md` for the canonical SVG.

---

## Colors

### Base palette

| Token | Light mode | Dark mode |
|-------|------------|-----------|
| `--bg` | `#F2EAD8` parchment | `#0E1116` midnight |
| `--bg-2` | `#F7F0DE` | `#161A21` |
| `--bg-3` | `#EDE3CD` | `#1F242D` |
| `--bg-4` | `#E9DFC6` | `#2A3038` |
| `--surface` | `#0E1116` | `#F2EAD8` |
| `--hair` | `rgba(14,17,22,0.14)` | `rgba(242,234,216,0.12)` |

`#F2EAD8` is the brand parchment. Don't drift to lighter trendy creams like `#F6EFE5` — that's the AI-generic warm-off-white and it kills the distinctive feel. Commit to the yellow.

### Accents (identical across light/dark)

| Token | Value | Role |
|-------|-------|------|
| `--ember` | `#E66A3C` | Warm signal. Heat, heart, the primary brand color. |
| `--aurora` | `#6FE0B4` | Cool signal. Go, live, active. |
| `--frost` | `#8FB8D6` | Quiet. Notes, drafts, support. |

### Accent text variants (CRITICAL for accessibility)

The full-saturation accents fail WCAG AA contrast on parchment for small text. Use these darkened variants for any text under 24px:

| Token | Light mode | Dark mode |
|-------|------------|-----------|
| `--ember-text` | `#C25431` | `#E66A3C` |
| `--aurora-text` | `#2A8E6D` | `#6FE0B4` |
| `--frost-text` | `#4A779E` | `#8FB8D6` |

**Rule:** large display text (24px+) → `--ember`. Small body text, labels, links → `--ember-text`. Same pattern for aurora and frost. Never put `--ember` directly on a 12px mono label on parchment — it'll fail contrast.

---

## Typography

### Three families

- **Fraunces** (display, variable, SOFT + opsz + ital axes) — `--serif`
- **Geist Sans** (body, UI) — `--sans`
- **Geist Mono** (captions, code, technical labels) — `--mono`

### Google Fonts URL (must include italic axis)

```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght,SOFT@0,9..144,300..900,0..100;1,9..144,300..900,0..100&family=Geist:wght@300..700&family=Geist+Mono:wght@400..600&display=swap" rel="stylesheet">
```

The `ital,` prefix and `0,...;1,...` value syntax is what loads real italic Fraunces. Without it, the browser fakes italic by slanting upright text — the `f` and `g` will look strange. Always include both axes.

### Type scale tokens

```css
--t-xs:    clamp(10px,  1.0vw,  11px);   /* micro labels */
--t-sm:    clamp(11px,  1.1vw,  12px);   /* mono captions */
--t-base:  clamp(13px,  1.3vw,  14px);
--t-md:    clamp(14px,  1.5vw,  16px);   /* body */
--t-lg:    clamp(18px,  2.0vw,  20px);   /* prominent body */
--t-xl:    clamp(22px,  2.6vw,  28px);   /* sub-display */
--t-2xl:   clamp(28px,  3.6vw,  40px);   /* card titles */
--t-3xl:   clamp(40px,  5.0vw,  56px);   /* h2 */
--t-4xl:   clamp(56px,  8.0vw,  96px);   /* big specimens */
--t-hero:  clamp(64px, 12.0vw, 168px);   /* hero only */
```

Use these tokens. Don't improvise new clamp() values. The scale is the source of truth.

### Fraunces SOFT axis cheat sheet

The SOFT axis is Fraunces' curve-roundness setting. Lower = more geometric. Higher = more decorative/cursive.

- **SOFT 30** — body serif, longest reading
- **SOFT 40** — wordmark, lists, mid-size headings
- **SOFT 50–60** — section headings, lockups
- **SOFT 70–80** — italic tagline-scale type
- **SOFT 100** — display-only italic, hero scale, big editorial moments

When in doubt, lower SOFT for reading, higher SOFT for impact. SOFT 100 italic is gorgeous but only at 28px+.

### Italic discipline

Italic Fraunces is the brand's signature flourish. Use it on **the words after the periods**:

- "Aim high. Pull *hard.* Leave *tracks.*"
- "A builder's log for *modern finance.*"
- "The DataStore is the *swap point.*"

One italic phrase per heading. Never italicize whole sentences (that's just "italic text"). The italic should land on the *idea word*. Always pair italic Fraunces with `--ember` color for that signature heat-on-italic look.

---

## Motion

```css
--t-fast:   150ms;     /* hover, focus, color transitions */
--t-base-d: 200ms;     /* the canonical interaction speed */
--t-slow:   320ms;     /* theme switches, page-level transitions */
--easing:   cubic-bezier(0.4, 0, 0.2, 1);
```

Use these tokens. Don't improvise. The 200ms base is deliberately snappier than the lazy 500ms — products feel slow at 500ms.

Always respect `prefers-reduced-motion`:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Status pill system

Four states, one vocabulary:

| Pill | Color | Meaning |
|------|-------|---------|
| `SHIPPING` | Ember | Live commercial product. Reserved for products that aren't quite here yet. |
| `ACTIVE` | Aurora | Currently being worked on, used, iterated. Has a subtle pulse animation. |
| `NOTES` | Frost | Drafts, field notes, work-in-progress writing. |
| `GRADUATED` | Muted | Done, archived, earned its slot. |

See `references/components.md` for the full pill CSS + HTML.

The `ACTIVE` pill pulses subtly (2.4s cycle) — animation respects `prefers-reduced-motion`.

---

## Theme system

Two themes (light, dark), driven by a single `data-theme` attribute on `<html>`. **Light is the default.**

Always include the no-flash inline script in `<head>`:

```html
<script>
  (function() {
    try {
      var saved = localStorage.getItem('dogsled-theme');
      if (saved === 'dark' || saved === 'light') {
        document.documentElement.setAttribute('data-theme', saved);
        return;
      }
      var prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      document.documentElement.setAttribute('data-theme', prefersDark ? 'dark' : 'light');
    } catch (e) {}
  })();
</script>
```

Priority: explicit user choice > OS preference > light default. Always store in `localStorage` under the key `dogsled-theme`.

Why light default: dogsled.dev's audience is CFOs and controllers reading long-form. Light mode is the canonical reading surface. Dark mode is the toggle, not the front door.

---

## Voice

**Say:**
- "Aim high. Pull hard. Leave tracks."
- "Pulls weight. Doesn't bark."
- "A builder's log for modern finance."
- "Built it, shipped it, here's the post."

**Don't say:**
- "Synergies." "Unlocks." "Verticals."
- "Disrupting." "Revolutionizing."
- "Leveraging AI-powered solutions"
- "Reach out to learn more"

Tone is direct, builder-grade, finance-literate. Specific over general. Particular over performative.

---

## Reference files

For the full implementations, read these as needed:

- `references/tokens.css` — All CSS custom properties for both themes. Copy-paste into any project.
- `references/components.md` — Status pills, theme toggle, topbar, footer patterns
- `references/lockup-svg.md` — Canonical SVG for the wordmark + mark lockups
- `references/voice.md` — Extended voice/copywriting guidelines with examples
- `references/anti-ai-tells.md` — How to make output not look AI-generated (specific to this brand)
- `references/starter.html` — Complete minimal HTML page with everything wired up

---

## Critical decisions baked into this system

These were debated and locked. Don't second-guess them in any output:

1. **Light is default.** Reading surface, not dashboard.
2. **Parchment is `#F2EAD8`** — committed yellow, not trendy off-white.
3. **`pull hard`, not "push forward"** — the sled metaphor needs pull.
4. **Italic Fraunces at SOFT 60 for wordmarks**, SOFT 100 only for display.
5. **Ember-text variants are mandatory** for any text under 24px on parchment.
6. **The mark uses `currentColor`** — never hardcode its color.
7. **One italic phrase per heading** — italic is a flourish, not a default.
8. **The Trail in the mark stays connected** to the Lead at the same starting Y — not right-shifted like a sliding step.

---

## Quick start

When asked to build *anything* dogsled-branded from scratch, start by reading `references/starter.html` and `references/tokens.css`. They have everything wired up — fonts, theme switching, mark defs, the system's full CSS variable set. Build on top of that floor.

Now build. Match the system. When the user hands you a brief, your first move is to confirm whether dogsled-brand should apply — and if it should, **apply it without hedging.** That's how a brand becomes a brand: by showing up consistently every time.
