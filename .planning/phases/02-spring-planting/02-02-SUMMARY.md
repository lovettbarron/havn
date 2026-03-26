---
phase: 02-spring-planting
plan: 02
subsystem: garden-sessions
tags: [planting-script, bug-hotel, pollinator, adhd-engagement, session-structure]

# Dependency graph
requires:
  - phase: 01-bed-infrastructure
    provides: bed dimensions, placement, and layout for session references
provides:
  - W16 planting day session script with timed sessions, break points, and transition cues
  - W17-W18 follow-up session plans for succession sowing
  - Bug hotel construction guide as separate weekend activity
  - Two pollinator water station setup guides with maintenance
  - Creature observation checklist
  - Pre-planting craft activity (painted markers) for W15
affects: [03-warm-season, 04-data-system]

# Tech tracking
tech-stack:
  added: []
  patterns: [session-script-format, motor-skill-task-split, nature-activity-guide]

key-files:
  created:
    - docs/planting-day-script.md
    - docs/bug-hotel-guide.md
  modified: []

key-decisions:
  - "Session script uses mandatory snack break after Session 1 (his bed) to reset ADHD attention"
  - "Terrace beds (Session 3) marked as optional to keep total under 100 min"
  - "Bug hotel treasure hunt (15 min material collection) is half the child activity"
  - "Two water stations create two observation points for sustained engagement"

patterns-established:
  - "Session script format: prep, numbered sessions with HE/FATHER task splits, transition cues, time targets"
  - "Nature activity format: materials list, step-by-step build, child involvement callouts, observation checklist"

requirements-completed: [ENGM-02, ENGM-03, CRTR-03, CRTR-04]

# Metrics
duration: 3min
completed: 2026-03-26
---

# Phase 2 Plan 02: Session Script and Bug Hotel Summary

**W16 planting day session script with motor-skill task splits, mandatory breaks, and transition cues, plus bug hotel construction guide with two pollinator water stations for W17-W18**

## Performance

- **Duration:** 3 min
- **Started:** 2026-03-26T22:09:27Z
- **Completed:** 2026-03-26T22:13:11Z
- **Tasks:** 2
- **Files modified:** 2

## Accomplishments
- Complete W16 planting day script: 3 sessions + mandatory break, ~75-100 min total, with contingency plans for rain, meltdowns, and germination failure
- Bug hotel construction guide as standalone W17/W18 weekend activity with treasure hunt, step-by-step build, and creature observation checklist
- Two pollinator water stations with maintenance schedule and mosquito prevention
- Pre-planting craft activity (painted plant markers) for W15 anticipation building

## Task Commits

Each task was committed atomically:

1. **Task 1: Create planting day session script** - `19efe89` (feat)
2. **Task 2: Create bug hotel guide and pollinator water stations** - `93487fe` (feat)

## Files Created/Modified
- `docs/planting-day-script.md` - W16 planting day sessions (prep, his bed, shared beds, terrace), W17-W18 follow-ups, craft activity, contingency plans
- `docs/bug-hotel-guide.md` - Nature corner placement, bug hotel construction, two pollinator water stations, creature observation checklist

## Decisions Made
- Session 3 (terrace beds) marked as optional -- backyard beds are the priority, terrace can wait to W17 if energy runs out
- Treasure hunt (15 min material collection) built into bug hotel activity as engagement mechanism, not just construction
- Lemon balm containment approach: plant at outer edge corner only, trim runners monthly, relocate to pot if invasive in season 2
- Water station cleaning weekly to prevent mosquito breeding (7-10 day larval cycle)

## Deviations from Plan

None -- plan executed exactly as written.

## Issues Encountered

None.

## User Setup Required

None -- no external service configuration required.

## Next Phase Readiness
- Session script and bug hotel guide are ready for use on planting weekend
- Grid maps (Plan 02-01) are referenced but not yet created -- must be completed before W16
- Both files cross-reference each other and the grid map files for a connected documentation set

---
*Phase: 02-spring-planting*
*Completed: 2026-03-26*
