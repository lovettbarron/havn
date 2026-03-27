# Havn -- A Learning Garden

A backyard garden project in Vejle, Denmark designed as a developmental tool for a neurodiverse 7-year-old. The garden gives him incrementally increasing agency over something living -- his own raised beds, his own routines, his own harvest decisions -- while producing tangible, edible output from his work.

## Core Value

A child who independently checks on, cares for, and harvests from plants he chose to grow -- and sees the direct connection between his effort and the food on his plate.

## What's Here

This repo contains the complete planning and documentation for building, planting, and maintaining a raised bed garden across one growing season in Denmark (USDA Zone 7b). Everything is markdown and JSON -- no application code. Fork it, swap in your own site details and crop choices, and you have a full garden plan.

### `docs/` -- Garden Documents

The docs are organized by the order you'd actually use them: figure out what you're building, build it, plant it, maintain it, and prepare for time away.

#### Planning and Layout

Start here. These documents define what you're working with and what you need to buy.

| Document | Description |
|----------|-------------|
| [Property Map](docs/property-map.md) | Full site overview with sun exposure zones and bed placement |
| [Bed Layout](docs/bed-layout.md) | Dimensions, materials, and spacing for all 5 beds |
| [Shopping List](docs/shopping-list.md) | Complete materials list with DKK pricing and budget alternatives |
| [Warm Season Shopping](docs/warm-season-shopping-list.md) | Second-round seeds, seedlings, and supplies for late spring |

#### Building

Construction guides for beds and infrastructure. The setup guide is the master sequence -- the others are referenced from it.

| Document | Description |
|----------|-------------|
| [Setup Guide](docs/setup-guide.md) | Master 2-day construction sequence for all beds and infrastructure |
| [Soil Layers](docs/soil-layers.md) | Three-layer fill system (drainage, growing medium, top dressing) per bed type |
| [Reservoir Build](docs/reservoir-build.md) | DIY self-watering wicking system for high-demand beds |
| [Trellis Build](docs/trellis-build.md) | A-frame cucumber trellis -- child picks from underneath |
| [Slug Defense](docs/slug-defense.md) | Copper tape installation guide for all beds |

#### Planting

What goes where, and session scripts for planting days. The scripts are designed for short attention spans -- timed steps, sensory transitions, and built-in breaks.

| Document | Description |
|----------|-------------|
| Planting Grids ([A](docs/planting-grid-bed-a.md), [B](docs/planting-grid-bed-b.md), [C](docs/planting-grid-bed-c.md), [D](docs/planting-grid-bed-d.md), [E](docs/planting-grid-bed-e.md)) | Per-bed maps with exact cm positions for every plant |
| [Planting Day Script](docs/planting-day-script.md) | Spring planting session with timing and transition cues |
| [Warm Season Sessions](docs/warm-season-session-scripts.md) | Scripts for W21-W22 warm season transplants |
| [Crop Difficulty Tiers](docs/crop-difficulty-tiers.md) | Which crops a child can manage independently vs. with help |

#### Maintenance and Activities

Ongoing care, troubleshooting, and weekend projects.

| Document | Description |
|----------|-------------|
| [Troubleshooting Guide](docs/troubleshooting-guide.md) | Common problems (pests, wilting, yellowing) with visual diagnosis and fixes |
| [Mulching Guide](docs/mulching-guide.md) | Per-bed mulching instructions with material types and volume calculations |
| [Bug Hotel Guide](docs/bug-hotel-guide.md) | Weekend build activity -- insect habitat with treasure hunt |
| [Garlic Autumn Plan](docs/garlic-autumn-plan.md) | Year 2 garlic planting for October |

#### Vacation and Handoff

Everything needed to leave the garden for 2-3 weeks and come back to living plants.

| Document | Description |
|----------|-------------|
| [Reservoir Test Protocol](docs/reservoir-test-protocol.md) | 5-day dry-run test with daily log and pass/fail criteria |
| [Vacation Countdown Script](docs/vacation-countdown-script.md) | 3-day pre-departure session script |
| [Pre-Departure Checklist](docs/pre-departure-checklist.md) | One-page printable checklist (19 items) |
| [Neighbor Vacation Guide](docs/neighbor-vacation-guide.md) | Plain-language handoff for someone who doesn't know your garden |

### `data/` -- Structured Data

JSON reference data for planning and Home Assistant integration. Each directory has a schema in `data/schemas/`.

| Directory | Description |
|-----------|-------------|
| [Crop Database](data/crops/) | 27 crop files -- varieties, growth stages, child actions (EN/DA), difficulty tiers, companion plants |
| [Bed Definitions](data/beds/) | 5 bed files -- crops mapped to cm positions with sensor references |
| [Weekly Schedules](data/schedules/) | 30 weekly files (W15-W44) -- themed names, hero tasks, bilingual prompts |
| [Succession Calendar](data/succession-calendar.json) | Sowing/harvest timeline for continuous harvest W22-W43 |
| [HA Integration](data/ha/) | Home Assistant sensors, plant monitors, and alert rules |
| [Sensor Guide](data/sensors/) | Hardware recommendations for soil moisture and temperature |
| [JSON Schemas](data/schemas/) | Validation schemas for all data types |

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

## Forking This

This garden is specific to our site, climate, and child -- but the structure is general. If you want to adapt it:

1. Start with [Property Map](docs/property-map.md) and [Bed Layout](docs/bed-layout.md) -- replace with your site
2. Pick your crops -- edit the files in `data/crops/` or start fresh using `data/schemas/crop.schema.json`
3. Redo the planting grids for your bed sizes and chosen plants
4. Adjust the session scripts for your child's profile -- the timing, transitions, and break structure matter more than the specific tasks
5. The [Weekly Schedules](data/schedules/) are keyed to Danish climate weeks -- shift them for your growing season

The ADHD/Autism adaptations (timed steps, sensory transitions, meltdown-resilient sequencing, clear start/end for every activity) are baked into the session scripts and are the hardest part to get right. Read a few before rewriting them.

## License

This project is shared as a reference for anyone building a garden with similar goals. Use what's useful to you.
