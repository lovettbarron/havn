---
phase: 4
slug: data-system-and-schedules
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-26
---

# Phase 4 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | JSON Schema Draft 2020-12 validation + python3 json.tool |
| **Config file** | `data/schemas/crop.schema.json` (created in Wave 0) |
| **Quick run command** | `python3 -m json.tool data/crops/*.json > /dev/null` |
| **Full suite command** | Manual review: every crop file has all required fields, every week file exists W15-W44, succession calendar has no gaps |
| **Estimated runtime** | ~5 seconds |

---

## Sampling Rate

- **After every task commit:** Run `python3 -m json.tool {new-file}.json`
- **After every plan wave:** Count files against expected totals; spot-check 3 random crop files for field completeness
- **Before `/gsd:verify-work`:** All 9 requirements verified — full suite must be green
- **Max feedback latency:** 5 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 04-01-01 | 01 | 1 | DATA-01 | manual review | Verify schema file has growth_stages, water_needs, harvest, companion_plants, difficulty, child_actions, alert thresholds | ❌ W0 | ⬜ pending |
| 04-01-02 | 01 | 1 | DATA-02 | manual count | `ls data/crops/*.json \| wc -l` should be >= 27 | ❌ W0 | ⬜ pending |
| 04-02-01 | 02 | 1 | DATA-03 | manual count | `ls data/schedules/w*.json \| wc -l` should be 30 | ❌ W0 | ⬜ pending |
| 04-02-02 | 02 | 1 | SCHED-02 | manual review | Check succession-calendar.json gap_analysis.gaps_found is empty | ❌ W0 | ⬜ pending |
| 04-02-03 | 02 | 1 | SCHED-03 | manual review | Every weekly JSON has at least one must_do task | ❌ W0 | ⬜ pending |
| 04-02-04 | 02 | 1 | SCHED-04 | manual review | Check succession-calendar.json has entries for all 5 succession crops | ❌ W0 | ⬜ pending |
| 04-03-01 | 03 | 2 | DATA-04 | manual review | Check sensors.json for haven_bed_{a-e}_{measurement} pattern | ❌ W0 | ⬜ pending |
| 04-03-02 | 03 | 2 | DATA-05 | manual review | Check plants.json has min_moisture, max_moisture, min_temperature per bed | ❌ W0 | ⬜ pending |
| 04-03-03 | 03 | 2 | DATA-06 | manual review | Check sensor-recommendations.md for 2-3 Zigbee + 1 LoRaWAN with prices | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] `data/` directory structure — does not exist yet
- [ ] `data/schemas/crop.schema.json` — formal schema for crop files
- [ ] JSON syntax validation uses built-in `python3 -m json.tool` — no framework install needed

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Crop schema covers all required fields | DATA-01 | Schema correctness is a design review | Review crop.schema.json against requirements list |
| Succession planting has no 2-week harvest gap | SCHED-02 | Requires domain knowledge of growth timelines | Review succession-calendar.json gap_analysis section |
| HA entity naming follows haven_ convention | DATA-04 | Naming convention check | Grep sensors.json for haven_ prefix pattern |
| Sensor recommendations have prices and HA compatibility | DATA-06 | Requires human judgement on completeness | Review sensor-recommendations.md for specificity |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 5s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
