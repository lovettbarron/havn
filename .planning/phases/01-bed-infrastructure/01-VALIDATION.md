---
phase: 1
slug: bed-infrastructure
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-26
---

# Phase 1 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Physical verification (checklist-based) + document validation |
| **Config file** | none — Wave 0 creates checklist templates |
| **Quick run command** | Visual inspection checklist per bed |
| **Full suite command** | Complete walkthrough of all 5 beds + trellis + reservoirs + document review |
| **Estimated runtime** | ~30 minutes (physical inspection) |

---

## Sampling Rate

- **After every task commit:** Review deliverable completeness against checklist
- **After every plan wave:** Cross-reference all documents for internal consistency (e.g., shopping list quantities match setup instructions)
- **Before `/gsd:verify-work`:** Full suite must be green — all 9 requirements verified
- **Max feedback latency:** N/A (manual verification phase)

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 01-01-01 | 01 | 1 | INFRA-07 | unit | Verify shopping list has: product, qty, price, supplier, link | Wave 0 | ⬜ pending |
| 01-01-02 | 01 | 1 | DOCS-06 | unit | Verify two price columns exist (corten + galvanized) | Wave 0 | ⬜ pending |
| 01-02-01 | 02 | 1 | INFRA-01 | manual-only | Visual inspection + measurement of 3 backyard beds | N/A — physical | ⬜ pending |
| 01-02-02 | 02 | 1 | INFRA-02 | manual-only | Visual inspection + weight documentation for terrace beds | N/A — physical | ⬜ pending |
| 01-02-03 | 02 | 1 | INFRA-03 | manual-only | Layer depth measurement during fill | N/A — physical | ⬜ pending |
| 01-03-01 | 03 | 2 | INFRA-04 | manual-only | Visual + continuity check (no gaps in copper tape) | N/A — physical | ⬜ pending |
| 01-03-02 | 03 | 2 | INFRA-05 | manual-only | Fill reservoir via tube, observe water level, verify overflow | N/A — physical | ⬜ pending |
| 01-03-03 | 03 | 2 | INFRA-06 | manual-only | Stability test (push test), mesh attached | N/A — physical | ⬜ pending |
| 01-03-04 | 03 | 2 | INFRA-08 | unit | Verify instructions cover: placement, soil fill, reservoir, trellis | Wave 0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] Verification checklist template (for physical inspection of completed beds)
- [ ] Shopping list template with dual-pricing columns (corten + galvanized)
- [ ] Setup instructions template covering all construction steps

*Physical construction phases have minimal automated testing — Wave 0 focuses on document structure validation.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| 3 corten beds positioned in west-central yard | INFRA-01 | Physical construction | Measure positions, verify sun exposure, confirm near water tap |
| 2 terrace beds on roof terrace | INFRA-02 | Physical construction | Verify placement along railing, document weight calculation |
| Soil layers correct | INFRA-03 | Physical material | Measure drainage layer (5-10cm gravel), garden waste layer, hojbedsmuld top layer |
| Copper tape on all bed edges | INFRA-04 | Physical material | Check all 4 sides of each bed, verify no gaps, 50mm+ width |
| Self-watering reservoirs functional | INFRA-05 | Physical system | Fill via tube, check water level indicator, trigger overflow |
| A-frame trellis installed | INFRA-06 | Physical construction | Push test for stability, verify mesh attachment |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency documented
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
