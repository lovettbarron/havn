# Havn -- A Learning Garden

A backyard garden project in Vejle, Denmark designed as a developmental tool for a neurodiverse 7-year-old. The garden gives him incrementally increasing agency over something living -- his own raised beds, his own routines, his own harvest decisions -- while producing tangible, edible output from his work.

## Core Value

A child who independently checks on, cares for, and harvests from plants he chose to grow -- and sees the direct connection between his effort and the food on his plate.

## What's Here

This repo contains the complete planning and documentation for building, planting, and maintaining a raised bed garden across one growing season in Denmark (USDA Zone 7b).

### `docs/` -- Garden Documents

| Document | Description |
|----------|-------------|
| [Shopping List](docs/shopping-list.md) | All materials with DKK pricing -- corten steel and budget alternatives |
| [Warm Season Shopping](docs/warm-season-shopping-list.md) | Materials for W21-W22 warm season planting |
| [Bed Layout](docs/bed-layout.md) | Where each of the 5 beds goes, with ASCII diagrams and spacing |
| [Property Map](docs/property-map.md) | Garden site overview with bed placement |
| [Soil Layers](docs/soil-layers.md) | Three-layer fill system for each bed type |
| [Slug Defense](docs/slug-defense.md) | Copper tape installation guide |
| [Reservoir Build](docs/reservoir-build.md) | DIY self-watering wicking system for tomato and cucumber beds |
| [Trellis Build](docs/trellis-build.md) | A-frame cucumber trellis -- child picks from underneath |
| [Setup Guide](docs/setup-guide.md) | Master construction sequence across 2 days |
| [Planting Grids](docs/planting-grid-bed-a.md) | Bed-by-bed planting maps with exact cm positions (5 beds, A-E) |
| [Planting Day Script](docs/planting-day-script.md) | Step-by-step session guide for spring planting with timing and transition cues |
| [Warm Season Sessions](docs/warm-season-session-scripts.md) | Planting scripts for W21-W22 warm season transplants |
| [Bug Hotel Guide](docs/bug-hotel-guide.md) | Weekend creature habitat building activity |
| [Crop Difficulty Tiers](docs/crop-difficulty-tiers.md) | Crop categorization by child independence level |
| [Troubleshooting Guide](docs/troubleshooting-guide.md) | Common garden problems and fixes |
| [Neighbor Vacation Guide](docs/neighbor-vacation-guide.md) | Handoff instructions for garden care during holidays |
| [Garlic Autumn Plan](docs/garlic-autumn-plan.md) | Year 2 garlic planting preparation |

### `data/` -- Structured Data

| Directory | Description |
|-----------|-------------|
| [Crop Database](data/crops/) | 27 JSON files -- one per planted variety with growth stages, child actions (EN/DA), difficulty tiers, companion plants, and alert triggers |
| [Bed Definitions](data/beds/) | 5 JSON files mapping crops to exact cm positions with HA sensor references |
| [Weekly Schedules](data/schedules/) | 30 weekly JSON files (W15-W44) with themed names, hero tasks, and bilingual prompts |
| [Succession Calendar](data/succession-calendar.json) | Master sowing/harvest timeline with gap analysis -- continuous harvest W22-W43 |
| [HA Integration](data/ha/) | Home Assistant sensor definitions, plant monitors, alert rules (bilingual), and entity customization |
| [Sensor Guide](data/sensors/) | Hardware recommendations for soil moisture and temperature monitoring |
| [JSON Schemas](data/schemas/) | Validation schemas for crops, beds, and weekly schedules |

## The Garden

**5 raised beds** -- 3 corten steel in the backyard (120x60x40cm) + 2 galvanized on the roof terrace (80x40x30cm).

**His crops:** Strawberries, raspberries, cherry tomatoes, cucumbers, sweet peppers, radishes, sunflowers, edible flowers (nasturtiums, calendula, borage, viola), and sensory plants (lamb's ear, lemon balm, thyme, mint).

**Family crops:** Spring onions, kale, peas, bush beans, leeks, broccoli, garlic (Year 2).

**Design principles:**
- Quick wins for 5-10 minute attention windows -- always something to pick, smell, or measure
- Manual watering is intentional -- it's the daily routine that builds agency
- Staggered planting for continuous harvest (late May through October)
- Companion planting throughout (tomato+basil+nasturtium, cucumber+pepper+radish+borage)
- Vacation-proof with self-watering reservoirs and a neighbor guide

## Phases

| # | Phase | Status |
|---|-------|--------|
| 1 | Bed Infrastructure | Complete |
| 2 | Spring Planting (W16-W18) | Complete |
| 3 | Warm Season Planting (W21-W22) | Complete |
| 4 | Data System and Schedules | Complete |
| 5 | Documentation and Guides | Complete |
| 6 | Vacation Preparation | Not started |

## License

This project is shared as a reference for anyone building a garden with similar goals. Use what's useful to you.
