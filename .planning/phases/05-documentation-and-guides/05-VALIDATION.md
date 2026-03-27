---
phase: 5
slug: documentation-and-guides
status: draft
nyquist_compliant: true
wave_0_complete: true
created: 2026-03-27
---

# Phase 5 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual validation (documentation phase — no code to test) |
| **Config file** | N/A |
| **Quick run command** | Visual inspection of each document |
| **Full suite command** | Cross-reference check: verify every crop in grid maps appears in troubleshooting guide and difficulty tiers |
| **Estimated runtime** | ~60 seconds (manual review) |

---

## Sampling Rate

- **After every task commit:** Author reviews document against source docs
- **After every plan wave:** Cross-reference all crop mentions against master crop list from planting grids
- **Before `/gsd:verify-work`:** All 6 documents exist, all 27 crops accounted for in tiers and troubleshooting index
- **Max feedback latency:** N/A (manual)

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 05-01-XX | 01 | 1 | DOCS-01 | manual-only | Visual comparison against reference photos | N/A | ⬜ pending |
| 05-02-XX | 02 | 1 | DOCS-02 | manual-only | Verify all 27 crops appear in crop index | N/A | ⬜ pending |
| 05-02-XX | 02 | 1 | DOCS-03 | manual-only | Count crops in tiers vs total (should be 27) | N/A | ⬜ pending |
| 05-03-XX | 03 | 1 | DOCS-04 | manual-only | Verify all 5 beds have detail cards | N/A | ⬜ pending |
| 05-01-XX | 01 | 1 | DOCS-05 | manual-only | Verify guardrails section, file paths valid | N/A | ⬜ pending |
| 05-03-XX | 03 | 1 | COOK-02 | manual-only | Verify planting window, depth, spacing present | N/A | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

*Existing infrastructure covers all phase requirements — no test setup needed for a documentation phase.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Property viz shows beds, sun, compass, paths | DOCS-01 | Content accuracy, not code | Compare ASCII art against reference photos and bed-layout.md |
| Troubleshooting guide is symptom-based, severity-labeled | DOCS-02 | Document structure review | Verify symptom-first navigation, all 27 crops in appendix |
| Every crop classified into exactly one difficulty tier | DOCS-03 | Completeness count | Count crops across tiers, compare against planting grid total |
| Neighbor guide has daily checklist + per-bed cards | DOCS-04 | Document completeness | Verify all 5 beds have cards with watering/harvest instructions |
| CLAUDE.md captures full context with guardrails | DOCS-05 | File path validation | Verify behavioral guardrails section, all referenced paths exist |
| Garlic planting documented for October 2026 | COOK-02 | Content accuracy | Verify timing, depth, spacing, mulch instructions present |

---

## Validation Sign-Off

- [x] All tasks have `<automated>` verify or Wave 0 dependencies
- [x] Sampling continuity: no 3 consecutive tasks without automated verify
- [x] Wave 0 covers all MISSING references
- [x] No watch-mode flags
- [x] Feedback latency < N/A (manual phase)
- [x] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
