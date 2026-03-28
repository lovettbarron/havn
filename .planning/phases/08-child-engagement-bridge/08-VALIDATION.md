---
phase: 8
slug: child-engagement-bridge
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 8 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual review (documentation phase, no code tests) |
| **Config file** | none — no test framework needed |
| **Quick run command** | Visual inspection of markdown rendering |
| **Full suite command** | Render each markdown file to PDF via browser print, verify single-page A4 fit |
| **Estimated runtime** | ~60 seconds (manual) |

---

## Sampling Rate

- **After every task commit:** Verify markdown renders correctly, bed names are A-E, crop references match JSON data
- **After every plan wave:** Print all documents to PDF and verify single-page fit
- **Before `/gsd:verify-work`:** All documents reviewed against success criteria
- **Max feedback latency:** 60 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 8-01-01 | 01 | 1 | CENG-01 | manual-only | Render markdown, verify fits A4 single page | ❌ W0 | ⬜ pending |
| 8-01-02 | 01 | 1 | CENG-03 | manual-only | Count activities (3-5), sum time (5-10 min) | ❌ W0 | ⬜ pending |
| 8-01-03 | 01 | 1 | CENG-02 | manual-only | Verify activities reference correct crops/weeks | ❌ W0 | ⬜ pending |
| 8-01-04 | 01 | 1 | CENG-04 | manual-only | Verify max 1 step for child, approach documented | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements. No test framework installation needed — this is a documentation-only phase. Verification is manual review against success criteria.

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Daily routine card is printable, visual, 5-min checklist | CENG-01 | Human judgment: visual design, icon clarity, print layout | Render to PDF, check A4 fit, verify 5 steps with icons, no reading required |
| W19-W20 gap activities are structured | CENG-02 | Content correctness: activities match schedule data | Cross-check activities against `data/schedules/w19.json` and `w20.json` |
| Weekly walk has 3-5 activities, 5-10 min | CENG-03 | Count and time verification | Count listed activities (3-5), sum time estimates (5-10 min range) |
| Photo log is low friction | CENG-04 | Friction assessment is subjective | Verify approach is ≤3 sentences, requires one action from child |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 60s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
