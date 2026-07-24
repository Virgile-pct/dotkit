# DOTKIT

[![npm](https://img.shields.io/npm/v/dotkitjs)](https://www.npmjs.com/package/dotkitjs)
[![license](https://img.shields.io/badge/license-MIT-7b5cff)](LICENSE)

Brutalist UX micro-library. Thirteen modules, zero dependencies, no build step.
**Live demo: [virgile-pct.github.io/lab/dotkit/demo.html](https://virgile-pct.github.io/lab/dotkit/demo.html)**
· *Documentation française : [README.fr.md](README.fr.md)*

## The idea: quantized motion

Every animation library on the market chases smoothness. DOTKIT does the
opposite: **every motion value is rounded to a step**
(`Math.round(v/step)*step`). Magnetic buttons snap in 4 px increments, tilt
rotates in 1.5° notches, the cursor trail lands on a 12 px grid, CSS
transitions run on `steps()`. Motion feels mechanical — like an instrument,
not a ribbon.

Born from a three-part study: **Nothing**'s visual language (strict
typographic roles, technical naming, concentrated identity), the cult
mechanics of award-winning portfolios and **Codrops** (magnetic buttons,
cursor trails, text scramble), and the API patterns of GitHub's most-starred
libraries (**AOS** for declarative data-attributes, GSAP/Lenis/vanilla-tilt
for the effect catalog).

## Install

```bash
npm install dotkitjs
```

```html
<link rel="stylesheet" href="node_modules/dotkitjs/dotkit.css">
<script src="node_modules/dotkitjs/dotkit.js" data-dk-cursor data-dk-trail></script>
```

Or straight from a CDN — two files, nothing to build:

```html
<link rel="stylesheet" href="https://unpkg.com/dotkitjs@1.0.1/dotkit.css">
<script src="https://unpkg.com/dotkitjs@1.0.1/dotkit.js" data-dk-cursor data-dk-trail></script>
```

Auto-inits on load. `data-dk-cursor` and `data-dk-trail` enable the global
modules. Manual init: `<script src="dotkit.js" data-dk-manual>` then
`DotKit.init({cursor: true, trail: true})`.

## Modules

| Module | Usage | Options |
|---|---|---|
| reveal | `data-dk="reveal"` | `data-dk-variant="rise\|fade\|wipe"`, `data-dk-delay`, `data-dk-stagger` (cascades children) |
| split | `data-dk="split"` | — (letter by letter, auto aria-label) |
| scramble | `data-dk="scramble"` | `data-dk-trigger="visible\|hover"` |
| counter | `data-dk="counter"` | `data-dk-to`, `data-dk-duration` |
| marquee | `data-dk="marquee"` | `data-dk-speed` (px/s), `data-dk-reverse` |
| magnetic | `data-dk="magnetic"` | `data-dk-strength` (px, default 14) |
| tilt | `data-dk="tilt"` | `data-dk-max` (degrees, default 6) |
| parallax | `data-dk="parallax"` | `data-dk-speed` (default 0.2, capped ±60 px) |
| grid | `data-dk="grid"` | `data-dk-step` (dot pitch, default 22) |
| progress | `data-dk="progress"` | — (reading bar, width in %) |
| clock | `data-dk="clock"` | `data-dk-zone="local\|utc"` |
| cursor | script `data-dk-cursor` | `data-dk-cursor-label="WORD"` on any element |
| trail | script `data-dk-trail` | — |

Modules combine freely: `data-dk="reveal tilt"`.

## API

```js
DotKit.init(opts)      // {cursor, trail} — called automatically unless data-dk-manual
DotKit.scan(root)      // initialize dynamically injected content
DotKit.cursor()        // enable the crosshair cursor
DotKit.trail()         // enable the dot trail
DotKit.destroy()       // remove global listeners, canvases, timers
DotKit.quantize(v, s)  // the step-rounding function, exposed
```

## Guarantees (non-negotiable)

- **`prefers-reduced-motion`**: final states applied instantly, zero decorative movement.
- **Touch devices**: cursor, trail, magnetic, tilt and interactive grid are disabled.
- **No JavaScript**: content stays fully visible (hidden states only exist under `html.dk-js`).
- One shared `IntersectionObserver`; canvases only compute while visible; ~30 fps is plenty.

## Size

~19 KB JS + ~4 KB CSS, unminified, uncompressed, comments included.
Zero dependencies.

## Who

Built by [Virgile Pourchet](https://virgile-pct.github.io), with AI agents —
the library powers his portfolio, which vendors a copy (`lab/dotkit`).
[MIT](LICENSE) licensed.
