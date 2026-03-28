---
phase: 09-operational-readiness
plan: 01
subsystem: docs
tags: [shopping-list, budget, tools, purchase-priority, markdown]

# Dependency graph
requires:
  - phase: 07-data-consistency
    provides: Correct bed naming (A-B) and crop assignments
provides:
  - Spring planting shopping list with all Phase 2 plant purchases
  - Purchase priority timeline across all three shopping lists
  - Consolidated tool inventory for build day and planting days
  - Corrected PROJECT.md budget figures
affects: [12-planning-artifact-maintenance]

# Tech tracking
tech-stack:
  added: []
  patterns: [shopping-list-format, purchase-timeline-pattern, tool-inventory-pattern]

key-files:
  created:
    - docs/spring-planting-shopping-list.md
  modified:
    - docs/shopping-list.md
    - docs/warm-season-shopping-list.md
    - .planning/PROJECT.md

key-decisions:
  - "Budget range updated to ~8,500-10,500 DKK based on actual shopping list totals (infrastructure 7,200-7,900 + spring 520-910 + warm-season 430-625)"
  - "Adapted plan from 5-bed to 2-bed reality -- plant inventory extracted from Bed A and Bed B grids only"

patterns-established:
  - "Purchase Priority Timeline: consolidated cross-list ordering in shopping-list.md"
  - "Tool Inventory: categorized by activity with likely-have vs buy-confirm status"

requirements-completed: [OPRD-01, OPRD-02, OPRD-03, OPRD-04]

# Metrics
duration: 2min
completed: 2026-03-28
---

# Phase 9 Plan 1: Operational Readiness Summary

**Spring planting shopping list with 7 plant types and 7 seed packets, cross-list purchase priority timeline (W12-W21), consolidated tool inventory, and corrected PROJECT.md budget**

## Performance

- **Duration:** 2 min
- **Started:** 2026-03-28T13:48:19Z
- **Completed:** 2026-03-28T13:50:30Z
- **Tasks:** 2
- **Files modified:** 4

## Accomplishments
- Created spring planting shopping list covering all Phase 2 purchases (strawberry plugs, raspberry canes, herb plants, seedlings, 7 seed packets, craft materials) with DKK pricing and Danish sourcing tips
- Added Purchase Priority Timeline to shopping-list.md consolidating ordering across all three lists from W12 through W21
- Added Tool Inventory covering build day, spring planting, warm-season planting, and pre-planting craft -- each tool marked as "likely have" or "buy/confirm"
- Updated PROJECT.md budget in both Context and Constraints sections to consistent ~8,500-10,500 DKK with full breakdown

## Task Commits

Each task was committed atomically:

1. **Task 1: Create spring planting shopping list** - `dfdd9d4` (feat)
2. **Task 2: Add purchase priority, tool inventory, and fix budget** - `b601383` (feat)

## Files Created/Modified
- `docs/spring-planting-shopping-list.md` - New Phase 2 spring planting shopping list with plants, seeds, craft materials, budget summary, and shopping timeline
- `docs/shopping-list.md` - Added Tool Inventory section and Purchase Priority Timeline (All Lists) section
- `docs/warm-season-shopping-list.md` - Added cross-reference note pointing to consolidated purchase priority in shopping-list.md
- `.planning/PROJECT.md` - Budget figures updated from 2,000-5,000 DKK to ~8,500-10,500 DKK in both Context and Constraints sections

## Decisions Made
- Budget range calculated as ~8,500-10,500 DKK based on summing actual shopping list subtotals (infrastructure 7,200-7,900 + spring plants 520-910 + warm-season 430-625), rather than the research file's ~10,500-12,000 estimate which was based on a 5-bed layout
- Adapted 5-bed plant inventory from the research file to the current 2-bed reality (Bed A "Family Bed" 230x120 + Bed B "His Bed" 150x60)

## Deviations from Plan

### Auto-fixed Issues

**1. [Rule 3 - Blocking] Adapted plant inventory from 5-bed to 2-bed layout**
- **Found during:** Task 1 (spring planting shopping list creation)
- **Issue:** Plan and research file referenced beds A-E (5 beds) with plant counts extracted from planting-grid-bed-a through bed-e. The garden was finalized as 2 beds (A and B) -- grid files for C, D, and E no longer exist.
- **Fix:** Extracted plant inventory from the actual planting-grid-bed-a.md and planting-grid-bed-b.md files. Adjusted quantities and destinations accordingly (e.g., 3 creeping thyme for Bed B instead of 5 across Beds A+D).
- **Files modified:** docs/spring-planting-shopping-list.md
- **Verification:** All plants from both grid files appear in the shopping list
- **Committed in:** dfdd9d4 (Task 1 commit)

**2. [Rule 1 - Bug] Corrected budget range from ~10,500-12,000 to ~8,500-10,500**
- **Found during:** Task 2 (budget update)
- **Issue:** Plan specified updating budget to "~10,500-12,000 DKK" based on the research file's 5-bed infrastructure estimate of ~9,100-10,300. The actual infrastructure shopping list total is ~7,175-7,875 DKK (2-bed layout).
- **Fix:** Calculated correct total from current shopping list subtotals: 7,200-7,900 (infrastructure) + 520-910 (spring) + 430-625 (warm-season) = ~8,150-10,435, rounded to ~8,500-10,500.
- **Files modified:** .planning/PROJECT.md
- **Verification:** Budget figures are consistent between Context and Constraints sections and match actual list totals
- **Committed in:** b601383 (Task 2 commit)

---

**Total deviations:** 2 auto-fixed (1 blocking, 1 bug)
**Impact on plan:** Both deviations were necessary to align the plan with the current 2-bed garden reality. No scope creep.

## Issues Encountered
None beyond the deviations documented above.

## User Setup Required
None - no external service configuration required.

## Next Phase Readiness
- All three shopping lists are complete and cross-referenced
- Father can execute build day (W16) and planting days without re-consulting any grid maps
- Phase 10 (Home Assistant Setup) has no dependency on this phase and can proceed independently
- Phase 12 (Planning Artifact Maintenance) may want to verify shopping list cross-references remain accurate

---
*Phase: 09-operational-readiness*
*Completed: 2026-03-28*
