# Phase 10: Home Assistant Setup - Research

**Researched:** 2026-03-28
**Domain:** Home Assistant configuration (YAML), Lovelace dashboards, automation notifications
**Confidence:** HIGH

## Summary

Phase 10 produces documentation artifacts -- a setup walkthrough, a dashboard YAML snippet, and notification target instructions -- not live HA code. All the structured data already exists in `data/ha/` (sensors.json, plants.json, alert-rules.json, customize.json) and `data/sensors/sensor-recommendations.md`. The phase converts this prepared JSON into copy-pasteable YAML with step-by-step instructions for a father who already runs Home Assistant.

The key insight is that every YAML snippet already exists embedded in the JSON files (via `yaml_output` fields). The walkthrough's job is to sequence these snippets into a coherent setup flow, explain where each goes in `configuration.yaml`, and call out the one thing that cannot be pre-configured: the notification service name.

**Primary recommendation:** Create a single `docs/ha-setup-guide.md` walkthrough document that walks through sensor configuration, plant monitors, alert automations, and dashboard setup in numbered steps, with all YAML blocks ready to paste. Keep it simple -- this is reference data documentation, not a production system.

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| HAIG-01 | Step-by-step HA setup walkthrough for configuring sensors, plant monitors, and alerts | Walkthrough document sequencing existing JSON yaml_output fields into configuration.yaml steps. Sensor templates, plant monitor config, and automation YAML all documented below. |
| HAIG-02 | Basic Lovelace dashboard YAML showing per-bed moisture and temperature cards | Gauge cards for moisture (with severity thresholds matching plant monitor min/max) and entities card for temperature. YAML patterns documented below. |
| HAIG-03 | Alert rule notification target documented as requiring user-specific configuration | notify.mobile_app_<device_name> service is device-specific. Instructions for finding the correct service name via Developer Tools documented below. |
</phase_requirements>

## Standard Stack

This phase produces markdown documentation with embedded YAML. No libraries or packages are involved.

### Core HA Components Used

| Component | HA Docs Path | Purpose | Why Standard |
|-----------|-------------|---------|--------------|
| Template sensors | `/integrations/template/` | Wrap Zigbee raw sensors into havn_ namespace | Native HA, no custom components needed |
| Plant Monitor | `/integrations/plant/` | Per-bed health monitoring with thresholds | Built-in integration, ~2000 active installs, community maintained |
| Automations | `/docs/automation/yaml/` | Alert rules for moisture/temperature thresholds | Core HA feature |
| Lovelace gauge card | `/dashboards/gauge/` | Moisture display with color severity | Built-in card, no HACS dependency |
| Lovelace entities card | `/dashboards/entities/` | Temperature and sensor overview | Built-in card |
| Mobile App notify | `/integrations/mobile_app/` | Push notifications to father's phone | Standard companion app integration |

### No Custom Components

The walkthrough must use ONLY built-in HA integrations. No HACS cards, no custom components. This keeps the setup reproducible and avoids maintenance burden on a non-developer user.

## Architecture Patterns

### Existing Data Structure (Source of Truth)

All HA configuration data already exists in `data/ha/`:

```
data/ha/
  sensors.json      -- 4 template sensors (moisture + temp for beds A, B)
  plants.json       -- 2 plant monitors with thresholds per bed
  alert-rules.json  -- 10 automation rules (moisture + frost alerts)
  customize.json    -- Friendly names and icons for all entities
```

Each JSON file contains a `yaml_output` field with pre-formatted YAML. The walkthrough extracts and sequences these.

### Walkthrough Document Structure

```
docs/ha-setup-guide.md
  Step 1: Prerequisites (what must exist before starting)
  Step 2: Template sensors (configuration.yaml)
  Step 3: Entity customization (customize.yaml)
  Step 4: Plant monitors (configuration.yaml)
  Step 5: Alert automations (automations.yaml)
  Step 6: Find your notification service name
  Step 7: Lovelace dashboard (manual YAML card config)
  Step 8: Verification checklist
```

### Lovelace Dashboard Layout

Two sections, one per bed. Each section has:
- Gauge card for moisture (with green/yellow/red severity matching plant thresholds)
- Gauge card for temperature (with frost warning colors)
- Plant monitor entity showing overall bed health status

```yaml
# Bed A moisture gauge with severity colors
type: gauge
entity: sensor.havn_bed_a_moisture
name: Bed A Soil Moisture
unit: '%'
min: 0
max: 100
needle: true
severity:
  green: 40    # min_moisture threshold
  yellow: 30   # warning zone
  red: 0       # critical dry
```

```yaml
# Bed A temperature gauge with frost warning
type: gauge
entity: sensor.havn_bed_a_temperature
name: Bed A Soil Temperature
unit: 'C'
min: -5
max: 40
needle: true
segments:
  - from: -5
    color: '#2196F3'   # blue = frost danger
  - from: 0
    color: '#FF9800'   # orange = cold warning
  - from: 4
    color: '#4CAF50'   # green = safe for all crops
  - from: 35
    color: '#F44336'   # red = heat stress
```

### Automation YAML Pattern

The alert-rules.json uses a `delay_hours` field. In HA, this maps to the `for` parameter on `numeric_state` triggers:

```yaml
automation:
  - alias: "Havn: Bed A moisture below 40%"
    id: havn_bed_a_moisture_below_min
    triggers:
      - trigger: numeric_state
        entity_id: sensor.havn_bed_a_moisture
        below: 40
        for:
          hours: 6
    actions:
      - action: notify.mobile_app_REPLACEME
        data:
          title: "Havn Garden"
          message: "Bed A (Family Bed) soil moisture is below 40% -- time to water!"
```

### Notification Service Name Pattern

The `notify.mobile_app` placeholder in alert-rules.json is intentional. The actual service name is:

```
notify.mobile_app_<device_name>
```

Where `<device_name>` is derived from the phone name in Settings > General > About (iOS) or Settings > About phone (Android), with spaces replaced by underscores and lowercased.

**How to find it:** Developer Tools > Actions > search "notify" in the Action dropdown. The correct service will appear as `notify.mobile_app_andrews_iphone` or similar.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Sensor data transformation | Custom scripts to transform JSON to YAML | Pre-existing `yaml_output` fields in JSON files | Already done in Phase 4/7 |
| Dashboard design | Complex custom card layouts | Built-in gauge + entities cards | No HACS dependencies, father can maintain |
| Notification routing | Complex notification groups or conditional logic | Single `notify.mobile_app_<device>` target | Only one user (father), keep it simple |
| Seasonal threshold switching | Automation blueprints or input_select helpers | Document both spring and warm-season rules as separate automations | Matches existing alert-rules.json structure which has both sets |

**Key insight:** This phase is documentation, not implementation. The JSON data system already contains all the configuration. The walkthrough sequences it for a human to copy-paste.

## Common Pitfalls

### Pitfall 1: YAML Indentation Errors
**What goes wrong:** User pastes YAML into configuration.yaml with wrong indentation, HA fails to start.
**Why it happens:** YAML is whitespace-sensitive and the walkthrough will contain nested structures.
**How to avoid:** Provide complete, self-contained YAML blocks with explicit indentation. Include a "check configuration" step (Developer Tools > Check Configuration) before restart.
**Warning signs:** HA logs show "invalid configuration" after restart.

### Pitfall 2: Entity Names Don't Match
**What goes wrong:** Template sensors reference `sensor.zigbee_soil_sensor_bed_a_moisture` but Zigbee2MQTT creates a different entity name.
**Why it happens:** Z2M entity naming depends on device name set during pairing.
**How to avoid:** Document the expected source entity names AND explain how to rename devices in Z2M to match. Include a verification step: "Check Developer Tools > States for your actual entity names."
**Warning signs:** Template sensors show "unknown" or 0.0 values.

### Pitfall 3: Notification Service Not Found
**What goes wrong:** Automation fails with "service not found" for notify.mobile_app.
**Why it happens:** The service name is device-specific and must be replaced with the actual device name.
**How to avoid:** HAIG-03 specifically addresses this. Use a prominent callout box in the walkthrough: "REPLACE THIS with your actual service name."
**Warning signs:** Automation trace shows failed action.

### Pitfall 4: Lovelace YAML Mode Deprecation
**What goes wrong:** User tries to use `mode: yaml` for Lovelace configuration.
**Why it happens:** HA 2026.8 will remove legacy `mode: yaml` for dashboards.
**How to avoid:** Use the manual card editor (UI-based) with YAML pasted in, not a YAML-mode dashboard file. The walkthrough should instruct: "Edit dashboard > Add card > Show code editor > Paste YAML."
**Warning signs:** Deprecation warning in HA logs.

### Pitfall 5: Plant Monitor Shows "Problem" Immediately
**What goes wrong:** Plant entity goes to "problem" state right after setup because sensors haven't reported yet.
**Why it happens:** Plant monitor evaluates thresholds on initial load when sensor state is unknown/0.
**How to avoid:** Document that this is expected before sensors are physically installed and reporting. The plant monitor will show correct state once real data flows.

## Code Examples

### Template Sensor YAML (from sensors.json yaml_output)

```yaml
# configuration.yaml
template:
  - sensor:
      - name: "Havn Bed A Soil Moisture"
        unique_id: havn_bed_a_moisture
        unit_of_measurement: "%"
        device_class: moisture
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_moisture') | float(0) }}"
      - name: "Havn Bed A Soil Temperature"
        unique_id: havn_bed_a_temperature
        unit_of_measurement: "C"
        device_class: temperature
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_temperature') | float(0) }}"
      - name: "Havn Bed B Soil Moisture"
        unique_id: havn_bed_b_moisture
        unit_of_measurement: "%"
        device_class: moisture
        state: "{{ states('sensor.zigbee_soil_sensor_bed_b_moisture') | float(0) }}"
      - name: "Havn Bed B Soil Temperature"
        unique_id: havn_bed_b_temperature
        unit_of_measurement: "C"
        device_class: temperature
        state: "{{ states('sensor.zigbee_soil_sensor_bed_b_temperature') | float(0) }}"
```

### Plant Monitor YAML (from plants.json yaml_output)

```yaml
# configuration.yaml
plant:
  havn_bed_a:
    sensors:
      moisture: sensor.havn_bed_a_moisture
      temperature: sensor.havn_bed_a_temperature
    min_moisture: 40
    max_moisture: 55
    min_temperature: 0
  havn_bed_b:
    sensors:
      moisture: sensor.havn_bed_b_moisture
      temperature: sensor.havn_bed_b_temperature
    min_moisture: 40
    max_moisture: 50
    min_temperature: 0
```

### Entity Customization YAML (from customize.json yaml_output)

```yaml
# customize.yaml (referenced from configuration.yaml)
homeassistant:
  customize:
    sensor.havn_bed_a_moisture:
      friendly_name: "Bed A (Family Bed) - Soil Moisture"
      icon: mdi:water-percent
    sensor.havn_bed_a_temperature:
      friendly_name: "Bed A (Family Bed) - Soil Temperature"
      icon: mdi:thermometer
    sensor.havn_bed_b_moisture:
      friendly_name: "Bed B (His Bed) - Soil Moisture"
      icon: mdi:water-percent
    sensor.havn_bed_b_temperature:
      friendly_name: "Bed B (His Bed) - Soil Temperature"
      icon: mdi:thermometer
```

### Automation Example (derived from alert-rules.json)

```yaml
# automations.yaml
- alias: "Havn: Bed A moisture below 40%"
  id: havn_bed_a_moisture_below_min
  triggers:
    - trigger: numeric_state
      entity_id: sensor.havn_bed_a_moisture
      below: 40
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Havn Garden"
        message: "Bed A (Family Bed) soil moisture is below 40% -- time to water!"

- alias: "Havn: Bed A frost warning"
  id: havn_bed_a_temperature_below_frost
  triggers:
    - trigger: numeric_state
      entity_id: sensor.havn_bed_a_temperature
      below: 0
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Havn Garden - FROST"
        message: "Frost warning for Bed A (Family Bed)! Soil temperature at 0C. Cover sensitive plants with fleece."
```

### Lovelace Dashboard Cards (paste via UI card editor)

```yaml
# Vertical stack for Bed A
type: vertical-stack
title: Bed A - Family Bed
cards:
  - type: gauge
    entity: sensor.havn_bed_a_moisture
    name: Soil Moisture
    unit: '%'
    min: 0
    max: 100
    needle: true
    severity:
      green: 40
      yellow: 25
      red: 0
  - type: gauge
    entity: sensor.havn_bed_a_temperature
    name: Soil Temperature
    unit: 'C'
    min: -5
    max: 40
    needle: true
    severity:
      green: 4
      yellow: 0
      red: -5
  - type: entity
    entity: plant.havn_bed_a
    name: Bed A Health
```

### Finding Your Notification Service Name

```
1. Open Home Assistant
2. Go to Developer Tools > Actions
3. In the "Action" dropdown, type "notify"
4. Look for: notify.mobile_app_<your_device_name>
   Example: notify.mobile_app_andrews_iphone
5. Replace every "notify.mobile_app_REPLACEME" in automations.yaml
   with your actual service name
```

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| `mode: yaml` Lovelace dashboards | UI-managed dashboards with YAML card editor | HA 2026.8 removes legacy mode | Walkthrough must use "Add card > code editor" flow, not yaml mode |
| `service:` in automations | `action:` in automations | HA 2024.x | Use `action:` not `service:` in all YAML examples |
| `notify.notify` generic | `notify.mobile_app_<device>` specific | HA 2023+ | Must document device-specific service name |
| `platform: template` sensors | `template:` top-level key | HA 2021.12+ | Use modern template sensor format |

**Deprecated/outdated:**
- `mode: yaml` for Lovelace: Being removed in HA 2026.8. Use UI dashboard with YAML card editor instead.
- `service:` keyword in automations: Replaced by `action:` keyword. Both still work but `action:` is the current standard.
- Legacy `platform: template` sensor format: Replaced by top-level `template:` key.

## Open Questions

1. **Seasonal automation switching**
   - What we know: alert-rules.json contains both spring (0C frost) and warm-season (4C cold, 45% moisture) rules for Bed A. These are separate automations, not conditional.
   - What's unclear: Should the walkthrough include instructions for enabling/disabling seasonal automations, or leave all active year-round?
   - Recommendation: Document all automations as always-on. The warm-season rules (4C threshold) will simply never trigger in spring when temps are above 4C anyway. Simpler than teaching automation toggling.

2. **Sensors not yet purchased**
   - What we know: Haozee sensors are recommended but not yet ordered (v2 scope per IOT-V2-01).
   - What's unclear: Should the walkthrough be written as "do this now" or "do this when you have sensors"?
   - Recommendation: Frame as a reference guide for when sensors arrive. Include a "Prerequisites" section listing what must exist first (HA running, Zigbee2MQTT, sensors paired).

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual verification (documentation phase) |
| Config file | N/A |
| Quick run command | Visual review of YAML syntax |
| Full suite command | HA Developer Tools > Check Configuration |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| HAIG-01 | Walkthrough covers sensors, plant monitors, alerts | manual-only | Review `docs/ha-setup-guide.md` for completeness | Wave 0 |
| HAIG-02 | Dashboard YAML shows per-bed moisture/temp cards | manual-only | Paste YAML into HA card editor, verify render | Wave 0 |
| HAIG-03 | Notification target documented as user-specific | manual-only | Search walkthrough for REPLACEME placeholder + instructions | Wave 0 |

### Sampling Rate
- **Per task commit:** Verify YAML blocks parse (no syntax errors)
- **Per wave merge:** Review complete walkthrough flow end-to-end
- **Phase gate:** All three HAIG requirements addressed in walkthrough

### Wave 0 Gaps
None -- this is a documentation-only phase. No test infrastructure needed.

## Sources

### Primary (HIGH confidence)
- `data/ha/sensors.json` - Template sensor definitions with yaml_output
- `data/ha/plants.json` - Plant monitor configs with thresholds and yaml_output
- `data/ha/alert-rules.json` - 10 automation rules with messages in EN/DA
- `data/ha/customize.json` - Entity customization with yaml_output
- `data/sensors/sensor-recommendations.md` - Haozee TS0601_soil sensor details
- [Plant Monitor Integration](https://www.home-assistant.io/integrations/plant/) - Official HA docs
- [Automation Triggers](https://www.home-assistant.io/docs/automation/trigger/) - numeric_state trigger format
- [Gauge Card](https://www.home-assistant.io/dashboards/gauge/) - Lovelace gauge configuration
- [Entities Card](https://www.home-assistant.io/dashboards/entities/) - Lovelace entities configuration

### Secondary (MEDIUM confidence)
- [Mobile App Notify](https://companion.home-assistant.io/docs/notifications/notifications-basic/) - Notification service naming
- [HA Community: Lovelace YAML update](https://community.home-assistant.io/t/help-with-lovelace-yaml-configuration-needs-update/984086) - mode: yaml deprecation timeline

### Tertiary (LOW confidence)
- HA 2026.8 removal of legacy YAML mode -- based on community forum reports, not official release notes yet

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH - all built-in HA components, official docs verified
- Architecture: HIGH - existing JSON data provides all configuration, walkthrough is sequencing
- Pitfalls: HIGH - common HA configuration issues well-documented in community

**Research date:** 2026-03-28
**Valid until:** 2026-06-28 (stable -- HA plant monitor and automation YAML unlikely to change significantly)
