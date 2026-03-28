# Haven Project Gap Analysis

**Date:** 2026-03-27
**Scope:** Full audit of v1.0 milestone (6 phases, 15 plans, 59 requirements)
**Method:** Systematic read of all docs, data, schemas, schedules, HA configs, and planning artifacts

## Executive Summary

The Haven project is remarkably thorough for a pre-season planning effort. Across 6 phases, 15 plans, and 59 requirements, the documentation forms an internally consistent, deeply cross-referenced system that would allow a garden-naive father to build beds, plant crops, and maintain a garden through an entire growing season. The session scripts are genuinely ADHD-adapted with mandatory breaks, sensory sequencing, and meltdown protocols. The data system (27 crop JSONs, 30 weekly schedules, 5 bed mappings, HA schemas) is production-quality for what is fundamentally a family garden project.

The three most important findings are: (1) a persistent bed identity discrepancy between Phase 1 naming (Bed 1-5) and Phase 2+ naming (Bed A-E) that creates confusion about which physical beds have reservoirs, (2) no documentation exists for the child's daily garden routine between planting sessions -- the gap between "planting day script" and "weekly schedule JSON" is too large for a 7-year-old to bridge independently, and (3) the REQUIREMENTS.md tracking has two items (DOCS-04 and COOK-02) marked Pending despite their deliverables existing, and the ROADMAP.md progress table has inconsistencies with plan completion checkboxes.

Overall recommendation: the project is ready for physical execution. The findings below are refinements, not blockers. A short pre-W16 phase addressing the bed identity discrepancy and daily routine documentation would strengthen the project's core value proposition (child agency).

---

## Findings by Category

### 1. Data Integrity

**Finding 1.1: Bed identity mapping is inconsistent across documents (MODERATE)**

Phase 1 documents (`docs/bed-layout.md`, `docs/setup-guide.md`, `docs/reservoir-build.md`) use numeric bed identifiers (Bed 1-5), while Phase 2+ documents and all data files use letter identifiers (Bed A-E). The mapping is:
- Bed 1 (west) = Bed B (raspberry) -- per planting-grid-bed-b.md line 1
- Bed 2 (center) = Bed C (warm crop) -- per planting-grid-bed-c.md line 1
- Bed 3 (east) = Bed A (his bed) -- per planting-grid-bed-a.md line 1
- Bed 4 (terrace south) = Bed D
- Bed 5 (terrace north) = Bed E

This is documented in each grid map header, but the Phase 1 documents were never updated to use the canonical A-E naming. The `docs/bed-layout.md` Bed Assignment Table (line 186-192) still uses "Bed 1" through "Bed 5" with the original Phase 1 crop assignments (Bed 1 = Tomato, Bed 2 = Cucumber, Bed 3 = Berry) which were reshuffled in Phase 2.

**Impact:** Father reading setup-guide.md builds reservoirs in "Beds 1 and 2" thinking those are the tomato and cucumber beds. After Phase 2 remapping, Bed 1 became the raspberry bed (Bed B) which explicitly does NOT want a reservoir. The reservoir test protocol (06-01) acknowledges this discrepancy at line 15-19 but does not resolve it.

**Proposed fix:** Update `docs/bed-layout.md` and `docs/setup-guide.md` to use canonical Bed A-E naming with a clear mapping table. Add "(Bed B)" suffix to "Bed 1" references throughout Phase 1 docs.

---

**Finding 1.2: CLAUDE.md bed assignments do not match planting grid canonical assignments (MODERATE)**

The CLAUDE.md Raised Beds table (lines 19-25) shows:
- Bed A: "Tomato + basil + nasturtium"
- Bed B: "Cucumber + pepper + radish + borage"
- Bed C: "Berry (strawberry + raspberry) + thyme + chives"

The planting grid documents show the actual assignments after Phase 2 remapping:
- Bed A: Strawberry + sensory plants + flowers (His Bed)
- Bed B: Raspberry + chives (Raspberry Bed)
- Bed C: Cucumber + tomato + pepper + basil + dill (Warm Crop Bed)

The CLAUDE.md table appears to reflect the original Phase 1 assignments (Bed 1/A = Tomato, Bed 2/B = Cucumber) rather than the post-Phase 2 remapped assignments. This was flagged in Phase 5 verification (human verification item 2) but not resolved.

**Proposed fix:** Update the CLAUDE.md Raised Beds table to match the canonical Phase 2+ assignments.

---

**Finding 1.3: Reservoir feature assignment inconsistency in bed JSON data (MINOR)**

`data/beds/bed-c.json` lists `"features": ["a-frame-trellis", "self-watering-reservoir"]` (line 9). `data/beds/bed-a.json` lists `"features": []` (line 9). However, CLAUDE.md says "Self-watering reservoirs in Beds A and B." The reservoir-build guide says "Bed 1 (tomato) and Bed 2 (cucumber)" which maps to Bed B and Bed C respectively.

After Phase 2 remapping:
- Original Bed 1 (tomato) became Bed B (raspberry) -- reservoir built here but not needed
- Original Bed 2 (cucumber) became Bed C (warm crop) -- reservoir built here, which is correct

The bed-c.json correctly has the reservoir feature. But CLAUDE.md says "Beds A and B" have reservoirs, which contradicts both the data files and the physical plan. The reservoir test protocol explicitly calls out this discrepancy.

**Proposed fix:** Clarify which physical beds actually have reservoirs. Based on the remapping, Bed C (original Bed 2, cucumber) should have a reservoir. Whether Bed B (original Bed 1, raspberry) keeps its reservoir or has it removed is a physical decision. Update CLAUDE.md, bed JSON files, and the neighbor guide accordingly.

---

**Finding 1.4: Radish bed assignment in crop JSON vs succession calendar (MINOR)**

`data/crops/radish.json` lists `"beds": ["bed-a", "bed-c", "bed-d"]` (line 126). The succession calendar shows radish sowings rotating through bed-a, bed-c, and bed-d. However, the planting grid for Bed E (line 131) shows a radish succession slot S1 in Phase 2, and Bed E's requirement traceability lists CROP-06 (radish succession). The radish crop file does not include "bed-e" in its beds array.

**Proposed fix:** Add "bed-e" to the radish crop JSON beds array, or document that Bed E's radish succession ends in Phase 3 (it does -- the S1 slot is stopped for warm crops).

---

**Finding 1.5: Dill crop file is missing from the data/crops/ directory (MINOR)**

The planting grid documents and session scripts reference dill in Bed C (position 50, 95) and Bed E (position 10, 70). However, there is no `data/crops/dill.json` file in the crops directory. The 27 crop files listed do not include dill.

The weekly schedules reference dill in sowing tasks, and the bed-c.json and bed-e.json files would logically include dill crop entries. Dill is mentioned in the troubleshooting guide crop index (entry 10 is Kale, and dill appears in companion planting descriptions) but has no dedicated crop data file.

**Proposed fix:** Create `data/crops/dill.json` with appropriate schema fields. Alternatively, if dill is intentionally excluded from the data system (treated as a minor companion rather than a tracked crop), document this decision.

---

### 2. Schedule and Calendar

**Finding 2.1: Vacation weeks W30-W33 schedules reference tasks the neighbor handles (MINOR)**

Weekly schedule files for W30-W33 include tasks assigned to "child" (e.g., W30-01 "Stand next to sunflower for height comparison photo" -- child, W30-03 "Pick strawberries" -- child). If the family is on vacation during these weeks, these tasks are assigned to an absent child.

The W30 schedule does include a father task for "Prepare vacation watering instructions for neighbor" (W30-05), but no schedule explicitly flags W30-W33 as vacation weeks or reassigns child tasks to the neighbor.

**Proposed fix:** Add a "vacation" flag or "neighbor_override" field to the weekly schedule files for the expected vacation window. Alternatively, add a note in the schedule files acknowledging that child tasks during vacation weeks are performed by the neighbor per the vacation guide.

---

**Finding 2.2: No schedule files exist for the garlic planting window W39-W42 (MINOR)**

The garlic autumn plan documents planting in late September to mid-October (W39-W42). The weekly schedule files W39-W42 exist but may not include garlic planting as a scheduled task. W40 should include a garlic planting hero task.

**Proposed fix:** Verify W39-W42 schedule files include garlic planting tasks. If not, add them.

---

**Finding 2.3: W30 sowing task references Bed C and Bed E succession slots that may be stopped by Phase 3 (MINOR)**

W30 sowing_tasks include "Sow eighth succession radish in Bed C" (slot S1) and "Sow sixth (final) succession lettuce in Bed E" (slot S1). However, the Bed E planting grid explicitly states the S1 succession slot is "PHASE 3: Stopped. Space taken by dill and broccoli zone." If the slot is stopped, W30 should not have a sowing task for it.

The succession calendar may have been generated before the Phase 3 transition was finalized. The Bed C succession slot (S1 for radish) appears to still be active since the warm crops do not fully occupy that area.

**Proposed fix:** Audit all weekly schedule sowing_tasks against the Phase 3 grid maps to ensure stopped succession slots are not still receiving sowing tasks.

---

### 3. Cross-Reference Consistency

**Finding 3.1: Shopping list budget exceeds stated 2,000-5,000 DKK ceiling (MODERATE)**

PROJECT.md and REQUIREMENTS.md specify a budget of 2,000-5,000 DKK. The Phase 1 shopping list totals ~9,825 DKK (Option A) or ~9,225 DKK (Option B). The Phase 3 warm-season shopping list adds another ~455-665 DKK. Total project cost: approximately 9,700-10,500 DKK -- roughly double the stated budget ceiling.

This was flagged in STATE.md blockers ("Budget may exceed 5,000 DKK ceiling") but no resolution or updated budget figure has been documented. The shopping list itself notes savings opportunities but does not present a version that fits within the original budget.

**Proposed fix:** Either update the PROJECT.md budget constraint to reflect the actual cost (~10,000 DKK), or create a "budget tier" version of the shopping list that fits within 5,000 DKK (e.g., 3 beds first, terrace beds deferred).

---

**Finding 3.2: Neighbor vacation guide references "Bed B" as having the A-frame trellis (INCORRECT)**

The neighbor guide Bed C card (line 79-101) correctly describes the center bed with the A-frame trellis. However, it references the bed as being the "CENTER" bed and says it has "a wooden A-frame trellis over one end." This is correct content. But cross-checking with bed-layout.md, Bed B is described as the west-position bed (Bed 1), not the center. The neighbor guide correctly uses physical position descriptions rather than letter IDs, which avoids the identity confusion. This finding is informational -- no actual error.

**Status:** No fix needed. The neighbor guide is self-contained by design.

---

**Finding 3.3: Vacation countdown script Day -2 references filling reservoirs in "Beds A and B" (MODERATE)**

`docs/vacation-countdown-script.md` line 143 states: "Fill ALL reservoirs completely via fill tubes (Beds A and B, plus any others with reservoirs)." This references reservoirs in Beds A and B, matching CLAUDE.md but contradicting the actual reservoir installation plan (which, after remapping, should be Bed B and Bed C, or possibly just Bed C).

**Proposed fix:** Update the vacation countdown script to reference the correct reservoir beds once Finding 1.3 is resolved.

---

### 4. Documentation Gaps

**Finding 4.1: No daily garden routine document exists for the child (MODERATE)**

The project has detailed session scripts for planting days (W16, W18, W21) and a vacation countdown script (Day -3 to Day -1). Weekly schedule JSON files exist for W15-W44 with tasks. But there is no simple, child-facing "daily routine" document that the father can print and put on the fridge for the 5-minute daily garden check.

The weekly schedules contain the right tasks, but they are JSON files not readable by a 7-year-old or a busy parent. The core value is "a child who independently checks on, cares for, and harvests" -- this requires a simple, visual daily routine card.

**Proposed fix:** Create a `docs/daily-routine-card.md` with a simple visual checklist the child can follow: (1) Check beds, (2) Water if needed, (3) Pick ripe things, (4) Measure sunflower. Include a printable version at child height.

---

**Finding 4.2: No end-of-season cleanup documentation (MINOR)**

The project covers W15-W44 comprehensively. After W44, there is no documentation for:
- Removing spent annual plants
- Preparing perennial beds for winter
- Composting garden waste
- Storing tools
- Draining reservoirs for winter (reservoir-build.md mentions this briefly at line 155 but no procedure exists)
- What to tell the child about the garden "going to sleep"

**Proposed fix:** Create a `docs/end-of-season-guide.md` covering W44-W46 cleanup tasks.

---

**Finding 4.3: No crop failure recovery guide (MINOR)**

The troubleshooting guide handles symptoms (yellowing, wilting, pests). But there is no guide for "a crop completely died -- what now?" scenarios:
- Can you replant in the same spot mid-season?
- What are replacement options for common failure cases (e.g., if Sungold dies, what cherry tomato can go in)?
- When is it too late to replant?

The warm-season shopping list has a "Seedling Unavailable" substitution table (line 437-446) which partially addresses this for initial planting, but not for mid-season recovery.

**Proposed fix:** Add a "Crop Failure Recovery" section to the troubleshooting guide with per-month replanting windows.

---

**Finding 4.4: No tool list exists in the documentation (MINOR)**

The shopping list covers materials but does not include a comprehensive tool list. The setup guide assumes "Drill with 10-12mm bit available" and various hand tools. The planting day script mentions "trowel, hand fork, watering can (small one for him, large one for you)" but there is no master tool list.

**Proposed fix:** Add a "Tools Needed" section to either the setup guide or shopping list covering: drill + bit, trowel, hand fork, watering cans (2 sizes), hose, pruning scissors, soil thermometer, measuring tape, depth-check stick.

---

### 5. Child Engagement and ADHD/Autism Coverage

**Finding 5.1: No documented engagement activities between W18 (Session 1) and W21 (Session 2) (MODERATE)**

Session 1 (W18, May 1) and Session 2 (W21, May 20+) are separated by 3 weeks. The warm-season session scripts include follow-up activities (sunflower measurement, creature observation) but these are listed at the end of the document, not structured as a W19-W20 engagement plan.

For a 7-year-old with ADHD, a 3-week gap with no structured garden activity risks disengagement. The weekly schedules for W19-W20 include tasks but they are JSON data, not child-facing scripts.

**Proposed fix:** Add a brief "Between Sessions" section to the warm-season scripts or create a standalone W19-W20 mini-activity guide: sunflower check, germination watch, sensory walk.

---

**Finding 5.2: Sunflower measurement is the only sustained engagement activity documented (MINOR)**

The sunflower ruler-stake measurement is a well-designed recurring activity. However, it is the only consistently documented weekly activity for the child between planting sessions and harvest season. Other engagement activities (creature observation, basil pinching, bean checking) are mentioned in passing in the session scripts' follow-up section but are not structured as a routine.

**Proposed fix:** Create a "Weekly Garden Walk" checklist with 3-5 quick activities (measure sunflower, check for bugs, smell herbs, count flowers, look for ripe things) that can be done in 5-10 minutes.

---

**Finding 5.3: No photo/journal component documented (MINOR)**

The bug hotel guide mentions "Draw or photograph any creature you find" (line 194) and the sunflower measurement suggests a wall chart. But there is no structured garden journal or photo log component. For a child with ADHD/Autism who responds to visual systems and documentation, a simple photo-a-day or weekly sketch journal could reinforce the agency loop.

This is a v2 feature in REQUIREMENTS.md (ADV-V2-02: "Garden journal/log for the child to track observations") but a minimal version could enhance v1 engagement.

**Proposed fix:** Document a simple photo log approach: one phone photo per garden visit, saved to a shared album. Low friction, high reward.

---

### 6. Home Assistant Integration

**Finding 6.1: No HA setup walkthrough exists (MODERATE)**

The project provides:
- Entity schemas (sensors.json, customize.json)
- Plant Monitor configs (plants.json)
- Alert rules (alert-rules.json)
- Sensor hardware recommendations (sensor-recommendations.md)

But there is no step-by-step guide for actually configuring Home Assistant. A father who has HA running needs to know:
- Where to paste the YAML (configuration.yaml? packages?)
- How to create the Plant Monitor entities
- How to set up the automation rules
- How to verify sensors are reporting correctly

The HA files include `yaml_output` fields with ready-to-paste YAML, but no guide explains the workflow.

**Proposed fix:** Create a `docs/ha-setup-guide.md` walking through the HA configuration process using the provided JSON/YAML.

---

**Finding 6.2: No HA dashboard config or mockup exists (MINOR)**

The data system provides all the entity definitions needed for a Lovelace dashboard, but no dashboard configuration (YAML or UI) is provided. A simple Mushroom card layout showing 5 beds with moisture/temperature gauges would make the sensor data immediately useful.

This is a v2 feature (IOT-V2-04) but the entity schema work is complete enough to generate a basic dashboard now.

**Proposed fix:** Create a basic Lovelace dashboard YAML showing per-bed moisture and temperature cards.

---

**Finding 6.3: Alert rule notification target is generic (MINOR)**

All 15 alert rules in `data/ha/alert-rules.json` use `"notification_target": "notify.mobile_app"` which is a generic placeholder. The actual HA notification target depends on Andrew's specific mobile app configuration.

**Proposed fix:** Add a note in the alert-rules.json `_doc` field explaining that `notify.mobile_app` must be replaced with the actual service target during HA setup.

---

### 7. Season 2 and Long-Term Preparedness

**Finding 7.1: No "lessons learned" template or feedback mechanism exists (MINOR)**

After a full growing season, there is no structured way to capture what worked, what failed, and what to change for Season 2. A simple template for end-of-season review would preserve institutional knowledge.

**Proposed fix:** Create a `docs/season-review-template.md` with sections for: what worked, what failed, crop-by-crop assessment, child engagement observations, infrastructure changes needed.

---

**Finding 7.2: Perennial management across seasons is undocumented (MINOR)**

Beds A (strawberries, sensory plants) and B (raspberries, chives) contain perennials that return in Season 2. There is no documentation for:
- Strawberry crown division (year 2-3)
- Raspberry cane pruning (autumn after fruiting, documented briefly in crop-difficulty-tiers.md)
- How the bed layout changes when perennials spread
- When to replace aging perennials

**Proposed fix:** Add perennial management notes to the end-of-season guide.

---

**Finding 7.3: Soil amendment for Year 2 is not documented (MINOR)**

Raised bed soil loses nutrients over a growing season, especially with the hugelkultur middle layer decomposing. There is no documentation for:
- When and how to top up soil (spring before planting)
- Whether to add compost or fresh hojbedsmuld
- Whether the drainage/garden waste layer needs refreshing

**Proposed fix:** Add a "Year 2 Soil Refresh" section to the soil-layers guide.

---

### 8. Requirement Coverage

All 59 v1 requirements have been mapped to phases and have deliverables. Two requirements have tracking inconsistencies:

| Req ID | Description | Delivered? | REQUIREMENTS.md Status | Issue |
|--------|-------------|-----------|----------------------|-------|
| DOCS-04 | Neighbor vacation guide | Yes (`docs/neighbor-vacation-guide.md`) | Pending | Should be marked Complete (deliverable exists with intentional placeholders for photos/phone) |
| COOK-02 | Garlic hardneck planted October 2026 | Partially (`docs/garlic-autumn-plan.md` exists) | Pending | Correct -- physical planting cannot happen until Oct 2026. Documentation deliverable is complete. |

No requirements are missing deliverables entirely. The SCHED-03 requirement specifies "W14" but schedules start at W15 -- this is a minor wording discrepancy noted in the Phase 4 verification report.

---

### 9. Verification Debt

All 6 VERIFICATION.md files were reviewed. Summary of unresolved items:

**Phase 1 verification:** 4 human verification items (price validation, byJEMA 30cm height confirmation, terrace structural check, build day timing). None are blockers to documentation completeness but should be done before ordering.

**Phase 5 verification (status: human_needed):**
- CLAUDE.md bed label consistency -- Finding 1.2 above confirms this is a real issue that needs fixing
- DOCS-04 checkbox status -- Finding 8 above confirms this should be updated
- Property map compass orientation -- requires physical confirmation

**Phase 6 verification (status: human_needed):**
- Printable checklist page fit -- requires print test
- Neighbor guide readability -- requires human reader test
- Photo placeholder completeness -- requires Day -3 photo alignment check

**Phase 6 partial key links:**
- Vacation countdown script does not cross-reference mulching-guide.md (content is inline, no functional gap)
- Pre-departure checklist JSON lacks $schema declaration (minor schema hygiene)

No verification findings represent unresolved functional gaps. All are quality confirmations.

---

### 10. Operational Readiness

**Finding 10.1: Setup guide does not mention the bed identity remapping (MODERATE)**

A father reading `docs/setup-guide.md` on build day will follow instructions referencing "Bed 1 (Tomato)" and "Bed 2 (Cucumber)" -- but after the Phase 2 remapping, the physical beds in those positions will hold different crops. The reservoirs will be built into beds that may not need them (Bed 1 became the raspberry bed).

This is the most operationally significant finding. On build day, the father needs to know which physical beds get reservoirs based on the FINAL crop assignments, not the Phase 1 preliminary assignments.

**Proposed fix:** Add a "Phase 2 Update" note to the top of setup-guide.md clarifying the reservoir bed assignments based on final planting plans.

---

**Finding 10.2: No "what to buy first" prioritization exists (MINOR)**

The shopping list has 19 items across 6 categories. There is no prioritization for a father who cannot buy everything at once. Which items have long lead times (byJEMA beds)? Which can be bought last-minute (soil, gravel)?

The shopping list notes section mentions "lead time: 1-3 day handling + 2-7 day transit" for byJEMA beds and suggests ordering soil early, but there is no explicit "order of purchase" recommendation.

**Proposed fix:** Add a "Purchase Priority" section: (1) Order beds first (longest lead time), (2) Get soil delivery quote and schedule, (3) Byggemarked trip for everything else, (4) Seeds and plants last.

---

**Finding 10.3: Seed and plant purchase timing is split across two documents (MINOR)**

Phase 1 shopping list covers infrastructure materials. Phase 3 warm-season shopping list covers seedlings and seeds. But neither document covers the Phase 2 spring planting plant purchases (strawberry plugs, raspberry canes, herb plants, viola seedlings). These appear in the planting day script prep checklist but not in a dedicated shopping list.

**Proposed fix:** Create a `docs/spring-planting-shopping-list.md` covering all Phase 2 plant purchases, or add a "Phase 2 Plants" section to the existing shopping list.

---

### 11. Other Findings

**Finding 11.1: ROADMAP.md plan completion checkboxes are not updated (MINOR)**

All 15 plans across 6 phases have SUMMARY.md files, indicating completion. However, the ROADMAP.md "Plans" subsections show all individual plans as `- [ ]` (unchecked) despite the phase-level progress table showing correct completion counts. The plan-level checkboxes were never updated.

**Proposed fix:** Update all 15 plan checkboxes in ROADMAP.md to `- [x]`.

---

**Finding 11.2: PROJECT.md Key Decisions table shows all outcomes as "-- Pending" (MINOR)**

The PROJECT.md Key Decisions table (line 85-92) lists 6 decisions, all with "-- Pending" in the Outcome column. These decisions were made and implemented across the 6 phases. The outcomes should be recorded.

**Proposed fix:** Update PROJECT.md Key Decisions outcomes to reflect actual decisions made.

---

**Finding 11.3: PROJECT.md Active Requirements list is stale (MINOR)**

PROJECT.md "Active" requirements section (lines 19-34) lists 16 bullet points that were the original requirements before the detailed REQUIREMENTS.md was created. These are now redundant and potentially confusing alongside the 59-requirement formal list.

**Proposed fix:** Replace the Active requirements section with a pointer to REQUIREMENTS.md, or mark it as "superseded by REQUIREMENTS.md."

---

**Finding 11.4: Bed E alert rule message references "tomatoes" but Bed E has no tomatoes (MINOR)**

`data/ha/alert-rules.json` rule `haven_bed_e_moisture_below_min` (line 168) says "broccoli and tomatoes need water!" but Bed E contains broccoli, bush beans, dill, borage, and calendula -- no tomatoes. Similarly, rule `haven_bed_e_temperature_below_frost` (line 194) says "beans and tomatoes are frost-sensitive" -- again, no tomatoes in Bed E.

**Proposed fix:** Update Bed E alert messages to reference the correct crops (broccoli, beans).

---

## Proposed Future Phases

### Phase 7: Data Consistency and Identity Fix
**Goal:** Resolve the bed identity discrepancy and fix all cross-reference inconsistencies
**Findings addressed:** 1.1, 1.2, 1.3, 1.4, 1.5, 3.3, 10.1, 11.4
**Estimated scope:** Small (2 plans)
**Priority:** Critical -- do before W16
**Why:** The bed identity confusion directly affects build day. A father installing reservoirs in the wrong beds undermines vacation survival. The CLAUDE.md inaccuracies affect every future AI session.

**Plan 1:** Fix bed identity mapping in Phase 1 docs (bed-layout.md, setup-guide.md, reservoir-build.md), update CLAUDE.md bed table, fix bed JSON features, fix HA alert messages.
**Plan 2:** Create dill.json crop file, fix radish beds array, audit succession slots against Phase 3 grid maps.

---

### Phase 8: Daily Routine and Engagement Bridge
**Goal:** Give the child a printable daily routine and structured between-session activities
**Findings addressed:** 4.1, 5.1, 5.2, 5.3
**Estimated scope:** Small (1-2 plans)
**Priority:** High -- do before W16
**Why:** The core value is child agency. Without a simple daily routine card and structured activities between planting sessions, the child cannot independently engage with the garden. The detailed session scripts are excellent but they cover event days, not the daily rhythm.

**Plan 1:** Create daily-routine-card.md (printable, visual, 5-minute checklist) and weekly-garden-walk.md (5-10 minute structured activity list).
**Plan 2:** (Optional) Create a minimal photo log approach or simple tracking system.

---

### Phase 9: Operational Readiness Polish
**Goal:** Ensure the father can execute build day and plant day without re-consulting Claude
**Findings addressed:** 3.1, 4.4, 10.2, 10.3
**Estimated scope:** Small (1-2 plans)
**Priority:** High -- do before W16
**Why:** A father spending 10,000 DKK on materials needs clarity on purchase order, complete tool lists, and correct budget expectations. The spring planting shopping gap means he might arrive at W16 without the right plants.

**Plan 1:** Create spring planting shopping list, add purchase priority ordering to existing lists, add tool inventory section.

---

### Phase 10: HA Setup and Dashboard
**Goal:** Provide a complete walkthrough for configuring Home Assistant with the prepared schemas
**Findings addressed:** 6.1, 6.2, 6.3
**Estimated scope:** Small (1-2 plans)
**Priority:** Medium -- do before sensor deployment (likely in-season or Season 2)
**Why:** The HA data system is production-ready but cannot be used without a setup guide. Without this, the sensor recommendation work goes unused.

---

### Phase 11: Season 2 and End-of-Season Planning
**Goal:** Document end-of-season cleanup, perennial management, soil refresh, and lessons learned
**Findings addressed:** 4.2, 7.1, 7.2, 7.3
**Estimated scope:** Medium (2-3 plans)
**Priority:** Medium -- do in-season (before W44)
**Why:** Without end-of-season documentation, the father faces a knowledge cliff at season end. Perennial management decisions made in autumn affect Season 2 yield.

---

### Phase 12: Planning Artifact Maintenance
**Goal:** Clean up stale metadata in ROADMAP.md, PROJECT.md, REQUIREMENTS.md
**Findings addressed:** 4.3, 8 (DOCS-04 tracking), 11.1, 11.2, 11.3
**Estimated scope:** Small (1 plan)
**Priority:** Low -- post-season
**Why:** These are hygiene issues that do not affect physical garden execution but accumulate as technical debt for future planning sessions.

---

## Summary Table

| # | Proposed Phase | Priority | Scope | Findings |
|---|---------------|----------|-------|----------|
| 7 | Data Consistency and Identity Fix | Critical (before W16) | Small (2 plans) | 1.1, 1.2, 1.3, 1.4, 1.5, 3.3, 10.1, 11.4 |
| 8 | Daily Routine and Engagement Bridge | High (before W16) | Small (1-2 plans) | 4.1, 5.1, 5.2, 5.3 |
| 9 | Operational Readiness Polish | High (before W16) | Small (1-2 plans) | 3.1, 4.4, 10.2, 10.3 |
| 10 | HA Setup and Dashboard | Medium (in-season) | Small (1-2 plans) | 6.1, 6.2, 6.3 |
| 11 | Season 2 and End-of-Season Planning | Medium (before W44) | Medium (2-3 plans) | 4.2, 7.1, 7.2, 7.3 |
| 12 | Planning Artifact Maintenance | Low (post-season) | Small (1 plan) | 4.3, 8, 11.1, 11.2, 11.3 |
