# Soil Sensor Hardware Recommendations

**Budget target:** 500-1000 DKK for 2 beds
**Strategy:** Zigbee-first (mesh network, HA native). LoRaWAN only as fallback if range fails.
**Coordinator assumed:** Sonoff ZBDongle-P or equivalent already running Zigbee2MQTT in Home Assistant.

---

## BUY THIS ONE: Haozee Tuya Zigbee Soil Tester (TS0601_soil)

**This is the primary recommendation.** One sensor per bed, 2 total.

| Spec | Value |
|------|-------|
| Protocol | Zigbee 3.0 (Tuya) |
| Measurements | Soil moisture (%) + soil temperature (C) |
| IP rating | IP66/IP67 (outdoor rated) |
| Battery | 2x AA, approximately 1 year life |
| Zigbee2MQTT | Supported as `TS0601_soil` (Tuya specific) |
| Price | ~150 DKK per unit (~750 DKK for 5) |
| Where to buy | AliExpress -- search "Haozee Tuya Zigbee soil sensor TS0601". Confirm IP66+ rating in listing. |

**Why this one:**
- Community sensor shootout winner -- best range, minimal unit-to-unit variance, stable long-term readings
- Reports both moisture and temperature in one device (matches our 2-sensor-per-bed HA schema)
- Tuya Zigbee devices are well-tested with Zigbee2MQTT; TS0601_soil has a dedicated converter
- Price point fits the budget: 2 units at ~150 DKK = ~300 DKK total

**Setup notes:**
- Pair through Zigbee2MQTT as a Tuya device
- Entity appears as `sensor.zigbee_soil_sensor_bed_a_moisture`, `_bed_b_moisture`, and `_temperature` after renaming
- May need TS0601_soil specific calibration offset in Zigbee2MQTT configuration if readings are consistently off
- Insert probe fully into soil (10-15cm depth) for accurate readings

---

## Alternative 1: ThirdReality 3RSM0147Z

| Spec | Value |
|------|-------|
| Protocol | Zigbee 3.0 |
| Measurements | Soil moisture (%) |
| IP rating | IP67 |
| Battery | 1x AA, up to 3 years |
| Zigbee2MQTT | Supported |
| Price | ~140 DKK per unit (~280 DKK for 2) |

**Tradeoffs:**
- Narrow useful moisture range (reports 50-70% with poor resolution outside that band)
- Bulky form factor -- may look oversized in 80x40cm terrace beds
- Reports as "humidity" in Zigbee2MQTT, requiring entity renaming or a Z2M converter workaround
- No temperature sensor -- would need separate temperature probes (adds cost and complexity)
- Better battery life (3 years vs 1 year) is the main advantage

**Verdict:** Acceptable backup if Haozee is unavailable. The narrow moisture range and missing temperature make it second choice.

---

## Alternative 2 (LoRaWAN Fallback): Dragino LSE01

| Spec | Value |
|------|-------|
| Protocol | LoRaWAN |
| Measurements | Soil moisture (%) + temperature (C) + electrical conductivity (EC) |
| IP rating | IP68 |
| Battery | Built-in 4000mAh, 2+ years |
| Price | ~500-650 DKK per unit |

**When to use:** ONLY if Zigbee range from the house coordinator to the backyard beds is insufficient (unlikely for Vejle property -- ~10-15m through one wall).

**Why not primary:**
- 2 units = 1000-1300 DKK -- 3-4x the Zigbee budget
- Requires a LoRaWAN gateway (~800-1200 DKK for Dragino LPS8 or similar)
- Total cost: 3300-4450 DKK -- exceeds budget target significantly
- More complex setup (gateway, network server, MQTT bridge to HA)
- EC sensor is nice but unnecessary for raised bed gardening

---

## NOT Recommended: Tuya GXM-01

**Do not buy.** Documented issues:
- Moisture readings stuck at 100% or 94% regardless of actual soil moisture
- Rapid battery drain (weeks instead of months)
- Manufacturer unresponsive to firmware/calibration complaints
- Multiple community reports of identical issues across batches

This sensor shares the Tuya Zigbee ecosystem with the Haozee but is a different (inferior) hardware design. The model numbers matter.

---

## Zigbee Range Extension

**Test first:** The Vejle property is ~10-15m from house to backyard beds. Zigbee 3.0 with the ZBDongle-P coordinator can typically reach 10-15m through one standard wall. This may work without any repeater.

**If range is insufficient:**
- **IKEA TRETAKT smart plug** (~100 DKK)
- Place in a weatherproof outdoor outlet box on the house exterior wall facing the garden
- Acts as a Zigbee router/repeater, extending mesh to the bed cluster
- Also functions as a switchable outdoor power outlet

**Alternative repeaters:** Any mains-powered Zigbee device acts as a repeater. An outdoor-rated smart plug is the simplest solution.

---

## Budget Summary

| Item | Qty | Unit (DKK) | Total (DKK) |
|------|-----|-----------|-------------|
| Haozee TS0601_soil sensor | 2 | ~150 | ~300 |
| AA batteries (spare set) | 4 | ~5 | ~20 |
| IKEA TRETAKT repeater (optional) | 1 | ~100 | ~100 |
| **Total** | | | **~320-420** |

Fits within the 500-1000 DKK budget target. The TRETAKT is optional -- test range first.

**Not included (assumed existing):**
- Zigbee coordinator (Sonoff ZBDongle-P or similar)
- Zigbee2MQTT addon in Home Assistant
- Home Assistant installation

---

## Setup Checklist

1. Confirm Zigbee coordinator is running in HA with Zigbee2MQTT
2. Order 2x Haozee TS0601_soil from AliExpress (allow 2-3 weeks shipping)
3. Insert 2x AA batteries in each sensor
4. Pair each sensor through Zigbee2MQTT (permit join, insert batteries to trigger pairing)
5. Rename entities in Zigbee2MQTT to match Haven naming: `zigbee_soil_sensor_bed_a`, `zigbee_soil_sensor_bed_b`
6. Place one sensor per bed, probe inserted 10-15cm into soil at bed center
7. Test range -- if readings drop out, add IKEA TRETAKT repeater
8. Optional: apply TS0601_soil calibration offset in Z2M if readings are consistently off vs a reference moisture meter
9. Verify entities appear in HA matching `data/ha/sensors.json` source entity references
