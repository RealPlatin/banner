# Banner Tool v2.0 — Task Log

## Status: COMPLETE ✓

All v2.0 features were implemented and verified via full codebase audit.

---

## Completed Items

- [x] Background always fills canvas (`fillBg()` called in `render()`, not individual renderers)
- [x] Two new color pickers: Graphic Elements (`#accentColor`) and ASCII Characters (`#asciiCharColor`)
- [x] `state.accentColor` and `state.asciiCharColor` synced into `C.accent`, `C.asciiChar`, `C.inkFaint` at render time
- [x] Alignment fixed via `textX(align, leftDefault, rightMargin=52)` helper — all 5 themes use it
- [x] Map shift left: `mapX = mapOnRight ? panelW : 0` (was `panelW + CHAR_W * 1.5`)
- [x] Skyline height variety: width 2–12 chars, height range extended, skyscraper spike at p>0.85, min 4%
- [x] Banner Shape Selector: Airplane (AIRLINER + rope + box) and Hot Air Balloon (centered, no rope/box)
- [x] `HOT_AIR_BALLOON` ASCII constant added above `AIRLINER`
- [x] `bannerOptions` section in HTML with `.banner-shape-btn` buttons wired
- [x] Image upload: aspect-ratio-correct fit into maxCols×maxRows grid with centering offsets
- [x] Header reads: "ASCII-Generator Edition | Marc von Gehlen"

---

## Browser Verification Checklist

Open `index.html` locally (no server needed).

| Test | Expected |
|---|---|
| Switch LinkedIn → YouTube → Facebook | Full canvas repaints each time, no strips |
| Brand + tagline → cycle Left / Center / Right on all 5 themes | Text stays on canvas, consistent margins |
| Map theme → "Map Left" | Map on left side |
| Skyline → Randomize ×10 | Mix of narrow huts and skyscrapers visible |
| Banner → Balloon button | HOT_AIR_BALLOON rendered centered; no rope/box |
| Banner → Airplane button | AIRLINER with rope and banner box |
| Graphic Elements picker → blue | Rope, chart accents, fin-centre markers turn blue; brand text unchanged |
| ASCII Characters picker → red | Skyline chars, chart data line turn red |
| Upload portrait image | ASCII grid taller than wide, centered horizontally |
| Upload landscape image | ASCII grid fills width, centered vertically |
| Header | Reads "ASCII-Generator Edition \| Marc von Gehlen" |
