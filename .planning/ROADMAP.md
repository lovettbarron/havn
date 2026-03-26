# Roadmap: Havn -- A Learning Garden

## Overview

This roadmap delivers a complete backyard learning garden for a 7-year-old in Vejle, Denmark by late July 2026. The sequence is dictated by the Danish growing season: beds must be built before anything can be planted, cold-hardy crops go in first (W16), warm crops follow after last frost (W21), and everything must be vacation-proof before the family leaves in late July. Data systems and documentation run in parallel with physical garden work since they are desk work with no seasonal deadline. The end state is a child who walks out each morning to beds he owns, checks what changed overnight, waters, picks something ripe, and understands that his effort produced the food.

## Phases

**Phase Numbering:**
- Integer phases (1, 2, 3): Planned milestone work
- Decimal phases (2.1, 2.2): Urgent insertions (marked with INSERTED)

Decimal phases appear between their surrounding integers in numeric order.

- [x] **Phase 1: Bed Infrastructure** - Order, build, and fill 5 raised beds with soil, drainage, and slug defense (completed 2026-03-26)
- [ ] **Phase 2: Spring Planting** - Plant all cold-hardy crops, perennials, edible flowers, and sensory plants (W16-W18)
- [ ] **Phase 3: Warm Season Planting** - Transplant frost-tender seedlings and complete companion planting layouts (W21-W22)
- [ ] **Phase 4: Data System and Schedules** - Build crop JSON database, weekly schedule files, and Home Assistant schemas (parallel with Phases 2-3)
- [ ] **Phase 5: Documentation and Guides** - Property visualization, troubleshooting guide, difficulty tiers, and project CLAUDE.md
- [ ] **Phase 6: Vacation Preparation** - Test reservoirs, mulch beds, finalize neighbor guide, execute pre-departure protocol

## Phase Details

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
- [ ] 01-01-PLAN.md — Shopping list (dual-priced) and bed layout with placement diagrams
- [ ] 01-02-PLAN.md — Soil layers, slug defense, reservoir build, and trellis build guides
- [ ] 01-03-PLAN.md — Master setup guide sequencing all construction + user review checkpoint

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
**Plans:** 2 plans

Plans:
- [ ] 02-01-PLAN.md — Bed-by-bed planting grid maps (5 beds) with exact cm positions, companion planting, and succession slots
- [ ] 02-02-PLAN.md — Planting day session script (W16-W18) and bug hotel / pollinator water station guide

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
**Plans:** 2 plans

Plans:
- [ ] 03-01-PLAN.md — Updated grid maps (Beds A, C, D, E) with warm-season crop positions and shopping list
- [ ] 03-02-PLAN.md — Session 1 (W18 direct-sow) and Session 2 (W21 transplant) scripts with pea harvest party

### Phase 4: Data System and Schedules
**Goal**: A structured JSON data system covers every planted crop, every week of the season, and the Home Assistant integration schema -- ready for IoT sensors in season 2
**Depends on**: Phase 1 (needs bed layout); can run in parallel with Phases 2-3
**Requirements**: DATA-01, DATA-02, DATA-03, DATA-04, DATA-05, DATA-06, SCHED-02, SCHED-03, SCHED-04
**Success Criteria** (what must be TRUE):
  1. A JSON schema defines all crop fields (growth stages, water needs, harvest timing, companion plants, difficulty tier, child actions, alert triggers) and every planted crop has a populated JSON file
  2. Weekly schedule JSON files exist for W15 through W44 with themed names, prioritized tasks, and expected growth events
  3. A staggered planting schedule ensures continuous harvest from late May through October with no 2-week gap
  4. Home Assistant entity schemas follow the havn_ prefix convention with per-bed sensor entities and Plant Monitor configurations
  5. Zigbee/LoRaWAN sensor recommendations are documented with specific models, prices, and HA compatibility
**Plans**: TBD

Plans:
- [ ] 04-01: TBD
- [ ] 04-02: TBD
- [ ] 04-03: TBD

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
**Plans**: TBD

Plans:
- [ ] 05-01: TBD
- [ ] 05-02: TBD
- [ ] 05-03: TBD

### Phase 6: Vacation Preparation
**Goal**: The garden survives 2-3 weeks of family absence in July-August with zero crop loss, and a neighbor can maintain it using a printed guide
**Depends on**: Phases 3, 5 (garden must be fully planted; neighbor guide content from docs)
**Requirements**: VACN-01, VACN-02, VACN-03, VACN-04
**Success Criteria** (what must be TRUE):
  1. Self-watering reservoirs in tomato and cucumber beds are tested and confirmed to sustain plants for 5+ days without manual watering
  2. All beds are mulched with 5-8cm of straw or bark before departure
  3. A pre-vacation harvest protocol has been executed (everything showing color picked)
  4. The neighbor has received a printed vacation guide with per-bed photos, watering frequency, harvest instructions, and emergency contacts
**Plans**: TBD

Plans:
- [ ] 06-01: TBD
- [ ] 06-02: TBD

## Progress

**Execution Order:**
Phases execute in numeric order: 1 -> 2 -> 3 -> 4 -> 5 -> 6
Note: Phase 4 (Data) and Phase 5 (Docs) can run in parallel with physical planting phases.

| Phase | Plans Complete | Status | Completed |
|-------|----------------|--------|-----------|
| 1. Bed Infrastructure | 3/3 | Complete   | 2026-03-26 |
| 2. Spring Planting | 0/2 | Planned | - |
| 3. Warm Season Planting | 0/2 | Planned | - |
| 4. Data System and Schedules | 0/3 | Not started | - |
| 5. Documentation and Guides | 0/3 | Not started | - |
| 6. Vacation Preparation | 0/2 | Not started | - |
