---
phase: 08-child-engagement-bridge
plan: 01
subsystem: docs
tags: [printable, adhd, bilingual, routine, engagement]

# Dependency graph
requires:
  - phase: 04-data-system
    provides: crop JSON files with child_actions and sensory engagement data
  - phase: 07-data-consistency
    provides: correct bed-to-crop assignments in data/beds/*.json
provides:
  - "Printable daily 5-minute routine card (docs/daily-routine-card.md)"
  - "Printable weekly 10-minute garden walk checklist (docs/weekly-garden-walk.md)"
affects: [08-child-engagement-bridge, 09-operational-readiness]

# Tech tracking
tech-stack:
  added: []
  patterns: [visual-first-emoji-icons, bilingual-english-danish, adhd-adapted-time-boxing]

key-files:
  created:
    - docs/daily-routine-card.md
    - docs/weekly-garden-walk.md
  modified: []

key-decisions:
  - "Danish cues are father-spoken prompts, not child-readable text"
  - "No checkboxes on daily card -- it is a walk-through, not a form"
  - "Weekly walk uses pick-2-of-4 model for child choice"

patterns-established:
  - "Visual-first docs: emoji icons as primary communication for child-facing materials"
  - "Bilingual pattern: English action word + Danish father cue (Far siger)"
  - "ADHD time-boxing: explicit max duration with permission to finish early"

requirements-completed: [CENG-01, CENG-03]

# Metrics
duration: 2min
completed: 2026-03-28
---

# Phase 8 Plan 1: Child Engagement Bridge Summary

**Printable daily routine card (5-step morning walk) and weekly garden walk checklist (4 sensory/harvest/growth activities) with bilingual emoji-driven design for independent use by a 7-year-old**

## Performance

- **Duration:** 2 min
- **Started:** 2026-03-28T07:47:04Z
- **Completed:** 2026-03-28T07:48:47Z
- **Tasks:** 2
- **Files created:** 2

## Accomplishments
- Daily routine card with 5 predictable steps (LOOK, TOUCH, WATER, PICK, MEASURE) using emoji icons as primary communication
- Weekly garden walk with 4 self-contained activities (SENSORY, CREATURE, HARVEST, GROWTH) each time-boxed to 2-3 minutes
- All bed-to-crop assignments verified against data/beds/*.json source of truth
- Bilingual design: English action words for the child + Danish verbal cues for the father
- Father's notes sections with ADHD-aware guidance (skip-friendly, early-exit-encouraged, never-extend rules)

## Task Commits

Each task was committed atomically:

1. **Task 1: Create daily routine card** - `0b707a8` (feat)
2. **Task 2: Create weekly garden walk checklist** - `5018ef0` (feat)

## Files Created/Modified
- `docs/daily-routine-card.md` - Printable 5-step daily morning garden routine card
- `docs/weekly-garden-walk.md` - Printable weekly garden walk with 4 activities + seasonal highlights

## Decisions Made
- Danish cues are designed for the father to say aloud, not for the child to read -- the child follows emoji icons only
- Daily card has no checkboxes -- it is a walk-through routine, not a completion form
- Weekly walk uses a "pick 2-3 of 4" model so the child has agency over which activities to do
- Seasonal highlights kept as a separate section (potential second page) to keep the main activities on one A4 page

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None.

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness
- Both printable cards ready for lamination before W16 planting season
- Plan 08-02 (if it exists) can build on these cards with additional engagement materials
- Cards reference correct crop assignments that were fixed in Phase 7

---
*Phase: 08-child-engagement-bridge*
*Completed: 2026-03-28*
