# Phase 7: Data Consistency and Identity Fix - Research

**Researched:** 2026-03-28
**Domain:** Documentation consistency, JSON data integrity, cross-reference audit
**Confidence:** HIGH

## Summary

Phase 7 addresses a set of data integrity issues that accumulated as the project evolved through 6 phases. The core problem is that bed identities were remapped between Phase 1 (numeric Bed 1-5) and Phase 2 (canonical Bed A-E), but Phase 1 documents were never updated to reflect the new naming. This creates operationally dangerous confusion: a father reading the setup guide on build day will install reservoirs in the wrong physical beds.

Beyond the naming issue, there are specific data inconsistencies in bed JSON files (wrong features, phantom crop entries), HA alert messages referencing crops that are not in the stated beds, a missing dill.json crop file, an incomplete radish bed assignment, and weekly schedule sowing tasks that reference succession slots stopped in Phase 3.

**Primary recommendation:** Treat this as a systematic find-and-replace audit across three file categories: (1) Phase 1 markdown docs, (2) JSON data files, (3) weekly schedule files. Each category has a well-defined set of changes documented below. No new architecture or tooling is needed -- this is pure editorial/data correction work.

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| DFIX-01 | Phase 1 docs use canonical Bed A-E naming with mapping table | Bed identity mapping fully documented below with exact file locations and line references |
| DFIX-02 | CLAUDE.md bed assignment table matches Phase 2+ grids | Exact current vs correct assignments documented; CLAUDE.md lines 19-25 need updating |
| DFIX-03 | Bed JSON feature arrays and HA alerts reference correct crops | All 5 bed JSON files audited; bed-b.json missing reservoir feature, bed-e.json has phantom Tumbling Tom crop, HA alert messages itemized |
| DFIX-04 | HA alert rule messages reference correct crops per bed | Three Bed E alert rules identified with incorrect crop references |
| DFIX-05 | Vacation countdown script references correct reservoir beds | Line 143 of vacation-countdown-script.md says "Beds A and B" but should reference Bed B and Bed C (or just Bed C pending reservoir decision) |
| DFIX-06 | Missing dill.json crop file created | Schema structure documented with basil.json as template; dill goes in bed-c and bed-e |
| DFIX-07 | Radish crop JSON beds array includes bed-e or documents exclusion | Current array is ["bed-a", "bed-c", "bed-d"]; Bed E had radish in Phase 2 but stopped in Phase 3 -- document exclusion |
| DFIX-08 | Weekly schedule sowing tasks audited against Phase 3 grids | 3 problematic schedule entries identified: W19 lettuce in Bed E, W25 lettuce in Bed E, W30 lettuce in Bed E |
</phase_requirements>

## Bed Identity Mapping (Source of Truth)

This is the canonical mapping between Phase 1 numeric names and Phase 2+ letter names:

| Phase 1 Name | Position | Phase 2+ Name | Phase 2+ Purpose | Phase 1 Purpose (STALE) |
|-------------|----------|---------------|------------------|------------------------|
| Bed 1 | Backyard, west | **Bed B** | Raspberry + chives | Tomato (WRONG) |
| Bed 2 | Backyard, center | **Bed C** | Warm crops (cucumber, tomato, pepper, basil, dill) | Cucumber (PARTIALLY RIGHT) |
| Bed 3 | Backyard, east | **Bed A** | Strawberry + sensory + flowers ("His Bed") | Berry (PARTIALLY RIGHT) |
| Bed 4 | Terrace, south | **Bed D** | Herbs + lettuce + spring onion | Herbs + sensory (CLOSE) |
| Bed 5 | Terrace, north | **Bed E** | Broccoli + bush beans + dill + flowers | Lettuce + quick wins (STALE) |

### Reservoir Assignment (Current State)

| Bed | Has Reservoir? | Evidence |
|-----|---------------|----------|
| Bed A (east, His Bed) | NO | bed-a.json features: [] |
| Bed B (west, Raspberry) | Physical bed has reservoir hardware (was Bed 1/Tomato in Phase 1) but raspberries do not need it | bed-b.json features: [] |
| Bed C (center, Warm Crops) | YES | bed-c.json features: ["a-frame-trellis", "self-watering-reservoir"] |
| Bed D | NO | Terrace bed, no reservoir |
| Bed E | NO | Terrace bed, no reservoir |

**Decision needed from user:** Does Bed B keep its physically-installed reservoir or is it capped/removed? STATE.md flags this as a blocker. The planner should note this as requiring human input.

## Files Requiring Changes

### Category 1: Phase 1 Markdown Docs (DFIX-01, DFIX-02, DFIX-05)

**`docs/bed-layout.md`:**
- Lines 58-85: ASCII diagram uses "Bed 1", "Bed 2", "Bed 3" -- add "(Bed B)", "(Bed C)", "(Bed A)" suffixes
- Lines 120-140: Terrace diagram uses "Bed 4", "Bed 5" -- add "(Bed D)", "(Bed E)" suffixes
- Lines 186-192: Bed Assignment Table uses numeric names with STALE crop assignments. Replace entire table with canonical A-E naming and correct crop assignments. Add a mapping note explaining the rename.
- Lines 196-202: Assignment Rationale section references "Bed 1 (Tomato)", "Bed 2 (Cucumber)", "Bed 3 (Berry)" -- update to match actual assignments
- Lines 219-223: Shopping list cross-reference uses "Beds 1, 2, 3" and "Beds 4, 5" -- update with letter suffixes and correct reservoir bed references

**`docs/setup-guide.md`:**
- Line 38: "Skip this for terrace beds (Beds 4-5)" -- add "(Bed D, Bed E)"
- Line 42: "Assemble Backyard Beds (Beds 1-3)" -- add canonical names
- Line 48: "Place Bed 1 (tomato) in the west position, Bed 2 (cucumber) in the center, and Bed 3 (berry) in the east position" -- update crop names to match Phase 2+ assignments
- Lines 52-61: "Install Reservoirs in Beds 1 and 2" -- clarify which canonical beds (Bed B and Bed C, pending reservoir decision)
- Lines 75-83: "Assemble Terrace Beds (Beds 4-5)" -- add canonical names
- Lines 99-111: "Fill Beds 1 and 2 (Reservoir Beds)" and "Fill Bed 3" -- add canonical names
- Line 141-147: "Build and Install A-Frame Trellis on Bed 2" -- add "(Bed C)"
- Lines 161-163: "Fill both reservoirs (Beds 1 and 2)" -- correct to canonical names
- Lines 170-179: Completion Checklist -- update all numeric references
- Lines 193-194: Document Index references "Beds 1 and 2" -- update

**`docs/reservoir-build.md`:**
- Line 12: "Install reservoirs in Bed 1 (tomato) and Bed 2 (cucumber) only" -- update to canonical names with correct crops

**`CLAUDE.md`:**
- Lines 19-25: Raised Beds table shows STALE Phase 1 assignments. Must be updated to:
  - Bed A: Strawberry + sensory plants + flowers ("His Bed")
  - Bed B: Raspberry + chives
  - Bed C: Cucumber + tomato + pepper + basil + dill (warm crops)
  - Bed D: Herbs + lettuce + spring onion
  - Bed E: Broccoli + bush beans + dill + flowers
- Line 32: "Self-watering reservoirs in Beds A and B" -- correct to match actual reservoir beds (Bed C confirmed; Bed B pending decision)
- Line 33: "A-frame trellis on Bed B for cucumbers" -- should be "on Bed C"

**`docs/vacation-countdown-script.md`:**
- Line 143: "Fill ALL reservoirs completely via fill tubes (Beds A and B, plus any others with reservoirs)" -- correct to actual reservoir beds

### Category 2: JSON Data Files (DFIX-03, DFIX-04, DFIX-06, DFIX-07)

**`data/beds/bed-b.json`:**
- Line 9: features is `[]`. If Bed B keeps its physically-installed reservoir, add `"self-watering-reservoir"`. If removed/capped, leave empty and add a comment in a description field.

**`data/beds/bed-e.json`:**
- Lines 52-58: Contains `cherry-tomato-tumbling-tom` crop entry. The planting grid for Bed E does NOT include Tumbling Tom -- it is described in docs as a "pot overflow" backup, not a bed plant. This entry should be REMOVED from bed-e.json.
- Note: If Tumbling Tom ends up in a pot rather than a bed, it has no bed JSON entry (which is correct -- pots are not beds).

**`data/ha/alert-rules.json`:**
- Rule `havn_bed_e_moisture_below_min` (line 168-171): Message says "broccoli and tomatoes need water" -- should say "broccoli and beans need water" (Tumbling Tom is not in this bed per the grid; beans are the other water-sensitive crop)
- Rule `havn_bed_e_temperature_below_frost` (line 194-196): Message says "beans and tomatoes are frost-sensitive" -- should say "beans and broccoli are frost-sensitive" (or just "beans" since broccoli is frost-tolerant)
- Danish translations must be updated in parallel

**`data/crops/radish.json`:**
- Line 126: beds array is `["bed-a", "bed-c", "bed-d"]`. Bed E had a radish succession slot in Phase 2 (S1), but it was explicitly stopped in Phase 3 (planting-grid-bed-e.md line 28: "Stop sowing. Space needed for warm crops."). The correct fix is to add a note documenting the Phase 3 exclusion, NOT to add bed-e to the array. The current array is correct for Phase 3 state.

**New file: `data/crops/dill.json`:**
- Must follow crop.schema.json (required fields: id, name, type, difficulty, growth_stages, water_needs, temperature, harvest, companion_plants, engagement, beds, sowing, alerts)
- Template: use basil.json structure as reference (herb type, similar complexity)
- Key data points for dill:
  - id: "dill"
  - name.common: "Dill", name.botanical: "Anethum graveolens", name.da: "Dild", name.shortcode: "DIL"
  - type: "herb"
  - difficulty.tier: "cant_fail" (self-sows readily, grows fast)
  - beds: ["bed-c", "bed-e"] (per planting grids)
  - sowing.method: "seed", outdoor_sow: 18 (W18), succession: false
  - Key companion role: attracts hoverflies that eat broccoli aphids (documented in bed-e grid)

### Category 3: Weekly Schedule Files (DFIX-08)

**Succession slots stopped in Phase 3 that still have schedule entries:**

1. **Bed E radish S1** -- stopped at W20 per planting-grid-bed-e.md. No radish sowing tasks found in schedules for Bed E after W20 (good -- this is already correct).

2. **Bed E lettuce succession** -- this is the problematic one. Bed E's grid shows no lettuce in Phase 3 state. Yet schedules have:
   - W19: "Sow second succession lettuce in Bed E" -- this is Phase 2 timing, before Phase 3 transition. May be valid if lettuce was briefly in Bed E during Phase 2.
   - W25: "Sow fourth succession lettuce in Bed E" -- INVALID. By W25, Bed E is fully transitioned to Phase 3 crops (beans W20, broccoli W21). No space for lettuce.
   - W30: "Sow sixth (final) succession lettuce in Bed E" -- INVALID. Same reason.

3. **Bed D lettuce** -- Bed D grid says "lettuce will bolt in summer heat (June+)" and the zone becomes available for leeks. Schedule entries for Bed D lettuce at W16, W22, W28 should be checked: W28 (early July) lettuce sowing in Bed D is questionable since lettuce bolts in summer. However, this is a Bed D issue and may be intentional (late-season varieties). Flag for audit but lower priority.

**Specific schedule files to edit:**
- `data/schedules/w25.json`: Remove or flag "Sow fourth succession lettuce in Bed E" (line 81)
- `data/schedules/w30.json`: Remove or flag "Sow sixth (final) succession lettuce in Bed E" (line 85)
- `data/schedules/w19.json`: Review "Sow second succession lettuce in Bed E" (line 69) -- may be valid for Phase 2 window but should be flagged as last possible Bed E lettuce sowing

## Architecture Patterns

### Pattern: Correction Audit with Source-of-Truth Chain

**What:** Each fix traces back to a single source of truth (the planting grid files), and all downstream files (JSON, schedules, markdown docs) are updated to match.

**Source of truth hierarchy:**
1. `docs/planting-grid-bed-[a-e].md` -- canonical for what is in each bed
2. `data/beds/bed-[a-e].json` -- must match grid files
3. `data/crops/*.json` -- beds arrays must match grid assignments
4. `data/ha/alert-rules.json` -- crop references must match bed JSON
5. `data/schedules/w*.json` -- sowing tasks must respect Phase 3 transitions
6. `docs/*.md` and `CLAUDE.md` -- narrative must match data

**When to use:** Always resolve discrepancies by checking the grid files first, then cascading corrections downward.

### Anti-Patterns to Avoid

- **Partial updates:** Do not fix bed-layout.md naming without also fixing setup-guide.md, reservoir-build.md, and the shopping list cross-references. All Phase 1 docs must be updated together.
- **Removing the mapping:** The Bed 1 = Bed B mapping should be PRESERVED as a reference note, not deleted. Build day may reference both naming systems.
- **Over-correcting alert messages:** The HA alerts are templates. Fix crop names but do not restructure the alert rule format or add new rules.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Schema validation for dill.json | Manual field checking | `data/schemas/crop.schema.json` + copy basil.json structure | Schema defines all required fields; copying a working example prevents omissions |
| Finding all Bed 1-5 references | Manual grep | Systematic file-by-file audit using the list above | The files and line numbers are already identified in this research |

## Common Pitfalls

### Pitfall 1: Fixing Names Without Fixing Crop Assignments
**What goes wrong:** Renaming "Bed 1" to "Bed B" in bed-layout.md but leaving the crop assignment as "Tomato + basil + nasturtium" (the Phase 1 assignment). Bed B is actually the Raspberry bed.
**How to avoid:** Always update BOTH the name AND the crop description simultaneously. Use the mapping table in this research as the reference.

### Pitfall 2: CLAUDE.md Infrastructure References
**What goes wrong:** Fixing the bed table but missing the infrastructure bullet points lower in CLAUDE.md that reference "Beds A and B" for reservoirs and "Bed B" for the trellis.
**How to avoid:** Search CLAUDE.md for ALL bed references, not just the table. Lines 32-33 have infrastructure references that are also wrong.

### Pitfall 3: Danish Translations in Alert Rules
**What goes wrong:** Fixing the English alert message but leaving the Danish translation unchanged.
**How to avoid:** Every alert rule has both `en` and `da` message fields. Both must be updated together.

### Pitfall 4: Tumbling Tom Orphan
**What goes wrong:** Removing Tumbling Tom from bed-e.json but not checking if the crop file (cherry-tomato-tumbling-tom.json) has a beds array that still references bed-e.
**How to avoid:** After removing Tumbling Tom from bed-e.json, check cherry-tomato-tumbling-tom.json beds array and update it. If Tumbling Tom is pot-only, its beds array should be empty or document "pot" placement.

### Pitfall 5: Bed E Lettuce Schedule Entries
**What goes wrong:** Removing ALL lettuce references from Bed E schedules, including the W19 entry which may be valid during the Phase 2 window before Phase 3 transition.
**How to avoid:** Only remove entries from W21 onward (after Phase 3 transition). W19 is before Phase 3 and may be valid.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual audit (no automated test framework for markdown/JSON consistency) |
| Config file | none |
| Quick run command | `python3 -m json.tool data/crops/dill.json > /dev/null && echo "valid JSON"` |
| Full suite command | `for f in data/crops/*.json data/beds/*.json data/ha/*.json; do python3 -m json.tool "$f" > /dev/null || echo "INVALID: $f"; done` |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| DFIX-01 | Phase 1 docs use Bed A-E naming | manual | `grep -c "Bed [1-5]" docs/bed-layout.md docs/setup-guide.md docs/reservoir-build.md` (should be 0 standalone refs) | N/A |
| DFIX-02 | CLAUDE.md table matches grids | manual | `grep -A5 "Raised Beds" CLAUDE.md` visual check | N/A |
| DFIX-03 | Bed JSON features correct | manual | `python3 -c "import json; [print(f['id'], f['physical']['features']) for f in [json.load(open(f'data/beds/bed-{x}.json')) for x in 'abcde']]"` | N/A |
| DFIX-04 | HA alerts reference correct crops | manual | `grep -i "tomato\|tomat" data/ha/alert-rules.json` (should only appear in bed-c rules) | N/A |
| DFIX-05 | Vacation script correct reservoirs | manual | `grep -n "reservoir\|Beds A and B" docs/vacation-countdown-script.md` | N/A |
| DFIX-06 | dill.json exists and is valid | unit | `python3 -m json.tool data/crops/dill.json > /dev/null` | No -- Wave 0 |
| DFIX-07 | Radish beds documented | manual | `python3 -c "import json; print(json.load(open('data/crops/radish.json'))['beds'])"` | N/A |
| DFIX-08 | No stale succession tasks | manual | `grep -n "lettuce.*Bed E" data/schedules/w2[5-9].json data/schedules/w3*.json` (should be 0) | N/A |

### Sampling Rate
- **Per task commit:** JSON validation command on changed files
- **Per wave merge:** Full JSON validation + grep checks for stale references
- **Phase gate:** All grep checks return expected results

### Wave 0 Gaps
- [ ] `data/crops/dill.json` -- covers DFIX-06 (must be created as part of implementation)
- No test framework needed -- this is an editorial/data correction phase

## Open Questions

1. **Reservoir in Bed B**
   - What we know: Bed B (physical position: west, original Bed 1) will have reservoir hardware installed because the setup guide builds it before Phase 2 remapping happens. After remapping, Bed B holds raspberries which do not need a reservoir.
   - What's unclear: Does the father cap/ignore the reservoir, or remove it? This affects CLAUDE.md, bed-b.json, vacation-countdown-script.md, and setup-guide.md.
   - Recommendation: Flag this as a human decision in the plan. Default to "Bed B reservoir exists but is not actively used" -- document it but do not list Bed B as a reservoir bed in operational docs. The planner should make this the simplest path.

2. **Tumbling Tom final placement**
   - What we know: Tumbling Tom is in bed-e.json but NOT in the Bed E planting grid. Docs describe it as "pot overflow if Bed C is too full."
   - What's unclear: Is Tumbling Tom in the garden at all, or was it dropped?
   - Recommendation: Remove from bed-e.json. The crop file can remain (it is valid reference data) but its beds array should reflect actual placement. If pot-only, beds should be empty with a note.

## Sources

### Primary (HIGH confidence)
- All findings verified by direct file reads of the actual project files
- Planting grid files (docs/planting-grid-bed-[a-e].md) used as source of truth
- Bed JSON files (data/beds/bed-[a-e].json) cross-referenced against grids
- Gap analysis (`.planning/quick/1-analyze-project-gaps/1-ANALYSIS.md`) provided finding numbers; all were independently verified

### Secondary (MEDIUM confidence)
- Weekly schedule succession task audit covers W16-W32 explicitly; later weeks not exhaustively checked but pattern is clear

## Metadata

**Confidence breakdown:**
- Bed identity mapping: HIGH -- verified against all 5 planting grid headers
- File change inventory: HIGH -- every file and line number verified by direct read
- Schedule succession audit: MEDIUM -- checked representative weeks, pattern is clear but not every week exhaustively verified
- Dill.json requirements: HIGH -- schema and template both verified

**Research date:** 2026-03-28
**Valid until:** No expiry -- this is an internal data audit, not dependent on external libraries
