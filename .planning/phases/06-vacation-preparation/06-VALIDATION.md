---
phase: 6
slug: vacation-preparation
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-27
---

# Phase 6 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual validation (physical garden activities) |
| **Config file** | None — no automated test infrastructure for this phase |
| **Quick run command** | Manual checklist review |
| **Full suite command** | Physical walkthrough of all deliverables |
| **Estimated runtime** | N/A — manual verification |

---

## Sampling Rate

- **After every task commit:** Review markdown for formatting, completeness, and consistency with established patterns
- **After every plan wave:** Cross-reference all deliverables for consistency (bed letters, timing, material quantities)
- **Before `/gsd:verify-work`:** All checklist items accounted for, neighbor guide photo placeholders addressed, JSON validates against schema
- **Max feedback latency:** N/A — manual verification

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| TBD | 01 | 1 | VACN-01 | manual-only | N/A | N/A | ⬜ pending |
| TBD | 01 | 1 | VACN-02 | manual-only | N/A | N/A | ⬜ pending |
| TBD | 02 | 2 | VACN-03 | manual-only | N/A | N/A | ⬜ pending |
| TBD | 02 | 2 | VACN-04 | manual-only | N/A | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements. No test framework or stubs needed — this phase produces documentation and physical activity protocols, not code.

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Reservoir tested and confirmed for 5+ days | VACN-01 | Physical 5-day test with daily finger check | Fill reservoirs, stop manual watering, check soil moisture daily for 5 days |
| All beds mulched 5-8cm straw/bark | VACN-02 | Physical measurement with depth stick | Spread mulch, measure depth at 3 points per bed using marked stick |
| Pre-vacation harvest protocol executed | VACN-03 | Physical harvest of everything showing color | Walk all beds, pick all produce showing color, complete checklist |
| Neighbor received printed guide with walk-through | VACN-04 | Physical delivery and walk-through | Print guide, walk neighbor through garden bed-by-bed (15-20 min), hand over printed copy |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency confirmed
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
