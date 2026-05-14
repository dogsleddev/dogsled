# Components

Common patterns from the dogsled.dev brand system. Copy-paste these — they're calibrated to the tokens in `tokens.css`.

---

## Status pills

Four states. Same vocabulary across every dogsled surface.

### HTML

```html
<span class="pill shipping">SHIPPING</span>
<span class="pill active">ACTIVE</span>
<span class="pill notes">NOTES</span>
<span class="pill graduated">GRADUATED</span>
```

### CSS

```css
.pill {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 4px 10px;
  border-radius: 100px;
  font-family: var(--mono); font-size: 10px;
  letter-spacing: 0.14em; text-transform: uppercase;
  white-space: nowrap;
}
.pill::before {
  content: "";
  display: inline-block;
  width: 6px; height: 6px;
  border-radius: 50%;
}

.pill.shipping  { background: rgba(230,106,60,0.18);  color: var(--ember-text); }
.pill.shipping::before { background: var(--ember); }
[data-theme="dark"] .pill.shipping::before { box-shadow: 0 0 8px var(--ember); }

.pill.active    { color: var(--aurora-text); }
[data-theme="dark"] .pill.active { background: rgba(111,224,180,0.18); }
[data-theme="light"] .pill.active { background: rgba(111,224,180,0.28); }
.pill.active::before {
  background: var(--aurora);
  animation: pulse 2.4s var(--easing) infinite;
}
[data-theme="dark"] .pill.active::before { box-shadow: 0 0 8px var(--aurora); }

.pill.notes     { color: var(--frost-text); }
[data-theme="dark"] .pill.notes { background: rgba(143,184,214,0.18); }
[data-theme="light"] .pill.notes { background: rgba(143,184,214,0.30); }
.pill.notes::before { background: var(--frost); }

.pill.graduated { color: var(--surface-soft); }
[data-theme="dark"] .pill.graduated { background: rgba(242,234,216,0.08); }
[data-theme="light"] .pill.graduated { background: rgba(14,17,22,0.08); }
.pill.graduated::before { background: var(--surface-quiet); }

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50%      { opacity: 0.55; transform: scale(0.85); }
}
@media (prefers-reduced-motion: reduce) {
  .pill.active::before { animation: none; }
}
```

**Meaning rules:**
- `SHIPPING` — live commercial product. Use sparingly. Reserved for things that aren't quite here yet.
- `ACTIVE` — in flight, being worked on right now. Has the pulse.
- `NOTES` — drafts, field notes, work-in-progress writing.
- `GRADUATED` — done, archived. Lives in the trail behind.

---

## Theme toggle

Sticky pill in the topbar that swaps between light and dark.

### HTML

```html
<div class="theme-toggle" role="tablist" aria-label="Theme">
  <span class="toggle-slider" aria-hidden="true"></span>
  <button data-mode="dark" aria-label="Switch to dark mode">
    <svg viewBox="0 0 24 24">
      <path d="M21 12.8A9 9 0 1 1 11.2 3a7 7 0 0 0 9.8 9.8z"/>
    </svg>
    <span>Dark</span>
  </button>
  <button data-mode="light" aria-label="Switch to light mode">
    <svg viewBox="0 0 24 24">
      <circle cx="12" cy="12" r="4"/>
      <path d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41"/>
    </svg>
    <span>Light</span>
  </button>
</div>
```

### CSS

```css
.theme-toggle {
  display: inline-flex; align-items: center;
  padding: 3px;
  background: var(--bg-3);
  border: 1px solid var(--hair-2);
  border-radius: 100px;
  position: relative;
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  transition: background var(--t-base-d) var(--easing),
              border-color var(--t-base-d) var(--easing);
}
.theme-toggle .toggle-slider {
  position: absolute;
  top: 3px; bottom: 3px;
  width: calc(50% - 3px);
  background: var(--ember);
  border-radius: 100px;
  transition: transform var(--t-base-d) var(--easing);
  z-index: 1;
}
[data-theme="dark"]  .toggle-slider { transform: translateX(0); }
[data-theme="light"] .toggle-slider { transform: translateX(100%); }

.theme-toggle button {
  background: transparent; border: 0;
  padding: 6px 12px;
  cursor: pointer;
  color: var(--surface-soft);
  font: inherit; letter-spacing: inherit; text-transform: inherit;
  display: inline-flex; align-items: center; gap: 6px;
  position: relative; z-index: 2;
  transition: color var(--t-fast) var(--easing);
}
[data-theme="dark"]  .theme-toggle button[data-mode="dark"],
[data-theme="light"] .theme-toggle button[data-mode="light"] {
  color: #0E1116;
  font-weight: 500;
}
.theme-toggle button svg {
  width: 11px; height: 11px;
  stroke: currentColor; fill: none;
  stroke-width: 2; stroke-linecap: round; stroke-linejoin: round;
}
```

### JS

```js
function setTheme(mode) {
  document.documentElement.setAttribute('data-theme', mode);
  try { localStorage.setItem('dogsled-theme', mode); } catch(e) {}
}
document.querySelectorAll('.theme-toggle button').forEach(btn => {
  btn.addEventListener('click', () => setTheme(btn.dataset.mode));
});

// Keyboard shortcut: T to toggle
document.addEventListener('keydown', (e) => {
  if (e.target.tagName === 'INPUT' || e.target.tagName === 'TEXTAREA') return;
  if (e.key === 't' && !e.metaKey && !e.ctrlKey && !e.altKey) {
    const current = document.documentElement.getAttribute('data-theme');
    setTheme(current === 'dark' ? 'light' : 'dark');
  }
});
```

---

## Topbar

Sticky header with wordmark + toggle. Glassy backdrop blur over parchment.

```html
<header class="topbar">
  <div class="topbar-left">
    <a class="topbar-wm" href="/">
      <svg viewBox="0 0 64 64"><use href="#mark"/></svg>
      <span>dogsled<span class="dot">.</span><span class="dev">dev</span></span>
    </a>
  </div>
  <div class="topbar-right">
    <!-- theme toggle here -->
  </div>
</header>
```

```css
.topbar {
  display: flex; justify-content: space-between; align-items: center;
  padding: 18px clamp(24px, 6vw, 96px);
  font-family: var(--mono);
  font-size: 11px; letter-spacing: 0.14em; text-transform: uppercase;
  color: var(--surface-soft);
  border-bottom: 1px solid var(--hair);
  position: sticky; top: 0; z-index: 50;
  background: color-mix(in srgb, var(--bg) 88%, transparent);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  transition: background var(--t-slow) var(--easing);
}
.topbar-left, .topbar-right {
  display: flex; align-items: center; gap: 20px;
}
.topbar-wm {
  font-family: var(--serif);
  font-variation-settings: "SOFT" 40, "opsz" 144;
  font-size: 17px;
  letter-spacing: -0.025em;
  line-height: 1;
  color: var(--surface);
  text-decoration: none;
  display: inline-flex; align-items: center; gap: 10px;
  text-transform: none;
}
.topbar-wm svg { width: 22px; height: 22px; color: var(--surface); }
.topbar-wm .dot { color: var(--ember); }
.topbar-wm .dev {
  color: var(--ember); font-style: italic; font-weight: 400;
  font-variation-settings: "SOFT" 60, "opsz" 144;
}
```

---

## Section head

The `01 —— Section title` pattern used on every dogsled section.

```html
<div class="section-head">
  <span class="num">01 ——</span>
  <span>Section title</span>
  <span class="rule"></span>
  <span>Right-side metadata</span>
</div>
```

```css
.section-head {
  display: flex; align-items: baseline; gap: 16px;
  margin-bottom: 48px;
  font-family: var(--mono);
  font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase;
  color: var(--surface-soft);
  padding-bottom: 16px;
  border-bottom: 1px solid var(--hair);
}
.section-head .num { color: var(--ember-text); }
.section-head .rule { flex: 1; height: 1px; background: var(--hair); }
```

---

## Atmosphere

The faint topo lines + grain that sit behind everything dogsled.

```html
<div class="topo">
  <svg viewBox="0 0 1600 900" preserveAspectRatio="none">
    <g fill="none" stroke-width="0.5">
      <path d="M 0 200 Q 400 180, 800 230 T 1600 210"/>
      <path d="M 0 280 Q 400 250, 800 310 T 1600 290"/>
      <path d="M 0 360 Q 400 330, 800 380 T 1600 370"/>
      <path d="M 0 440 Q 400 410, 800 470 T 1600 450"/>
      <path d="M 0 540 Q 400 520, 800 560 T 1600 540"/>
      <path d="M 0 640 Q 400 610, 800 670 T 1600 650"/>
      <path d="M 0 740 Q 400 720, 800 770 T 1600 750"/>
    </g>
  </svg>
</div>
<div class="grain"></div>
```

```css
.topo {
  position: fixed; inset: 0; z-index: 0; pointer-events: none;
  opacity: var(--topo-opacity);
  transition: opacity var(--t-slow) var(--easing);
}
.topo svg path { stroke: var(--topo-stroke); transition: stroke var(--t-slow) var(--easing); }

.grain {
  position: fixed; inset: 0; z-index: 1; pointer-events: none;
  mix-blend-mode: var(--grain-blend);
  opacity: var(--grain-opacity);
  transition: opacity var(--t-slow) var(--easing);
}
[data-theme="dark"] .grain {
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 0.95  0 0 0 0 0.92  0 0 0 0 0.85  0 0 0 0.08 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>");
}
[data-theme="light"] .grain {
  background-image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 0.1  0 0 0 0 0.07  0 0 0 0 0.05  0 0 0 0.1 0'/></filter><rect width='100%' height='100%' filter='url(%23n)'/></svg>");
}

main { position: relative; z-index: 2; }
```

These two layers belong on every dogsled surface. They're what makes the brand feel like *itself* and not generic. Don't skip them.
