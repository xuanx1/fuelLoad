# Saudi Energy Grid // Sector.SA

Dystopian-futurism HUD for Saudi Arabia's downstream energy sector — refineries, refined-product flows, natural gas. [saudi.html](https://xuanx1.github.io/fuelLoad/saudi.html)

[Live preview →](https://xuanx1.github.io/fuelLoad/saudi.html)

![Screenshot 2025-08-23 191945](https://github.com/user-attachments/assets/8015f2df-a73f-46b9-836f-1dcf309fc4fb)
![Screenshot 2025-08-23 195339](https://github.com/user-attachments/assets/428fc1ab-6fbb-4b9d-8d5f-b63391419db3)

## Aesthetic

Sodium-amber-on-near-black control-room UI — desert-dystopian, NEOM / Blade Runner 2049 / Dune adjacent.

- **Display**: `Bahnschrift Condensed → Bahnschrift → Impact → Arial Narrow`
- **Telemetry / mono**: `Consolas → Lucida Console → Courier New`
- **Body**: `Segoe UI → system-ui`

Palette:

| Token | Hex | Role |
|---|---|---|
| `--accent` | `#ff8a1e` | Sodium amber — primary HUD signature |
| `--accent-hot` | `#ffb347` | Highlighted amber |
| `--sand` | `#e8ddc7` | Warm cream — body text |
| Lime | `#c8ff3a` | Production lines, hover / active tower glow |
| Pale gold | `#ffd599` | Exports / Reserve series |
| Burnt orange | `#ff5c00` | Deficit indicator |

Persistent overlays: viewport corner brackets, a top HUD status bar with a live UTC tick (`T+HH:MM:SSZ`), a bottom coordinate strip, faint amber grid and scanlines over the map. The CARTO dark basemap is tinted with `hue-rotate -18° / sepia 0.35 / saturate 0.75 / brightness 0.72 / contrast 1.12` for the desert-at-night feel.


## Map & overlay

- CARTO `dark_all` raster tiles, filter applied to the tile pane only so the SVG / canvas overlay is never bitmap-blurred
- High-resolution Saudi Arabia boundary from **geoBoundaries ADM0_simplified** (~397 KB), saved at [data/saudi-arabia.geo.json](data/saudi-arabia.geo.json)
- Rendered as two layered canvas paths — a wide amber halo (8 px stroke, 18% opacity) and a sharp inner border (1.2 px stroke, `#ffb347`)
- Rendered via `preferCanvas: true` with `zoomAnimation: false`, plus an explicit `redrawAll()` on `zoomend / moveend / resize` so the boundary cannot fall out of sync with the map pane
- `SAUDI ARABIA` watermark label rendered as a Leaflet `divIcon` marker anchored at the geojson bounds centre — same Bahnschrift Condensed display style as the corner title, 30% smaller (36 px)

## Refinery layer

Nine major Saudi refineries plotted as custom `divIcon` markers — each is a vertical amber arrow whose height encodes capacity (Ras Tanura at 550 kb/cd reaches the maximum; Riyadh at 126 kb/cd is the smallest), with a ◆ glyph at the base and a glowing dot at the antenna tip.

| State | Visual |
|---|---|
| Default | Amber gradient fill, `#ff8a1e` stroke, amber drop-shadow glow |
| Hover | Lime green `#c8ff3a` across polygon, antenna, tip and ◆ glyph; 8 px green drop-shadow |
| Active (popup open) | Same lime green highlight — persists for the duration the popup is open via an `.is-active` class toggled on `popupopen` / `popupclose` |

The popup is anchored 110 px above the marker via `popupAnchor: [0, -110]` so the click-popup never blocks the tallest tower. The hover tooltip uses container-point coordinates (not the mouse position) and is offset above the arrow tip — so it follows the marker but never sits on top of it.

## Energy data panel

Left-hand side panel cycling between two pages via `◀ ▶` and indicator-bar buttons:

### Page 1 — Refined Petroleum
- Stat grid: average production, average demand, average surplus, latest surplus (all in kb/d)
- Multi-line chart: Production (lime green `#c8ff3a`), Demand (amber `#ff8a1e`), Exports (pale gold `#ffd599`)
- Diagonal **surplus / deficit hatching** between Production and Demand: `/` lime hatch when production > demand (surplus), `\` burnt-orange hatch when demand > production (deficit). Generated via canvas `createPattern` on an 8×8 tile.

### Page 2 — Natural Gas
- Stat grid: average production, average consumption, current reserves (BCM), reserve growth %
- Multi-line chart: Production / Consumption / 50-year reserve-equivalent daily rate
- Same surplus / deficit hatching between Production and Consumption

Chart frame uses HUD typography (`Consolas` axes, `Bahnschrift Condensed` titles) on a near-black canvas with `rgba(255,138,30,0.08)` grid lines. Tooltip restyled as a brutalist amber-bordered terminal card.


## Data

Primary source: **[Saudi Open Data Portal](https://open.data.gov.sa/en/datasets)**. CSV files live in [data/](data/):

| File | Used for |
|---|---|
| `Refinery capacities csv.csv` | Refinery capacity history (popup line chart) |
| `Production of Refined Products csv.csv` | Refined products page — Production series |
| `refined products demand csv.csv` | Refined products page — Demand series |
| `Exports of Refined Products 2024 csv.csv` | Refined products page — Exports series (2024) |
| `Exports of Refined products csv.csv` | Refined products page — Exports series (historical) |
| `Annual natural gas production csv.csv` | Natural gas page — Production |
| `Annual Natural Gas Consumption csv.csv` | Natural gas page — Consumption |
| `Reserves, Natural Gas csv.csv` | Natural gas page — Reserves (BCM, converted via BCM → MMSCF → 50-year daily rate) |

Geographic boundary: **[geoBoundaries ADM0](https://www.geoboundaries.org/)** — `geoBoundaries-SAU-ADM0_simplified.geojson` saved locally at [data/saudi-arabia.geo.json](data/saudi-arabia.geo.json)
