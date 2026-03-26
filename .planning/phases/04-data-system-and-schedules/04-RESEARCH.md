# Phase 4: Data System and Schedules - Research

**Researched:** 2026-03-26
**Domain:** JSON data architecture, Home Assistant integration schemas, Zigbee sensor hardware
**Confidence:** HIGH

## Summary

Phase 4 establishes the canonical JSON data layer for the entire Havn project. This is a documentation/data project, not a software project -- the deliverables are JSON files that describe crops, weekly schedules, succession calendars, and Home Assistant entity schemas. The technical complexity lies in schema design that serves multiple consumers (human reading, HA Plant Monitor integration, future IoT automations, and Phase 5 doc generation) while remaining maintainable by hand.

The crop database covers approximately 25 distinct plant species across 5 beds (A-E), each requiring growth stage timelines calibrated to Danish zone 7b conditions (Vejle area, ~55.7N). Weekly schedules span W15-W44 (30 weeks), each with themed names, prioritized tasks, and child-friendly growth event prompts. The Home Assistant schemas must follow the official Plant Monitor integration format with per-bed sensors using the `havn_` prefix convention.

**Primary recommendation:** Design one JSON schema per concern (crop, bed, week, succession-calendar, HA sensors, HA plants), keep files flat and human-readable, and use `$ref` cross-references by filename rather than deep nesting. The Haozee Zigbee soil sensor is the clear hardware recommendation based on community testing.

<user_constraints>
## User Constraints (from CONTEXT.md)

### Locked Decisions
- One JSON file per crop species (e.g., strawberry-ostara.json, radish.json, thyme.json)
- Bed placement lives in separate bed JSON files (bed-a.json references crops)
- Week-level growth stages with named phases, week ranges, "look_for" observations, and child actions per stage
- Child actions and difficulty tiers embedded inside each crop file (not separate reference files)
- Engagement metadata per crop: action type, frequency, estimated attention minutes
- Alert thresholds included: soil moisture min/max %, temperature range, frost sensitivity, drought alert days
- Water needs include both human-readable frequency AND numeric thresholds for HA
- One JSON file per ISO week (W15 through W44) in data/schedules/
- Themed week names for the child with tagline and hero task
- Tasks structured with: priority (must_do / nice_to_do), who (child / father / together), estimated minutes, frequency
- Growth events section per week with child-friendly prompts
- Master succession-calendar.json shows full season sowing/harvest timeline with gap analysis
- JSON is the source of truth; HA YAML is generated/derived from JSON
- Split by concern: sensors.json, plants.json, customize.json -- each generates its own YAML output
- Per-bed sensors (not per-crop): havn_bed_a_moisture, havn_bed_a_temperature, etc.
- Plant Monitor configs map crop thresholds to bed sensors
- Alert rules included in JSON: trigger type, delay hours, message template, notification target
- Bilingual alert messages with i18n keys (da + en) for all notification text
- Budget target: under 200 DKK per sensor (~500-1000 DKK total for 5 beds)
- Zigbee-first with LoRaWAN as fallback only if Zigbee range is insufficient
- Top 2-3 Zigbee soil sensor picks with specific models, DKK prices, and confirmed Zigbee2MQTT compatibility
- 1 LoRaWAN fallback option documented
- Include one outdoor-rated Zigbee repeater recommendation
- Clear "buy this one" primary recommendation

### Claude's Discretion
- Exact JSON schema field names and nesting structure
- Growth stage names and week assignments per crop (based on Danish zone 7b timelines)
- Themed week name choices (fun, child-appropriate, tied to what's happening that week)
- Succession calendar gap analysis methodology
- Specific sensor model selections within the decided criteria
- File organization within data/ directory

### Deferred Ideas (OUT OF SCOPE)
None -- discussion stayed within phase scope
</user_constraints>

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| DATA-01 | JSON schema for crop database (growth stages, water needs, harvest timing, companion plants, difficulty tier, child actions, alert triggers) | Schema pattern with field inventory documented below; JSON Schema Draft 2020-12 recommended for formal validation |
| DATA-02 | Individual JSON crop files for every planted crop with all schema fields populated | Complete plant inventory (25+ species) derived from existing planting grids; growth timelines for Danish zone 7b researched |
| DATA-03 | Weekly schedule JSON files (one per ISO week) with themed names, prioritized tasks, expected growth events | 30-week span (W15-W44) with task structure, themed naming approach, and growth event prompt patterns documented |
| DATA-04 | Home Assistant entity schema following havn_ prefix convention with per-bed sensor entities | HA entity naming conventions researched; template sensor YAML format documented |
| DATA-05 | Home Assistant Plant Monitor configuration with moisture/temperature thresholds per crop | Official Plant Monitor integration YAML format verified (active integration, ~1971 installations); threshold fields documented |
| DATA-06 | Zigbee/LoRaWAN sensor recommendations with specific models, prices, and HA compatibility confirmation | Sensor shootout data analyzed; Haozee wins; ThirdReality and Dragino LSE01 as alternatives; pricing researched |
| SCHED-02 | Staggered planting schedule ensuring continuous harvest from late May through October | Succession methodology documented; gap analysis approach using harvest-window overlap verification |
| SCHED-03 | Week-by-week maintenance plan from W14 through W44 | Weekly schedule JSON format covers this; task taxonomy (must_do/nice_to_do, who, minutes) defined |
| SCHED-04 | Succession sowing calendar for radish, lettuce, beans, spring onion, and peas | Succession intervals researched per crop; integrated into succession-calendar.json design |
</phase_requirements>

## Standard Stack

### Core
| Library/Tool | Version | Purpose | Why Standard |
|-------------|---------|---------|--------------|
| JSON Schema | Draft 2020-12 | Formal schema validation for crop and schedule files | Latest stable draft; supports `prefixItems`, `$ref`, `unevaluatedProperties` |
| Plain JSON files | N/A | All data storage | Human-readable, version-controllable, no database needed for a documentation project |

### Supporting
| Tool | Purpose | When to Use |
|------|---------|-------------|
| `ajv` (Node.js) or `jsonschema` (Python) | Optional: validate JSON files against schema | Only if automated validation is desired; not required for v1 |
| `jq` | Command-line JSON querying | Gap analysis on succession calendar, quick data checks |

### Alternatives Considered
| Instead of | Could Use | Tradeoff |
|------------|-----------|----------|
| JSON files | SQLite database | Overkill for ~30 crop files + ~30 schedule files; harder to version control |
| JSON Schema | TypeScript interfaces | Schema is language-agnostic, works with any consumer; TS ties to Node ecosystem |
| Hand-authored JSON | YAML source + JSON build | YAML is easier to type but adds a build step; JSON is the canonical format per user decision |

## Architecture Patterns

### Recommended Project Structure
```
data/
  crops/                     # One file per crop species
    strawberry-ostara.json
    strawberry-korona.json
    raspberry-autumn-bliss.json
    radish.json
    pea-kelvedon-wonder.json
    kale-nero-di-toscana.json
    lettuce-baby-mix.json
    spring-onion-white-lisbon.json
    thyme.json
    lemon-balm.json
    lambs-ear.json
    viola.json
    calendula.json
    borage.json
    pea-shoots.json
    chives.json
    sunflower.json           # Phase 3 (ENGM-01)
    nasturtium.json          # Phase 3 (FLWR-01)
    cherry-tomato-sungold.json
    cherry-tomato-tumbling-tom.json
    cucumber-mini-munch.json
    sweet-pepper-lipstick.json
    mint.json
    basil.json
    bush-bean-provider.json
    broccoli-calabrese.json
    leek-musselburgh.json
  beds/                      # One file per bed
    bed-a.json
    bed-b.json
    bed-c.json
    bed-d.json
    bed-e.json
  schedules/                 # One file per ISO week
    w15.json
    w16.json
    ...
    w44.json
  succession-calendar.json   # Master sowing/harvest timeline
  ha/                        # Home Assistant schemas
    sensors.json
    plants.json
    customize.json
    alert-rules.json
  sensors/                   # Hardware recommendations
    sensor-recommendations.md
  schemas/                   # Optional: formal JSON schemas
    crop.schema.json
    bed.schema.json
    week.schema.json
```

### Pattern 1: Crop JSON Structure
**What:** Each crop file contains all information about one species/variety
**When to use:** Every planted crop gets one file

```json
{
  "$schema": "../schemas/crop.schema.json",
  "id": "strawberry-ostara",
  "name": {
    "common": "Strawberry Ostara",
    "botanical": "Fragaria x ananassa 'Ostara'",
    "da": "Jordbær Ostara",
    "shortcode": "ST-O"
  },
  "type": "fruit",
  "difficulty": {
    "tier": "cant_fail",
    "label": { "en": "Can't Fail", "da": "Kan ikke fejle" },
    "reason": "Perennial, tolerates neglect, produces fruit with minimal care"
  },
  "growth_stages": [
    {
      "name": "Dormant",
      "weeks": { "start": 1, "end": 14 },
      "look_for": "Brown/dry leaves from winter, small green buds at crown",
      "child_actions": []
    },
    {
      "name": "Spring Growth",
      "weeks": { "start": 15, "end": 18 },
      "look_for": "Fresh green leaves uncurling from the center",
      "child_actions": [
        {
          "action": "Remove dead leaves",
          "type": "tend",
          "who": "together",
          "minutes": 5,
          "frequency": "once",
          "prompt": { "en": "Can you find the brown crunchy leaves? Pull them off gently!", "da": "Kan du finde de brune blade? Træk dem forsigtigt af!" }
        }
      ]
    },
    {
      "name": "Flowering",
      "weeks": { "start": 19, "end": 22 },
      "look_for": "White flowers with yellow centers",
      "child_actions": [
        {
          "action": "Count flowers",
          "type": "observe",
          "who": "child",
          "minutes": 3,
          "frequency": "weekly",
          "prompt": { "en": "How many white flowers can you count today?", "da": "Hvor mange hvide blomster kan du tælle i dag?" }
        }
      ]
    },
    {
      "name": "Fruiting",
      "weeks": { "start": 23, "end": 38 },
      "look_for": "Green berries turning white, then red",
      "child_actions": [
        {
          "action": "Pick ripe berries",
          "type": "harvest",
          "who": "child",
          "minutes": 5,
          "frequency": "daily",
          "prompt": { "en": "Only pick the RED ones -- leave the white ones for tomorrow!", "da": "Pluk kun de RØDE -- lad de hvide sidde til i morgen!" }
        }
      ]
    },
    {
      "name": "Runner Production",
      "weeks": { "start": 30, "end": 40 },
      "look_for": "Long thin stems reaching out from the plant with baby plants at the end",
      "child_actions": [
        {
          "action": "Spot runners",
          "type": "observe",
          "who": "child",
          "minutes": 3,
          "frequency": "weekly",
          "prompt": { "en": "See the baby plants on strings? Those are runners -- the plant is making babies!", "da": "Ser du de små planter på snore? Det er udløbere -- planten laver babyer!" }
        }
      ]
    }
  ],
  "water_needs": {
    "human_readable": { "en": "Keep soil moist, not soggy. Water every 2-3 days in summer.", "da": "Hold jorden fugtig, ikke gennemblødt. Vand hver 2-3 dag om sommeren." },
    "thresholds": {
      "soil_moisture_min": 30,
      "soil_moisture_max": 70,
      "drought_alert_days": 3
    }
  },
  "temperature": {
    "optimal_min": 15,
    "optimal_max": 25,
    "frost_sensitive": true,
    "frost_threshold": -2,
    "heat_stress": 30
  },
  "harvest": {
    "first_harvest_week": 23,
    "last_harvest_week": 38,
    "days_to_maturity": null,
    "continuous": true,
    "notes": "Everbearing: produces from June through September with peaks in early summer and early autumn"
  },
  "companion_plants": {
    "good": ["thyme", "calendula", "borage", "viola"],
    "bad": ["raspberry-autumn-bliss"],
    "notes": "Thyme deters slugs; calendula repels aphids. Keep away from raspberries (verticillium wilt)."
  },
  "engagement": {
    "action_types": ["harvest", "observe", "tend"],
    "peak_engagement_weeks": { "start": 23, "end": 35 },
    "attention_minutes_per_week": 10,
    "sensory": ["taste", "smell", "touch"]
  },
  "beds": ["bed-a"],
  "sowing": {
    "method": "plug",
    "indoor_start": null,
    "outdoor_sow": null,
    "transplant_week": 16,
    "succession": false
  }
}
```

### Pattern 2: Bed JSON Structure
**What:** Maps physical bed to its crop placements, referencing crop files by ID
**When to use:** Each of the 5 beds (A-E)

```json
{
  "id": "bed-a",
  "name": "His Bed",
  "physical": {
    "position": "Bed 3, backyard east",
    "dimensions": { "length_cm": 120, "width_cm": 60, "height_cm": 40 },
    "material": "corten_steel",
    "features": [],
    "orientation": "N-S"
  },
  "crops": [
    {
      "crop_id": "strawberry-ostara",
      "shortcode": "ST-O",
      "positions": [
        { "center_w": 25, "center_l": 30, "spread_cm": 30 },
        { "center_w": 25, "center_l": 70, "spread_cm": 30 }
      ],
      "planted_week": 16
    }
  ],
  "succession_slots": [
    {
      "id": "S1",
      "area": { "w_start": 40, "w_end": 60, "l_start": 30, "l_end": 50 },
      "crop_id": "radish",
      "first_sow_week": 18,
      "interval_weeks": 2
    }
  ],
  "ha_sensors": {
    "moisture": "sensor.havn_bed_a_moisture",
    "temperature": "sensor.havn_bed_a_temperature"
  }
}
```

### Pattern 3: Weekly Schedule JSON Structure
**What:** One file per ISO week with themed name, tasks, and growth events
**When to use:** W15 through W44

```json
{
  "week": 16,
  "iso_week": "2026-W16",
  "date_range": { "start": "2026-04-13", "end": "2026-04-19" },
  "theme": {
    "name": { "en": "Planting Day Week", "da": "Plantedags Uge" },
    "tagline": { "en": "Our farm begins TODAY!", "da": "Vores gård starter I DAG!" },
    "hero_task": "Plant strawberries in His Bed"
  },
  "tasks": [
    {
      "id": "W16-01",
      "action": "Plant strawberry plugs in Bed A",
      "priority": "must_do",
      "who": "together",
      "minutes": 15,
      "frequency": "once",
      "bed": "bed-a",
      "crop_id": "strawberry-ostara",
      "prompt": { "en": "Dig a hole, place the crown at soil level, press soil around it. He places each plug!", "da": "Grav et hul, placer kronen i jordniveau, tryk jorden fast. Han sætter hver plante!" }
    },
    {
      "id": "W16-02",
      "action": "Sow pea seeds along trellis in Bed C",
      "priority": "must_do",
      "who": "together",
      "minutes": 10,
      "frequency": "once",
      "bed": "bed-c",
      "crop_id": "pea-kelvedon-wonder",
      "prompt": { "en": "Push each big seed into the hole -- he can do this one alone!", "da": "Tryk hvert stort frø ned i hullet -- det kan han selv!" }
    }
  ],
  "growth_events": [
    {
      "crop_id": "viola",
      "event": "Violas already blooming from nursery seedlings",
      "prompt": { "en": "The purple flowers are already open! Can you smell them?", "da": "De lilla blomster er allerede åbne! Kan du lugte dem?" }
    }
  ],
  "sowing_tasks": [
    {
      "crop_id": "pea-shoots",
      "bed": "bed-a",
      "slot": "S2",
      "action": "Dense-sow pea shoots in north end of Bed A"
    }
  ]
}
```

### Pattern 4: Succession Calendar
**What:** Master timeline showing all sowing and harvest windows with gap analysis
**When to use:** Single file: `succession-calendar.json`

```json
{
  "season": "2026",
  "zone": "7b",
  "location": "Vejle, Denmark",
  "frost_dates": {
    "last_spring_frost": "2026-05-10",
    "first_autumn_frost": "2026-10-15"
  },
  "crops": [
    {
      "crop_id": "radish",
      "succession": true,
      "sowings": [
        { "sow_week": 18, "harvest_week": 21, "bed": "bed-a", "slot": "S1" },
        { "sow_week": 20, "harvest_week": 23, "bed": "bed-c", "slot": "S1" },
        { "sow_week": 22, "harvest_week": 25, "bed": "bed-a", "slot": "S1" }
      ]
    },
    {
      "crop_id": "strawberry-ostara",
      "succession": false,
      "harvest_windows": [
        { "start_week": 23, "end_week": 38, "continuous": true }
      ]
    }
  ],
  "gap_analysis": {
    "target": "No 2-week gap in harvestable crops from W22 (late May) through W43 (late October)",
    "weeks": {
      "W22": ["radish", "pea-shoots", "lettuce-baby-mix"],
      "W23": ["radish", "strawberry-ostara", "pea-shoots", "lettuce-baby-mix"],
      "W24": ["radish", "strawberry-ostara", "pea-shoots", "lettuce-baby-mix", "chives"]
    },
    "gaps_found": [],
    "coverage_ok": true
  }
}
```

### Anti-Patterns to Avoid
- **Deep nesting beyond 4 levels:** Keep JSON flat enough to read and edit by hand. If a field needs more than 4 levels of nesting, split into a separate file.
- **Duplicating data across files:** Crop details belong in crop files only. Bed files reference by `crop_id`, not by copying fields.
- **Hardcoding HA entity IDs in crop files:** Crops are bed-agnostic. The bed file maps crops to HA sensors, not the crop file.
- **Mixing schedule concerns:** Weekly schedules reference crops/beds by ID. They do not contain crop growth data -- that lives in the crop file.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Danish growing timelines | Guessing week numbers | Cross-reference planting grids (already have exact sow weeks from Phase 2) + standard zone 7b maturity data | Existing grids have exact dates; supplement with days-to-maturity from seed packets |
| HA entity naming | Inventing entity ID patterns | Follow HA official convention: `sensor.havn_bed_{letter}_{measurement}` | HA auto-generates entity IDs from name; custom IDs must use `unique_id` |
| Plant Monitor thresholds | Making up moisture/temp ranges | Use crop-specific thresholds from agricultural references; the sensor shootout data for calibration context | Threshold values directly affect alert accuracy |
| ISO week calculations | Manual date math | Use ISO 8601 week numbering; 2026 W15 = Apr 6-12, W44 = Oct 26-Nov 1 | Week boundaries must match ISO standard |

**Key insight:** The planting grids from Phase 2 already contain exact sow dates, bed positions, and spacing for all Phase 2 crops. Phase 4 does not need to re-derive this data -- it needs to structure it into JSON format and add the missing fields (growth stages, thresholds, child actions, harvest timing).

## Common Pitfalls

### Pitfall 1: Inconsistent Cross-References
**What goes wrong:** Crop files reference bed names differently than bed files define them (e.g., "Bed A" vs "bed-a" vs "bed_a")
**Why it happens:** No enforced ID convention across files
**How to avoid:** Define an ID format in the schema: lowercase, hyphen-separated (e.g., `bed-a`, `strawberry-ostara`, `pea-kelvedon-wonder`). All cross-references use this exact format.
**Warning signs:** Any reference containing spaces, uppercase, or underscores

### Pitfall 2: HA Entity ID Conflicts
**What goes wrong:** Entity IDs in sensors.json don't match what Zigbee2MQTT or ZHA will actually create
**Why it happens:** Zigbee2MQTT auto-generates entity IDs from device names, often different from what you'd expect
**How to avoid:** The HA schema should define the *desired* entity IDs. When actual sensors are set up in v2, entity IDs can be customized via `customize.yaml` or renamed in HA UI. The JSON schema defines the *intent*, not the runtime state.
**Warning signs:** Entity IDs that assume a specific Zigbee2MQTT naming pattern

### Pitfall 3: Harvest Gap in Succession Calendar
**What goes wrong:** Succession schedule looks complete but has hidden 2-week gaps due to optimistic harvest timing
**Why it happens:** Days-to-maturity assumes ideal conditions; Danish summers can be cool, adding 5-7 days
**How to avoid:** Add a 1-week buffer to all harvest estimates. Overlap succession crops so at least 2 crops are harvestable in any given week. Use the gap_analysis field to verify coverage.
**Warning signs:** Any week between W22 and W43 with only one harvestable crop

### Pitfall 4: HA Plant Monitor Sensor Mismatch
**What goes wrong:** Plant Monitor expects per-plant sensors but the project uses per-bed sensors shared across crops
**Why it happens:** HA Plant Monitor is designed for one sensor per plant, but this project has one sensor per bed with 3-8 crops
**How to avoid:** Define one HA Plant Monitor entity per bed (not per crop), using the most restrictive thresholds among the bed's crops. Document this design decision clearly.
**Warning signs:** Plant Monitor configs referencing nonexistent per-crop sensors

### Pitfall 5: Themed Week Names Don't Match Reality
**What goes wrong:** "Strawberry Week" assigned to W20 but strawberries don't fruit until W23
**Why it happens:** Naming weeks before populating growth timeline data
**How to avoid:** Populate crop growth stages and weekly task data FIRST, then assign themed names based on what's actually happening that week. The hero task should be the most exciting real event.
**Warning signs:** Theme names referencing events that don't appear in the tasks or growth_events arrays

## Code Examples

### Home Assistant Plant Monitor YAML (derived from plants.json)
```yaml
# Source: https://www.home-assistant.io/integrations/plant/
# This YAML would be generated FROM data/ha/plants.json

plant:
  havn_bed_a:
    sensors:
      moisture: sensor.havn_bed_a_moisture
      temperature: sensor.havn_bed_a_temperature
    # Use the most restrictive thresholds from Bed A crops
    # Strawberry Ostara: min 30%, max 70%
    # Thyme: min 20%, max 50% (most restrictive max)
    # Pea shoots: min 40%, max 80% (most restrictive min)
    min_moisture: 30
    max_moisture: 70
    min_temperature: 5

  havn_bed_b:
    sensors:
      moisture: sensor.havn_bed_b_moisture
      temperature: sensor.havn_bed_b_temperature
    min_moisture: 25
    max_moisture: 65
    min_temperature: 3

  havn_bed_c:
    sensors:
      moisture: sensor.havn_bed_c_moisture
      temperature: sensor.havn_bed_c_temperature
    min_moisture: 30
    max_moisture: 75
    min_temperature: 5
```

### Home Assistant Template Sensor YAML (derived from sensors.json)
```yaml
# Source: https://www.home-assistant.io/docs/configuration/customizing-devices/
# Per-bed sensors with havn_ prefix

template:
  - sensor:
      - name: "Havn Bed A Moisture"
        unique_id: havn_bed_a_moisture
        unit_of_measurement: "%"
        device_class: moisture
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_soil_moisture') }}"

      - name: "Havn Bed A Temperature"
        unique_id: havn_bed_a_temperature
        unit_of_measurement: "C"
        device_class: temperature
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_temperature') }}"
```

### Home Assistant Customize YAML (derived from customize.json)
```yaml
# Source: https://www.home-assistant.io/docs/configuration/customizing-devices/
homeassistant:
  customize:
    sensor.havn_bed_a_moisture:
      friendly_name: "Bed A (His Bed) - Soil Moisture"
      icon: mdi:water-percent
    sensor.havn_bed_a_temperature:
      friendly_name: "Bed A (His Bed) - Temperature"
      icon: mdi:thermometer
```

### Alert Rule JSON (for future v2 automation)
```json
{
  "id": "bed-a-dry",
  "trigger": "moisture_below_min",
  "entity": "sensor.havn_bed_a_moisture",
  "threshold": 30,
  "delay_hours": 6,
  "message": {
    "en": "Bed A (His Bed) needs water! Soil moisture is {{ state }}%.",
    "da": "Bed A (Hans Bed) har brug for vand! Jordfugtighed er {{ state }}%."
  },
  "notification_target": "notify.mobile_app"
}
```

## Sensor Hardware Recommendations

### Primary Recommendation: Haozee Zigbee Soil Sensor
| Property | Value |
|----------|-------|
| Model | Haozee Tuya Zigbee Soil Tester (TS0601_soil variant) |
| Protocol | Zigbee 3.0 |
| Measures | Soil moisture (%), soil temperature (C) |
| IP Rating | IP66/IP67 (varies by model) |
| Battery | 2x AA, ~1 year life |
| Zigbee2MQTT | Supported as TS0601_soil |
| Price (est.) | ~USD $15-25 / ~100-175 DKK per unit |
| Why | Community sensor shootout winner: best range (0% dry to ~100% wet), minimal variance between units, stable long-term readings |

**Source:** [HA Community sensor shootout](https://community.home-assistant.io/t/my-zigbee-soil-moisture-sensor-shootout/907192) -- tested 5 brands with 2 units each; Haozee was the clear winner.

### Alternative 1: ThirdReality 3RSM0147Z
| Property | Value |
|----------|-------|
| Model | ThirdReality Smart Soil Moisture Sensor (3RSM0147Z) |
| Protocol | Zigbee 3.0 |
| IP Rating | IP67 |
| Battery | 1x AA, up to 3-year life |
| Zigbee2MQTT | Supported; ThirdReality maintains their own converters |
| Price (est.) | ~USD $20 / ~140 DKK |
| Tradeoff | Reliable but narrow moisture range (~50-70%), bulky (18cm tall), reports "humidity" instead of "moisture" requiring Z2M workaround |

### Alternative 2 (LoRaWAN Fallback): Dragino LSE01
| Property | Value |
|----------|-------|
| Model | Dragino LSE01 LoRaWAN Soil Moisture & EC Sensor |
| Protocol | LoRaWAN |
| Measures | Soil moisture, temperature, electrical conductivity |
| Battery | Li-SOCI2 4000mAh/8500mAh, up to 10-year life |
| Price (est.) | ~USD $70-90 / ~500-650 DKK |
| When to use | Only if Zigbee range from house to garden is insufficient (requires LoRaWAN gateway, additional cost) |

### NOT Recommended: Tuya GXM-01
Despite being the most commonly found Zigbee soil sensor, the community reports persistent issues: sensors stuck at 100%/94%, battery drain in 2-3 weeks (not 1 year), manufacturer went unresponsive. Avoid.

### Zigbee Range Extension
No dedicated outdoor-rated Zigbee repeater exists in the consumer market. Options:
- **IKEA TRETAKT smart plug (~100 DKK)** in a weatherproof outdoor outlet box -- acts as Zigbee router, indoor-rated but works in sheltered outdoor enclosure
- **Any mains-powered Zigbee device** placed between house and garden acts as a mesh router
- **Distance consideration:** Vejle garden -- if the Zigbee coordinator (e.g., Sonoff ZBDongle-P) is near a window facing the garden, range to raised beds should be 10-15m through one wall, which is within typical Zigbee range without a repeater. Test before buying a repeater.

### Budget Estimate (5 beds)
| Item | Qty | Unit Price (DKK) | Total (DKK) |
|------|-----|-------------------|-------------|
| Haozee Zigbee soil sensor | 5 | ~150 | ~750 |
| AA batteries | 10 | ~5 | ~50 |
| IKEA TRETAKT (optional repeater) | 1 | ~100 | ~100 |
| **Total** | | | **~800-900** |

This fits within the 500-1000 DKK budget. Without the repeater: ~800 DKK.

## Complete Plant Inventory

All crops that need JSON files, derived from Phase 2 planting grids and Phase 3 plans:

### Phase 2 Crops (already planted/planned for W16-W17)
| Crop | Variety | Bed(s) | Shortcode | Sow Week |
|------|---------|--------|-----------|----------|
| Strawberry | Ostara | A | ST-O | W16 (plug) |
| Strawberry | Korona | A | ST-K | W16 (plug) |
| Raspberry | Autumn Bliss | B | RB | W16 (bare-root) |
| Pea | Kelvedon Wonder | C | PEA | W16 |
| Kale | Nero di Toscana | C | KAL | W17 |
| Baby lettuce | Mix | D | LET | W16 |
| Spring onion | White Lisbon | D | SON | W16 |
| Radish | Generic | A, C, D, E | RAD/SUCC | W16-W18+ |
| Pea shoots | Generic | A | PSHOOT | W16 |
| Thyme | Creeping | A, D | THY | W16 |
| Lemon balm | Generic | A | LE | W16 |
| Lamb's ear | Stachys | A | LAM | W16 |
| Viola | Generic | A, D | VIO | W16 |
| Calendula | Generic | A, C, E | CAL | W17 |
| Borage | Generic | C, E | BOR | W17 |
| Chives | Generic | B | CHV | W16 |

### Phase 3 Crops (warm season transplants, W21+)
| Crop | Variety | Bed(s) | Sow Week |
|------|---------|--------|----------|
| Cherry tomato | Sungold | E (or B) | W21 transplant |
| Cherry tomato | Tumbling Tom | E | W21 transplant |
| Cucumber | Mini Munch / Picolino | C (trellis end) | W21 transplant |
| Sweet pepper | Lipstick / King of North | D or E | W22 transplant |
| Sunflower | Generic | TBD | W18 direct sow |
| Nasturtium | Trailing | TBD | W18 direct sow |
| Mint | Generic | Own pot | W16 |
| Basil | Generic | With tomatoes | W21 |
| Bush bean | Provider / Speedy | TBD | W20 |
| Broccoli | Calabrese | TBD | W21 transplant |
| Leek | Musselburgh | TBD | W21 transplant |

**Total: ~27 crop JSON files needed.**

## Danish Zone 7b Growing Timeline (Key Dates)

| Event | Week | Date (approx) |
|-------|------|---------------|
| Last spring frost (Vejle avg) | W19 | ~May 10 |
| First autumn frost (Vejle avg) | W42 | ~Oct 15 |
| Earliest outdoor sowing (hardy) | W15-16 | Apr 7-19 |
| Warm-season transplant safe | W21 | May 18+ |
| Longest day | W25 | Jun 21 |
| Peak summer warmth | W27-31 | Jul-Aug |
| First succession harvest (radish) | W21 | ~May 18 |
| Strawberry first fruit (Korona) | W23-24 | ~Jun 8 |
| Strawberry first fruit (Ostara) | W24-25 | ~Jun 15 |
| Raspberry fruit (Autumn Bliss) | W31-40 | Aug-Oct |
| Baby lettuce first cut | W19-20 | ~May 4 |
| Pea first harvest | W24-26 | ~Jun 15 |

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| HA Plant Monitor only | Plant Monitor + custom template sensors | 2023+ | Template sensors allow per-bed abstraction over raw device sensors |
| Resistive soil sensors | Capacitive soil sensors | 2023+ | Capacitive sensors last years vs months; no galvanic corrosion |
| ZHA only for Zigbee | Zigbee2MQTT preferred | 2024+ | Z2M has broader device support, better community; ZHA still works but Z2M is the community standard |

**Deprecated/outdated:**
- Tuya/GIEX GXM-01: Hardware QA issues, manufacturer unresponsive since mid-2023. Avoid.
- HA `openplantbook` integration: Optional enrichment, not needed when manually curating crop data.

## Open Questions

1. **Exact Haozee model number for European purchase**
   - What we know: Haozee wins the sensor shootout; available on AliExpress and Amazon
   - What's unclear: Exact model SKU varies (multiple Haozee variants exist with different IP ratings -- IP66 vs IP67)
   - Recommendation: Document "Haozee Tuya Zigbee Soil Tester" with AliExpress link; note IP66+ required for outdoor use. Exact SKU confirmed at purchase time.

2. **Bed-level vs crop-level Plant Monitor thresholds**
   - What we know: HA Plant Monitor expects one sensor set per entity; project has per-bed sensors
   - What's unclear: Whether to use most restrictive thresholds (safest) or average (most realistic) for mixed-crop beds
   - Recommendation: Use most restrictive min and least restrictive max among bed crops. Document the compromise.

3. **Phase 3 crop bed assignments**
   - What we know: Phase 3 crops (tomatoes, cucumbers, peppers, etc.) are planned but exact bed assignments may shift
   - What's unclear: Final bed placement for some Phase 3 crops
   - Recommendation: Create crop JSON files with growth data now; leave `beds` field as tentative based on Phase 2/3 context. Update when Phase 3 is executed.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | JSON Schema Draft 2020-12 validation (manual or `ajv` CLI) |
| Config file | `data/schemas/crop.schema.json` (created in Wave 0) |
| Quick run command | `ajv validate -s data/schemas/crop.schema.json -d "data/crops/*.json"` (optional) |
| Full suite command | Manual review: every crop file has all required fields, every week file exists W15-W44, succession calendar has no gaps |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| DATA-01 | Crop schema defines all required fields | manual review | Verify schema file has growth_stages, water_needs, harvest, companion_plants, difficulty, child_actions, alert thresholds | Wave 0 |
| DATA-02 | Every planted crop has a populated JSON file | manual count | `ls data/crops/*.json \| wc -l` should be >= 27 | Wave 0 |
| DATA-03 | Weekly schedule JSON files W15-W44 exist with required fields | manual count | `ls data/schedules/w*.json \| wc -l` should be 30 | Wave 0 |
| DATA-04 | HA entity schema uses havn_ prefix, per-bed sensors | manual review | Check sensors.json for havn_bed_{a-e}_{measurement} pattern | Wave 0 |
| DATA-05 | HA Plant Monitor configs have moisture/temp thresholds | manual review | Check plants.json has min_moisture, max_moisture, min_temperature per bed | Wave 0 |
| DATA-06 | Sensor recommendations with models, prices, HA compatibility | manual review | Check sensor-recommendations.md for 2-3 Zigbee + 1 LoRaWAN with prices | Wave 0 |
| SCHED-02 | No 2-week harvest gap late May through October | manual review | Check succession-calendar.json gap_analysis.gaps_found is empty | Wave 0 |
| SCHED-03 | Week-by-week maintenance plan W14-W44 | manual review | Every weekly JSON has at least one must_do task | Wave 0 |
| SCHED-04 | Succession sowing calendar for radish, lettuce, beans, spring onion, peas | manual review | Check succession-calendar.json has entries for all 5 crops | Wave 0 |

### Sampling Rate
- **Per task commit:** Verify new JSON files are valid JSON (`python3 -m json.tool data/crops/new-file.json`)
- **Per wave merge:** Count files against expected totals; spot-check 3 random crop files for field completeness
- **Phase gate:** All 9 requirements verified before `/gsd:verify-work`

### Wave 0 Gaps
- [ ] `data/` directory structure -- does not exist yet
- [ ] `data/schemas/crop.schema.json` -- formal schema for crop files (optional but recommended)
- [ ] JSON syntax validation can use built-in `python3 -m json.tool` -- no framework install needed

## Sources

### Primary (HIGH confidence)
- [Home Assistant Plant Monitor integration](https://www.home-assistant.io/integrations/plant/) -- official docs, verified active integration with ~1971 installations, YAML format confirmed
- [Home Assistant entity customization](https://www.home-assistant.io/docs/configuration/customizing-devices/) -- official docs for customize.yaml format
- [Zigbee2MQTT TS0601_soil device page](https://www.zigbee2mqtt.io/devices/TS0601_soil.html) -- confirmed exposed entities and calibration options
- [JSON Schema Draft 2020-12](https://json-schema.org/draft/2020-12) -- official specification
- Existing planting grids (docs/planting-grid-bed-{a-e}.md) -- exact crop positions, sow dates, spacing

### Secondary (MEDIUM confidence)
- [HA Community sensor shootout](https://community.home-assistant.io/t/my-zigbee-soil-moisture-sensor-shootout/907192) -- comparative test of 5 sensor brands, Haozee recommended
- [SmartHomeScene Tuya GXM-01 review](https://smarthomescene.com/reviews/tuya-zigbee-plant-soil-sensor-gxm-01-review/) -- detailed specs and reported issues
- [SmartHomeScene ThirdReality review](https://smarthomescene.com/reviews/thirdreality-smart-soil-moisture-sensor-review/) -- specs, pricing ($19.99), IP67 confirmed
- [Dragino LSE01 product page](https://www.dragino.com/products/lora-lorawan-end-node/item/159-lse01.html) -- LoRaWAN fallback option specs

### Tertiary (LOW confidence)
- Haozee pricing (~150 DKK per unit) -- estimated from USD pricing + shipping; actual European pricing varies by retailer and shipping. Needs validation at purchase time.
- Zone 7b frost dates for Vejle -- approximated from general Danish climate data; actual dates vary year to year.

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH -- JSON files are the decided format; schema approach is straightforward
- Architecture: HIGH -- patterns derived directly from locked CONTEXT.md decisions and existing project structure
- Pitfalls: HIGH -- HA Plant Monitor format verified against official docs; sensor issues verified from community reports
- Sensor recommendations: MEDIUM -- community shootout is reliable but pricing and availability in Denmark needs validation at purchase time
- Growing timelines: MEDIUM -- based on general zone 7b data and existing planting grid dates; actual harvest timing varies with weather

**Research date:** 2026-03-26
**Valid until:** 2026-05-01 (growing timelines are seasonal; sensor market changes slowly)
