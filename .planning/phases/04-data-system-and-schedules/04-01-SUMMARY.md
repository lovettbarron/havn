---
phase: 04-data-system-and-schedules
plan: 01
subsystem: database
tags: [json-schema, crop-data, bed-mapping, bilingual, ha-sensors]

# Dependency graph
requires:
  - phase: 02-spring-planting
    provides: planting grid maps with exact cm positions and bed assignments
  - phase: 03-warm-season-planting
    provides: Phase 3 crop additions and bed transitions
provides:
  - 27 crop JSON files with growth stages, difficulty tiers, child actions, alerts
  - 5 bed JSON files mapping physical beds to crop positions
  - JSON Schema Draft 2020-12 for crop and bed validation
  - Bilingual child action prompts (en/da) per growth stage
  - HA sensor entity references per bed
affects: [04-02-weekly-schedules, 04-03-ha-schemas, 05-difficulty-tiers]

# Tech tracking
tech-stack:
  added: [json-schema-draft-2020-12]
  patterns: [one-file-per-crop, bed-references-by-crop-id, bilingual-prompts]

key-files:
  created:
    - data/schemas/crop.schema.json
    - data/schemas/bed.schema.json
    - data/crops/*.json (27 files)
    - data/beds/*.json (5 files)
  modified: []

key-decisions:
  - "Crop schema includes alerts array with drought/frost/heat_stress types and bilingual messages"
  - "Bed files reference crops by lowercase-hyphen ID with exact cm positions from planting grids"
  - "Sowing method enum includes buy-plant for nursery-purchased perennials (thyme, lemon-balm, lambs-ear, mint)"
  - "Mint positioned outside bed (in pot) but still tracked under bed-a for HA sensor association"

patterns-established:
  - "Crop ID format: lowercase-hyphen (e.g., strawberry-ostara, cherry-tomato-sungold)"
  - "Bilingual prompt pattern: {en: string, da: string} for all child-facing text"
  - "HA sensor naming: sensor.haven_bed_{letter}_moisture / sensor.haven_bed_{letter}_temperature"
  - "Difficulty tier enum: cant_fail / needs_care / year_2_challenge"

requirements-completed: [DATA-01, DATA-02]

# Metrics
duration: 15min
completed: 2026-03-27
---

# Phase 4 Plan 01: Crop Database and Bed Files Summary

**27 crop JSON files with bilingual child actions and growth stages, 5 bed JSON files with cm positions, plus formal JSON Schema validation for both**

## Performance

- **Duration:** 15 min
- **Started:** 2026-03-27T06:06:44Z
- **Completed:** 2026-03-27T06:21:38Z
- **Tasks:** 2
- **Files modified:** 34

## Accomplishments
- Created JSON Schema Draft 2020-12 for crop and bed data with full field inventory from CONTEXT.md
- Populated all 27 crop files covering every species in the plant inventory across 3 difficulty tiers
- Created 5 bed files with exact cm positions extracted from planting grid maps
- All crop files include bilingual (en/da) child action prompts, growth stage timelines for Danish zone 7b, water/temperature thresholds, companion planting data, and alert definitions

## Task Commits

Each task was committed atomically:

1. **Task 1: Create JSON schemas and first 3 crop files as templates** - `553b706` (feat)
2. **Task 2: Create remaining 24 crop files and all 5 bed files** - `393040e` (feat)

## Files Created/Modified
- `data/schemas/crop.schema.json` - Formal JSON Schema for crop files (all required fields)
- `data/schemas/bed.schema.json` - Formal JSON Schema for bed files (crops, positions, HA sensors)
- `data/crops/*.json` (27 files) - Individual crop data for every planted species
- `data/beds/bed-a.json` - "His Bed": strawberries, sensory plants, succession radish, Phase 3 sunflower/nasturtium/mint
- `data/beds/bed-b.json` - "Raspberry Bed": 3 Autumn Bliss canes, 12 chive divisions
- `data/beds/bed-c.json` - "Shared Bed": peas, kale, cucumber (trellis), tomato, basil, pepper
- `data/beds/bed-d.json` - "Terrace Herb Bed": lettuce, spring onion, thyme, viola, leeks
- `data/beds/bed-e.json` - "Terrace Flower Bed": broccoli, bush beans, borage, calendula, Tumbling Tom

## Decisions Made
- Used `buy-plant` as sowing method for nursery-purchased perennials to distinguish from `plug` (started from seed)
- Mint tracked under bed-a despite being in a separate pot (for HA sensor proximity and child sensory route)
- Cherry Tomato Tumbling Tom assigned to bed-e (terrace) rather than bed-c to reduce crowding in the warm crop bed
- Alert thresholds set conservatively: drought alerts fire before critical damage, frost alerts fire immediately (0 delay_hours)

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness
- Crop data foundation complete: all 27 species with growth stages, difficulty tiers, and bilingual prompts
- Bed-to-crop cross-references established with consistent lowercase-hyphen IDs
- Ready for Plan 02 (weekly schedules) which will reference crop_id and bed_id from this data
- Ready for Plan 03 (HA schemas) which will use sensor entity references and alert thresholds from this data

## Self-Check: PASSED

- All 27 crop files exist and are valid JSON
- All 5 bed files exist and are valid JSON
- Both schema files exist
- Both task commits verified (553b706, 393040e)

---
*Phase: 04-data-system-and-schedules*
*Completed: 2026-03-27*
