# Requirements: Haven -- A Learning Garden

**Defined:** 2026-03-26
**Core Value:** A child who independently checks on, cares for, and harvests from plants he chose to grow

## v1 Requirements

### Infrastructure

- [x] **INFRA-01**: 3 backyard raised beds (120x60x40cm corten steel) positioned in west-central backyard for 8-10 hours summer sun
- [x] **INFRA-02**: 2 terrace raised beds (80x40x30cm, lightweight) on roof terrace after structural assessment
- [x] **INFRA-03**: Soil layer system with drainage layer, garden waste fill, and purchased hojbedsmuld top layer in all beds
- [x] **INFRA-04**: Copper tape slug defense installed on all bed edges
- [x] **INFRA-05**: Self-watering reservoirs (SIP/wicking) built into tomato and cucumber beds
- [x] **INFRA-06**: Vertical support/trellis for cucumber bed
- [x] **INFRA-07**: Shopping list with specific products, DKK prices, and suppliers for corten steel and galvanized alternatives
- [x] **INFRA-08**: Step-by-step setup instructions for bed placement, soil filling, and reservoir installation

### His Crops (Child's Beds)

- [x] **CROP-01**: Strawberries planted -- everbearing (Ostara) and June-bearing (Korona) for continuous June-September picking
- [x] **CROP-02**: Cherry tomatoes planted -- Sungold and Tumbling Tom as seedlings after May 20
- [x] **CROP-03**: Cucumbers planted -- Mini Munch or Picolino as seedlings after May 20
- [x] **CROP-04**: Sweet peppers planted -- Lipstick and/or King of the North as seedlings after May 25
- [x] **CROP-05**: Raspberries planted -- Autumn Bliss bare-root canes in March-April for Aug-Oct fruit
- [x] **CROP-06**: Radishes succession-sown every 2 weeks from April 20 through August 1 for continuous 3-week harvest cycles

### Quick Wins & Engagement

- [x] **ENGM-01**: Sunflowers direct-sown May 1 for daily height measurement activity
- [x] **ENGM-02**: Baby lettuce (cut-and-come-again) sown for 3-week harvests
- [x] **ENGM-03**: Pea shoots sown for 2-3 week quick harvest
- [x] **ENGM-04**: Bed-by-bed companion planting layout following researched recipes (tomato+basil+nasturtium, cucumber+pepper+radish+borage, berry+thyme+chives, etc.)

### Edible Flowers

- [x] **FLWR-01**: Nasturtium direct-sown May 1 -- trailing variety for bed edges, edible flowers for baking
- [x] **FLWR-02**: Calendula direct-sown April 20 -- orange/yellow petals for baking decoration
- [x] **FLWR-03**: Borage direct-sown April 20 -- blue star flowers, exceptional bee attractor
- [x] **FLWR-04**: Viola/pansy planted as seedlings March-April -- immediate color, crystallizable petals
- [x] **FLWR-05**: Chive flowers harvested May-June from planted chive divisions -- edible purple pompoms

### Sensory Plants

- [x] **SENS-01**: Lamb's ear (Stachys) planted at bed edge for tactile engagement
- [x] **SENS-02**: Lemon balm planted for crush-and-smell sensory activity
- [x] **SENS-03**: Mint planted in own pot (prevents spreading) for pick-and-smell activity
- [x] **SENS-04**: Thyme planted as creeping ground cover at bed edges
- [x] **SENS-05**: Basil planted as seedling alongside tomatoes for aroma and pinching activity

### Family Cooking Crops

- [x] **COOK-01**: Spring onions (White Lisbon) direct-sown April 15, succession monthly
- [ ] **COOK-02**: Garlic hardneck cloves planted October 2026 for July 2027 harvest
- [x] **COOK-03**: Leeks (Musselburgh) sown indoors March, transplanted May
- [x] **COOK-04**: Bush beans (Provider/Speedy) direct-sown May 15 after frost
- [x] **COOK-05**: Dinosaur kale (Nero di Toscana) direct-sown April 20 -- "dinosaur" name for engagement
- [x] **COOK-06**: Peas (Kelvedon Wonder) direct-sown April 15 -- edible pods for garden snacking
- [x] **COOK-07**: Broccoli (Calabrese) transplanted May -- side shoots for extended harvest

### Creature Attractions

- [x] **CRTR-01**: Borage and dill planted to attract bees, ladybugs, and hoverflies
- [x] **CRTR-02**: Nasturtium positioned as trap crop to create visible aphid-ladybug predator-prey dynamic
- [x] **CRTR-03**: Log pile or stone pile placed near beds for beetle/woodlice habitat
- [x] **CRTR-04**: Shallow water dish with pebbles placed near flowers for pollinator/bird watering

### Planting Schedule

- [x] **SCHED-01**: Bed-by-bed planting distribution specifying exactly which plants go in which bed with spacing
- [x] **SCHED-02**: Staggered planting schedule ensuring continuous harvest from late May through October
- [x] **SCHED-03**: Week-by-week maintenance plan from W14 (early April) through W44 (late October)
- [x] **SCHED-04**: Succession sowing calendar for radish, lettuce, beans, spring onion, and peas

### Data System

- [x] **DATA-01**: JSON schema for crop database (growth stages, water needs, harvest timing, companion plants, difficulty tier, child actions, alert triggers)
- [x] **DATA-02**: Individual JSON crop files for every planted crop with all schema fields populated
- [x] **DATA-03**: Weekly schedule JSON files (one per ISO week) with themed names, prioritized tasks, expected growth events
- [x] **DATA-04**: Home Assistant entity schema following haven_ prefix convention with per-bed sensor entities
- [x] **DATA-05**: Home Assistant Plant Monitor configuration with moisture/temperature thresholds per crop
- [x] **DATA-06**: Zigbee/LoRaWAN sensor recommendations with specific models, prices, and HA compatibility confirmation

### Documentation

- [x] **DOCS-01**: Property visualization showing bed placement, sun patterns, compass orientation, and access paths
- [x] **DOCS-02**: Troubleshooting guide structured for father-son reference (visual, searchable, symptom-based)
- [x] **DOCS-03**: Difficulty-tiered crop collection clearly marking "can't fail" vs "needs care" vs "Year 2 challenge"
- [ ] **DOCS-04**: "Help us keep our farm alive" neighbor vacation guide with per-bed watering frequency and harvest instructions
- [x] **DOCS-05**: CLAUDE.md project file based on ~/book/vibes patterns with full garden context
- [x] **DOCS-06**: Shopping list with corten steel AND budget alternative pricing in DKK

### Vacation Survival

- [x] **VACN-01**: Self-watering reservoirs installed and tested in tomato and cucumber beds before July
- [x] **VACN-02**: Mulching protocol (5-8cm straw/bark) for all beds before each absence
- [x] **VACN-03**: Pre-vacation harvest protocol (pick everything showing color)
- [x] **VACN-04**: Neighbor guide delivered as printable document with photos, per-bed instructions, and emergency contacts

## v1.1 Requirements

Requirements for gap closure and operational readiness. Each maps to roadmap phases 7-12.

### Data Consistency

- [x] **DFIX-01**: All Phase 1 docs (bed-layout, setup-guide, reservoir-build) use canonical Bed A-E naming with clear mapping from original Bed 1-5
- [x] **DFIX-02**: CLAUDE.md bed assignment table matches actual Phase 2+ planting grid assignments
- [x] **DFIX-03**: Bed JSON feature arrays correctly reflect which beds have reservoirs after Phase 2 remapping
- [x] **DFIX-04**: HA alert rule messages reference correct crops per bed (fix Bed E tomato references)
- [x] **DFIX-05**: Vacation countdown script references correct reservoir beds
- [x] **DFIX-06**: Missing dill.json crop file created with proper schema fields
- [x] **DFIX-07**: Radish crop JSON beds array includes bed-e or documents why it is excluded
- [x] **DFIX-08**: Weekly schedule sowing tasks audited against Phase 3 grid maps for stopped succession slots

### Child Engagement

- [x] **CENG-01**: Printable daily routine card exists for the child's 5-minute garden check (visual, child-facing)
- [x] **CENG-02**: Structured between-session activities for W19-W20 gap (sunflower check, germination watch, sensory walk)
- [x] **CENG-03**: Weekly garden walk checklist with 3-5 recurring quick activities
- [x] **CENG-04**: Simple photo log approach documented (low friction, one photo per visit)

### Operational Readiness

- [x] **OPRD-01**: Spring planting shopping list covering all Phase 2 plant purchases (plugs, canes, herbs, seedlings)
- [x] **OPRD-02**: Purchase priority ordering added to shopping lists (lead times, what to order first)
- [x] **OPRD-03**: Tool inventory section covering all required tools across build and planting days
- [x] **OPRD-04**: PROJECT.md budget constraint updated to reflect actual ~10,000 DKK cost

### HA Integration

- [x] **HAIG-01**: Step-by-step HA setup walkthrough for configuring sensors, plant monitors, and alerts
- [x] **HAIG-02**: Basic Lovelace dashboard YAML showing per-bed moisture and temperature cards
- [x] **HAIG-03**: Alert rule notification target documented as requiring user-specific configuration

### Season 2 Preparation

- [ ] **SSN2-01**: End-of-season cleanup guide (W44-W46) covering plant removal, composting, reservoir draining
- [ ] **SSN2-02**: Perennial management notes for strawberry crowns, raspberry canes, and herb plants
- [ ] **SSN2-03**: Year 2 soil refresh documentation (when and how to amend raised bed soil)
- [x] **SSN2-04**: Season review template for capturing lessons learned
- [x] **SSN2-05**: Crop failure recovery section added to troubleshooting guide with mid-season replanting windows

### Planning Maintenance

- [ ] **PMNT-01**: All 15 v1.0 plan checkboxes in ROADMAP.md updated to checked
- [ ] **PMNT-02**: PROJECT.md Key Decisions outcomes updated from Pending to actual results
- [ ] **PMNT-03**: REQUIREMENTS.md DOCS-04 and COOK-02 traceability statuses corrected
- [ ] **PMNT-04**: Vacation week schedule files flag neighbor override for child-assigned tasks
- [ ] **PMNT-05**: W40 schedule includes garlic planting hero task per garlic-autumn-plan.md

## v2 Requirements

### Season 2 Crops
- **CROP-V2-01**: Carrots (Paris Market round variety -- 55 days, visible pulling activity)
- **CROP-V2-02**: Fennel (bronze fennel for beneficial insects)
- **CROP-V2-03**: Seed saving from best-performing crops
- **CROP-V2-04**: Exotic varieties (purple carrots, white strawberries)
- **CROP-V2-05**: Garlic scapes harvest (from autumn-planted garlic)

### IoT Expansion
- **IOT-V2-01**: 3x Haozee Zigbee soil moisture/temperature sensors (one per backyard bed)
- **IOT-V2-02**: Zigbee2MQTT configuration for sensor ingestion
- **IOT-V2-03**: Automated watering reminder notifications in Danish
- **IOT-V2-04**: Lovelace dashboard with Mushroom cards showing per-bed health
- **IOT-V2-05**: LoRaWAN sensor evaluation if Zigbee range is insufficient

### Advanced Features
- **ADV-V2-01**: Visual checklist cards (pictures, not text) at bed height for 3-step routine
- **ADV-V2-02**: Garden journal/log for the child to track observations
- **ADV-V2-03**: Yield tracking and season comparison data

## Out of Scope

| Feature | Reason |
|---------|--------|
| Greenhouse/polytunnel | Complexity and cost -- raised beds are sufficient for v1 |
| Automated irrigation system | Manual watering is part of the agency-building routine |
| Indoor seed starting | Requires 6-8 weeks of consistent daily attention, high failure rate for beginners |
| Fruit trees | Long-term commitment, consider after first season validates approach |
| Lemon/citrus outdoors | Not viable in Danish climate (zone 7b) |
| Exotic fruits (pomegranate, passion fruit, kiwi) | Climate incompatible |
| Corn/sweetcorn | Needs huge space, won't reliably ripen in Danish raised beds |
| Melon/watermelon | Needs sustained heat Denmark rarely provides, high failure = devastating for ADHD |
| Courgette as main crop | Takes enormous space, powdery mildew magnet in Danish humidity |
| Brussels sprouts | 150+ days, zero engagement value, "the most boring crop" |

## Traceability

### v1.0

| Requirement | Phase | Status |
|-------------|-------|--------|
| INFRA-01 | Phase 1 | Complete |
| INFRA-02 | Phase 1 | Complete |
| INFRA-03 | Phase 1 | Complete |
| INFRA-04 | Phase 1 | Complete |
| INFRA-05 | Phase 1 | Complete |
| INFRA-06 | Phase 1 | Complete |
| INFRA-07 | Phase 1 | Complete |
| INFRA-08 | Phase 1 | Complete |
| DOCS-06 | Phase 1 | Complete |
| CROP-01 | Phase 2 | Complete |
| CROP-05 | Phase 2 | Complete |
| CROP-06 | Phase 2 | Complete |
| ENGM-02 | Phase 2 | Complete |
| ENGM-03 | Phase 2 | Complete |
| ENGM-04 | Phase 2 | Complete |
| FLWR-02 | Phase 2 | Complete |
| FLWR-03 | Phase 2 | Complete |
| FLWR-04 | Phase 2 | Complete |
| FLWR-05 | Phase 2 | Complete |
| SENS-01 | Phase 2 | Complete |
| SENS-02 | Phase 2 | Complete |
| SENS-04 | Phase 2 | Complete |
| COOK-01 | Phase 2 | Complete |
| COOK-05 | Phase 2 | Complete |
| COOK-06 | Phase 2 | Complete |
| CRTR-03 | Phase 2 | Complete |
| CRTR-04 | Phase 2 | Complete |
| SCHED-01 | Phase 2 | Complete |
| CROP-02 | Phase 3 | Complete |
| CROP-03 | Phase 3 | Complete |
| CROP-04 | Phase 3 | Complete |
| ENGM-01 | Phase 3 | Complete |
| FLWR-01 | Phase 3 | Complete |
| SENS-03 | Phase 3 | Complete |
| SENS-05 | Phase 3 | Complete |
| COOK-03 | Phase 3 | Complete |
| COOK-04 | Phase 3 | Complete |
| COOK-07 | Phase 3 | Complete |
| CRTR-01 | Phase 3 | Complete |
| CRTR-02 | Phase 3 | Complete |
| DATA-01 | Phase 4 | Complete |
| DATA-02 | Phase 4 | Complete |
| DATA-03 | Phase 4 | Complete |
| DATA-04 | Phase 4 | Complete |
| DATA-05 | Phase 4 | Complete |
| DATA-06 | Phase 4 | Complete |
| SCHED-02 | Phase 4 | Complete |
| SCHED-03 | Phase 4 | Complete |
| SCHED-04 | Phase 4 | Complete |
| DOCS-01 | Phase 5 | Complete |
| DOCS-02 | Phase 5 | Complete |
| DOCS-03 | Phase 5 | Complete |
| DOCS-04 | Phase 5 | Pending |
| DOCS-05 | Phase 5 | Complete |
| COOK-02 | Phase 5 | Pending |
| VACN-01 | Phase 6 | Complete |
| VACN-02 | Phase 6 | Complete |
| VACN-03 | Phase 6 | Complete |
| VACN-04 | Phase 6 | Complete |

**v1.0 Coverage:**
- v1.0 requirements: 59 total
- Mapped to phases: 59
- Unmapped: 0

**v1.0 Notes:**
- DOCS-06 and INFRA-07 overlap (both are shopping lists with pricing). Both mapped to Phase 1; DOCS-06 will be satisfied by the same deliverable as INFRA-07.
- INFRA-05 (build reservoirs) and VACN-01 (test reservoirs) are complementary -- build in Phase 1, verify in Phase 6.
- COOK-02 (garlic) is an October 2026 planting; mapped to Phase 5 as documentation of the autumn plan.

### v1.1

| Requirement | Phase | Status |
|-------------|-------|--------|
| DFIX-01 | Phase 7 | Complete |
| DFIX-02 | Phase 7 | Complete |
| DFIX-03 | Phase 7 | Complete |
| DFIX-04 | Phase 7 | Complete |
| DFIX-05 | Phase 7 | Complete |
| DFIX-06 | Phase 7 | Complete |
| DFIX-07 | Phase 7 | Complete |
| DFIX-08 | Phase 7 | Complete |
| CENG-01 | Phase 8 | Complete |
| CENG-02 | Phase 8 | Complete |
| CENG-03 | Phase 8 | Complete |
| CENG-04 | Phase 8 | Complete |
| OPRD-01 | Phase 9 | Complete |
| OPRD-02 | Phase 9 | Complete |
| OPRD-03 | Phase 9 | Complete |
| OPRD-04 | Phase 9 | Complete |
| HAIG-01 | Phase 10 | Complete |
| HAIG-02 | Phase 10 | Complete |
| HAIG-03 | Phase 10 | Complete |
| SSN2-01 | Phase 11 | Pending |
| SSN2-02 | Phase 11 | Pending |
| SSN2-03 | Phase 11 | Pending |
| SSN2-04 | Phase 11 | Complete |
| SSN2-05 | Phase 11 | Complete |
| PMNT-01 | Phase 12 | Pending |
| PMNT-02 | Phase 12 | Pending |
| PMNT-03 | Phase 12 | Pending |
| PMNT-04 | Phase 12 | Pending |
| PMNT-05 | Phase 12 | Pending |

**v1.1 Coverage:**
- v1.1 requirements: 29 total
- Mapped to phases: 29
- Unmapped: 0

**v1.1 Notes:**
- DFIX requirements address gap analysis findings 1.1-1.5, 3.3, 10.1, 11.4
- PMNT-01 overlaps with the v1.0 ROADMAP.md plan checkboxes -- updates the same file
- PMNT-03 resolves the DOCS-04 and COOK-02 status discrepancies noted in v1.0 traceability

---
*Requirements defined: 2026-03-26*
*Last updated: 2026-03-27 after v1.1 roadmap creation*
