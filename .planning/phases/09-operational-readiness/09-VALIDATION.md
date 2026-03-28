---
phase: 9
slug: operational-readiness
status: draft
nyquist_compliant: false
wave_0_complete: false
created: 2026-03-28
---

# Phase 9 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | Manual verification (documentation phase) |
| **Config file** | none |
| **Quick run command** | Visual inspection of shopping list completeness |
| **Full suite command** | Cross-reference all grid maps against shopping list entries |
| **Estimated runtime** | ~60 seconds (manual review) |

---

## Sampling Rate

- **After every task commit:** Visual review of changed files
- **After every plan wave:** Cross-reference grid maps against shopping lists for completeness
- **Before `/gsd:verify-work`:** All four OPRD requirements verified by inspection
- **Max feedback latency:** 60 seconds

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|-----------|-------------------|-------------|--------|
| 09-01-01 | 01 | 1 | OPRD-01 | manual-only | Compare grid map plant lists against shopping list rows | N/A -- doc review | ⬜ pending |
| 09-01-02 | 01 | 1 | OPRD-02 | manual-only | Verify timeline section covers all three shopping lists | N/A -- doc review | ⬜ pending |
| 09-01-03 | 01 | 1 | OPRD-03 | manual-only | Cross-reference setup-guide + planting-day-script + slug-defense against tool list | N/A -- doc review | ⬜ pending |
| 09-01-04 | 01 | 1 | OPRD-04 | manual-only | Check PROJECT.md Constraints section for ~10,000+ DKK figure with rationale | N/A -- doc review | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements. This is a documentation phase with no test infrastructure needed.

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Spring shopping list has all Phase 2 plants | OPRD-01 | Documentation output — no code to test | Compare planting-grid-bed-[a-e].md plant lists against spring shopping list rows |
| Purchase priority ordering exists | OPRD-02 | Timeline is editorial content | Verify priority/timeline section covers all three shopping lists with lead times |
| Tool inventory is complete | OPRD-03 | Tool list is editorial content | Cross-reference setup-guide.md + planting-day-script.md + slug-defense.md against tool inventory |
| PROJECT.md budget updated | OPRD-04 | Single value update | Check PROJECT.md Constraints section for ~10,000 DKK figure with documented rationale |

---

## Validation Sign-Off

- [ ] All tasks have `<automated>` verify or Wave 0 dependencies
- [ ] Sampling continuity: no 3 consecutive tasks without automated verify
- [ ] Wave 0 covers all MISSING references
- [ ] No watch-mode flags
- [ ] Feedback latency < 60s
- [ ] `nyquist_compliant: true` set in frontmatter

**Approval:** pending
