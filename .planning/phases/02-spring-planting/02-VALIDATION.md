---
phase: 2
slug: spring-planting
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-26
---

# Phase 2 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Physical verification (checklist-based) + document review |
| **Config file** | None — documentation + physical gardening phase |
| **Quick run command** | Visual inspection of planted beds against grid maps |
| **Full suite command** | Walk all 5 beds, verify each plant position matches grid map, check session script was followed |
| **Estimated runtime** | ~15 minutes (physical walk-through) |

---

## Sampling Rate

- **After every task commit:** Review deliverable (grid map, script) for internal consistency and companion planting compliance
- **After every plan wave:** Cross-reference all grid maps for: no companion violations, total plant count realistic for bed size, succession slots marked
- **Before `/gsd:verify-work`:** Full suite must be green — all grid maps printed and ready for planting day
- **Max feedback latency:** Same-day review

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 02-01-01 | 01 | 1 | ENGM-04 | unit | Verify grid map documents exist for all 5 beds with plant positions and spacing | ❌ W0 | ⬜ pending |
| 02-01-02 | 01 | 1 | SCHED-01 | unit | Verify 5 grid map files with spacing, positions, and succession slots | ❌ W0 | ⬜ pending |
| 02-02-01 | 02 | 1 | CROP-01 | manual-only | Count strawberry plants, verify spacing against grid map | N/A | ⬜ pending |
| 02-02-02 | 02 | 1 | CROP-05 | manual-only | Count canes (3), verify 45cm spacing | N/A | ⬜ pending |
| 02-02-03 | 02 | 1 | CROP-06 | manual-only | Verify sown rows + empty succession slots in grid map | N/A | ⬜ pending |
| 02-02-04 | 02 | 1 | ENGM-02 | manual-only | Verify broadcast area matches grid map | N/A | ⬜ pending |
| 02-02-05 | 02 | 1 | ENGM-03 | manual-only | Verify dense sowing in designated area | N/A | ⬜ pending |
| 02-02-06 | 02 | 1 | FLWR-02 | manual-only | Verify calendula positions match grid map | N/A | ⬜ pending |
| 02-02-07 | 02 | 1 | FLWR-03 | manual-only | Verify borage position in Bed C/E per grid map | N/A | ⬜ pending |
| 02-02-08 | 02 | 1 | FLWR-04 | manual-only | Verify viola edge placement | N/A | ⬜ pending |
| 02-02-09 | 02 | 1 | FLWR-05 | manual-only | Verify chive perimeter planting around raspberry canes | N/A | ⬜ pending |
| 02-02-10 | 02 | 1 | SENS-01 | manual-only | Verify lamb's ear at path-side edge | N/A | ⬜ pending |
| 02-02-11 | 02 | 1 | SENS-02 | manual-only | Verify lemon balm edge placement, containment method | N/A | ⬜ pending |
| 02-02-12 | 02 | 1 | SENS-04 | manual-only | Verify creeping thyme at bed edges on path side | N/A | ⬜ pending |
| 02-02-13 | 02 | 1 | COOK-01 | manual-only | Verify spring onion row, away from peas | N/A | ⬜ pending |
| 02-02-14 | 02 | 1 | COOK-05 | manual-only | Verify kale position in Bed C, 30cm spacing | N/A | ⬜ pending |
| 02-02-15 | 02 | 1 | COOK-06 | manual-only | Verify peas sown at trellis base, 5cm spacing | N/A | ⬜ pending |
| 02-03-01 | 03 | 2 | CRTR-03 | manual-only | Verify bug hotel/log pile in shaded area | N/A | ⬜ pending |
| 02-03-02 | 03 | 2 | CRTR-04 | manual-only | Verify two dishes with pebbles placed | N/A | ⬜ pending |
| 02-03-03 | 03 | 2 | ENGM-02, ENGM-03, ENGM-04 | manual-only | Verify session script was followed, child engagement documented | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] Grid map template file — establish the format for all 5 beds (positions, spacing, companion notes)
- [ ] Session script template file — planting day activity structure for child engagement

*These must exist before Wave 1 planning deliverables can be verified.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Strawberries planted correctly | CROP-01 | Physical planting | Count plants, verify spacing matches grid map |
| Raspberry canes in place | CROP-05 | Physical planting | Count 3 canes, verify 45cm spacing |
| Radish rows sown | CROP-06 | Physical sowing | Verify rows + succession slots marked |
| Lettuce broadcast | ENGM-02 | Physical sowing | Verify broadcast area matches grid map |
| Pea shoots sown | ENGM-03 | Physical sowing | Verify dense sowing in designated area |
| Calendula positioned | FLWR-02 | Physical planting | Verify positions near vegetables across beds |
| Borage positioned | FLWR-03 | Physical planting | Verify in Bed C/E near tomato/cucumber areas |
| Viola at edges | FLWR-04 | Physical planting | Verify edge placement in his bed |
| Chives at raspberry base | FLWR-05 | Physical planting | Verify perimeter around canes |
| Lamb's ear at edges | SENS-01 | Physical planting | Verify path-side edge in his bed |
| Lemon balm contained | SENS-02 | Physical planting | Verify edge or pot containment |
| Thyme at edges | SENS-04 | Physical planting | Verify creeping thyme at path-side edges |
| Spring onions sown | COOK-01 | Physical sowing | Verify row placement, separated from peas |
| Kale sown | COOK-05 | Physical sowing | Verify Bed C position, 30cm spacing |
| Peas on trellis | COOK-06 | Physical sowing | Verify at A-frame trellis base, 5cm spacing |
| Bug hotel built | CRTR-03 | Physical construction | Verify structure in shaded area |
| Water dishes placed | CRTR-04 | Physical placement | Verify 2 dishes with pebbles |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < same-day
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
