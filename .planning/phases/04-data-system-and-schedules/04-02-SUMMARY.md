---
phase: 04-data-system-and-schedules
plan: 02
subsystem: database
tags: [json-schema, weekly-schedules, succession-calendar, bilingual, child-prompts]

# Dependency graph
requires:
  - phase: 04-data-system-and-schedules
    plan: 01
    provides: 27 crop JSON files with crop_id references and growth stages
provides:
  - 30 weekly schedule JSON files (W15-W44) with themed names, hero tasks, bilingual prompts
  - JSON Schema Draft 2020-12 for weekly schedule validation
  - Master succession calendar with gap analysis proving no 2-week harvest gap
  - Sowing schedule for 5 succession crops (radish, lettuce, spring onion, peas, beans)
affects: [04-03-ha-schemas, 06-vacation-planning]

# Tech tracking
tech-stack:
  added: []
  patterns: [weekly-schedule-per-iso-week, succession-sowing-slots, bilingual-growth-event-prompts]

key-files:
  created:
    - data/schemas/week.schema.json
    - data/succession-calendar.json
    - data/schedules/w15.json through data/schedules/w44.json (30 files)
  modified: []

key-decisions:
  - "Succession radish sowing every 2 weeks W16-W32 across beds A/C/D rotating for continuous supply"
  - "Vacation weeks W30-W33 flag neighbor watering with simple instructions"
  - "Late-season hero tasks shift from planting to harvesting, observation, and seasonal activities"
  - "Gap analysis validates minimum 2 harvestable crops every week W22-W43 with 1-week buffer on estimates"

patterns-established:
  - "Weekly schedule ID format: W{nn}-{nn} for task IDs"
  - "Hero task is most exciting child-visible activity that week"
  - "Growth event prompts use discovery language (Can you find/Kan du finde) not botanical facts"
  - "Sowing tasks array links succession calendar sowings to weekly action items"

requirements-completed: [DATA-03, SCHED-02, SCHED-03, SCHED-04]

# Metrics
duration: 13min
completed: 2026-03-27
---

# Phase 4 Plan 02: Weekly Schedules and Succession Calendar Summary

**30 weekly schedule JSON files (W15-W44) with child-friendly bilingual prompts and themed hero tasks, plus succession calendar proving continuous harvest W22-W43**

## Performance

- **Duration:** 13 min
- **Started:** 2026-03-27T06:25:42Z
- **Completed:** 2026-03-27T06:38:42Z
- **Tasks:** 2
- **Files modified:** 32

## Accomplishments
- Created JSON Schema Draft 2020-12 for weekly schedule files with bilingual support, task priority/who/minutes structure, and sowing_tasks array
- Built succession calendar with 5 succession crops (radish, lettuce, spring onion, peas, bush beans) and 11 continuous-harvest crops, with gap analysis confirming no 2-week harvest gap W22-W43
- Populated 30 weekly schedule files spanning the full growing season from preparation (W15) through winter tuck-in (W44)
- Every week has themed name, hero task, at least one must_do task, and bilingual growth event prompts using discovery-oriented child language

## Task Commits

Each task was committed atomically:

1. **Task 1: Create week schema, succession calendar, and weekly schedules W15-W29** - `d62ae6d` (feat)
2. **Task 2: Create weekly schedules W30-W44 (late season)** - `0e3aed1` (feat)

## Files Created/Modified
- `data/schemas/week.schema.json` - JSON Schema for weekly schedule validation
- `data/succession-calendar.json` - Master sowing/harvest timeline with gap analysis for 16 crops
- `data/schedules/w15.json` - Preparation Week (paint markers, check beds)
- `data/schedules/w16.json` - Planting Day Week (big planting day with all beds)
- `data/schedules/w23.json` - First Strawberry Week (first harvest milestone)
- `data/schedules/w28.json` - Tomato Treasure Week (cherry tomato harvest begins)
- `data/schedules/w31.json` - Raspberry Rush (Autumn Bliss starts producing)
- `data/schedules/w35.json` - Harvest Festival (peak diversity, 9+ crops)
- `data/schedules/w42.json` - Frost Watch (frost protection, seasonal change)
- `data/schedules/w44.json` - Tuck In Week (mulch beds, store tools, season end)
- Plus 22 additional weekly schedule files (W17-W22, W24-W27, W29-W30, W32-W34, W36-W41, W43)

## Decisions Made
- Succession radish uses 3-bed rotation (A, C, D) to avoid depleting any single bed
- Lettuce alternates between beds D and E for continuous cut-and-come-again supply
- W30-W33 (typical Danish summer holiday) include vacation prep tasks and neighbor watering flagging
- Garlic planting for Year 2 placed in W40-W41 per CLAUDE.md key dates
- 1-week buffer added to all harvest estimates per research pitfall 3 (Danish summers can be cool)

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness
- Weekly schedule data complete: all 30 weeks with bilingual prompts and task structure
- Succession calendar validated: continuous harvest coverage W22-W43
- Ready for Plan 03 (HA schemas) which will use sensor entity references and alert thresholds
- Weekly schedules reference crop_id values consistent with Plan 01 crop files

## Self-Check: PASSED

- All 30 weekly schedule files exist and are valid JSON
- Week schema exists
- Succession calendar exists with gap_analysis.coverage_ok = true
- Both task commits verified (d62ae6d, 0e3aed1)

---
*Phase: 04-data-system-and-schedules*
*Completed: 2026-03-27*
