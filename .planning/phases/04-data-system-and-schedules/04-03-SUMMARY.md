---
phase: 04-data-system-and-schedules
plan: 03
subsystem: database
tags: [home-assistant, zigbee, sensors, json-schema, bilingual, iot]

# Dependency graph
requires:
  - phase: 04-data-system-and-schedules
    plan: 01
    provides: crop JSON files with moisture/temperature thresholds and bed-to-crop mappings
provides:
  - 10 HA template sensor definitions (moisture + temperature per bed) with havn_ prefix
  - 5 Plant Monitor configurations with most-restrictive thresholds derived from crop data
  - 15 bilingual alert rule definitions (dry, wet, frost per bed)
  - Entity customization with friendly names and mdi icons
  - Sensor hardware buying guide with primary Haozee recommendation
affects: [v2-iot-expansion, ha-dashboard, ha-automations]

# Tech tracking
tech-stack:
  added: [zigbee2mqtt, tuya-ts0601-soil]
  patterns: [per-bed-sensors, most-restrictive-threshold, json-to-yaml-output]

key-files:
  created:
    - data/ha/sensors.json
    - data/ha/plants.json
    - data/ha/customize.json
    - data/ha/alert-rules.json
    - data/sensors/sensor-recommendations.md
  modified: []

key-decisions:
  - "Plant Monitor thresholds use most-restrictive crop value per bed (e.g., Bed A max moisture 50% from lambs-ear)"
  - "Haozee TS0601_soil selected as primary sensor -- community shootout winner, ~150 DKK/unit"
  - "Alert delay: 6 hours for moisture (avoid false alarms from watering), 0 hours for frost (immediate)"

patterns-established:
  - "HA entity naming: sensor.havn_bed_{letter}_{measurement} across all 4 JSON files"
  - "JSON yaml_output field pattern: each JSON file includes the exact HA YAML it would generate"
  - "Bilingual alert messages: {en: string, da: string} consistent with crop file pattern"

requirements-completed: [DATA-04, DATA-05, DATA-06]

# Metrics
duration: 5min
completed: 2026-03-27
---

# Phase 4 Plan 03: HA Schemas and Sensor Recommendations Summary

**10 HA template sensors, 5 Plant Monitor configs with crop-derived thresholds, 15 bilingual alert rules, and Haozee Zigbee sensor buying guide within 800-900 DKK budget**

## Performance

- **Duration:** 5 min
- **Started:** 2026-03-27T06:25:59Z
- **Completed:** 2026-03-27T06:31:00Z
- **Tasks:** 2
- **Files modified:** 5

## Accomplishments
- Created complete HA entity layer: sensors, Plant Monitors, customizations, and alert rules with consistent havn_ naming across all files
- Derived per-bed thresholds from crop data using most-restrictive logic (highest min moisture, lowest max moisture, highest frost threshold)
- Produced actionable sensor buying guide with clear primary recommendation (Haozee TS0601_soil) and budget within 500-1000 DKK target

## Task Commits

Each task was committed atomically:

1. **Task 1: Create Home Assistant JSON schemas** - `8b4b52b` (feat)
2. **Task 2: Create sensor hardware recommendations document** - `c075262` (feat)

## Files Created/Modified
- `data/ha/sensors.json` - 10 template sensor definitions (2 per bed: moisture + temperature)
- `data/ha/plants.json` - 5 Plant Monitor configs with most-restrictive thresholds and derivation notes
- `data/ha/customize.json` - Friendly names and mdi icons for all 10 sensor entities
- `data/ha/alert-rules.json` - 15 automation-ready bilingual alert rules (dry, wet, frost per bed)
- `data/sensors/sensor-recommendations.md` - Hardware buying guide with Haozee primary, ThirdReality alt, Dragino fallback

## Decisions Made
- Plant Monitor thresholds use the most-restrictive value across all crops in a bed (safest -- alerts before any single crop is stressed). Example: Bed A max moisture set to 50% from lambs-ear even though strawberries tolerate 70%.
- Haozee TS0601_soil chosen as primary recommendation based on community testing results, dual-sensor capability, and price point (~150 DKK).
- Alert delay hours set to 6 for moisture (avoids false alarms right after watering) and 0 for frost (immediate notification needed).
- Frost thresholds per bed reflect the most sensitive crop, not an average. Bed C at 4C because cucumbers/basil/peppers are warm-season crops.

## Deviations from Plan

None - plan executed exactly as written.

## Issues Encountered

None

## User Setup Required

None - no external service configuration required. These are reference data files for future v2 HA integration.

## Next Phase Readiness
- HA entity layer complete: all sensor, plant monitor, customization, and alert JSON files ready for YAML generation
- Entity IDs consistent with bed JSON files from Plan 01 (ha_sensors field)
- Sensor hardware guide ready for ordering when v2 IoT expansion begins
- Phase 4 data system complete (all 3 plans delivered)

## Self-Check: PASSED

- All 4 HA JSON files exist and are valid JSON
- sensors.json has 10 entries (5 beds x 2 measurements)
- plants.json has 5 Plant Monitor entries
- alert-rules.json has 15 rules with bilingual messages
- sensor-recommendations.md exists with Haozee primary recommendation
- Both task commits verified (8b4b52b, c075262)

---
*Phase: 04-data-system-and-schedules*
*Completed: 2026-03-27*
