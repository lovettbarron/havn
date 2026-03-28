# Project Research Summary

**Project:** Haven -- A Learning Garden
**Domain:** Physical garden infrastructure + IoT sensor integration for child with ADHD/Autism
**Researched:** 2026-03-26
**Confidence:** MEDIUM-HIGH

## Executive Summary

Haven is a backyard learning garden in Vejle, Denmark (zone 7b) designed around a 7-year-old with ADHD and Autism. The project spans physical infrastructure (corten/galvanized steel raised beds, soil systems), crop planning (engagement-optimized for neurodivergent child), structured data (JSON schemas for crops, schedules, troubleshooting), and Home Assistant IoT integration (Zigbee soil sensors, automated alerts, dashboards). Experts in this domain emphasize that the garden must be built around the child's engagement patterns, not around horticultural efficiency. The single most important design constraint is continuous harvest events -- the child needs to pick something every visit from late May through October, or interest dies.

The recommended approach is to prioritize physical beds and planting above all else, given that it is late March and the growing season clock is ticking. Beds must be ordered immediately (week 13), placed and filled by week 15, and first cold-hardy crops in the ground by week 16. Data architecture and IoT sensors are explicitly secondary -- the JSON schemas and HA configuration can be developed in parallel or after planting. Sensors should be deferred to season two as a "level up" moment. The budget reality is that the premium path (corten beds + soil + sensors + tools) exceeds the 5,000 DKK ceiling at 6,500-8,000 DKK. A hybrid approach using corten for visible backyard beds and galvanized steel for the terrace bed, with sensors deferred, lands at approximately 6,200-6,750 DKK.

The critical risks are: (1) the child loses interest in the first two weeks if nothing visible happens (buy seedlings, do not rely on seeds), (2) the 2-3 week summer vacation kills tomato and cucumber beds without self-watering reservoirs and a neighbor care plan, (3) the 1932 roof terrace may not support the weight of wet soil without structural assessment, and (4) Danish slug invasion destroys seedlings overnight without copper tape defenses on bed edges. Each of these is preventable with upfront planning but catastrophic if ignored.

## Key Findings

### Recommended Stack

Corten steel raised beds from Danish manufacturers (byJEMA, Gronfeld) form the durable backbone -- 20+ year lifespan, food-safe, aesthetically suited to an oldervilla. Soil is a purchased big bag of hojbedsmuld (1,000L from Grat.dk or HaveHandel.dk, ~1,200 DKK delivered free to Jutland) layered over free garden waste. Zigbee 3.0 soil sensors (Haozee recommended, IP66, confirmed winner of HA community shootout) connect through the family's existing Zigbee network to Home Assistant via Zigbee2MQTT. OpenPlantbook provides species threshold data. A custom JSON schema per crop structures all garden data.

**Core technologies:**
- **Corten steel raised beds (byJEMA CUBY):** 2mm bent corten, Danish-made, 150x80x40cm for backyard -- durable, child-height, food-safe
- **Zigbee soil sensors (Haozee):** IP66, Zigbee 3.0, accurate readings confirmed by HA community testing -- months of battery life vs days for WiFi
- **Home Assistant + Zigbee2MQTT + Plant Monitor:** Existing family infrastructure, no new platforms needed -- alerts in Danish, Lovelace dashboard
- **Custom JSON schema + OpenPlantbook:** No dominant open standard exists; project-specific schema with child-facing fields (growth stages, child actions, difficulty tiers)
- **Hojbedsmuld bulk soil:** Big bag delivery eliminates per-bag markup, Danish sifted gravel pit soil + organic mushroom compost

### Expected Features

**Must have (table stakes):**
- Strawberries (everbearing + June-bearing) -- anchor engagement crop, continuous picking June-September
- Cherry tomatoes (Sungold) -- the daily "is it ripe?" ritual, highest engagement crop
- Radishes (succession sown every 2 weeks) -- 3-week seed-to-harvest, the quick-win engine
- Nasturtiums -- edible flowers for his baking interest, zero maintenance, drought-proof
- Herb pot (mint, chives, thyme) -- perennial sensory engagement, snip-and-smell activity
- Self-watering reservoir in tomato/cucumber beds -- vacation survival for high-water crops
- Neighbor vacation guide -- actual deliverable, not an afterthought

**Should have (differentiators for this child):**
- Edible flowers for baking decoration (calendula, borage, viola) -- his specific request
- Sensory crops (lamb's ear for touch, lemon balm for smell) -- multi-sensory ADHD engagement
- Creature-attracting plants (borage for bees, dill for ladybugs) -- leverages his interest in living things
- Companion planting combinations per bed -- validated groupings that double as teaching moments
- Raspberry (Autumn Bliss) -- fills August-October gap when strawberry peak fades
- Visual checklist (pictures, not text) at bed height -- 3-step max routine for ADHD working memory

**Defer (v2+):**
- Zigbee soil sensors and HA dashboard -- garden works manually in season one
- Broccoli, leeks, carrots, fennel -- Tier 3 difficulty, low engagement for first season
- Seed saving, exotic varieties -- year 2 experiments
- LoRaWAN sensors -- only if Zigbee range proves insufficient (unlikely)

### Architecture Approach

The architecture has two distinct halves: physical and data. Physically, the garden comprises 5 beds across 2 zones -- 3 ground-level backyard beds (120x60x40cm, child-ergonomic width) positioned in the west-central backyard for 8-10 hours of summer sun, and 2 shallow terrace beds (80x40x30cm, lightweight soil) on the elevated roof terrace with best sun exposure but wind and weight constraints. The data system uses one JSON file per crop, one JSON file per ISO week for scheduling, plus structured troubleshooting and vacation guide schemas. Home Assistant entities follow a `haven_` prefix convention with per-bed sensor entities, plant monitor configurations with moisture/temperature thresholds, and Danish-language automations.

**Major components:**
1. **Physical beds (5 total)** -- 3 backyard (Sol-bedet, Baer-bedet, Eventyr-bedet) + 2 terrace (Terasse-krydder, Terasse-baer), each with named purposes and companion planting layouts
2. **Crop data system** -- JSON schema per crop with planting info, care requirements, growth stages with child-friendly actions, harvest instructions, companion relationships, and alert triggers
3. **Weekly schedule system** -- One JSON file per ISO week with themed names, prioritized tasks (must-do/should-do/fun-bonus), expected growth events, and weather alerts
4. **Home Assistant integration** -- Zigbee2MQTT sensor ingestion, Plant Monitor per-bed health status, automated watering reminders and frost warnings in Danish, Lovelace dashboard with Mushroom cards
5. **Vacation system** -- Structured neighbor guide generated from current schedule week, with per-bed watering frequency and harvest instructions

### Critical Pitfalls

1. **ADHD waiting game (PROJECT KILLER)** -- Child plants seeds, sees dirt for 10 days, quits permanently. Prevention: buy seedlings for main crops, reserve seeds only for fast-germinators (radish 3-5 days, sunflower 5-7 days). Always have something already growing when introducing a new planting activity.
2. **Sensory landmines (PROJECT KILLER)** -- One slug encounter or slimy texture causes garden aversion. Prevention: gardening gloves as standard "gear," pre-check beds for slugs before child sessions, hand-washing station at garden, remove rotting produce before child sees it.
3. **Vacation gap kills crops (PROJECT KILLER)** -- Raised beds in full sun dry out in 2-3 days. Tomatoes and cucumbers die during 2-3 week July absence. Prevention: self-watering reservoirs designed into tomato/cucumber beds from construction, thick mulch, neighbor guide as actual project deliverable.
4. **Danish slug apocalypse (HIGH)** -- Spanish slugs eat all seedlings overnight. Beer traps and eggshells do not work (Aarhus University research). Prevention: copper tape on all bed edges, 40cm smooth-sided metal beds, evening slug patrol as a game.
5. **Roof terrace structural overload (SAFETY CRITICAL)** -- Wet soil at 1,200 kg/m3 on an oldercarport roof. Prevention: structural assessment mandatory before any terrace beds, shallow beds (max 20-25cm), lightweight soil mix with perlite, beds positioned over structural supports only.

## Implications for Roadmap

Based on research, suggested phase structure:

### Phase 1: Bed Infrastructure and First Planting (W13-W16)
**Rationale:** The growing season is the hard constraint. Last frost is mid-April. Every week of delay means missed planting windows for cold-hardy crops. Physical infrastructure must come first.
**Delivers:** 3 backyard beds ordered, placed, and filled with soil. First cold-hardy crops planted (radish, pea, lettuce, spring onion). Perennials in ground (strawberry, chives, thyme). Terrace structural assessment initiated.
**Addresses:** Table stakes crops, bed construction, soil layering
**Avoids:** Over-engineering data before planting (anti-pattern), planting too early (hard May 1 rule for tender crops), all-seed approach killing engagement

### Phase 2: Warm Season Planting and Companion Setup (W17-W20)
**Rationale:** After last frost, warm-season favorites go in. This is when the child's most-anticipated crops (tomatoes, peppers, cucumbers) get planted alongside companion plants and edible flowers.
**Delivers:** Seedlings transplanted (tomato, pepper, cucumber, basil). Edible flowers direct-sown (nasturtium, calendula, borage). Succession sowing engine started. Terrace beds placed (if structural assessment passes) with herbs and alpine strawberries.
**Addresses:** Differentiator crops (sensory, creature-attracting, edible flowers), companion planting layouts
**Avoids:** Wrong crops for Danish outdoor growing (use cold-tolerant varieties), overcrowding beds (max 2-3 species per small bed)

### Phase 3: Data System and Schedule (W14-W20, parallel)
**Rationale:** JSON schemas and crop data files can be built while waiting for bed delivery and between planting sessions. This is desk work that does not block the growing season.
**Delivers:** Crop JSON schema finalized, individual crop data files for all planted crops, weekly schedule files for W15-W25, troubleshooting guide entries for common issues.
**Uses:** Custom JSON schema, OpenPlantbook for thresholds, one-file-per-crop and one-file-per-week patterns
**Implements:** Crop data system, weekly schedule system, troubleshooting guide format

### Phase 4: Vacation Preparation (W22-W26)
**Rationale:** Summer vacation is the existential threat to the garden. Self-watering reservoirs, mulching, and the neighbor guide must be complete before departure (typically late July).
**Delivers:** Self-watering reservoirs installed in tomato/cucumber beds, all beds mulched (5-8cm straw), neighbor vacation guide generated from schedule data, harvest-everything-ripe protocol executed before departure.
**Addresses:** Vacation survival feature
**Avoids:** Vacation gap killing crops, no watering plan existing by mid-June

### Phase 5: IoT and Home Assistant Integration (W20+ or Season 2)
**Rationale:** Sensors are explicitly "not immediate" per project scope. The garden works fine with manual observation. Deferring sensors to after first harvest season means the data format is proven and the child experiences a "level up" when the garden gets its digital brain.
**Delivers:** 3x Haozee Zigbee soil sensors installed (one per backyard bed), Zigbee2MQTT configured, Plant Monitor entities with per-crop thresholds, automated watering reminders in Danish, Lovelace dashboard with Mushroom cards.
**Uses:** Zigbee sensors, Zigbee2MQTT, HA Plant Monitor, OpenPlantbook
**Implements:** HA entity structure, automation rules, dashboard

### Phase 6: Season Review and Year 2 Planning (W40-W44)
**Rationale:** First season data (what grew, what failed, what engaged the child) informs year 2 expansion. This is when Tier 3 crops, exotic varieties, and advanced companion planting get considered.
**Delivers:** Season retrospective, crop performance notes, year 2 crop list, budget for any deferred purchases (sensors if not done in Phase 5).

### Phase Ordering Rationale

- Physical infrastructure before data systems because the growing season has a hard deadline and data does not
- Cold-hardy planting before warm-season planting because frost dates dictate the sequence
- Data work runs in parallel with physical work because it is independent desk work
- Vacation prep has its own phase because it is time-critical (must be done before departure) and involves physical work (reservoirs, mulching) plus documentation (neighbor guide)
- IoT is last because the project explicitly says sensors are not immediate, and manual observation teaches the child more in season one
- Season review is a reflection phase that feeds into iterative improvement

### Research Flags

Phases likely needing deeper research during planning:
- **Phase 1 (Bed Infrastructure):** Terrace structural assessment requires professional input -- research cannot resolve load-bearing capacity of an oldercarport roof
- **Phase 4 (Vacation Prep):** Self-watering reservoir design for corten steel beds needs specific DIY plans or product research (SIP inserts vs wicking systems)
- **Phase 5 (IoT):** HA template entity deprecation in 2025.12 (removed 2026.6) means configuration must use newer format -- verify current HA version

Phases with standard patterns (skip research-phase):
- **Phase 2 (Warm Planting):** Crop selection and companion planting are well-documented with verified variety recommendations
- **Phase 3 (Data System):** JSON schema design and file structure are fully specified in ARCHITECTURE.md
- **Phase 6 (Season Review):** Retrospective, no technical research needed

## Confidence Assessment

| Area | Confidence | Notes |
|------|------------|-------|
| Stack | MEDIUM-HIGH | Bed suppliers and prices verified against Danish retailer websites. Sensor compatibility confirmed via HA community testing. Soil products verified with composition details. |
| Features | MEDIUM-HIGH | Crop viability in zone 7b confirmed by multiple sources. Days-to-harvest may be 10-20% longer in cool Danish summer vs US seed company data. ADHD/Autism engagement strategies based on therapeutic garden literature, needs real-world validation. |
| Architecture | MEDIUM-HIGH | Sun path calculations formula-derived from known latitude. Child ergonomic dimensions from extension service sources. HA entity conventions from official docs. Bed placement based on property description, not surveyed on-site. |
| Pitfalls | HIGH | All critical pitfalls sourced from domain experts, university research (Aarhus slug study), structural engineering principles, and ADHD/Autism therapeutic literature. Prevention strategies are concrete and actionable. |

**Overall confidence:** MEDIUM-HIGH

### Gaps to Address

- **Terrace structural capacity:** Cannot be resolved by research alone. Requires professional assessment of the older carport roof before placing any beds. If assessment fails, terrace beds move to ground level or become windowsill herb pots.
- **Local seedling availability:** Specific varieties (Sungold, Mini Munch, Lipstick, King of the North) may not be stocked at Vejle-area nurseries in May. Plan substitutions: any cherry tomato, any mini cucumber, any sweet pepper. The variety is less important than having the crop.
- **Actual sun exposure:** Shadow calculations use estimated building/tree heights. On-site observation over 1-2 sunny days in April should confirm bed placement before permanent installation.
- **Child's actual sensory profile:** Therapeutic garden literature provides general guidance. The specific triggers for this child will only emerge through real interaction. Build in flexibility to relocate "pungent" plants away from his primary zone.
- **Budget overshoot:** Hybrid approach at 6,200-6,750 DKK exceeds the 5,000 DKK ceiling. Either accept the overshoot as an investment in 20-year infrastructure, or downgrade all beds to galvanized steel (3,450 DKK for beds, ~4,800-5,900 total).

## Sources

### Primary (HIGH confidence)
- [HA Community Zigbee soil sensor shootout](https://community.home-assistant.io/t/my-zigbee-soil-moisture-sensor-shootout/907192) -- sensor accuracy and reliability comparison
- [Home Assistant Plant Monitor integration](https://www.home-assistant.io/integrations/plant/) -- entity configuration and thresholds
- [TimeAndDate.com Vejle sun data](https://www.timeanddate.com/sun/denmark/vejle) -- sunrise/sunset for shadow calculations
- [Garden.org Copenhagen planting calendar](https://garden.org/apps/calendar/?q=copenhagen) -- frost dates and planting windows
- [Science Nordic: Spanish slug research (Aarhus University)](https://www.sciencenordic.com/denmark-gardening-slugs/only-one-way-to-get-rid-of-spanish-slugs/1420123) -- slug control evidence

### Secondary (MEDIUM confidence)
- [byJEMA](https://byjema.dk), [Gronfeld](https://gronfeld.com), [Zinkbakken](https://zinkbakken.dk) -- Danish bed supplier pricing (may vary by configuration)
- [Grat.dk](https://grat.dk), [HaveHandel.dk](https://havehandel.dk) -- Soil product pricing and composition
- [Frosnapperen](https://froesnapperen.dk), [Frobutikken](https://froebutikken.dk) -- Danish seed supplier availability
- [KidsGardening](https://kidsgardening.org), [Thrive](https://www.thrive.org.uk) -- ADHD/Autism garden design principles
- [Old Farmer's Almanac](https://www.almanac.com/companion-planting-guide-vegetables) -- Companion planting relationships

### Tertiary (LOW confidence)
- Variety-specific days-to-harvest from US seed companies -- may be 10-20% longer in Danish conditions
- Roof terrace load capacity -- estimated, requires professional assessment
- Child's specific sensory triggers -- inferred from general ADHD/Autism literature, needs real-world validation

---
*Research completed: 2026-03-26*
*Ready for roadmap: yes*
