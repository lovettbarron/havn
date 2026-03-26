# Havn -- A Learning Garden

## What This Is

A backyard garden project in Vejle, Denmark designed as a developmental tool for a 7-year-old with ADHD and Autism. The garden gives him incrementally increasing agency over something living -- his own raised beds, his own routines, his own harvest decisions -- while producing tangible, edible output from his work. The project includes physical garden infrastructure, structured planting plans, maintenance schedules, data systems for Home Assistant integration, and documentation for family and neighbors.

## Core Value

A child who independently checks on, cares for, and harvests from plants he chose to grow -- and sees the direct connection between his effort and the food on his plate.

## Requirements

### Validated

(None yet -- ship to validate)

### Active

- [ ] Property-specific raised bed placement recommendations (sun exposure, accessibility, aesthetics)
- [ ] Visualization of property with bed placement
- [ ] Raised bed specifications with soil layer breakdown
- [ ] Shopping/materials list with corten steel and budget alternatives
- [ ] Setup instructions for bed construction and soil filling
- [ ] Denmark-appropriate crop recommendations (fruits, vegetables, herbs, edible flowers)
- [ ] Bed-by-bed planting distribution with companion planting
- [ ] Week-by-week maintenance and growth plan (spring through autumn)
- [ ] Staggered planting schedule for continuous harvest cadence
- [ ] Structured data format for all crops (JSON -- growth stages, water needs, harvest timing, alerts)
- [ ] Home Assistant sensor recommendations (Zigbee/LoRaWAN soil moisture, temperature)
- [ ] Troubleshooting guide for common problems (father-son reference)
- [ ] Difficulty-tiered crop collection (easy wins + stretch challenges)
- [ ] "Help us keep our farm alive" neighbor vacation guide
- [ ] CLAUDE.md project file based on ~/book/vibes patterns
- [ ] Property visualization showing bed placement, sun patterns, and access paths

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
- **Budget:** 2000-5000 DKK for beds, soil, seeds, tools (corten steel preferred but need both price points)

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
- **Budget:** 2000-5000 DKK total. Corten steel beds will push toward upper end or beyond -- need tiered pricing.

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Raised beds over in-ground | Defined ownership ("his bed"), better soil control, accessible height for a 7-year-old | -- Pending |
| Buy pre-made beds over DIY | Time efficiency, consistent quality. Corten steel aesthetic preferred. | -- Pending |
| Staggered planting for continuous harvest | Quick wins -- always something ready to pick. Keeps engagement high across the season. | -- Pending |
| Manual watering over irrigation | Watering IS the routine. It's the daily touchpoint that builds agency. Self-watering reservoirs OK for vacation. | -- Pending |
| Structured JSON data from day one | Enables Home Assistant integration, future visualizations, alerts. Even if sensors come later. | -- Pending |
| Include crops he doesn't eat | Family cooks with alliums, greens, legumes. His beds focus on his favorites; family beds round out the garden. | -- Pending |

---
*Last updated: 2026-03-26 after initialization*
