# Havn -- A Learning Garden

Backyard raised-bed garden in Vejle, Denmark, designed to build developmental agency in a 7-year-old with ADHD/Autism.

**Core value:** A child who independently checks on, cares for, and harvests from plants he chose to grow.

**Location:** Vejle, Denmark (USDA Zone 7b, maritime climate)
**Family:** Andrew (father, PM) and son (7, ADHD/Autism)
**Growing season:** W16 (mid-April) through W44 (late October)

---

## Garden Overview

### Raised Beds

Three raised beds in the backyard area:

| Bed | Location | Size (cm) | Material | Purpose |
|-----|----------|-----------|----------|---------|
| A | Backyard, east (grass, near trampoline) | 120 x 60 x 40 | Corten steel | Strawberry + sensory plants + flowers ("His Bed") |
| B | Backyard, west (grass, near stairway) | 230 x 80 x 40 | Corten steel | Warm crops south zone + raspberry north zone ("Family Bed") |
| C | Backyard, cobblestones (near north fence) | 150 x 40 x 40 | Corten steel, on wheels | Herbs + salad + broccoli ("Kitchen Cart") |

Bed letters A-C are canonical identifiers used throughout all documentation.

### Infrastructure

- **Self-watering reservoir** in Bed B south zone (warm crops -- cucumber, tomato, pepper, basil)
- **A-frame trellis** on Bed B south end for cucumbers to climb
- **Copper tape** slug defense on all 3 beds
- **Mole mesh** under Beds A and B (bottomless on grass). Not needed for Bed C (on cobblestones).
- **Mint** lives in a pot beside Bed A (contained to prevent spread)

### Planting Summary

Detailed grid maps with cm-level positions are in `docs/planting-grid-bed-a.md` through `docs/planting-grid-bed-c.md`. Do not duplicate grid data here -- reference those files.

**Spring planting (W16-W18):** Strawberries, peas, radishes, lettuce, herbs, spring onions, sensory plants
**Warm season planting (W20-W22):** Tomatoes, cucumbers, peppers, bush beans, basil, kale, sunflowers

### Key Dates

| Week | What |
|------|------|
| W16 (mid-April) | Spring planting day -- Session 1 with son |
| W20-W22 (mid-May) | Warm season transplants after last frost |
| W28-W34 (Jul-Aug) | Peak harvest season |
| W40-W42 (Oct) | Garlic planting for Year 2 harvest |
| W44 (late Oct) | Season wind-down |

---

## Project Structure

### `docs/` -- All documentation (markdown)

| File | Contents |
|------|----------|
| `bed-layout.md` | Bed positions, dimensions, orientation |
| `property-map.md` | Full property ASCII visualization with sun zones |
| `planting-grid-bed-[a-c].md` | Per-bed grid maps with cm positions |
| `planting-day-script.md` | Spring planting session script (ADHD-adapted) |
| `warm-season-session-scripts.md` | Warm season planting sessions |
| `shopping-list.md` | Phase 1 materials and costs |
| `warm-season-shopping-list.md` | Phase 3 seeds, seedlings, materials |
| `setup-guide.md` | 12-step bed construction sequence |
| `soil-layers.md` | Soil layer recipes per bed type |
| `reservoir-build.md` | Self-watering reservoir construction |
| `trellis-build.md` | A-frame trellis for Bed B |
| `slug-defense.md` | Copper tape application guide |
| `bug-hotel-guide.md` | Insect hotel build + treasure hunt activity |

### `data/` -- Structured reference data (JSON)

| Directory | Contents |
|-----------|----------|
| `data/schemas/` | JSON schemas for crop and bed data (`crop.schema.json`, `bed.schema.json`) |
| `data/crops/` | Per-crop JSON files (varieties, spacing, care requirements) |
| `data/beds/` | Per-bed JSON files (dimensions, soil, assignments) |

The data system is reference data for planning and Home Assistant integration. It is not a production database -- keep it simple.

### `references/` -- Source materials

Property photos (Google Earth views, property description), used for spatial reference. Not version-controlled content -- reference only.

### `.planning/` -- Project management

Roadmap, requirements, phase plans, research, and summaries. Contains the full planning history. See `.planning/ROADMAP.md` for the phase overview.

---

## Guardrails

When working on this project, push back if I try to:

- **Add crops mid-season** -- the beds are full. New additions compete with established plants for space, nutrients, and light. Wait for next season.

- **Expand beyond raised beds** -- the garden boundary is the 3 beds + mint pot, not the full ~600m2 property. We are not landscaping the backyard.

- **Skip manual watering** -- manual watering is intentional. It is part of the child's daily agency-building routine. Do not suggest automating it away.

- **Over-automate** -- sensors and Home Assistant inform decisions, they do not replace the child checking on his plants. The child observes, decides, and acts.

- **Complexify the data system** -- JSON files are reference data for planning and HA dashboards. They are not a production database. No ORM, no API layer, no migrations.

- **Ignore the child's ADHD/Autism profile** -- sessions need built-in breaks, sensory transitions, and meltdown-resilient sequencing. Activities must have clear start/end, minimal waiting, and tangible results. If a session runs long, cut it short rather than push through.

---

## Current Season Status

**Last updated:** 2026-03-28
**Status:** Pre-season planning complete. Garden reconfigured from 5 beds (3 backyard + 2 terrace) to 3 beds (all backyard). All documentation updated. Awaiting W16 (mid-April) for first physical planting.

**What is done:**
- Garden reconfigured: 3 corten steel beds in backyard (no terrace beds)
- Bed layout, construction guides, and soil recipes written
- Spring and warm-season planting grids complete for all 3 beds
- Session scripts adapted for ADHD/Autism (with breaks, transitions, sensory elements)
- Crop data JSON files created with schemas
- Shopping lists finalized for both planting rounds

**Next milestone:** Phase 1 physical execution -- order beds from byJEMA, build beds, install reservoir in Bed B, apply copper tape. Then Phase 2: spring planting W16-W18.

**Upcoming decisions:**
- Confirm trampoline buffer distance from Bed A on build day
- Garlic variety selection for October planting (hardneck, e.g., Music or Chesnok Red)

---

## Key Conventions

- All documentation is markdown in `docs/`
- Home Assistant entities use `havn_` prefix (e.g., `havn_bed_a_moisture`)
- Bed letters A-C are canonical -- never use Bed 1-3 or Bed D/E in new documents
- Danish plant names appear alongside English where relevant (e.g., tomat/tomato, agurk/cucumber)
- Photo placeholders use `[PHOTO: description]` format for in-season replacement
- Dimensions are always in centimeters unless otherwise noted
- Weeks use ISO format (W16, W20, etc.) aligned to the Danish calendar

---

## For AI Sessions

If you are an AI assistant starting a new session on this project:

1. Read this file first for full context
2. Check `Current Season Status` above for what is current
3. Reference `docs/` files for detailed specifications -- do not ask the user to re-explain what is already documented
4. Follow the guardrails above -- they exist for good reasons
5. The child's developmental needs take priority over garden optimization
