# Haven -- A Learning Garden

## What This Is

A backyard garden project in Vejle, Denmark designed as a developmental tool for a 7-year-old with ADHD and Autism. The garden gives him incrementally increasing agency over something living -- his own raised beds, his own routines, his own harvest decisions -- while producing tangible, edible output from his work. The project includes physical garden infrastructure, structured planting plans, maintenance schedules, data systems for Home Assistant integration, and documentation for family and neighbors.

## Core Value

A child who independently checks on, cares for, and harvests from plants he chose to grow -- and sees the direct connection between his effort and the food on his plate.

## Requirements

### Validated

- ✓ Property-specific raised bed placement recommendations -- v1.0 Phase 1
- ✓ Visualization of property with bed placement -- v1.0 Phase 5
- ✓ Raised bed specifications with soil layer breakdown -- v1.0 Phase 1
- ✓ Shopping/materials list with corten steel and budget alternatives -- v1.0 Phase 1
- ✓ Setup instructions for bed construction and soil filling -- v1.0 Phase 1
- ✓ Denmark-appropriate crop recommendations -- v1.0 Phase 2-3
- ✓ Bed-by-bed planting distribution with companion planting -- v1.0 Phase 2-3
- ✓ Week-by-week maintenance and growth plan -- v1.0 Phase 4
- ✓ Staggered planting schedule for continuous harvest cadence -- v1.0 Phase 4
- ✓ Structured data format for all crops (JSON) -- v1.0 Phase 4
- ✓ Home Assistant sensor recommendations -- v1.0 Phase 4
- ✓ Troubleshooting guide for common problems -- v1.0 Phase 5
- ✓ Difficulty-tiered crop collection -- v1.0 Phase 5
- ✓ Neighbor vacation guide -- v1.0 Phase 5
- ✓ CLAUDE.md project file -- v1.0 Phase 5
- ✓ Property visualization showing bed placement -- v1.0 Phase 5

## Current Milestone: v1.1 Gap Closure and Operational Readiness

**Goal:** Fix cross-reference inconsistencies, add missing child-facing daily routine documentation, complete operational readiness for build day and planting, set up HA integration guide, and prepare end-of-season materials.

**Target features:**
- Resolve bed identity discrepancy (Bed 1-5 vs A-E) across all Phase 1 docs and data files
- Daily routine card and between-session engagement activities for the child
- Spring planting shopping list, purchase priority ordering, and tool inventory
- HA setup walkthrough and basic Lovelace dashboard
- End-of-season cleanup guide, perennial management, soil refresh documentation
- Planning artifact maintenance (ROADMAP checkboxes, PROJECT.md decisions, REQUIREMENTS.md statuses)

### Active

- [ ] Bed identity consistency across all documents and data files
- [ ] Daily garden routine card (printable, child-facing)
- [ ] Between-session engagement activities (W19-W20 bridge)
- [ ] Spring planting shopping list with plant purchases
- [ ] HA setup walkthrough guide
- [ ] End-of-season cleanup documentation
- [ ] Planning artifact accuracy and hygiene

### Out of Scope

- Greenhouse or polytunnel construction -- keeping it to raised beds for v1
- Automated irrigation system -- manual watering is part of the routine/agency goal (self-watering reservoirs OK)
- Indoor growing/seed starting setup -- direct sow or buy seedlings
- Fruit trees -- long-term commitment, consider for v2 after first season success
- Lemon/citrus growing -- not viable outdoors in Danish climate (zone 7b)
- Exotic fruits (pomegranate, passion fruit, kiwi) -- climate incompatible

## Context

### Property
- **Location:** Vejle, Denmark
- **Plot:** ~600 m² total, 
- **Orientation:** House faces west. Backyard extends east/northeast.
- **Key features:** Roof terrace (68 m², tagterrasse) above carport, lawn area in backyard, significant mature tree coverage on east side
- **Deck plan:** 1-2 raised beds on roof terrace, keep majority for seating
- **Climate:** USDA Zone 7b / Danish coastal. Last frost ~mid-April, first frost ~mid-October. Growing season ~180 days.

### The Child
- **Age:** Turning 7 (2026)
- **Diagnoses:** ADHD and Autism
- **Engagement pattern:** Needs quick wins (5-10 min attention bursts). Drawn to creatures/nature, counting/systems, colors/patterns. Sustained engagement through task variety (dig, then water, then pick).
- **Food preferences:** Loves strawberries, raspberries, cucumbers, tomatoes, peppers. Loves edible flowers for decorating baked goods. Does not enjoy (but family cooks with): spring onions, onions, garlic, leeks, broccoli, beans, lettuce, peas.
- **Agency goal:** His own beds, his own daily routine, and he makes planting/harvesting decisions with increasing independence.

### Family Context
- **Gardening experience:** Some basics (herbs, a tomato plant)
- **Daily time:** Varies wildly -- 5 min some days, hour+ on weekends
- **Vacations:** 2-3 weeks mid-summer (peak watering season), plus other 1-2 week trips throughout the year, occasional weekends away
- **Budget:** ~8,500-10,500 DKK total (infrastructure ~7,200-7,900 + spring plants ~520-910 + warm-season plants ~430-625). See shopping lists in docs/ for full breakdown.

### Technical Infrastructure
- **Home Assistant:** Running, being transferred to TuringPi cluster (~/src/turingpi)
- **Protocols:** Zigbee network established, LoRaWAN capable
- **Plan:** Soil moisture/temperature sensors per bed (not immediate, but data format should be ready)
- **Signal:** Will position Zigbee repeaters near garden area

## Constraints

- **Climate:** Danish zone 7b -- limits crop selection, growing season ~April-October
- **Sun exposure:** Significant tree cover on east side may limit full-sun crops in parts of backyard. Roof terrace likely gets best sun exposure (elevated, less tree shadow).
- **Vacation gaps:** 2-3 weeks mid-summer without daily care. Must design for drought tolerance or neighbor maintenance.
- **Child's attention:** 5-10 minute engagement windows. Tasks must be concrete, varied, and produce visible results.
- **Deck weight:** Roof terrace beds must account for structural load (soil + water is heavy). Smaller/shallower beds recommended.
- **Budget:** ~8,500-10,500 DKK total across infrastructure, spring planting, and warm-season purchases. Original estimate of 2,000-5,000 DKK was pre-corten-steel decision. Full breakdown in docs/shopping-list.md, docs/spring-planting-shopping-list.md, and docs/warm-season-shopping-list.md.

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Raised beds over in-ground | Defined ownership ("his bed"), better soil control, accessible height for a 7-year-old | ✓ Good |
| Buy pre-made beds over DIY | Time efficiency, consistent quality. Corten steel aesthetic preferred. | ✓ Good |
| Staggered planting for continuous harvest | Quick wins -- always something ready to pick. Keeps engagement high across the season. | ✓ Good |
| Manual watering over irrigation | Watering IS the routine. It's the daily touchpoint that builds agency. Self-watering reservoirs OK for vacation. | ✓ Good |
| Structured JSON data from day one | Enables Home Assistant integration, future visualizations, alerts. Even if sensors come later. | ✓ Good |
| Include crops he doesn't eat | Family cooks with alliums, greens, legumes. His beds focus on his favorites; family beds round out the garden. | ✓ Good |
| Bed remapping (1-5 → A-E) | Phase 2 reshuffled bed assignments for better companion planting. Phase 1 docs not updated. | ⚠️ Revisit (v1.1 Phase 7) |
| Zinkbakken terrace beds | 80x40x40cm galvanized with capillary insert, replacing byJEMA open-bottom beds for deck protection | ✓ Good |

---
*Last updated: 2026-03-28 after v1.1 milestone start*
