---
phase: 02-spring-planting
plan: 01
subsystem: planting-layout
tags: [grid-map, companion-planting, raised-bed, succession-sowing, sensory-garden]

# Dependency graph
requires:
  - phase: 01-bed-infrastructure
    provides: bed dimensions, positions, trellis and reservoir placement
provides:
  - 5 bed-by-bed planting grid maps with cm-precise plant positions
  - companion planting layout verified against research constraints
  - succession sowing schedule slots marked in 4 beds
  - requirement traceability matrix across all beds
affects: [03-warm-season, 04-data-system, 02-02 session-script]

# Tech tracking
tech-stack:
  added: []
  patterns: [grid-map-format, bed-letter-remapping, requirement-traceability-per-bed]

key-files:
  created:
    - docs/planting-grid-bed-a.md
    - docs/planting-grid-bed-b.md
    - docs/planting-grid-bed-c.md
    - docs/planting-grid-bed-d.md
    - docs/planting-grid-bed-e.md
  modified: []

key-decisions:
  - "3 strawberries in Bed A (2 Ostara + 1 Korona) instead of 4-6 to avoid overcrowding 0.72m2"
  - "Lemon balm containment via sunken pot at bed edge, not center placement"
  - "Spring onions isolated in Bed D (terrace) to avoid pea/allium conflict in Bed C"
  - "Bed E kept 60% reserved for Phase 3 warm-season transplants"
  - "Pea rows at trellis base in Bed C with explicit W21 cutback note for cucumber handoff"

patterns-established:
  - "Grid map format: header, 10cm grid table, precise positions table, plant key, succession slots, companion rationale, cross-references, requirement traceability"
  - "Bed letter remapping: Phase 2 letters (A-E) map to Phase 1 numbers (3,1,2,4,5) with remapping note in each file"
  - "Cross-bed requirement summary table appended to every grid map for full traceability"

requirements-completed: [SCHED-01, ENGM-04, CROP-01, CROP-05, CROP-06, ENGM-02, ENGM-03, FLWR-02, FLWR-03, FLWR-04, FLWR-05, SENS-01, SENS-02, SENS-04, COOK-01, COOK-05, COOK-06]

# Metrics
duration: 6min
completed: 2026-03-26
---

# Phase 2 Plan 1: Planting Grid Maps Summary

**5 bed-by-bed grid maps with cm-precise plant positions, companion planting verification, and succession sowing slots for W16 planting day**

## Performance

- **Duration:** 6 min
- **Started:** 2026-03-26T22:09:26Z
- **Completed:** 2026-03-26T22:15:42Z
- **Tasks:** 2
- **Files created:** 5

## Accomplishments

- Created 5 printable grid maps (one per bed) with exact plant positions in cm, spacing, and sowing depth
- Verified all companion planting constraints: peas isolated from alliums (separate beds), strawberries isolated from raspberries (separate beds), lemon balm contained at edge with sunken pot recommendation
- Marked succession sowing slots in 4 of 5 beds (A, C, D, E) with specific re-sow dates and crop rotations
- Placed sensory plants (lamb's ear, thyme, lemon balm) on path-facing edges of Bed A for tactile/olfactory engagement
- Distributed edible flowers across 4 beds: calendula in A/C/E, borage in C/E, viola in A/D
- All 17 plan requirements traced to specific beds via cross-bed summary matrix in every file

## Task Commits

Each task was committed atomically:

1. **Task 1: Create grid maps for backyard beds A, B, C** - `317f847` (feat)
2. **Task 2: Create grid maps for terrace beds D, E + cross-bed requirement summary** - `b557336` (feat)

## Files Created

- `docs/planting-grid-bed-a.md` - His Bed: 3 strawberries, pea shoots, sensory edges, calendula, viola, succession radish
- `docs/planting-grid-bed-b.md` - Raspberry Bed: 3 Autumn Bliss canes with 12 chive divisions perimeter
- `docs/planting-grid-bed-c.md` - Pea & Cooking Bed: peas on A-frame trellis, kale, borage, calendula, radish succession
- `docs/planting-grid-bed-d.md` - Salad & Herb Terrace: lettuce broadcast, spring onions, thyme, viola
- `docs/planting-grid-bed-e.md` - Future Warm-Season: borage, calendula, radish, 60% reserved for Phase 3

## Decisions Made

- **3 strawberries (not 4-6):** The 120x60cm bed is only 0.72m2. 2 Ostara + 1 Korona gives continuous picking (Jun-Sep) without overcrowding. Anti-pattern from research explicitly warns against excess variety in small beds.
- **Lemon balm at edge in sunken pot:** Follows research recommendation to contain aggressive spreader. Positioned at outer corner of west edge where it can be trimmed or removed to a separate pot if it escapes.
- **Spring onions in Bed D only:** Alliums stunt pea growth. Spring onions isolated on terrace (Bed D) while peas occupy Bed C with the trellis. Explicit constraint notes in both bed files.
- **Bed E 60% reserved:** Minimal spring planting (borage + calendula + radish) with most space held for Phase 3 tomato transplants. Borage and calendula pre-positioned as future companions.
- **Bed letter remapping documented:** Each grid map includes a remapping note explaining how Phase 2 letters (A-E) map to Phase 1 bed numbers (3,1,2,4,5).

## Deviations from Plan

None -- plan executed exactly as written.

## Issues Encountered

None.

## User Setup Required

None -- no external service configuration required.

## Next Phase Readiness

- Grid maps ready for printing before W16 planting day
- Plan 02-02 (planting day session script, bug hotel, water stations) can proceed -- it references these grid maps for planting sequence
- Phase 3 warm-season planning can reference Bed C trellis handoff (W21) and Bed E reserved space

## Self-Check: PASSED

- All 5 grid map files: FOUND
- SUMMARY.md: FOUND
- Commit 317f847: FOUND
- Commit b557336: FOUND

---
*Phase: 02-spring-planting*
*Completed: 2026-03-26*
