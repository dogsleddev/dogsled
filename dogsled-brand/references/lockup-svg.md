# Lockup SVG

The canonical wordmark lockups. **Use these exactly.** Past attempts that hardcoded x-positions for each text element created visible gaps between "dogsled" and ".dev" — the SVG flow below uses `<tspan>` children so kerning works naturally.

## Mark + Wordmark — stacked

```html
<symbol id="lockup-stack" viewBox="0 0 320 160">
  <use href="#mark" x="128" y="0" width="64" height="64"/>
  <text x="160" y="134" text-anchor="middle"
        font-family="Fraunces, serif" font-size="56"
        font-weight="400" letter-spacing="-2" fill="currentColor"
        style="font-variation-settings: 'SOFT' 40, 'opsz' 144;">
    <tspan>dogsled</tspan>
    <tspan fill="#E66A3C">.</tspan>
    <tspan fill="#E66A3C" font-weight="400" font-style="italic"
           style="font-variation-settings: 'SOFT' 60, 'opsz' 144;">dev</tspan>
  </text>
</symbol>
```

## Mark + Wordmark — horizontal

```html
<symbol id="lockup-horiz" viewBox="0 0 420 64">
  <use href="#mark" x="0" y="0" width="64" height="64"/>
  <text x="82" y="48"
        font-family="Fraunces, serif" font-size="56"
        font-weight="400" letter-spacing="-2" fill="currentColor"
        style="font-variation-settings: 'SOFT' 40, 'opsz' 144;">
    <tspan>dogsled</tspan>
    <tspan fill="#E66A3C">.</tspan>
    <tspan fill="#E66A3C" font-weight="400" font-style="italic"
           style="font-variation-settings: 'SOFT' 60, 'opsz' 144;">dev</tspan>
  </text>
</symbol>
```

## Usage

```html
<!-- Define once in your <defs> -->
<svg width="0" height="0" style="position:absolute">
  <defs>
    <!-- mark and mark-sm symbols here -->
    <!-- lockup-stack and lockup-horiz here -->
  </defs>
</svg>

<!-- Use anywhere -->
<svg viewBox="0 0 420 64" style="color: var(--surface); width: 240px; height: auto;">
  <use href="#lockup-horiz"/>
</svg>
```

The `color` on the parent controls the upright "dogsled" text color via `fill="currentColor"`. The "." and ".dev" stay ember regardless. This means the same lockup works in both light and dark mode without any extra logic.
