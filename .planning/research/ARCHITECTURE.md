# Architecture: Physical Garden + Data Systems

**Project:** Haven -- A Learning Garden
**Location:** Vejle, Denmark (55.7N, 9.5E)
**Researched:** 2026-03-26

---

## Part 1: Physical Architecture

### 1.1 Property Layout and Sun Analysis

#### Property Visualization (Top-Down, North Up)

```
                            N
                            |
                    ~~~~~~~~|~~~~~~~~
                   |  NEIGHBOR NORTH  |
                    ~~~~~~~~~~~~~~~~~
        ___________________________________
       |          BACKYARD (EAST)           |
       |                                    |
       |   [mature trees ****]    ****      |
       |        ****  ****    ****  ****    |
       |     ****                   ****    |
       |                                    |
       |      .........                     |
       |      : BED-3 :  "Eventyr-bedet"   |
  NW   |      : 120x60:  (Adventure Bed)   |   NE
       |      :........:                    |
       |                                    |
       |      .........   .........         |
       |      : BED-1 :   : BED-2 :        |
       |      : 120x60:   : 120x60:        |
       |      :........:   :........:       |
       |       "Sol-bedet"  "Bær-bedet"     |
       |       (Sun Bed)    (Berry Bed)     |
       |                                    |
       |    ===== path (bark/gravel) =====  |
       |                                    |
  W ---|------+========================+    |--- E
       |      |                        |    |
       | HOUSE|     CARPORT            |    |
       |      |  (tagterrasse above)   |    |
       |      +====+===============+===+    |
       |      |    | ROOF TERRACE  |   |    |
       |      |    | 68 m^2        |   |    |
       |      |    |  ..........   |   |    |
       |      |    |  : BED-T1 :   |   |    |
  SW   |      |    |  :  80x40 :   |   |  SE
       |      |    |  :........:   |   |    |
       |      |    |  ..........   |   |    |
       |      |    |  : BED-T2 :   |   |    |
       |      |    |  :  80x40 :   |   |    |
       |      |    |  :........:   |   |    |
       |      |    |               |   |    |
       |      +====+===============+===+    |
       |                                    |
  -----+---- Street (road, WEST) ----------+----
                            |
                            S
```

**Key observations:**
- House faces WEST toward the street. Backyard extends EAST/NORTHEAST.
- Mature trees dominate the EAST side, creating shade especially in morning hours.
- The roof terrace (tagterrasse) is ELEVATED above the carport -- less tree shadow, longer sun exposure.
- ~600 m2 total plot. Usable backyard lawn area estimated at ~200-250 m2.

#### 1.2 Sun Path at 55.7N Latitude

Solar elevation angles at solar noon (due south):

| Date | Noon Elevation | Sunrise Direction | Sunset Direction | Day Length |
|------|---------------|-------------------|------------------|------------|
| Mar 20 (equinox) | 34.3 deg | East (90 deg) | West (270 deg) | ~12h |
| Apr 15 (last frost) | ~42 deg | ENE (~70 deg) | WNW (~290 deg) | ~14h |
| Jun 21 (solstice) | 57.8 deg | NNE (~45 deg) | NNW (~315 deg) | ~17.5h |
| Aug 1 (peak harvest) | ~50 deg | NE (~55 deg) | NW (~305 deg) | ~16h |
| Oct 15 (first frost) | ~25 deg | ESE (~100 deg) | WSW (~260 deg) | ~10.5h |

**Shadow calculations** (formula: shadow length = object height / tan(sun elevation)):

For a 7m tall house at noon:
- Summer solstice (57.8 deg): shadow = 7 / tan(57.8) = **4.4m** northward
- Spring equinox (34.3 deg): shadow = 7 / tan(34.3) = **10.2m** northward
- October (25 deg): shadow = 7 / tan(25) = **15.0m** northward

For a 10m mature tree at summer noon: shadow = **6.3m**

**Critical insight:** In summer, the house casts a short shadow (4-5m) to the north/northeast. The backyard beds positioned 6m+ from the house will get full midday and afternoon sun. Morning sun (from NE) is partially blocked by mature trees on the east side. The roof terrace, being elevated, escapes tree shadows entirely.

#### 1.3 Bed Placement Strategy

**Zone A: Backyard Ground Level (3 beds)**

Position beds in the WEST-CENTRAL portion of the backyard, at least 6m from the house wall and west of the mature tree line. This zone receives:
- Morning sun from ~8-9 AM (after clearing house shadow)
- Full midday sun (south-facing, no obstructions)
- Afternoon sun until ~7-8 PM in summer
- Estimated 8-10 hours direct sun in midsummer

Arrange beds in an L-pattern or staggered rows running EAST-WEST (long axis). This maximizes south-facing exposure and avoids beds shading each other.

**Zone B: Roof Terrace (2 smaller beds)**

The tagterrasse gets the BEST sun exposure on the property:
- Elevated above ground-level tree shadows
- Open to south sky
- Estimated 10-12 hours direct sun in midsummer
- Wind exposure higher (consider wind-tolerant crops or a small windbreak)

Beds here must be SMALLER and LIGHTER due to structural load concerns. Use shallow beds (25-30cm depth) with lightweight growing medium.

#### 1.4 Bed Specifications for a 7-Year-Old

**Ergonomic dimensions based on child reach:**

A 7-year-old's comfortable reach is approximately 35-40cm from the edge. For beds accessible from BOTH sides, max width is 70-80cm. For beds against a wall (one side access), max width is 40cm.

| Bed ID | Location | Dimensions (LxWxH) | Access | Weight Concern |
|--------|----------|---------------------|--------|----------------|
| BED-1 "Sol-bedet" | Backyard | 120 x 60 x 40 cm | Both sides | No |
| BED-2 "Baer-bedet" | Backyard | 120 x 60 x 40 cm | Both sides | No |
| BED-3 "Eventyr-bedet" | Backyard | 120 x 60 x 40 cm | Both sides | No |
| BED-T1 "Terasse-krydder" | Roof terrace | 80 x 40 x 30 cm | One side (wall) | YES -- shallow, light soil |
| BED-T2 "Terasse-bær" | Roof terrace | 80 x 40 x 30 cm | One side (railing) | YES -- shallow, light soil |

**Height rationale:** 40cm bed height puts the soil surface at roughly elbow height for a 120cm-tall child. This is comfortable for digging, planting, and harvesting without bending uncomfortably. Terrace beds at 30cm placed on a low stand or bench could bring them to similar working height.

**Material:** Corten steel preferred (see STACK.md for suppliers and pricing). 2mm plate thickness is standard for residential beds this size.

### 1.5 Bed Naming Scheme

Names are in Danish, meaningful to the child, and map to data system IDs:

| System ID | Danish Name | English Meaning | Purpose |
|-----------|-------------|-----------------|---------|
| `bed-1-sol` | Sol-bedet | The Sun Bed | Tomatoes, peppers, basil (full sun lovers) |
| `bed-2-baer` | Baer-bedet | The Berry Bed | Strawberries, edible flowers, companion herbs |
| `bed-3-eventyr` | Eventyr-bedet | The Adventure Bed | Cucumbers, radishes, experiments (his choice bed) |
| `bed-t1-krydder` | Terasse-krydder | Terrace Herbs | Herbs: thyme, oregano, chives, parsley |
| `bed-t2-baer` | Terasse-baer | Terrace Berries | Strawberries (alpine/everbearing), nasturtium |

The child names his own beds. The names above are suggestions -- let him pick. The system IDs remain stable regardless of the display name.

### 1.6 Bed-by-Bed Planting Layout with Companion Planting

#### BED-1 "Sol-bedet" (120x60cm, backyard)

```
+--------------------------------------------------+
|  TOMATO (cherry)    TOMATO (cherry)    BASIL      |
|      *                  *               |||       |
|                                                   |
|  PEPPER (sweet)     PEPPER (sweet)     BASIL      |
|      *                  *               |||       |
|                                                   |
|  MARIGOLD (edge)   MARIGOLD (edge)   MARIGOLD    |
|      @                  @               @         |
+--------------------------------------------------+
```

**Rationale:** Cherry tomatoes and sweet peppers are his favorites. Basil is the classic tomato companion (repels aphids, may improve flavor). Marigolds along the south-facing edge repel nematodes and add color. All are full-sun crops.

**Companion logic:** Tomato + basil (proven companion). Pepper + tomato (same family, similar needs, acceptable neighbors). Marigold (universal pest deterrent).

#### BED-2 "Baer-bedet" (120x60cm, backyard)

```
+--------------------------------------------------+
|  STRAWBERRY   STRAWBERRY   STRAWBERRY   STRAWBERRY|
|      o            o            o            o     |
|                                                   |
|  BORAGE        THYME         NASTURTIUM           |
|    *~*          |||            @@                  |
|                                                   |
|  STRAWBERRY   STRAWBERRY   STRAWBERRY   STRAWBERRY|
|      o            o            o            o     |
+--------------------------------------------------+
```

**Rationale:** Strawberries are his top favorite food. Borage is the classic strawberry companion (attracts pollinators, said to improve yield and sweetness). Thyme provides ground cover between plants. Nasturtium is edible (flowers for decorating baked goods -- mentioned in his preferences) and acts as a trap crop for aphids.

**Companion logic:** Strawberry + borage (pollinator attraction). Strawberry + thyme (ground cover, moisture retention). Nasturtium (trap crop + edible flowers).

#### BED-3 "Eventyr-bedet" (120x60cm, backyard)

```
+--------------------------------------------------+
|  CUCUMBER       CUCUMBER        DILL              |
|    \|/            \|/           |||               |
|                                                   |
|  RADISH  RADISH  RADISH  RADISH  SPRING ONION    |
|    .       .       .       .        ||            |
|                                                   |
|  LETTUCE (family)    PEAS (family)                |
|    ~~~                  ^  ^  ^                   |
+--------------------------------------------------+
```

**Rationale:** This is the "adventure" bed where he experiments. Radishes are the ultimate quick-win crop (harvest in 25-30 days -- perfect for ADHD engagement). Cucumbers are on his favorites list. Dill is a proven cucumber companion. Lettuce and peas are family crops he does not eat but family cooks with. Spring onions likewise.

**Companion logic:** Cucumber + dill (improves cucumber health). Radish (fast harvest, breaks soil). Lettuce (shade-tolerant, fills gaps). Peas (nitrogen fixer, benefits all neighbors).

#### BED-T1 "Terasse-krydder" (80x40cm, roof terrace)

```
+--------------------------------+
|  THYME    OREGANO    CHIVES    |
|   |||       |||       ||       |
|                                |
|  PARSLEY     MINT (contained!) |
|   |||         [pot]            |
+--------------------------------+
```

**Rationale:** Herbs on the terrace get maximum sun. All are perennial or self-seeding, reducing replanting effort. Mint MUST be in a pot-within-bed or it will take over. These herbs supply the kitchen and teach "snip and smell" engagement.

#### BED-T2 "Terasse-baer" (80x40cm, roof terrace)

```
+--------------------------------+
|  ALPINE STRAWBERRY (everbearing)|
|    o    o    o    o    o        |
|                                 |
|  NASTURTIUM     VIOLA (edible)  |
|    @@             **            |
+--------------------------------+
```

**Rationale:** Alpine/everbearing strawberries fruit continuously from June-October, providing constant small harvests (perfect for a child's daily check). Nasturtium and viola provide edible flowers for his baking interest. All tolerate the slightly windier terrace conditions.

### 1.7 Access Paths and Child Workflow

```
                    BACKYARD
                       |
         +----[BED-3 Eventyr]----+
         |                       |
    ===== bark path (60cm wide) =====
         |                       |
    +--[BED-1 Sol]--+  +--[BED-2 Baer]--+
         |                       |
    ===== main path to house =====
         |
      [water tap / hose connection]
         |
       HOUSE
```

**Path specifications:**
- 60cm wide minimum (child with watering can)
- Material: bark chips or pea gravel (soft, drains well, defines zones)
- All beds reachable within 15m of water source
- Watering can sized for child: 3-5 liter (manageable weight when full)

**Daily workflow route:**
1. Fill watering can at tap
2. Check BED-1 and BED-2 (closest to house, morning routine)
3. Walk to BED-3 (furthest, the "adventure" -- builds anticipation)
4. Roof terrace beds on separate circuit (via house stairs)
5. Total route: ~5 minutes at child pace

---

## Part 2: Data Architecture

### 2.1 JSON Schema for Crop Data

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "CropData",
  "description": "Structured crop data for Haven garden project",
  "type": "object",
  "required": ["id", "name", "name_da", "category", "bed_id", "planting", "care", "harvest", "companions"],
  "properties": {
    "id": {
      "type": "string",
      "description": "Unique crop identifier",
      "pattern": "^[a-z][a-z0-9-]+$",
      "examples": ["cherry-tomato", "strawberry-main", "radish-spring"]
    },
    "name": {
      "type": "string",
      "description": "English common name"
    },
    "name_da": {
      "type": "string",
      "description": "Danish common name"
    },
    "category": {
      "type": "string",
      "enum": ["fruit", "vegetable", "herb", "flower"]
    },
    "bed_id": {
      "type": "string",
      "description": "Which bed this crop is planted in",
      "enum": ["bed-1-sol", "bed-2-baer", "bed-3-eventyr", "bed-t1-krydder", "bed-t2-baer"]
    },
    "difficulty": {
      "type": "string",
      "enum": ["easy", "medium", "challenge"],
      "description": "Child-facing difficulty tier"
    },
    "child_favorite": {
      "type": "boolean",
      "description": "True if child likes eating this crop"
    },
    "planting": {
      "type": "object",
      "required": ["method", "earliest_outdoor", "depth_cm", "spacing_cm"],
      "properties": {
        "method": {
          "type": "string",
          "enum": ["direct-sow", "transplant-seedling", "plant-root"]
        },
        "earliest_outdoor": {
          "type": "string",
          "description": "Earliest outdoor planting, ISO week format",
          "pattern": "^W(0[1-9]|[1-4][0-9]|5[0-3])$",
          "examples": ["W16", "W20"]
        },
        "latest_outdoor": {
          "type": "string",
          "pattern": "^W(0[1-9]|[1-4][0-9]|5[0-3])$"
        },
        "depth_cm": { "type": "number" },
        "spacing_cm": { "type": "number" },
        "succession_interval_weeks": {
          "type": ["number", "null"],
          "description": "Weeks between successive plantings for continuous harvest, null if not applicable"
        }
      }
    },
    "care": {
      "type": "object",
      "required": ["water_need", "sun_need"],
      "properties": {
        "water_need": {
          "type": "string",
          "enum": ["low", "medium", "high"],
          "description": "low=drought-tolerant, medium=every 2-3 days, high=daily in summer"
        },
        "sun_need": {
          "type": "string",
          "enum": ["full-sun", "partial-shade", "shade-tolerant"]
        },
        "feed_schedule": {
          "type": "string",
          "description": "Fertilizing guidance",
          "examples": ["Every 2 weeks with tomato feed once fruiting begins"]
        },
        "pruning_notes": {
          "type": ["string", "null"]
        },
        "support_needed": {
          "type": "string",
          "enum": ["none", "stake", "cage", "trellis"]
        }
      }
    },
    "growth_stages": {
      "type": "array",
      "description": "Ordered growth stages with expected timing",
      "items": {
        "type": "object",
        "required": ["stage", "description", "weeks_from_planting", "child_action"],
        "properties": {
          "stage": {
            "type": "string",
            "examples": ["seed", "sprout", "seedling", "growing", "flowering", "fruiting", "harvest-ready"]
          },
          "description": {
            "type": "string",
            "description": "Child-friendly description of what to look for"
          },
          "weeks_from_planting": {
            "type": "number"
          },
          "child_action": {
            "type": "string",
            "description": "What the child should do at this stage",
            "examples": ["Water gently every day", "Look for tiny yellow flowers!", "Pick the red ones - leave the green ones"]
          }
        }
      }
    },
    "harvest": {
      "type": "object",
      "required": ["days_to_harvest", "harvest_window_weeks", "how_to_harvest"],
      "properties": {
        "days_to_harvest": {
          "type": "number",
          "description": "Days from planting/transplant to first harvest"
        },
        "harvest_window_weeks": {
          "type": "number",
          "description": "How many weeks harvesting continues"
        },
        "how_to_harvest": {
          "type": "string",
          "description": "Child-friendly harvest instructions"
        },
        "signs_of_readiness": {
          "type": "string",
          "description": "Visual cues the child can check"
        }
      }
    },
    "companions": {
      "type": "object",
      "properties": {
        "good": {
          "type": "array",
          "items": { "type": "string" },
          "description": "Crop IDs that benefit from proximity"
        },
        "bad": {
          "type": "array",
          "items": { "type": "string" },
          "description": "Crop IDs to keep separated"
        },
        "why": {
          "type": "string",
          "description": "Brief explanation of companion relationships"
        }
      }
    },
    "alerts": {
      "type": "array",
      "description": "Automated alert triggers for Home Assistant",
      "items": {
        "type": "object",
        "required": ["trigger", "condition", "message"],
        "properties": {
          "trigger": {
            "type": "string",
            "enum": ["soil_moisture_low", "soil_moisture_high", "temperature_low", "temperature_high", "growth_stage_reached", "harvest_due", "feeding_due", "succession_planting_due"]
          },
          "condition": {
            "type": "object",
            "properties": {
              "sensor": { "type": "string" },
              "threshold": { "type": "number" },
              "operator": { "type": "string", "enum": ["<", ">", "<=", ">=", "=="] },
              "calendar_week": { "type": "string" }
            }
          },
          "message": {
            "type": "string",
            "description": "Child-friendly alert message"
          },
          "severity": {
            "type": "string",
            "enum": ["info", "action-needed", "urgent"]
          }
        }
      }
    },
    "vacation_resilience": {
      "type": "string",
      "enum": ["high", "medium", "low"],
      "description": "How well this crop survives 2-3 weeks without daily care"
    },
    "sources": {
      "type": "array",
      "items": { "type": "string" },
      "description": "URLs or references for crop data"
    }
  }
}
```

### 2.2 Home Assistant Entity Structure

**Entity naming convention:** `sensor.<zone>_<bed_id>_<measurement>`

All garden entities use the `haven_` prefix for easy filtering and grouping.

#### Sensor Entities

| Entity ID | Device Class | Unit | Description |
|-----------|-------------|------|-------------|
| `sensor.haven_bed1_sol_soil_moisture` | `moisture` | `%` | Soil moisture, Sun Bed |
| `sensor.haven_bed1_sol_soil_temperature` | `temperature` | `C` | Soil temp, Sun Bed |
| `sensor.haven_bed2_baer_soil_moisture` | `moisture` | `%` | Soil moisture, Berry Bed |
| `sensor.haven_bed2_baer_soil_temperature` | `temperature` | `C` | Soil temp, Berry Bed |
| `sensor.haven_bed3_eventyr_soil_moisture` | `moisture` | `%` | Soil moisture, Adventure Bed |
| `sensor.haven_bed3_eventyr_soil_temperature` | `temperature` | `C` | Soil temp, Adventure Bed |
| `sensor.haven_terrace_air_temperature` | `temperature` | `C` | Air temp, roof terrace |
| `sensor.haven_terrace_light_level` | `illuminance` | `lx` | Light level, roof terrace |
| `sensor.haven_backyard_air_temperature` | `temperature` | `C` | Air temp, backyard |

**Note:** Terrace beds (BED-T1, BED-T2) share one set of sensors due to proximity. Backyard beds each get individual soil sensors because moisture varies with position relative to trees.

#### Plant Monitor Integration Configuration

```yaml
plant:
  haven_bed1_sol_tomato:
    sensors:
      moisture: sensor.haven_bed1_sol_soil_moisture
      temperature: sensor.haven_bed1_sol_soil_temperature
      brightness: sensor.haven_terrace_light_level  # placeholder until backyard sensor
    min_moisture: 30
    max_moisture: 70
    min_temperature: 8
    max_temperature: 35

  haven_bed2_baer_strawberry:
    sensors:
      moisture: sensor.haven_bed2_baer_soil_moisture
      temperature: sensor.haven_bed2_baer_soil_temperature
    min_moisture: 35
    max_moisture: 75
    min_temperature: 5
    max_temperature: 30

  haven_bed3_eventyr_mixed:
    sensors:
      moisture: sensor.haven_bed3_eventyr_soil_moisture
      temperature: sensor.haven_bed3_eventyr_soil_temperature
    min_moisture: 25
    max_moisture: 70
    min_temperature: 8
    max_temperature: 35
```

#### Automation Entities

| Automation | Trigger | Action |
|-----------|---------|--------|
| `automation.haven_water_reminder` | Any bed moisture < 30% for 2h | Notify: "[Bed name] er torstig! Kan du vande?" |
| `automation.haven_frost_warning` | Air temp forecast < 2 degC | Notify: "Frost i nat! Skal vi daekke bedene?" |
| `automation.haven_harvest_check` | Weekly schedule (Wed + Sat) | Notify: "Tjek [crop] -- måske klar til høst!" |
| `automation.haven_vacation_mode` | Input boolean toggle | Adjust alerts to neighbor-facing mode |

#### Dashboard Cards

```yaml
# Lovelace card structure
type: vertical-stack
cards:
  - type: custom:mushroom-title-card
    title: "Havens Have"  # Haven's Garden
    subtitle: "{{ states('sensor.haven_backyard_air_temperature') }}°C udenfor"

  - type: horizontal-stack
    cards:
      - type: custom:mushroom-template-card
        primary: "Sol-bedet"
        secondary: "{{ states('sensor.haven_bed1_sol_soil_moisture') }}% fugt"
        icon: mdi:sprout
        icon_color: >
          {% if states('sensor.haven_bed1_sol_soil_moisture') | int < 30 %}
            red
          {% else %}
            green
          {% endif %}
      # ... repeat for each bed
```

### 2.3 Data Flow

```
                    PHYSICAL WORLD
                         |
          +------+  +------+  +------+
          |Sensor|  |Sensor|  |Sensor|   Zigbee soil moisture/temp
          |Bed 1 |  |Bed 2 |  |Bed 3 |   per bed
          +--+---+  +--+---+  +--+---+
             |         |         |
             v         v         v
         +----------------------------+
         |    Zigbee Coordinator      |   (on HA host / TuringPi)
         |    (Zigbee2MQTT or ZHA)    |
         +-------------+--------------+
                       |
                       v
         +----------------------------+
         |     HOME ASSISTANT         |
         |                            |
         |  sensor.haven_*             |   Entity layer
         |  plant.haven_*              |   Plant monitor
         |  automation.haven_*         |   Alert rules
         |  input_boolean.vacation    |   Vacation mode toggle
         +---+----------+--------+---+
             |          |        |
             v          v        v
         Dashboard   Alerts   History
         (Lovelace)  (Notify) (Grafana/HA)
             |          |
             v          v
         Child's     Parent's
         tablet/     phone
         wall panel
```

### 2.4 Week-by-Week Schedule Data Format

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "WeeklySchedule",
  "type": "object",
  "required": ["year", "week", "tasks"],
  "properties": {
    "year": { "type": "number" },
    "week": {
      "type": "number",
      "minimum": 1,
      "maximum": 53
    },
    "iso_week": {
      "type": "string",
      "pattern": "^\\d{4}-W(0[1-9]|[1-4][0-9]|5[0-3])$",
      "examples": ["2026-W14"]
    },
    "theme": {
      "type": "string",
      "description": "Child-friendly name for the week",
      "examples": ["Planteugen!", "Radisetjek", "Jordbær-fest"]
    },
    "tasks": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["task_id", "type", "bed_id", "description", "duration_min"],
        "properties": {
          "task_id": { "type": "string" },
          "type": {
            "type": "string",
            "enum": ["plant", "water", "feed", "harvest", "observe", "maintain", "protect"]
          },
          "bed_id": {
            "type": "string",
            "enum": ["bed-1-sol", "bed-2-baer", "bed-3-eventyr", "bed-t1-krydder", "bed-t2-baer", "all"]
          },
          "crop_id": {
            "type": ["string", "null"]
          },
          "description": {
            "type": "string",
            "description": "Child-friendly task description"
          },
          "duration_min": {
            "type": "number",
            "description": "Expected time in minutes (keep under 10 for daily tasks)"
          },
          "frequency": {
            "type": "string",
            "enum": ["once", "daily", "every-other-day", "twice-weekly", "weekly"]
          },
          "priority": {
            "type": "string",
            "enum": ["must-do", "should-do", "fun-bonus"]
          },
          "weather_dependent": {
            "type": "boolean",
            "description": "Skip if raining (e.g., watering)"
          }
        }
      }
    },
    "expected_events": {
      "type": "array",
      "description": "Growth milestones to watch for this week",
      "items": {
        "type": "object",
        "properties": {
          "crop_id": { "type": "string" },
          "event": { "type": "string" },
          "excitement_level": {
            "type": "string",
            "enum": ["normal", "exciting", "super-exciting"]
          }
        }
      }
    },
    "alerts": {
      "type": "array",
      "description": "Things to watch out for this week",
      "items": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string",
            "enum": ["frost-risk", "heat-risk", "pest-watch", "vacation-prep"]
          },
          "message": { "type": "string" }
        }
      }
    }
  }
}
```

### 2.5 Troubleshooting Guide Format

Structured for searchability by symptom, crop, and bed:

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "TroubleshootingEntry",
  "type": "object",
  "required": ["id", "symptom", "likely_cause", "solution"],
  "properties": {
    "id": { "type": "string" },
    "symptom": {
      "type": "string",
      "description": "What the child/parent observes",
      "examples": ["Yellow leaves on tomato", "White powder on leaves", "Holes in leaves"]
    },
    "symptom_tags": {
      "type": "array",
      "items": { "type": "string" },
      "description": "Searchable tags",
      "examples": [["leaves", "yellow", "wilting"], ["pest", "holes", "caterpillar"]]
    },
    "affected_crops": {
      "type": "array",
      "items": { "type": "string" },
      "description": "Crop IDs this commonly affects"
    },
    "photo_reference": {
      "type": ["string", "null"],
      "description": "Path to reference photo showing the symptom"
    },
    "likely_cause": {
      "type": "string"
    },
    "severity": {
      "type": "string",
      "enum": ["cosmetic", "treat-soon", "urgent"]
    },
    "solution": {
      "type": "object",
      "properties": {
        "child_action": {
          "type": "string",
          "description": "What the child can do (simple, safe)"
        },
        "parent_action": {
          "type": "string",
          "description": "What might need adult help"
        },
        "prevention": {
          "type": "string",
          "description": "How to avoid next time"
        }
      }
    },
    "organic_only": {
      "type": "boolean",
      "default": true,
      "description": "Solutions must be child-safe and organic"
    }
  }
}
```

### 2.6 Neighbor Vacation Guide Format

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "VacationGuide",
  "type": "object",
  "required": ["vacation_start", "vacation_end", "beds", "daily_routine", "emergency_contact"],
  "properties": {
    "vacation_start": { "type": "string", "format": "date" },
    "vacation_end": { "type": "string", "format": "date" },
    "generated_from_week": {
      "type": "string",
      "description": "Which schedule week was active when guide was generated"
    },
    "emergency_contact": {
      "type": "object",
      "properties": {
        "name": { "type": "string" },
        "phone": { "type": "string" }
      }
    },
    "daily_routine": {
      "type": "object",
      "properties": {
        "estimated_time_min": {
          "type": "number",
          "description": "Total daily time needed"
        },
        "steps": {
          "type": "array",
          "items": {
            "type": "object",
            "properties": {
              "order": { "type": "number" },
              "action": { "type": "string" },
              "bed_id": { "type": "string" },
              "skip_if_rain": { "type": "boolean" },
              "notes": { "type": "string" }
            }
          }
        }
      }
    },
    "beds": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "bed_id": { "type": "string" },
          "bed_name": { "type": "string" },
          "location_hint": {
            "type": "string",
            "description": "Plain language: 'the two beds closest to the house'"
          },
          "water_frequency": { "type": "string" },
          "harvest_instructions": {
            "type": ["string", "null"],
            "description": "What to pick and what to leave"
          },
          "keep_harvested": {
            "type": "boolean",
            "description": "Should neighbor keep what they harvest? (goodwill gesture)"
          }
        }
      }
    },
    "weather_rules": {
      "type": "object",
      "properties": {
        "hot_day_above_25c": { "type": "string" },
        "rainy_day": { "type": "string" },
        "storm_warning": { "type": "string" }
      }
    }
  }
}
```

---

## Part 3: File and Directory Structure

### 3.1 Project Repository Structure

```
haven/
  .planning/
    PROJECT.md                    # Project context (exists)
    CLAUDE.md                     # Claude project instructions
    research/
      ARCHITECTURE.md             # This file
      STACK.md                    # Technology/materials
      FEATURES.md                 # Feature landscape
      PITFALLS.md                 # Domain pitfalls
      SUMMARY.md                  # Research summary
    roadmap/
      ROADMAP.md                  # Phase plan
      milestones/                 # Per-milestone details

  data/
    crops/
      cherry-tomato.json          # One file per crop
      strawberry-main.json
      radish-spring.json
      ...
    schema/
      crop.schema.json            # JSON Schema for crops
      schedule.schema.json        # JSON Schema for schedules
      troubleshooting.schema.json
      vacation.schema.json
    schedule/
      2026-W14.json               # One file per week
      2026-W15.json
      ...
    troubleshooting/
      index.json                  # Master symptom index
      entries/
        yellow-leaves-tomato.json
        white-powder-mildew.json
        ...

  guides/
    vacation-template.json        # Template for generating vacation guides
    vacation-2026-summer.json     # Generated for specific trip
    bed-setup.md                  # Construction instructions
    soil-recipe.md                # Soil layer breakdown
    planting-calendar.md          # Visual planting calendar

  homeassistant/
    packages/
      haven_garden.yaml            # HA package: sensors, automations, plant monitors
    dashboards/
      haven_garden_dashboard.yaml  # Lovelace dashboard config
    blueprints/
      haven_water_reminder.yaml    # Reusable automation blueprints

  assets/
    photos/                       # Reference photos (troubleshooting, progress)
    diagrams/                     # Property layout, bed diagrams
```

### 3.2 Why One File Per Crop

Each crop gets its own JSON file rather than one monolithic file because:
1. **Easy to update** -- change tomato data without risk to strawberry data
2. **Diffable** -- git history shows exactly what changed for which crop
3. **Composable** -- scripts can load only relevant crops per bed
4. **Extensible** -- add a new crop by adding a new file, no merge conflicts

### 3.3 Why One File Per Week

Weekly schedule files enable:
1. **Progressive generation** -- generate next 4 weeks, not entire season at once
2. **Adjustment** -- edit week 20 based on actual growth without touching other weeks
3. **HA integration** -- automation reads current week file to determine active tasks
4. **History** -- look back at what was planned vs what actually happened

---

## Part 4: Build Order

### Seasonal Urgency: It Is Late March

The growing season clock is ticking. Last frost in Vejle is ~mid-April (W16). Some crops need to go in the ground by W17-W18. Build order must prioritize getting beds ready to plant.

### Suggested Build Order

| Priority | What | When | Why |
|----------|------|------|-----|
| 1 | Order/buy raised beds + soil | NOW (W13) | Delivery takes 1-2 weeks. Corten beds from Danish suppliers. |
| 2 | Create crop data files (JSON) | W13-W14 | Needed to generate planting schedule. Can do while waiting for beds. |
| 3 | Define weekly schedule W15-W20 | W14 | First 6 weeks of the season planned before beds arrive. |
| 4 | Build/place backyard beds | W14-W15 | As soon as materials arrive. Ground beds first (bigger, more crops). |
| 5 | Fill beds with soil layers | W15 | Soil needs ~1 week to settle before planting. |
| 6 | Plant cold-hardy crops | W16 | Radishes, peas, lettuce, spring onions (frost-tolerant). |
| 7 | Plant warm crops | W18-W20 | Tomatoes, peppers, cucumbers (after last frost, soil warm). |
| 8 | Set up terrace beds | W16-W18 | Lower priority -- herbs and alpine strawberries are forgiving on timing. |
| 9 | Create troubleshooting guide | W16-W20 | Needed once plants are growing. Build incrementally. |
| 10 | Create vacation guide template | W20-W22 | Needed before summer holiday, not before. |
| 11 | Install HA sensors | W20+ | Nice-to-have. Garden works fine without sensors for first season. Manual observation first. |
| 12 | Build HA dashboard | W22+ | After sensors are in and producing data. |

**Critical path:** Beds ordered (W13) -> Beds placed and filled (W15) -> First planting (W16). Everything else can happen in parallel or later.

---

## Anti-Patterns to Avoid

### Anti-Pattern: Over-Engineering the Data System Before Planting

**What:** Spending weeks perfecting JSON schemas, HA dashboards, and automation while the planting window passes.
**Why bad:** No amount of data architecture matters if seeds are not in soil by May.
**Instead:** Minimal viable data (crop files + first 6 weeks of schedule) before planting. Iterate the data system throughout the season.

### Anti-Pattern: Beds Too Wide for Child

**What:** Using standard 120x90cm or 120x120cm beds because they are common adult sizes.
**Why bad:** A 7-year-old cannot reach the center of a 90cm-wide bed. They step on soil, compact it, or simply ignore the middle.
**Instead:** 60cm max width for beds accessed from both sides. 40cm for one-side access.

### Anti-Pattern: All Beds in Tree Shadow

**What:** Placing beds in the northeast corner because "it's the backyard" without analyzing sun path.
**Why bad:** Mature trees on east side block morning sun. At 55.7N, the sun arcs LOW -- even moderate trees cast long shadows.
**Instead:** Beds in west-central backyard, 6m+ from house, west of tree line. Terrace for sun-hungry crops.

### Anti-Pattern: Monolithic Schedule File

**What:** One giant JSON with 30 weeks of schedule data.
**Why bad:** Hard to edit week 22 without breaking week 15. Merge conflicts. Overwhelming to read.
**Instead:** One file per ISO week. Small, focused, independently editable.

---

## Sources

- [TimeAndDate.com Vejle Sun Data](https://www.timeanddate.com/sun/denmark/vejle) -- sunrise/sunset times and day lengths
- [PVEducation: Elevation Angle](https://www.pveducation.org/pvcdrom/properties-of-sunlight/elevation-angle) -- solar elevation calculation methodology
- [UGA Extension: Raised Bed Dimensions](https://extension.uga.edu/publications/detail.html?number=C1027-4) -- ergonomic bed sizing
- [Deep Green Permaculture: Bed Sizing](https://deepgreenpermaculture.com/2019/04/29/raised-garden-beds-what-size-is-best/) -- child reach distances
- [Fine Gardening: DIY Starter Bed for Kids](https://www.finegardening.com/article/diy-starter-raised-bed-for-kids) -- child bed dimensions
- [Home Assistant Plant Monitor Integration](https://www.home-assistant.io/integrations/plant/) -- entity configuration
- [Old Farmer's Almanac Companion Planting Guide](https://www.almanac.com/companion-planting-guide-vegetables) -- companion planting relationships
- [Eartheasy Companion Planting for Raised Beds](https://learn.eartheasy.com/guides/companion-planting-for-raised-garden-beds/) -- bed-specific companion strategies
- [Zinkbakken Corten Beds](https://zinkbakken.dk/hojbede/hojbede-i-corten-stal) -- Danish corten steel bed supplier
- [Stålhaven Corten Beds](https://staalhaven.dk/collections/hojbede-cortenstal) -- Danish corten steel bed supplier
- [HA Community: Zigbee Soil Sensor Shootout](https://community.home-assistant.io/t/my-zigbee-soil-moisture-sensor-shootout/907192) -- sensor hardware comparison

**Confidence levels:**
- Sun path calculations: HIGH (formula-derived from known latitude, verified against TimeAndDate)
- Child ergonomic dimensions: HIGH (multiple extension service sources agree)
- Companion planting: MEDIUM (well-established practice, but not Denmark-specific validated)
- HA entity conventions: HIGH (official documentation)
- Shadow calculations: MEDIUM (formula correct, but actual building/tree heights are estimates)
- Bed placement: MEDIUM (based on property description, not surveyed -- verify with on-site observation)
