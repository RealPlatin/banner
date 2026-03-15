# ASCII Banner Generator

A browser-based social banner generator that renders ASCII art themes across multiple social media formats. No frameworks, no build step, no dependencies. Just open the HTML file.

![Version](https://img.shields.io/badge/version-3.0-c86440?style=flat-square) ![No dependencies](https://img.shields.io/badge/dependencies-none-4a4740?style=flat-square) ![Formats](https://img.shields.io/badge/formats-4-4a4740?style=flat-square)

---

## Quick Start

```bash
# Clone or download the repo, then simply open the file:
open index.html
```

No npm, no server required. For live stock data (Yahoo Finance), serve over HTTP:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

---

## Formats

| Format | Dimensions |
|---|---|
| LinkedIn | 1584 × 396 px |
| Twitter/X | 1500 × 500 px |
| Facebook | 851 × 315 px |
| YouTube | 2560 × 1440 px |

---

## The 5 Themes

| Theme | Meaning | Key elements |
|---|---|---|
| **The Chart** | Capital Market Dynamics & Growth | `/`, `\`, `_`, `^`, `v` data line · area fill · peak labels · volume strip · optional live ticker |
| **The Map** | Global Logistics & Geopolitics | Point-in-polygon continents · 10 financial centres (`NYC`, `LON`, `TYO`…) · panel left or right |
| **The Skyline** | Industrial Infrastructure & Real Estate | ~44 procedural buildings in 4 styles · tagline auto-fits into a rooftop billboard |
| **The Banner** | Strategic Perspective & Vision | Top-down airliner or hot air balloon · tow rope · banner box auto-sizes to your tagline |
| **ASCII Upload** | Custom image conversion | Upload any JPG/PNG/GIF/WebP · converted to character art in-browser |

---

## Controls

### Text
| Control | What it does |
|---|---|
| **Brand / Name** | Large text placed on the canvas |
| **Tagline** | Used in billboard, banner box, or as a subtitle |
| **Text Alignment** | Left · Center · Right |
| **Tagline Position** | Theme default · or pin to any corner/edge (tl, tc, tr, bl, bc, br) |

### Style
| Control | What it does |
|---|---|
| **Background** | Canvas background colour |
| **Ink / Text** | Primary text and ASCII art colour |
| **ASCII Characters** | Colour of procedural ASCII characters (chart line, skyline, etc.) |
| **Graphic Elements** | Accent colour — rope, chart peaks, fin markers, tagline |
| **Brand Font** | Serif (Playfair Display) · Sans (Inter) · Mono (JetBrains Mono) |
| **Export Quality** | 1× · 2× · 3× · 4× — multiplies canvas pixel dimensions |

### Variation
| Control | What it does |
|---|---|
| **Seed slider** | Deterministic variation — same seed = same layout |
| **↺ Randomize** | Pick a random seed instantly |

> The Variation section is hidden in ASCII Upload mode (seed has no effect there).

### Theme-specific options

**Chart — Hybrid Finance Engine**
- Type any ticker: `BTC`, `ETH`, `SOL`… → fetches via CoinGecko (crypto)
- Type any stock symbol: `AAPL`, `TSLA`, `MSFT`… → fetches via Yahoo Finance
- Status indicators: `✓` live data · `~` seeded mock (CORS/offline fallback) · `✗` crypto not found

**Map**
- Toggle between Map Right and Map Left panel layouts

**Banner**
- ✈ Airplane — top-down view airliner with tow rope and banner box
- 🎈 Balloon — centered hot air balloon, no rope

**ASCII Upload**
- Accepts JPG · PNG · GIF · WebP
- Aspect-ratio-correct fit into the character grid
- Automatically switches to the ASCII Upload theme on load

---

## File Structure

```
banner/
├── index.html        — App shell, canvas element, control panel UI
├── style.css         — Light-mode UI (cream #f4f2eb, charcoal #1c1b18, orange #c86440)
├── script.js         — Canvas rendering engine, all 5 themes, finance APIs, UI wiring
└── tasks/
    ├── todo.md       — Implementation task log
    └── lessons.md    — Self-improvement notes
```

No external files are downloaded at runtime except Google Fonts (Playfair Display, Inter, JetBrains Mono).

---

## Export

- File named: `banner-{format}-{theme}-{seed}.png`
- Physical size: `W × SCALE` by `H × SCALE` px
- At default 2×: LinkedIn exports at **3168 × 792 px** — platforms downsample cleanly
- Upload the high-res file directly; all major platforms handle the resize

---

## Customisation

### Change the colour palette
Edit the `C` object at the top of `script.js`:
```js
const C = {
  bg:       '#f4f2eb',  // canvas background
  ink:      '#1c1b18',  // primary text & ASCII art colour
  accent:   '#c86440',  // graphic elements & tagline
  asciiChar:'#1c1b18',  // procedural ASCII characters
};
```

### Force a specific export resolution
Change the scale button default in `index.html` or set `SCALE` in `script.js`:
```js
let SCALE = 3;  // 3× = LinkedIn exports at 4752 × 1188 px
```

### Add a new theme
1. Write a `renderMyTheme(rng)` function in `script.js`
2. Add a case to the `switch` in `render()`
3. Add a `<button class="theme-btn" data-theme="myTheme">` in `index.html`

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires:
- HTML5 Canvas
- CSS Grid
- Google Fonts (optional — falls back to system serif / sans-serif / monospace)

---

## License

MIT — free to use, modify, and distribute.
