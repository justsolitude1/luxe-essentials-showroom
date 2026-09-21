# Luxe Essentials Kitchen Showroom — concept build

Interactive 3D kitchen showroom (Three.js r170, single `index.html`, no build step).

## Run
```
python -m http.server 8123 --directory showroom
```
Open http://localhost:8123 (must be served over http, not opened as a file).

## Features
- 16 × 11 m showroom: limestone-tile floor, encaustic tiles under the dining area, limewash walls
  (terracotta / forest green / sand), zellige and subway splashbacks
- 5 zones, 21 products, each with a clickable hotspot: Modern Kitchen, Heritage Kitchen,
  Appliances & Storage, Sinks & Taps, Dining & Accessories
- Product panel: category, reference, description, spec table, enquiry + spec-sheet actions
- Live finish switching (tap metals, cabinet paints & timbers, appliance colours, range enamels,
  granite colours, cookware enamels)
- Camera control pad (walk, turn, zoom, reset, help) + first-visit "How to explore" guide
- Navigation: orbit / zoom / pan, click-the-floor to walk, zone buttons, product catalogue,
  prev/next, auto-playing guided tour, keyboard (← → Esc)
- Mobile: bottom-sheet panel, touch controls, reduced pixel ratio and no shadows on phones
- Respects `prefers-reduced-motion`

## Swapping in real products
All products live in the `PRODUCTS` array. Each entry has data (`name`, `sku`, `specs`, `finish`)
and a `build(group, reg)` function that currently creates placeholder geometry procedurally.
For production, replace `build` with a GLTFLoader call that loads the client's optimised `.glb`
(Draco/Meshopt + KTX2 textures) and passes its swappable materials to `reg()`. The hotspot,
camera view and finish logic stay the same.

Product names, SKUs and specs are placeholders, not Luxe Essentials catalogue data.
