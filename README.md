# ASCII Banner Generator

A browser-based LinkedIn banner generator that renders elegant ASCII art at 1584 × 396 px — the LinkedIn standard header size. No frameworks, no build step, no dependencies. Just open the HTML file.

![ASCII Banner Generator](https://img.shields.io/badge/format-1584%20×%20396%20px-c86440?style=flat-square) ![No dependencies](https://img.shields.io/badge/dependencies-none-4a4740?style=flat-square)

---

## Quick Start

```bash
# Clone or download the repo, then simply open the file:
open index.html
```

That's it. No npm, no server required.

---

## Features

- **4 ASCII art themes** — each procedurally generated, never the same twice
- **Fully editable text** — brand name and tagline update the canvas live
- **High-DPI export** — renders at 2× (or your screen's pixel ratio) for crisp PNGs on Retina displays
- **Seed-based variation** — drag the seed slider or hit Randomize to explore layouts
- **One-click PNG download** — exports the full-resolution canvas

---

## The 4 Themes

| Theme | Style | Key elements |
|---|---|---|
| **The Chart** | Market price chart | `/`, `\`, `_`, `^`, `v` data line · area fill · peak labels · volume bars |
| **The Map** | World map | Point-in-polygon continents · 10 financial centres (`NYC`, `LON`, `TYO`…) highlighted in orange |
| **The Skyline** | City skyline | ~42 procedural buildings in 4 styles · tagline auto-fits into a rooftop billboard |
| **The Banner** | Biplane towing a banner | Tow rope in accent orange · banner box auto-sizes to your tagline |

---

## Controls

| Control | What it does |
|---|---|
| **Theme buttons** | Switch between the 4 ASCII themes |
| **Brand / Name** | Large serif text placed in the canvas (Playfair Display) |
| **Tagline** | Used inside the billboard, banner box, or as a subtitle |
| **Text Position** | Left · Center · Right alignment |
| **Seed slider** | Deterministic variation — same seed always gives the same layout |
| **↺ Randomize** | Pick a random seed |
| **Download PNG** | Exports a high-resolution PNG at `1584 × SCALE` pixels |

---

## File Structure

```
banner/
├── index.html   — App shell, canvas element, control panel UI
├── style.css    — Light-mode UI (cream #f4f2eb, charcoal #1c1b18, orange #c86440)
└── script.js    — Canvas rendering engine, all 4 themes, UI wiring
```

No external files are downloaded at runtime except Google Fonts (Playfair Display, Inter, JetBrains Mono).

---

## Customisation

### Change the default text
Open `index.html` and edit the `value` attributes on the two inputs:
```html
<input id="brandText"   value="Your Brand" />
<input id="taglineText" value="Your tagline here." />
```

### Change the colour palette
Edit the `C` object at the top of `script.js`:
```js
const C = {
  bg:     '#f4f2eb',  // canvas background
  ink:    '#1c1b18',  // primary ASCII art colour
  accent: '#c86440',  // orange highlights & tagline
  ...
};
```

### Force a specific export resolution
Change the scale factor near the top of `script.js`:
```js
const SCALE = 3;  // 3× = exports at 4752 × 1188 px (ultra sharp)
```
LinkedIn will downsample this to 1584 × 396 cleanly.

### Add a new theme
1. Write a `renderMyTheme(rng)` function in `script.js`
2. Add a case to the `switch` in `render()`
3. Add a `<button class="theme-btn" data-theme="myTheme">` in `index.html`

---

## Export Notes

- The downloaded PNG is named `banner-{theme}-{seed}.png`
- Physical export size: `1584 × SCALE` × `396 × SCALE` px
- At default 2× SCALE: **3168 × 792 px** — LinkedIn downsamples this to the standard 1584 × 396 with no quality loss
- For maximum sharpness, upload the high-res file directly; LinkedIn handles the resize

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires:
- HTML5 Canvas
- CSS Grid
- Google Fonts (optional — falls back to system monospace / serif / sans-serif)

---

## License

MIT — free to use, modify, and distribute.
