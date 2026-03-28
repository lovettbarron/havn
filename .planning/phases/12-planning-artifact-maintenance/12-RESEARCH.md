# Phase 12: Planning Artifact Maintenance - Research

**Researched:** 2026-03-28
**Domain:** Planning file consistency and traceability hygiene
**Confidence:** HIGH

## Summary

Phase 12 is a pure bookkeeping phase -- no new features, no new documents, just correcting stale statuses, unchecked checkboxes, and missing metadata across the planning artifacts and schedule data files. The work is entirely mechanical: read the current state of each file, compare to actual project completion status, and update. The risk is low but the constraint surface is real -- the weekly schedule JSON schema enforces `additionalProperties: false`, so adding a `neighbor_override` flag to vacation week tasks (PMNT-04) requires a schema update first.

Five files are the primary targets: ROADMAP.md, PROJECT.md, REQUIREMENTS.md, four vacation-week schedule JSONs (w30-w33), and the w40 schedule JSON. All changes are corrections to existing content, not new content creation.

**Primary recommendation:** Group work into two plans -- (1) markdown artifact fixes (ROADMAP, PROJECT, REQUIREMENTS) and (2) JSON schedule fixes (vacation weeks + W40 garlic verification). The JSON work requires a schema migration.

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| PMNT-01 | All 15 v1.0 plan checkboxes in ROADMAP.md updated to checked | Audit below identifies exactly which checkboxes are stale (10 unchecked plan lines + 3 unchecked phase lines) |
| PMNT-02 | PROJECT.md Key Decisions outcomes updated from Pending to actual results | One row identified: "Bed remapping" still shows "Revisit (v1.1 Phase 7)" but Phase 7 is complete |
| PMNT-03 | REQUIREMENTS.md DOCS-04 and COOK-02 traceability statuses corrected | Both deliverables exist (neighbor-vacation-guide.md, garlic-autumn-plan.md); traceability table says "Pending" |
| PMNT-04 | Vacation week schedule files flag neighbor override for child-assigned tasks | Schema blocks new fields (additionalProperties: false); schema update required first |
| PMNT-05 | W40 schedule includes garlic planting hero task per garlic-autumn-plan.md | W40 already has garlic as hero_task and task W40-02; verify alignment with garlic-autumn-plan.md details |
</phase_requirements>

## Detailed Audit of Current State

### ROADMAP.md Stale Checkboxes (PMNT-01)

**v1.0 section (inside `<details>` block):**

| Line | Current | Should Be | Notes |
|------|---------|-----------|-------|
| Phase 2 header | `[ ]` | `[x]` | Phase marked Complete in progress table |
| Phase 3 header | `[ ]` | `[x]` | Phase marked Complete in progress table |
| Phase 6 header | `[ ]` | `[x]` | Phase marked Complete in progress table |
| 06-01-PLAN.md | `[ ]` | `[x]` | Phase 6 completed 2026-03-28 |
| 06-02-PLAN.md | `[ ]` | `[x]` | Phase 6 completed 2026-03-28 |

**v1.1 section:**

| Line | Current | Should Be | Notes |
|------|---------|-----------|-------|
| 08-01-PLAN.md | `[ ]` | `[x]` | Phase 8 completed 2026-03-28 |
| 08-02-PLAN.md | `[ ]` | `[x]` | Phase 8 completed 2026-03-28 |
| 09-01-PLAN.md | `[ ]` | `[x]` | Phase 9 completed (SUMMARY exists) |
| 10-01-PLAN.md | `[ ]` | `[x]` | Phase 10 completed 2026-03-28 |
| 11-01-PLAN.md | `[ ]` | `[x]` | Phase 11 completed 2026-03-28 |
| 11-02-PLAN.md | `[ ]` | `[x]` | Phase 11 completed 2026-03-28 |

**Progress table row fixes:**

| Phase | Current Status | Should Be |
|-------|---------------|-----------|
| Phase 9 | "Not started" / "0/1" | "Complete" / "1/1" |
| Phase 9 | Missing milestone column "v1.1" | Add "v1.1" |
| Phase 7 row | Malformed (missing milestone) | Fix column alignment |
| Phase 8 row | Malformed (missing milestone) | Fix column alignment |

Total: ~15 checkbox/status corrections in ROADMAP.md.

### PROJECT.md Key Decisions (PMNT-02)

Only one row needs updating:

| Decision | Current Outcome | Should Be |
|----------|----------------|-----------|
| Bed remapping (1-5 -> A-E) | "Revisit (v1.1 Phase 7)" | "Resolved -- Phase 7 applied canonical A-E naming across all docs and data" (or similar) |

The PROJECT.md "Active" checklist items under v1.1 should also be reviewed -- several are complete but still shown as `[ ]`.

### REQUIREMENTS.md Traceability (PMNT-03)

Two rows in v1.0 traceability table:

| Requirement | Current Status | Should Be | Evidence |
|-------------|---------------|-----------|----------|
| DOCS-04 | Pending | Complete | `docs/neighbor-vacation-guide.md` exists |
| COOK-02 | Pending | Planned (docs ready) | `docs/garlic-autumn-plan.md` exists; actual planting is Oct 2026 |

The DOCS-04 checkbox at the top of REQUIREMENTS.md (line 89) should also change from `[ ]` to `[x]`. COOK-02 (line 54) should remain `[ ]` since garlic is not yet planted -- the traceability note should be updated to clarify "Documentation complete; physical planting scheduled Oct 2026."

### Vacation Week Schedules (PMNT-04)

**Files:** w30.json, w31.json, w32.json, w33.json

**Current state:** Tasks with `"who": "child"` have no indication that the family may be on vacation and a neighbor would handle these tasks.

**Schema constraint:** `week.schema.json` has `"additionalProperties": false` on both the top-level object and the task object. Adding any new field (e.g., `vacation_note`, `neighbor_override`) will cause schema validation to fail unless the schema is updated first.

**Approach options:**

1. **Update schema + add field (recommended):** Add optional `vacation_note` string field to the top-level week schema and/or optional `neighbor_override` boolean to task schema. Then add the field to w30-w33.
2. **Use existing fields creatively:** Modify task `action` or `prompt` text to mention neighbor override (W31 already does this for watering -- "neighbor handles if on vacation"). No schema change needed but less structured.
3. **Top-level vacation flag:** Add optional `vacation_period` boolean/object at week level in schema, then flag w30-w33. Simpler than per-task override.

**Recommended:** Option 3 -- add an optional top-level `vacation_note` string to the week schema. Then add it to w30-w33 with text like "Family may be on vacation W30-W33. Child-assigned tasks should be handled by neighbor per neighbor-vacation-guide.md." This is minimal schema change and clearly flags the period.

**Already partially done:** W31 and W32 watering tasks already mention "neighbor handles if on vacation" in their action text.

### W40 Garlic Hero Task (PMNT-05)

**Current state:** W40 already has:
- `hero_task`: "Pick the very last raspberries and plant garlic for next year"
- Task W40-02: Garlic planting, `"who": "together"`, 15 minutes, `"priority": "must_do"`

**garlic-autumn-plan.md says:** 20-30 minute activity, Bed A middle or north zone, hardneck variety, 10-15cm deep, 15cm spacing, mulch with straw.

**Gap:** W40-02 says 15 minutes but the garlic plan says 20-30 minutes. The hero_task mentions garlic but as secondary to raspberries. Consider:
- Updating W40-02 minutes to 20-30
- Making garlic the primary hero task (it is the more significant seasonal event)
- Adding mulching as a follow-up task if not present

This is a minor alignment issue, not a major gap.

## Architecture Patterns

### File Modification Pattern

All changes follow the same pattern:
1. Read current file state
2. Identify specific lines/fields to change
3. Apply targeted edits (not full rewrites)
4. Verify the change against source of truth

### JSON Schema Migration Pattern

For PMNT-04, the schema update must happen before the data files are modified:
1. Update `week.schema.json` to add optional field
2. Update w30-w33 with the new field
3. Validate all 30 weekly schedule files still pass schema (unchanged files should pass since field is optional)

```json
// Addition to week.schema.json top-level properties:
"vacation_note": {
  "type": "string",
  "description": "Note about family vacation overlap -- neighbor handles child tasks per neighbor-vacation-guide.md"
}
```

No change to `"required"` array -- field is optional.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| JSON validation | Manual eyeballing | `ajv` or `node --eval` with schema | Schema has additionalProperties: false -- silent corruption risk |

## Common Pitfalls

### Pitfall 1: Missing the schema constraint
**What goes wrong:** Adding fields to JSON files without updating the schema, causing validation failures.
**How to avoid:** Always update week.schema.json BEFORE modifying data files. Test with schema validation after.

### Pitfall 2: Incomplete checkbox audit
**What goes wrong:** Fixing some checkboxes but missing others, especially in collapsed `<details>` blocks.
**How to avoid:** Systematic line-by-line comparison against the progress table and file system evidence (SUMMARY.md files).

### Pitfall 3: COOK-02 status confusion
**What goes wrong:** Marking COOK-02 as "Complete" when garlic is not yet planted.
**How to avoid:** COOK-02 requirement says "planted October 2026" -- documentation is ready but physical action is future. Update traceability note, not checkbox.

### Pitfall 4: ROADMAP progress table column misalignment
**What goes wrong:** The v1.1 rows in the progress table have inconsistent column structure (some missing Milestone column).
**How to avoid:** Fix all v1.1 rows to match the same column format as v1.0 rows.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | JSON Schema validation (ajv or manual) |
| Config file | data/schemas/week.schema.json |
| Quick run command | `node -e "const s=require('./data/schemas/week.schema.json'); console.log('schema OK')"` |
| Full suite command | Manual: verify all 30 weekly JSONs against schema |

### Phase Requirements -> Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| PMNT-01 | ROADMAP checkboxes match completion | manual | `grep -c '\[ \]' .planning/ROADMAP.md` (should show only Phase 12 items) | N/A |
| PMNT-02 | PROJECT.md decisions updated | manual | `grep 'Revisit' .planning/PROJECT.md` (should return 0) | N/A |
| PMNT-03 | REQUIREMENTS.md traceability correct | manual | `grep 'Pending' .planning/REQUIREMENTS.md` (should show only PMNT items) | N/A |
| PMNT-04 | Vacation weeks flagged | manual | Check w30-w33 for vacation_note field | N/A |
| PMNT-05 | W40 garlic hero task present | manual | Check w40.json hero_task and task alignment | N/A |

### Sampling Rate
- **Per task commit:** grep for stale markers (`Pending`, `[ ]`, `Revisit`)
- **Per wave merge:** Full audit of all 5 target files
- **Phase gate:** No `Pending` in traceability except PMNT items, no unchecked boxes for completed plans

### Wave 0 Gaps
None -- no test infrastructure needed. All validation is grep-based or manual inspection.

## Sources

### Primary (HIGH confidence)
- Direct file reads: ROADMAP.md, PROJECT.md, REQUIREMENTS.md, w30-w33.json, w40.json, week.schema.json
- File system evidence: SUMMARY.md files in completed phase directories

### Secondary (MEDIUM confidence)
- garlic-autumn-plan.md for PMNT-05 alignment details

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH -- no external libraries, just file edits
- Architecture: HIGH -- direct file manipulation, well-understood schema
- Pitfalls: HIGH -- constraints identified from actual schema reads

**Research date:** 2026-03-28
**Valid until:** No expiration -- project-internal artifacts only
