# Phase 4: Data System and Schedules - Context

**Gathered:** 2026-03-26
**Status:** Ready for planning

<domain>
## Phase Boundary

Build a structured JSON data system covering every planted crop, weekly schedules from W15 through W44, a staggered planting/succession calendar, and Home Assistant entity schemas with sensor recommendations. JSON is the canonical data source; HA YAML configs are derived outputs. No dashboards, automations, or notifications -- those are v2 implementation work.

</domain>

<decisions>
## Implementation Decisions

### Crop JSON structure
- One JSON file per crop species (e.g., strawberry-ostara.json, radish.json, thyme.json)
- Bed placement lives in separate bed JSON files (bed-a.json references crops)
- Week-level growth stages with named phases, week ranges, "look_for" observations, and child actions per stage
- Child actions and difficulty tiers embedded inside each crop file (not separate reference files)
- Engagement metadata per crop: action type, frequency, estimated attention minutes
- Alert thresholds included: soil moisture min/max %, temperature range, frost sensitivity, drought alert days
- Water needs include both human-readable frequency AND numeric thresholds for HA

### Weekly schedule format
- One JSON file per ISO week (W15 through W44) in data/schedules/
- Themed week names for the child (e.g., "Strawberry Watch Week", "First Sprouts Week") with tagline and hero task
- Tasks structured with: priority (must_do / nice_to_do), who (child / father / together), estimated minutes, frequency (daily / once / weekly)
- Growth events section per week with child-friendly prompts ("Can you find the curly bits grabbing the wire?")
- Hero task highlighted at the top of each week

### Succession and staggered planting
- Master succession-calendar.json shows full season sowing/harvest timeline with gap analysis
- Weekly schedule files also include specific "sow X this week" tasks -- calendar is the reference, weekly files are the action
- Must ensure no 2-week harvest gap from late May through October

### Home Assistant schema
- JSON is the source of truth; HA YAML is generated/derived from JSON
- Split by concern: sensors.json, plants.json, customize.json -- each generates its own YAML output
- Per-bed sensors (not per-crop): havn_bed_a_moisture, havn_bed_a_temperature, etc.
- Plant Monitor configs map crop thresholds to bed sensors
- Alert rules included in JSON: trigger type, delay hours, message template, notification target
- Bilingual alert messages with i18n keys (da + en) for all notification text
- Thresholds AND automation-ready alert rule definitions included (ready for v2 without schema redesign)

### Sensor hardware recommendations
- Budget target: under 200 DKK per sensor (~500-1000 DKK total for 5 beds)
- Zigbee-first with LoRaWAN as fallback only if Zigbee range is insufficient
- Top 2-3 Zigbee soil sensor picks with specific models, DKK prices, and confirmed Zigbee2MQTT compatibility
- 1 LoRaWAN fallback option documented
- Include one outdoor-rated Zigbee repeater recommendation for garden area coverage
- Clear "buy this one" primary recommendation

### Claude's Discretion
- Exact JSON schema field names and nesting structure
- Growth stage names and week assignments per crop (based on Danish zone 7b timelines)
- Themed week name choices (fun, child-appropriate, tied to what's happening that week)
- Succession calendar gap analysis methodology
- Specific sensor model selections within the decided criteria
- File organization within data/ directory

</decisions>

<specifics>
## Specific Ideas

- JSON as canonical source of truth for the entire project -- HA YAML is derived, and future helper applications and projects will also consume this data
- Growth events written for a 7-year-old: discovery-oriented prompts, not botanical facts ("Gently brush the soil -- see the pink top?" not "radish bulb diameter 2cm")
- Child actions should reflect the engagement pattern from PROJECT.md: 5-10 min bursts, variety (dig/water/pick/smell/count), concrete visible results
- Difficulty tiers match Phase 5 doc requirement (DOCS-03): "can't fail" / "needs care" / "Year 2 challenge" -- Phase 5 doc can be auto-generated from crop JSON
- Alert messages in both Danish and English to support bilingual use and sharing

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Planting grid maps (docs/planting-grid-bed-{a-e}.md): contain exact cm positions, plant shortcodes, companion planting notes -- source data for bed JSON files
- Phase 2 context (02-CONTEXT.md): bed assignments (A=his bed, B=raspberry, C=shared, D/E=terrace), crop-to-bed mapping

### Established Patterns
- Documentation project producing markdown deliverables in docs/
- No existing JSON or code files -- Phase 4 establishes the data layer pattern
- Planting grids use shortcodes (THY, VIO, CAL, ST-O, ST-K, LAM, LE) -- crop JSON should cross-reference these

### Integration Points
- Crop JSON feeds Phase 5 (difficulty tiers doc can auto-generate from crop data)
- Weekly schedules feed Phase 6 (vacation weeks need special handling)
- HA sensor schemas feed v2 IoT expansion (IOT-V2-01 through IOT-V2-05)
- Bed JSON files connect to existing planting grid maps (same bed naming A-E)
- Succession calendar validates the "no 2-week harvest gap" requirement across the full season

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 04-data-system-and-schedules*
*Context gathered: 2026-03-26*
