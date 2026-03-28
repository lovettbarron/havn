---
phase: 10
slug: home-assistant-setup
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 10 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual verification (documentation-only phase) |
| **Config file** | N/A |
| **Quick run command** | Visual review of YAML syntax in walkthrough |
| **Full suite command** | HA Developer Tools > Check Configuration (post-install) |
| **Estimated runtime** | ~30 seconds (manual review) |

---

## Sampling Rate

- **After every task commit:** Verify YAML blocks parse correctly (no syntax errors)
- **After every plan wave:** Review complete walkthrough flow end-to-end
- **Before `/gsd:verify-work`:** All three HAIG requirements addressed in walkthrough
- **Max feedback latency:** 30 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 10-01-01 | 01 | 1 | HAIG-01 | manual-only | Review `docs/ha-setup-guide.md` sections 1-5 | ❌ W0 | ⬜ pending |
| 10-01-02 | 01 | 1 | HAIG-02 | manual-only | Review dashboard YAML in walkthrough step 7 | ❌ W0 | ⬜ pending |
| 10-01-03 | 01 | 1 | HAIG-03 | manual-only | Search for REPLACEME placeholder + finding instructions | ❌ W0 | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

*Existing infrastructure covers all phase requirements. This is a documentation-only phase — no test framework or test files needed.*

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Walkthrough covers sensors, plant monitors, alerts in sequence | HAIG-01 | Documentation completeness requires human review | Read `docs/ha-setup-guide.md` end-to-end, verify all 8 steps present with YAML blocks |
| Dashboard YAML shows per-bed moisture and temperature cards | HAIG-02 | Visual layout verification requires human judgment | Paste vertical-stack YAML into HA card editor, verify Bed A and Bed B sections render with gauge cards |
| Notification target documented as user-specific with instructions | HAIG-03 | Instruction clarity requires human assessment | Search walkthrough for `REPLACEME`, verify step 6 explains how to find actual service name via Developer Tools > Actions |

---

## Validation Sign-Off

- [ ] All tasks have manual verification instructions
- [ ] Sampling continuity: every task has explicit review criteria
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 30s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
