# Roadmap: Haven -- A Learning Garden

## Overview

This roadmap delivers a complete backyard learning garden for a 7-year-old in Vejle, Denmark by late July 2026. The sequence is dictated by the Danish growing season: beds must be built before anything can be planted, cold-hardy crops go in first (W16), warm crops follow after last frost (W21), and everything must be vacation-proof before the family leaves in late July. Data systems and documentation run in parallel with physical garden work since they are desk work with no seasonal deadline. The end state is a child who walks out each morning to beds he owns, checks what changed overnight, waters, picks something ripe, and understands that his effort produced the food.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

Decimal phases appear between their surrounding integers in numeric order.

<details>
<summary>v1.0 Foundation Season (Phases 1-6) -- Complete 2026-03-28</summary>

- [x] **Phase 1: Bed Infrastructure** - Order, build, and fill 5 raised beds with soil, drainage, and slug defense (completed 2026-03-26)
- [x] **Phase 2: Spring Planting** - Plant all cold-hardy crops, perennials, edible flowers, and sensory plants (W16-W18) (completed 2026-03-27)
- [x] **Phase 3: Warm Season Planting** - Transplant frost-tender seedlings and complete companion planting layouts (W21-W22) (completed 2026-03-27)
- [x] **Phase 4: Data System and Schedules** - Build crop JSON database, weekly schedule files, and Home Assistant schemas (parallel with Phases 2-3) (completed 2026-03-27)
- [x] **Phase 5: Documentation and Guides** - Property visualization, troubleshooting guide, difficulty tiers, and project CLAUDE.md (completed 2026-03-27)
- [x] **Phase 6: Vacation Preparation** - Test reservoirs, mulch beds, finalize neighbor guide, execute pre-departure protocol (completed 2026-03-28)

</details>

### v1.1 Gap Closure and Operational Readiness (Phases 7-12)

- [x] **Phase 7: Data Consistency and Identity Fix** - Resolve bed naming discrepancy (1-5 vs A-E) and fix all cross-reference inconsistencies across docs and data (completed 2026-03-28)
- [x] **Phase 8: Child Engagement Bridge** - Create daily routine card and between-session activities so the child can independently engage with the garden (completed 2026-03-28)
- [x] **Phase 9: Operational Readiness** - Spring planting shopping list, purchase prioritization, and tool inventory for build and planting days (completed 2026-03-28)
- [x] **Phase 10: Home Assistant Setup** - Step-by-step HA configuration walkthrough and basic Lovelace dashboard for sensor deployment (completed 2026-03-28)
- [x] **Phase 11: Season 2 Preparation** - End-of-season cleanup, perennial management, soil refresh, and crop failure recovery documentation (completed 2026-03-28)
- [x] **Phase 12: Planning Artifact Maintenance** - Update stale checkboxes, statuses, and metadata across ROADMAP.md, PROJECT.md, and REQUIREMENTS.md (completed 2026-03-29)

## Phase Details

<details>
<summary>v1.0 Foundation Season (Phases 1-6)</summary>

### Phase 1: Bed Infrastructure
**Goal**: Five raised beds are physically in place, filled with layered soil, and ready to receive plants
**Depends on**: Nothing (first phase)
**Requirements**: INFRA-01, INFRA-02, INFRA-03, INFRA-04, INFRA-05, INFRA-06, INFRA-07, INFRA-08, DOCS-06
**Success Criteria** (what must be TRUE):
  1. Three backyard beds are positioned in the west-central yard and filled with drainage layer, garden waste, and hojbedsmuld
  2. Two terrace beds are placed on the roof terrace (or deferred with documented reason if structural assessment fails)
  3. Copper tape slug defense is installed on all bed edges
  4. Self-watering reservoirs and vertical trellis are built into the designated beds
  5. A complete shopping list exists with specific products, DKK prices, and suppliers for both corten steel and galvanized alternatives
**Plans:** 3/3 plans complete

Plans:
- [x] 01-01-PLAN.md -- Shopping list (dual-priced) and bed layout with placement diagrams
- [x] 01-02-PLAN.md -- Soil layers, slug defense, reservoir build, and trellis build guides
- [x] 01-03-PLAN.md -- Master setup guide sequencing all construction + user review checkpoint

### Phase 2: Spring Planting
**Goal**: All cold-hardy crops, perennials, edible flowers, sensory plants, and creature habitats are in the ground and the child has experienced his first planting sessions
**Depends on**: Phase 1
**Requirements**: CROP-01, CROP-05, CROP-06, ENGM-02, ENGM-03, ENGM-04, FLWR-02, FLWR-03, FLWR-04, FLWR-05, SENS-01, SENS-02, SENS-04, COOK-01, COOK-05, COOK-06, CRTR-03, CRTR-04, SCHED-01
**Success Criteria** (what must be TRUE):
  1. Strawberries (everbearing and June-bearing) and raspberries are planted in their designated beds
  2. Radishes, lettuce, pea shoots, spring onions, kale, and peas are sown in their bed positions per the companion planting layout
  3. Calendula, borage, viola, and chive divisions are planted for edible flowers
  4. Sensory plants (lamb's ear, lemon balm, thyme) are at bed edges where the child can touch and smell them
  5. A bed-by-bed planting layout document exists showing exactly which plant goes where with spacing
**Plans:** 2/2 plans complete

Plans:
- [x] 02-01-PLAN.md -- Bed-by-bed planting grid maps (5 beds) with exact cm positions, companion planting, and succession slots
- [x] 02-02-PLAN.md -- Planting day session script (W16-W18) and bug hotel / pollinator water station guide

### Phase 3: Warm Season Planting
**Goal**: All frost-tender crops are transplanted after May 20, completing the garden's full planting plan and starting the continuous harvest engine
**Depends on**: Phase 2
**Requirements**: CROP-02, CROP-03, CROP-04, ENGM-01, FLWR-01, SENS-03, SENS-05, COOK-03, COOK-04, COOK-07, CRTR-01, CRTR-02
**Success Criteria** (what must be TRUE):
  1. Cherry tomatoes, cucumbers, and sweet peppers are transplanted as seedlings into their companion-planted bed positions
  2. Sunflowers are direct-sown and the child has a height-measurement activity underway
  3. Nasturtiums are trailing from bed edges and positioned as aphid trap crops near the creature observation zone
  4. Basil, mint (potted), bush beans, leeks, and broccoli are planted in their designated positions
  5. Borage and dill are positioned to attract bees and beneficial insects, with a pollinator water dish nearby
**Plans:** 2/2 plans complete

Plans:
- [x] 03-01-PLAN.md -- Updated grid maps (Beds A, C, D, E) with warm-season crop positions and shopping list
- [x] 03-02-PLAN.md -- Session 1 (W18 direct-sow) and Session 2 (W21 transplant) scripts with pea harvest party

### Phase 4: Data System and Schedules
**Goal**: A structured JSON data system covers every planted crop, every week of the season, and the Home Assistant integration schema -- ready for IoT sensors in season 2
**Depends on**: Phase 1 (needs bed layout); can run in parallel with Phases 2-3
**Requirements**: DATA-01, DATA-02, DATA-03, DATA-04, DATA-05, DATA-06, SCHED-02, SCHED-03, SCHED-04
**Success Criteria** (what must be TRUE):
  1. A JSON schema defines all crop fields (growth stages, water needs, harvest timing, companion plants, difficulty tier, child actions, alert triggers) and every planted crop has a populated JSON file
  2. Weekly schedule JSON files exist for W15 through W44 with themed names, prioritized tasks, and expected growth events
  3. A staggered planting schedule ensures continuous harvest from late May through October with no 2-week gap
  4. Home Assistant entity schemas follow the haven_ prefix convention with per-bed sensor entities and Plant Monitor configurations
  5. Zigbee/LoRaWAN sensor recommendations are documented with specific models, prices, and HA compatibility
**Plans:** 3/3 plans complete

Plans:
- [x] 04-01-PLAN.md -- Crop JSON database (27 files) with schemas and bed mapping files
- [x] 04-02-PLAN.md -- Weekly schedules (W15-W44) and succession calendar with harvest gap analysis
- [x] 04-03-PLAN.md -- Home Assistant entity schemas and sensor hardware recommendations

### Phase 5: Documentation and Guides
**Goal**: Father and son have reference documents for every garden situation -- what to do when something goes wrong, which crops are easy vs hard, what the garden looks like from above, and a project file for Claude continuity
**Depends on**: Phase 2 (needs planted crops for context); can run in parallel with Phases 3-4
**Requirements**: DOCS-01, DOCS-02, DOCS-03, DOCS-04, DOCS-05, COOK-02
**Success Criteria** (what must be TRUE):
  1. A property visualization shows bed placement, sun patterns, compass orientation, and access paths
  2. A troubleshooting guide is structured for father-son use: visual, searchable by symptom, with photo-friendly format
  3. Every crop is classified into difficulty tiers ("can't fail" / "needs care" / "Year 2 challenge") in one reference document
  4. A CLAUDE.md project file captures full garden context for AI-assisted continuity across sessions
  5. Garlic hardneck planting (October 2026) is documented in the autumn schedule for Year 2 harvest
**Plans:** 3/3 plans complete

Plans:
- [x] 05-01-PLAN.md -- Property visualization (ASCII) and CLAUDE.md project continuity file
- [x] 05-02-PLAN.md -- Troubleshooting guide (symptom-based) and difficulty-tiered crop classification
- [x] 05-03-PLAN.md -- Neighbor vacation guide and garlic autumn planting documentation

### Phase 6: Vacation Preparation
**Goal**: The garden survives 2-3 weeks of family absence in July-August with zero crop loss, and a neighbor can maintain it using a printed guide
**Depends on**: Phases 3, 5 (garden must be fully planted; neighbor guide content from docs)
**Requirements**: VACN-01, VACN-02, VACN-03, VACN-04
**Success Criteria** (what must be TRUE):
  1. Self-watering reservoirs in tomato and cucumber beds are tested and confirmed to sustain plants for 5+ days without manual watering
  2. All beds are mulched with 5-8cm of straw or bark before departure
  3. A pre-vacation harvest protocol has been executed (everything showing color picked)
  4. The neighbor has received a printed vacation guide with per-bed photos, watering frequency, harvest instructions, and emergency contacts
**Plans:** 2/2 plans complete

Plans:
- [x] 06-01-PLAN.md -- Reservoir test protocol and per-bed mulching guide
- [x] 06-02-PLAN.md -- 3-day pre-departure countdown script, printable checklist, and JSON data

</details>

### Phase 7: Data Consistency and Identity Fix
**Goal**: Every document, data file, and automation rule references beds by their canonical A-E names with correct crop assignments, so build day instructions match actual planting plans
**Depends on**: Phase 6 (v1.0 milestone); no v1.1 internal dependencies
**Requirements**: DFIX-01, DFIX-02, DFIX-03, DFIX-04, DFIX-05, DFIX-06, DFIX-07, DFIX-08
**Success Criteria** (what must be TRUE):
  1. Phase 1 docs (bed-layout, setup-guide, reservoir-build) use Bed A-E naming with a clear mapping table from the original Bed 1-5
  2. CLAUDE.md bed assignment table matches the Phase 2+ planting grid assignments (Bed A = strawberry/sensory, Bed B = raspberry, Bed C = warm crops)
  3. Bed JSON feature arrays and HA alert messages reference the correct crops per bed (no tomato references in Bed E, correct reservoir beds)
  4. Weekly schedule sowing tasks align with Phase 3 grid maps -- stopped succession slots have no future sowing tasks
  5. A dill.json crop file exists with proper schema fields, and the radish crop JSON correctly documents its bed assignments
**Plans:** 2/2 plans complete

Plans:
- [x] 07-01-PLAN.md -- Phase 1 doc naming fix (bed-layout, setup-guide, reservoir-build) + CLAUDE.md bed table + vacation script reservoir refs
- [x] 07-02-PLAN.md -- JSON data fixes (bed features, HA alerts, dill.json, radish note, schedule succession audit)

### Phase 8: Child Engagement Bridge
**Goal**: The child has a simple visual daily routine and structured between-session activities that let him independently engage with the garden every day, not just on planting event days
**Depends on**: Phase 7 (needs correct bed names for routine card)
**Requirements**: CENG-01, CENG-02, CENG-03, CENG-04
**Success Criteria** (what must be TRUE):
  1. A printable daily routine card exists with a visual 5-minute checklist the child can follow without reading (check beds, water, pick, measure)
  2. Structured activities exist for the W19-W20 gap between planting sessions (sunflower check, germination watch, sensory walk)
  3. A weekly garden walk checklist provides 3-5 recurring quick activities that take 5-10 minutes
  4. A simple photo log approach is documented (one photo per visit, shared album, low friction)
**Plans:** 2/2 plans complete

Plans:
- [x] 08-01-PLAN.md -- Daily routine card (5-min visual checklist) and weekly garden walk checklist (3-5 activities)
- [x] 08-02-PLAN.md -- Between-session gap activities (W19-W20 treasure hunts) and photo log approach

### Phase 9: Operational Readiness
**Goal**: The father can execute build day and planting day without re-consulting Claude -- he knows what to buy, in what order, and has a complete tool list
**Depends on**: Phase 7 (needs correct bed/crop assignments for shopping list accuracy)
**Requirements**: OPRD-01, OPRD-02, OPRD-03, OPRD-04
**Success Criteria** (what must be TRUE):
  1. A spring planting shopping list covers all Phase 2 plant purchases (strawberry plugs, raspberry canes, herb plants, viola seedlings) with specific varieties and quantities
  2. Purchase priority ordering exists across all shopping lists showing what to order first based on lead times
  3. A tool inventory section lists every required tool across build day and planting days
  4. PROJECT.md budget constraint reflects the actual ~10,000 DKK cost with documented rationale for the increase
**Plans:** 1/1 plans complete

Plans:
- [x] 09-01-PLAN.md -- Spring planting shopping list, purchase priority timeline, tool inventory, and budget fix

### Phase 10: Home Assistant Setup
**Goal**: A father with Home Assistant running can configure sensors, plant monitors, and alerts using a step-by-step walkthrough and see bed status on a dashboard
**Depends on**: Phase 7 (needs correct bed/crop references in HA schemas)
**Requirements**: HAIG-01, HAIG-02, HAIG-03
**Success Criteria** (what must be TRUE):
  1. A setup walkthrough guides the user through configuring HA sensors, Plant Monitor entities, and alert automations using the prepared JSON/YAML
  2. A basic Lovelace dashboard YAML shows per-bed moisture and temperature cards that can be pasted into HA
  3. Alert rule notification targets are documented as requiring user-specific configuration with instructions for finding the correct service name
**Plans:** 1/1 plans complete

Plans:
- [x] 10-01-PLAN.md -- HA setup walkthrough with sensors, plant monitors, automations, and Lovelace dashboard

### Phase 11: Season 2 Preparation
**Goal**: Documentation exists for everything that happens after the growing season ends -- cleanup, perennial care, soil refresh, and lessons learned -- so the family is not stranded at W44
**Depends on**: Phases 8, 9 (engagement and operational docs should be complete first); can execute any time before W44
**Requirements**: SSN2-01, SSN2-02, SSN2-03, SSN2-04, SSN2-05
**Success Criteria** (what must be TRUE):
  1. An end-of-season cleanup guide covers W44-W46 tasks: plant removal, composting, reservoir draining, tool storage
  2. Perennial management notes exist for strawberry crowns, raspberry canes, and herb plants (what to cut, what to protect, when)
  3. Year 2 soil refresh documentation explains when and how to amend raised bed soil (compost vs fresh hojbedsmuld, timing)
  4. A season review template captures what worked, what failed, crop-by-crop assessment, and child engagement observations
  5. A crop failure recovery section in the troubleshooting guide documents mid-season replanting windows and replacement options
**Plans:** 2/2 plans complete

Plans:
- [x] 11-01-PLAN.md -- End-of-season countdown guide, perennial care, and soil refresh documentation
- [x] 11-02-PLAN.md -- Season review template (markdown + JSON schema) and crop failure recovery in troubleshooting guide

### Phase 12: Planning Artifact Maintenance
**Goal**: All planning files accurately reflect project state -- no stale checkboxes, outdated statuses, or missing traceability entries
**Depends on**: Phase 7 (identity fixes must land first so statuses are correct)
**Requirements**: PMNT-01, PMNT-02, PMNT-03, PMNT-04, PMNT-05
**Success Criteria** (what must be TRUE):
  1. All 15 v1.0 plan checkboxes in ROADMAP.md are checked to match actual completion status
  2. PROJECT.md Key Decisions outcomes are updated from Pending to actual results
  3. REQUIREMENTS.md DOCS-04 and COOK-02 traceability statuses are corrected to reflect deliverable state
  4. Vacation week schedule files (W30-W33) flag neighbor override for child-assigned tasks
  5. W40 schedule includes garlic planting hero task per garlic-autumn-plan.md
**Plans:** 2/2 plans complete

Plans:
- [x] 12-01-PLAN.md -- Fix stale checkboxes, decisions, and traceability in ROADMAP, PROJECT, and REQUIREMENTS markdown files
- [ ] 12-02-PLAN.md -- Add vacation_note to W30-W33 schedule files and align W40 garlic task with docs

## Progress

**Execution Order:**
- v1.0: 1 -> 2 -> 3 -> 4 -> 5 -> 6 (4 and 5 ran parallel with physical planting)
- v1.1: 7 -> 8 -> 9 -> 10 -> 11 -> 12 (7-9 before W16; 10 in-season; 11 before W44; 12 any time)

| Phase | Milestone | Plans Complete | Status | Completed |
|-------|-----------|----------------|--------|-----------|
| 1. Bed Infrastructure | v1.0 | 3/3 | Complete | 2026-03-26 |
| 2. Spring Planting | v1.0 | 2/2 | Complete | 2026-03-27 |
| 3. Warm Season Planting | v1.0 | 2/2 | Complete | 2026-03-27 |
| 4. Data System and Schedules | v1.0 | 3/3 | Complete | 2026-03-27 |
| 5. Documentation and Guides | v1.0 | 3/3 | Complete | 2026-03-27 |
| 6. Vacation Preparation | v1.0 | 2/2 | Complete | 2026-03-28 |
| 7. Data Consistency and Identity Fix | v1.1 | 2/2 | Complete | 2026-03-28 |
| 8. Child Engagement Bridge | v1.1 | 2/2 | Complete | 2026-03-28 |
| 9. Operational Readiness | v1.1 | 1/1 | Complete | 2026-03-28 |
| 10. Home Assistant Setup | v1.1 | 1/1 | Complete | 2026-03-28 |
| 11. Season 2 Preparation | v1.1 | 2/2 | Complete | 2026-03-28 |
| 12. Planning Artifact Maintenance | v1.1 | 2/2 | Complete | 2026-03-29 |
