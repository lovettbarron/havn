---
phase: 11-season-2-preparation
plan: 02
subsystem: documentation
tags: [season-review, troubleshooting, json-schema, child-engagement]

requires:
  - phase: 04-data-system
    provides: JSON schema conventions (crop.schema.json)
  - phase: 05-documentation
    provides: Troubleshooting guide format and severity system
provides:
  - Season review template (markdown scorecard + JSON schema)
  - Crop failure recovery guidance with replanting windows
affects: [11-season-2-preparation]

tech-stack:
  added: []
  patterns: [dual-format templates (markdown + JSON schema)]

key-files:
  created:
    - docs/season-review-template.md
    - data/schemas/season-review.schema.json
  modified:
    - docs/troubleshooting-guide.md

key-decisions:
  - "Included all 27 crops in scorecard (including Tumbling Tom backup and pea shoots)"
  - "Kept JSON schema flat (one season per file, not multi-year)"

patterns-established:
  - "Season review uses locked field set: crop_name, planted_week, germinated, harvested, yield, child_engagement, verdict, notes"
  - "Crop failure framing: emotional first, optional replacement, empty space is OK"

requirements-completed: [SSN2-04, SSN2-05]

duration: 2min
completed: 2026-03-28
---

# Phase 11 Plan 02: Season Review and Crop Failure Recovery Summary

**Season review scorecard (27 crops, dual markdown/JSON format) and crop failure recovery guide with month-by-month replanting windows**

## Performance

- **Duration:** 2 min
- **Started:** 2026-03-28T22:02:54Z
- **Completed:** 2026-03-28T22:05:15Z
- **Tasks:** 2
- **Files modified:** 3

## Accomplishments
- Season review template with pre-populated scorecard for all 27 garden crops (English/Danish names)
- JSON schema for structured season review data with child_engagement as first-class field
- Crop failure recovery section added to troubleshooting guide with 4 failure scenarios and month-by-month replanting windows (May-August)

## Task Commits

Each task was committed atomically:

1. **Task 1: Season review template and JSON schema** - `f13d18c` (feat)
2. **Task 2: Add crop failure recovery section to troubleshooting guide** - `09e88b3` (feat)

## Files Created/Modified
- `docs/season-review-template.md` - Markdown scorecard template with bed walk instructions and 27-crop table
- `data/schemas/season-review.schema.json` - JSON schema with yield/engagement/verdict enums, crop_id references
- `docs/troubleshooting-guide.md` - Extended with Crop Failure Recovery section (replanting table, 4 scenarios, quick growers)

## Decisions Made
- Included all 27 crops in scorecard including Tumbling Tom (backup pot crop) and pea shoots -- complete record even if some were not planted
- Kept JSON schema as single-season capture, not multi-year database (per project guardrails)

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None.

## User Setup Required

None - no external service configuration required.

## Next Phase Readiness
- Season review template ready for use at W44 (late October) season wind-down
- Crop failure recovery section ready for mid-season reference if any plants fail
- All files follow existing project conventions and naming

## Self-Check: PASSED

All 3 files verified present. Both task commits (f13d18c, 09e88b3) verified in git log.

---
*Phase: 11-season-2-preparation*
*Completed: 2026-03-28*
