---
phase: 3
slug: warm-season-planting
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-26
---

# Phase 3 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Physical verification (checklist-based) + document review |
| **Config file** | None — documentation + physical gardening phase |
| **Quick run command** | Visual inspection of planted beds against updated grid maps |
| **Full suite command** | Walk all 5 beds, verify each Phase 3 plant is in its grid-map position, check session scripts were followed |
| **Estimated runtime** | ~15 minutes per bed walk |

---

## Sampling Rate

- **After every task commit:** Review deliverable for internal consistency and companion planting compliance
- **After every plan wave:** Cross-reference all grid maps for companion violations, spacing realism, requirement coverage
- **Before `/gsd:verify-work`:** All 12 requirements verified; grid maps and session scripts ready for execution
- **Max feedback latency:** Immediate (document review)

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 03-01-01 | 01 | 1 | CROP-02 | manual-only | Verify tomato seedlings at grid map positions, stake in place | N/A | ⬜ pending |
| 03-01-02 | 01 | 1 | CROP-03 | manual-only | Verify cucumber seedlings at trellis base, pea stems removed | N/A | ⬜ pending |
| 03-01-03 | 01 | 1 | CROP-04 | manual-only | Verify pepper seedling at grid map position | N/A | ⬜ pending |
| 03-01-04 | 01 | 1 | ENGM-01 | manual-only | Verify 2-3 sunflower seedlings visible, ruler stake in place | N/A | ⬜ pending |
| 03-01-05 | 01 | 1 | FLWR-01 | manual-only | Verify nasturtiums sown at bed edge, trailing outward | N/A | ⬜ pending |
| 03-01-06 | 01 | 1 | SENS-03 | manual-only | Verify pot with mint plant adjacent to Bed A, path side | N/A | ⬜ pending |
| 03-01-07 | 01 | 1 | SENS-05 | manual-only | Verify basil seedling within 30cm of tomato | N/A | ⬜ pending |
| 03-01-08 | 01 | 1 | COOK-03 | manual-only | Verify 3-4 leek seedlings at 15cm spacing, 15cm deep | N/A | ⬜ pending |
| 03-01-09 | 01 | 1 | COOK-04 | manual-only | Verify bean row in separate bed from leeks | N/A | ⬜ pending |
| 03-01-10 | 01 | 1 | COOK-07 | manual-only | Verify broccoli seedling at grid map position, 30-45cm from neighbors | N/A | ⬜ pending |
| 03-01-11 | 01 | 1 | CRTR-01 | manual-only | Verify dill added near warm crops; borage from Phase 2 | N/A | ⬜ pending |
| 03-01-12 | 01 | 1 | CRTR-02 | manual-only | Verify nasturtiums at bed edge, on daily route, near creature zone | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

- [ ] Updated grid map for Bed C (major rewrite for pea-to-cucumber handoff + warm crop additions)
- [ ] Updated grid map for Bed A (minor — sunflower + nasturtium edge additions)
- [ ] Updated grid map for Bed D (minor — leek addition)
- [ ] Updated grid map for Bed E (moderate — broccoli + bean additions)
- [ ] Session 1 script (W18 direct-sow day)
- [ ] Session 2 script (W21 transplant day with pea harvest party)
- [ ] Sunflower ruler stake setup instructions
- [ ] Warm-season shopping list addendum

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Cherry tomatoes transplanted in Bed C | CROP-02 | Physical planting | Verify seedlings at grid map positions, stake in place |
| Cucumbers on trellis in Bed C | CROP-03 | Physical planting | Verify seedlings at trellis base, pea stems removed |
| Sweet peppers in designated bed | CROP-04 | Physical planting | Verify seedling at grid map position |
| Sunflowers with ruler stake | ENGM-01 | Physical planting + activity setup | Verify 2-3 seedlings visible, ruler stake in place |
| Nasturtiums trailing from bed edge | FLWR-01 | Physical planting | Verify sown at bed edge, trailing outward |
| Mint pot next to his bed | SENS-03 | Physical placement | Verify pot adjacent to Bed A, path side |
| Basil alongside tomatoes | SENS-05 | Physical planting | Verify basil within 30cm of tomato |
| Leeks in terrace bed | COOK-03 | Physical planting | Verify 3-4 seedlings at 15cm spacing, 15cm deep |
| Bush beans NOT adjacent to leeks | COOK-04 | Physical planting + separation | Verify bean row in separate bed from leeks |
| Broccoli transplanted | COOK-07 | Physical planting | Verify seedling at grid map position, 30-45cm spacing |
| Borage and dill for pollinators | CRTR-01 | Physical planting | Verify dill near warm crops; borage from Phase 2 |
| Nasturtiums as aphid trap crop | CRTR-02 | Physical planting | Verify nasturtiums at bed edge, near creature zone |

### Document Verification

| Deliverable | Test | Pass Criteria |
|-------------|------|---------------|
| Updated grid maps | Review for companion planting violations | No beans+leeks in same bed, no fennel near tomatoes, sunflowers at north end |
| Updated grid maps | Review for overcrowding | No bed has more than 6 distinct crop types |
| Session 1 script | Review against Phase 2 format | Has prep list, he-does/father-does split, timing, transition cues |
| Session 2 script | Review for pea harvest celebration | Harvest party is FIRST activity, before any transplanting |
| Session 2 script | Review for ADHD structure | Mandatory break after his-bed portion, total under 100 min |

---

## Validation Sign-Off

- [ ] All tasks have manual verification instructions or Wave 0 dependencies
- [ ] Sampling continuity: document review after every task commit
- [ ] Wave 0 covers all grid map and session script needs
- [ ] No watch-mode flags
- [ ] Feedback latency < immediate (document review)
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
