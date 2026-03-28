# Home Assistant Setup Guide -- Haven Garden

A step-by-step walkthrough for configuring Home Assistant to monitor your Haven garden beds. Follow these 8 steps in order. Each step includes the exact YAML to paste.

> **Note:** This guide is a reference for when your Zigbee soil sensors arrive and are paired. You can set up the configuration now (sensors will show 0 values), or wait until the hardware is installed. Either way, the steps are the same.

---

## Step 1: Prerequisites

Before starting, confirm the following are in place:

1. **Home Assistant is running** -- you can access it at `http://homeassistant.local:8123`
2. **Zigbee2MQTT is installed** -- the add-on is running and connected to your Zigbee coordinator
3. **Haozee soil sensors are paired** -- each sensor appears in Zigbee2MQTT with moisture and temperature readings
4. **File editor access** -- you can edit `configuration.yaml` (via File Editor add-on or SSH)

### Entity Naming Convention

All Haven garden entities use the `haven_` prefix:

- Sensors: `sensor.haven_bed_a_moisture`, `sensor.haven_bed_b_temperature`, etc.
- Plant monitors: `plant.haven_bed_a`, `plant.haven_bed_b`
- Automations: `haven_bed_a_moisture_below_min`, etc.

This keeps garden entities grouped together and easy to find in Developer Tools.

### Expected Zigbee2MQTT Entity Names

The template sensors below expect your Zigbee2MQTT devices to create these entities:

| Bed | Moisture Entity | Temperature Entity |
|-----|----------------|--------------------|
| A | `sensor.zigbee_soil_sensor_bed_a_moisture` | `sensor.zigbee_soil_sensor_bed_a_temperature` |
| B | `sensor.zigbee_soil_sensor_bed_b_moisture` | `sensor.zigbee_soil_sensor_bed_b_temperature` |

> **Note:** If Zigbee2MQTT creates different entity names (based on how you named the devices during pairing), replace the source entity names in the template sensors in Step 2. Check your actual entity names in Developer Tools > States.

---

## Step 2: Template Sensors

Template sensors wrap the raw Zigbee sensor entities into the `haven_` namespace with proper device classes.

Open `configuration.yaml` and add the following block. If you already have a `template:` section, merge the sensor list under it.

```yaml
# Haven Garden -- Template Sensors
# Source: data/ha/sensors.json
template:
  - sensor:
      - name: "Haven Bed A Soil Moisture"
        unique_id: haven_bed_a_moisture
        unit_of_measurement: "%"
        device_class: moisture
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_moisture') | float(0) }}"
      - name: "Haven Bed A Soil Temperature"
        unique_id: haven_bed_a_temperature
        unit_of_measurement: "°C"
        device_class: temperature
        state: "{{ states('sensor.zigbee_soil_sensor_bed_a_temperature') | float(0) }}"
      - name: "Haven Bed B Soil Moisture"
        unique_id: haven_bed_b_moisture
        unit_of_measurement: "%"
        device_class: moisture
        state: "{{ states('sensor.zigbee_soil_sensor_bed_b_moisture') | float(0) }}"
      - name: "Haven Bed B Soil Temperature"
        unique_id: haven_bed_b_temperature
        unit_of_measurement: "°C"
        device_class: temperature
        state: "{{ states('sensor.zigbee_soil_sensor_bed_b_temperature') | float(0) }}"
```

### Check Configuration Before Restart

1. Go to **Developer Tools > YAML > Check Configuration**
2. If it says "Configuration valid!", proceed to restart
3. Go to **Settings > System > Restart** (or Developer Tools > YAML > Restart)

### What You Should See

After restart, go to **Developer Tools > States** and search for `haven`. You should see 4 new entities:

- `sensor.haven_bed_a_moisture` -- value will be 0.0 until sensors are installed
- `sensor.haven_bed_a_temperature` -- value will be 0.0 until sensors are installed
- `sensor.haven_bed_b_moisture` -- value will be 0.0 until sensors are installed
- `sensor.haven_bed_b_temperature` -- value will be 0.0 until sensors are installed

---

## Step 3: Entity Customization

Entity customization adds friendly display names and icons so your sensors look clear on dashboards and in the States list.

Open `configuration.yaml` and ensure you have the `homeassistant:` block with a `customize:` section. If you already have one, merge these entries into it.

```yaml
# Haven Garden -- Entity Customization
# Source: data/ha/customize.json
homeassistant:
  customize:
    sensor.haven_bed_a_moisture:
      friendly_name: "Bed A (Family Bed) - Soil Moisture"
      icon: mdi:water-percent
    sensor.haven_bed_a_temperature:
      friendly_name: "Bed A (Family Bed) - Soil Temperature"
      icon: mdi:thermometer
    sensor.haven_bed_b_moisture:
      friendly_name: "Bed B (His Bed) - Soil Moisture"
      icon: mdi:water-percent
    sensor.haven_bed_b_temperature:
      friendly_name: "Bed B (His Bed) - Soil Temperature"
      icon: mdi:thermometer
```

> **Tip:** You can also put this in a separate `customize.yaml` file and reference it with `homeassistant: customize: !include customize.yaml` in `configuration.yaml`. Either approach works.

### What You Should See

After restart, go to **Developer Tools > States** and search for `haven`. The "Friendly Name" column should now show the bed names (e.g., "Bed A (Family Bed) - Soil Moisture") instead of the raw entity IDs.

---

## Step 4: Plant Monitors

Plant monitors give you a single health status per bed. If moisture or temperature goes outside the thresholds, the plant entity shows "problem" instead of "ok".

Add the following to `configuration.yaml`:

```yaml
# Haven Garden -- Plant Monitors
# Source: data/ha/plants.json
plant:
  haven_bed_a:
    sensors:
      moisture: sensor.haven_bed_a_moisture
      temperature: sensor.haven_bed_a_temperature
    min_moisture: 40
    max_moisture: 55
    min_temperature: 0
  haven_bed_b:
    sensors:
      moisture: sensor.haven_bed_b_moisture
      temperature: sensor.haven_bed_b_temperature
    min_moisture: 40
    max_moisture: 50
    min_temperature: 0
```

### Threshold Reference

| Bed | Min Moisture | Max Moisture | Min Temperature | Notes |
|-----|-------------|-------------|-----------------|-------|
| A (Family Bed) | 40% | 55% | 0°C | 55% max from thyme; 40% min from broccoli |
| B (His Bed) | 40% | 50% | 0°C | 50% max from lamb's ear; 40% min from pea shoots |

> **Note:** Plant monitors will show "problem" until real sensor data flows. This is expected -- the 0.0 default values are below the min_moisture threshold. Once sensors report real readings, the status will correct itself.

### What You Should See

After restart, check **Developer Tools > States** for `plant.haven_bed_a` and `plant.haven_bed_b`. They will show as "problem" until sensors are reporting real data above the minimum thresholds.

---

## Step 5: Alert Automations

These 10 automations send push notifications when moisture or temperature crosses a threshold. They cover both spring and warm-season conditions.

Open `automations.yaml` (or the automations section of `configuration.yaml`). Add all 10 automations below.

> **Important:** Replace every `notify.mobile_app_REPLACEME` with your actual notification service name. See Step 6 for how to find it.

### Bed A (Family Bed) -- 7 Automations

```yaml
# Bed A: Moisture too low (spring/general)
- alias: "Haven: Bed A moisture below 40%"
  id: haven_bed_a_moisture_below_min
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_moisture
      below: 40
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed A (Family Bed) soil moisture is below 40% -- time to water!"

# Bed A: Moisture too high (thyme sensitive)
- alias: "Haven: Bed A moisture above 55%"
  id: haven_bed_a_moisture_above_max
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_moisture
      above: 55
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed A (Family Bed) soil moisture is above 55% -- soil may be too wet for thyme."

# Bed A: Frost warning (0°C)
- alias: "Haven: Bed A frost warning"
  id: haven_bed_a_temperature_below_frost
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_temperature
      below: 0
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden - FROST"
        message: "Frost warning for Bed A (Family Bed)! Soil temperature at 0°C. Cover sensitive plants with fleece."

# Bed A: Warm-season moisture too low (cucumbers/tomatoes)
- alias: "Haven: Bed A moisture below 45% (warm season)"
  id: haven_bed_a_moisture_below_min_warm
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_moisture
      below: 45
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed A (Family Bed) soil moisture is below 45% -- cucumbers and tomatoes need water!"

# Bed A: Warm-season moisture too high (borage)
- alias: "Haven: Bed A moisture above 65% (warm season)"
  id: haven_bed_a_moisture_above_max_warm
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_moisture
      above: 65
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed A (Family Bed) soil moisture is above 65% -- too wet for borage."

# Bed A: Cold warning for warm-season crops (4°C)
- alias: "Haven: Bed A cold warning 4°C (warm season)"
  id: haven_bed_a_temperature_below_frost_warm
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_temperature
      below: 4
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden - COLD"
        message: "Cold warning for Bed A (Family Bed)! Soil at 4°C -- cucumbers, basil, and peppers are frost-sensitive. Cover or bring indoors."

# Bed A: Cold warning for beans (2°C)
- alias: "Haven: Bed A cold warning 2°C (beans)"
  id: haven_bed_a_temperature_below_frost_beans
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_a_temperature
      below: 2
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden - COLD"
        message: "Cold warning for Bed A (Family Bed)! Soil at 2°C -- beans are frost-sensitive. Cover tonight."
```

### Bed B (His Bed) -- 3 Automations

```yaml
# Bed B: Moisture too low
- alias: "Haven: Bed B moisture below 40%"
  id: haven_bed_b_moisture_below_min
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_b_moisture
      below: 40
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed B (His Bed) soil moisture is below 40% -- time to water!"

# Bed B: Moisture too high (lamb's ear sensitive)
- alias: "Haven: Bed B moisture above 50%"
  id: haven_bed_b_moisture_above_max
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_b_moisture
      above: 50
      for:
        hours: 6
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden"
        message: "Bed B (His Bed) soil moisture is above 50% -- soil may be too wet for lamb's ear."

# Bed B: Frost warning (0°C)
- alias: "Haven: Bed B frost warning"
  id: haven_bed_b_temperature_below_frost
  triggers:
    - trigger: numeric_state
      entity_id: sensor.haven_bed_b_temperature
      below: 0
  actions:
    - action: notify.mobile_app_REPLACEME
      data:
        title: "Haven Garden - FROST"
        message: "Frost warning for Bed B (His Bed)! Soil temperature at 0°C. Cover sensitive plants with fleece."
```

### Why All 10 Are Always Active

The warm-season rules (4°C cold warning, 45% moisture for cucumbers) will simply never trigger during spring when temperatures are above 4°C and warm crops are not yet planted. There is no need to toggle automations on/off by season. Leave all 10 active year-round.

### What You Should See

After saving and reloading automations (**Settings > Automations > Reload**), go to **Settings > Automations & Scenes**. You should see 10 automations starting with "Haven:".

---

## Step 6: Find Your Notification Service Name

Every automation above uses `notify.mobile_app_REPLACEME` as a placeholder. You must replace this with your actual notification service name.

> **IMPORTANT:** The notification service name is specific to your phone. It will NOT work with the placeholder `REPLACEME`. You must complete this step for alerts to function.

### How to Find Your Service Name

1. Open Home Assistant
2. Go to **Developer Tools > Actions** (tab at the top)
3. In the **Action** dropdown, start typing `notify`
4. Look for an entry like `notify.mobile_app_andrews_iphone` or `notify.mobile_app_andrews_pixel`
5. That is your notification service name

### How the Name is Derived

The service name comes from your phone's device name:

- **iOS:** Settings > General > About > Name (e.g., "Andrew's iPhone" becomes `notify.mobile_app_andrews_iphone`)
- **Android:** Settings > About phone > Device name (e.g., "Andrew's Pixel" becomes `notify.mobile_app_andrews_pixel`)

The naming convention is: lowercase, spaces become underscores, apostrophes are removed.

### Replace in All Automations

Once you have your service name, do a find-and-replace in `automations.yaml`:

- **Find:** `notify.mobile_app_REPLACEME`
- **Replace with:** `notify.mobile_app_your_actual_device_name`

This replacement needs to happen in all 10 automations.

### Test Your Notification

1. Go to **Developer Tools > Actions**
2. Select your `notify.mobile_app_<your_device>` service
3. In **Service Data**, enter:

```yaml
title: "Haven Garden Test"
message: "If you see this, notifications are working!"
```

4. Click **Perform Action**
5. You should receive a push notification on your phone within a few seconds

### What You Should See

A push notification on your phone with the title "Haven Garden Test" and the test message. If it does not arrive, check that the Home Assistant Companion App is installed and logged in on your phone.

---

## Step 7: Lovelace Dashboard

Create dashboard cards to visualize moisture and temperature for both beds with gauge displays and plant health status.

### How to Add Cards

1. Open your dashboard
2. Click the three-dot menu (top right) > **Edit Dashboard**
3. Click **+ Add Card**
4. Select **Manual** card type
5. Click **Show Code Editor**
6. Paste the YAML below
7. Click **Save**

Repeat for each card (Bed A stack, then Bed B stack).

### Bed A (Family Bed) -- Vertical Stack

```yaml
type: vertical-stack
title: Bed A - Family Bed
cards:
  - type: gauge
    entity: sensor.haven_bed_a_moisture
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
    entity: sensor.haven_bed_a_temperature
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
    entity: plant.haven_bed_a
    name: Bed A Health
```

### Bed B (His Bed) -- Vertical Stack

```yaml
type: vertical-stack
title: Bed B - His Bed
cards:
  - type: gauge
    entity: sensor.haven_bed_b_moisture
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
    entity: sensor.haven_bed_b_temperature
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
    entity: plant.haven_bed_b
    name: Bed B Health
```

> **Note:** Add each vertical-stack as a separate card. You should see gauge needles once sensors are reporting real data. Until then, gauges will show 0.

### What You Should See

Two card stacks on your dashboard, each with a moisture gauge, a temperature gauge, and a plant health entity. The moisture gauge uses green/yellow/red zones based on plant thresholds. The temperature gauge highlights frost danger in red and cold warning in yellow.

---

## Step 8: Verification Checklist

After completing all steps above, walk through this checklist to confirm everything is working.

- [ ] **Developer Tools > States** shows `sensor.haven_bed_a_moisture` (and all 3 other haven sensors)
- [ ] **Developer Tools > States** shows `plant.haven_bed_a` and `plant.haven_bed_b`
- [ ] **Settings > Automations & Scenes** lists all 10 Haven automations (search "Haven")
- [ ] **Dashboard** shows gauge cards for both beds (values will be 0 until sensors are installed)
- [ ] **Test notification:** Developer Tools > Actions > select `notify.mobile_app_<your_device>` > call with test message > push notification received
- [ ] **No errors** in Settings > System > Logs after restart

> **Tip:** If any entity shows "unavailable" instead of a number, check that the source entity names in Step 2 match your actual Zigbee2MQTT entity names. Go to Developer Tools > States and search for "zigbee" to find the correct names.

---

## Quick Reference -- All Haven Entities

A complete list of every entity created by this guide, for easy lookup.

### Sensors (4)

| Entity ID | Type | Bed |
|-----------|------|-----|
| `sensor.haven_bed_a_moisture` | Soil Moisture (%) | Bed A (Family Bed) |
| `sensor.haven_bed_a_temperature` | Soil Temperature (C) | Bed A (Family Bed) |
| `sensor.haven_bed_b_moisture` | Soil Moisture (%) | Bed B (His Bed) |
| `sensor.haven_bed_b_temperature` | Soil Temperature (C) | Bed B (His Bed) |

### Plant Monitors (2)

| Entity ID | Bed | Min Moisture | Max Moisture | Min Temp |
|-----------|-----|-------------|-------------|----------|
| `plant.haven_bed_a` | Bed A (Family Bed) | 40% | 55% | 0C |
| `plant.haven_bed_b` | Bed B (His Bed) | 40% | 50% | 0C |

### Automations (10)

| Automation ID | Bed | Trigger | Threshold | Delay |
|---------------|-----|---------|-----------|-------|
| `haven_bed_a_moisture_below_min` | A | Moisture below | 40% | 6h |
| `haven_bed_a_moisture_above_max` | A | Moisture above | 55% | 6h |
| `haven_bed_a_temperature_below_frost` | A | Temp below | 0C | immediate |
| `haven_bed_a_moisture_below_min_warm` | A | Moisture below | 45% | 6h |
| `haven_bed_a_moisture_above_max_warm` | A | Moisture above | 65% | 6h |
| `haven_bed_a_temperature_below_frost_warm` | A | Temp below | 4C | immediate |
| `haven_bed_a_temperature_below_frost_beans` | A | Temp below | 2C | immediate |
| `haven_bed_b_moisture_below_min` | B | Moisture below | 40% | 6h |
| `haven_bed_b_moisture_above_max` | B | Moisture above | 50% | 6h |
| `haven_bed_b_temperature_below_frost` | B | Temp below | 0C | immediate |
