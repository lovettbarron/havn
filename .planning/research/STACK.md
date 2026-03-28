# Technology Stack: Haven Learning Garden

**Project:** Haven -- Danish backyard learning garden with smart home monitoring
**Domain:** Physical garden infrastructure + IoT sensor integration
**Researched:** 2026-03-26
**Overall confidence:** MEDIUM-HIGH (prices verified against Danish retailer websites; sensor compatibility verified against Home Assistant community testing)

---

## Recommended Stack

### 1. Raised Beds -- Corten Steel (Primary Recommendation)

Use corten steel. It develops a self-sealing rust patina that stops further corrosion (20+ year lifespan), is food-safe for vegetable growing, and gives the garden a warm architectural look that complements an oldervilla. Danish-made options keep shipping costs down and support local manufacturing.

| Supplier | Product | Dimensions (cm) | Price (DKK) | Notes |
|----------|---------|-----------------|-------------|-------|
| **byJEMA** | CUBY Corten | 150 x 80 x 40 | ~1,600-1,800 | 2mm bent corten, no base. Danish-made in Herning. Best value for quality. |
| **byJEMA** | CUBY Corten | 120 x 60 x 40 | ~1,345 | Smaller option for roof terrace (lighter). |
| **byJEMA** | EDGY Corten | 120 x 120 x 40 | ~2,200-2,500 | 3mm plate, premium finish. Square format good for companion planting. |
| **Gronfeld** | Corten no base | 60 x 80 x 40 | ~1,415 | 2mm corten. Danish-designed. |
| **Gronfeld** | Corten with base | 60 x 80 x 40 | ~2,326 | With base plate -- required for roof terrace to protect membrane. |
| **Stalhaven** | Corten 40cm | 100+ x 40 x 40 | from 1,300 | Laser-cut in Logstorr. Custom lengths available. |

**Confidence:** MEDIUM -- Prices scraped from retailer sites as of March 2026. byJEMA and Gronfeld confirmed Danish manufacturers. Exact prices may vary by configuration; contact suppliers for quotes.

**Recommendation for this project:**
- **Backyard beds (2x):** byJEMA CUBY 150x80x40 corten, no base (~3,200-3,600 DKK for pair)
- **Roof terrace bed (1x):** Gronfeld 40x80x40 corten WITH base (~1,200-1,400 DKK) -- base plate protects roof membrane and contains water runoff; smaller size manages weight on structure

**Total corten bed budget: ~4,400-5,000 DKK** (beds only, exceeds budget ceiling -- see budget alternatives below)

### 2. Raised Beds -- Budget Alternatives

| Supplier | Product | Dimensions (cm) | Price (DKK) | Notes |
|----------|---------|-----------------|-------------|-------|
| **Zinkbakken** | Galvanized steel | 80 x ? x 40 | 1,049 | Hand-bent and soldered in Denmark. 100% watertight. ~20 year lifespan. |
| **Zinkbakken** | Galvanized steel | 120 x ? x 40 | 1,199 | Larger format. Clean silver look. |
| **byJEMA** | CUBY Galvanized | 120 x 60 x 40 | ~1,345 | Same build quality as corten, just zinc-galvanized finish. |
| **Bauhaus/Silvan** | Flat-pack wood | Various | 200-600 | Cheap but 3-5 year lifespan. Pressure-treated wood raises food safety questions. |

**Confidence:** MEDIUM -- Zinkbakken prices from product page. byJEMA galvanized confirmed same price as corten for equivalent CUBY sizes.

**Budget-optimized recommendation:**
- **Backyard beds (2x):** Zinkbakken galvanized 120cm (~2,400 DKK for pair)
- **Roof terrace bed (1x):** Zinkbakken galvanized 80cm (~1,049 DKK)
- **Total budget bed cost: ~3,450 DKK** (leaves ~1,550 DKK for soil/seeds/tools within 5,000 DKK ceiling)

**Galvanized steel is food-safe.** Zinc leaching is minimal and zinc is actually a plant micronutrient. The concern is largely mythological -- soil pH in vegetable beds (neutral to slightly alkaline) keeps zinc stable. Both corten and galvanized are safe choices.

### 3. Soil System

A 40cm-tall bed at 150x80cm = 480 liters of soil per bed. Two backyard beds + one terrace bed = roughly 1,000-1,200 liters total.

#### Recommended Soil Layering (per 40cm bed)

| Layer | Depth | Material | Purpose |
|-------|-------|----------|---------|
| Bottom 5cm | Drainage | Coarse gravel or LECA pebbles | Prevents waterlogging. Essential for beds with base plates (terrace). |
| Middle 15cm | Base fill | Rough compost + garden waste | Nutrient reservoir as it decomposes. Saves money vs. pure bought soil. |
| Top 20cm | Growing layer | Purchased hojbedsmuld | Where roots live. Must be high quality. |

#### Soil Products (Danish Market)

| Product | Supplier | Volume | Price (DKK) | Composition |
|---------|----------|--------|-------------|-------------|
| **Hojbedsmuld Big Bag** | Grat.dk | 1,000 L | 1,257 | 2/3 Danish sifted gravel pit soil + 1/3 organic mushroom compost |
| **Hojbedsmuld Big Bag** | HaveHandel.dk | 1,000 L | 1,135 | Sphagnum-free, organic nutrients |
| **Hojbedsmuld** | Bauhaus | 1,000 L | ~910 (per liter at scale) | GreenBio brand: pit sand, compost, natural fertilizer, soil |
| **Hojbedsmuld** | Silvan (Champost) | 20 L bags | ~50/bag (~2,500/1000L) | 100% organic. Expensive at small volume. |
| **Hojbedsmuld** | HaveGlad.dk | 2,000 L | 1,575 (0.78 kr/L) | Cheapest per-liter if you need volume |

**Confidence:** HIGH -- Grat.dk pricing and composition verified from product page. Price comparison site bedmuld.dk cross-referenced.

**Recommendation:** Order 1x Big Bag (1,000 L) from Grat.dk or HaveHandel.dk. Delivered to curb in Jutland for free (Vejle is Jutland). Use the top 20cm of each bed with this product. Fill the bottom with free garden waste (branches, leaves, old plant material) topped with rough compost to save ~300 liters of purchased soil.

**Soil budget: ~1,100-1,300 DKK** for 1,000 L big bag with free delivery to Jutland.

#### Soil Amendments

| Product | Where to Buy | Price (DKK) | When to Use |
|---------|-------------|-------------|-------------|
| LECA pebbles (10 L) | Bauhaus/Silvan | ~50-80 | Drainage layer in terrace bed |
| Perlite (10 L) | Bauhaus/Silvan | ~60-80 | Mix into terrace bed soil for weight reduction |
| Kompost (composted) | Local municipality or own pile | Free-100 | Annual top-dressing each spring (2-3 cm layer) |

### 4. Sensors and Smart Home Integration

#### Zigbee Soil Sensors (Primary -- Recommended)

Use Zigbee because the family already has an established Zigbee network with repeaters planned near the garden.

| Sensor | Price (est. DKK) | Protocol | Measures | Battery | IP Rating | HA Compatible |
|--------|-----------------|----------|----------|---------|-----------|---------------|
| **Haozee Zigbee Soil Sensor** | ~150-200 (Amazon.de) | Zigbee 3.0 | Soil moisture, air temp, humidity | CR2032 or AA | IP66 | YES -- Zigbee2MQTT confirmed |
| **Third Reality 3RSM0147Z** | ~180-250 (Amazon.de) | Zigbee 3.0 | Soil moisture, temperature | AA (3-year life) | IP67 | YES -- Zigbee2MQTT confirmed |
| **Tuya GXM-01** | ~100-150 (AliExpress) | Zigbee 3.0 | Soil moisture, temperature | CR2450 | IP67 | YES -- ZHA and Z2M |

**Confidence:** HIGH -- Sensor compatibility confirmed via Home Assistant community shootout testing (2025). Haozee won the comparison for accuracy and reliability.

**Recommendation: Haozee Zigbee Soil Sensor** -- Winner of HA community shootout. Showed accurate readings (low when dry, near 100% when freshly watered, steady decline over days). No issues with stuck values or unavailable entities. The Third Reality is a solid second choice with better IP67 rating.

**What NOT to buy:**
- **Giexpress/Tuya generic** -- One unit dead on arrival, the other had stuck temperature readings in community testing.
- **Plaid Spruce** -- Magnet-based pairing is unreliable, requires repeated re-pairing.
- **Afra II** -- Multiple issues with unavailable entities and stuck readings.
- **Any WiFi soil sensor** -- Drains batteries in days outdoors. Zigbee sleep mode gives months of battery life.

**Buy 3 sensors** (one per bed). Total sensor budget: ~450-750 DKK.

#### LoRaWAN Soil Sensors (Future/Alternative)

Only consider LoRaWAN if Zigbee range proves insufficient (unlikely with planned repeaters). LoRaWAN requires a gateway (e.g., Dragino LPS8N, ~800-1,200 DKK) plus ChirpStack server setup -- significantly more complex.

| Sensor | Price (est. DKK) | Protocol | Battery Life | Notes |
|--------|-----------------|----------|--------------|-------|
| Dragino LSE01 | ~600-800 | LoRaWAN | Up to 10 years | Soil moisture + EC. Requires LoRa gateway + ChirpStack + MQTT to HA. |
| SenseCAP S2104 | ~800-1,000 | LoRaWAN | Up to 10 years | IP66, soil moisture + temp. Industrial grade. Overkill for backyard. |

**Confidence:** MEDIUM -- LoRaWAN-to-HA integration confirmed via ChirpStack + MQTT, but setup complexity is high. Not recommended for v1.

**Recommendation:** Start with Zigbee. Only move to LoRaWAN if signal problems arise at garden distance from house.

#### Zigbee Coordinator (Already in place)

The project notes an existing Zigbee network. For reference, the standard coordinator is:

| Device | Price (DKK) | Notes |
|--------|-------------|-------|
| SONOFF ZBDongle-P (CC2652P) | ~200-250 | Pre-flashed, plug-and-play with HA. +20dBm range. |
| SONOFF ZBDongle-E (EFR32MG21) | ~200-250 | Newer chip, also excellent. |

**No purchase needed** -- family already has Zigbee infrastructure.

### 5. Data Format and Home Assistant Integration

#### Plant Data Schema (JSON)

No dominant open standard exists for garden management data. The closest are:

| Schema/API | Status | Use For This Project |
|------------|--------|---------------------|
| **OpenPlantbook API** | Active, free, integrated with HA | Species lookup, care thresholds (min/max moisture, temp, light) |
| **Open-Plant-Schema** (GitHub) | Abandoned (2017) | Reference only for field naming conventions |
| **FIWARE Garden Data Model** | Active but enterprise-focused | Too heavy for home use |
| **Custom JSON schema** | -- | Best approach: define project-specific schema informed by OpenPlantbook fields |

**Confidence:** HIGH -- OpenPlantbook confirmed active and integrated with HA Plant Monitor.

**Recommendation:** Define a custom JSON schema per crop that includes:

```json
{
  "plant_id": "tomat-sungold",
  "common_name": "Tomat (Sungold)",
  "latin_name": "Solanum lycopersicum 'Sungold'",
  "bed_id": "bed-1-backyard",
  "planted_date": "2026-05-15",
  "expected_harvest_start": "2026-08-01",
  "growth_stages": [
    {"stage": "seedling", "duration_days": 14, "description": "First true leaves"},
    {"stage": "vegetative", "duration_days": 30, "description": "Growing tall, needs staking"},
    {"stage": "flowering", "duration_days": 14, "description": "Yellow flowers appearing"},
    {"stage": "fruiting", "duration_days": 45, "description": "Green to orange to ripe"}
  ],
  "thresholds": {
    "soil_moisture_min": 30,
    "soil_moisture_max": 80,
    "temperature_min": 10,
    "temperature_max": 35
  },
  "care": {
    "water_frequency": "daily in summer, every 2-3 days spring/autumn",
    "fertilize": "every 2 weeks during fruiting with tomato feed",
    "child_task": "Check if soil feels dry. Water at base, not leaves."
  },
  "difficulty": "medium",
  "child_appeal": "high -- colorful, sweet, snackable from plant"
}
```

#### Home Assistant Integration Stack

| Component | Purpose | Notes |
|-----------|---------|-------|
| **Zigbee2MQTT** (add-on) | Sensor data ingestion | Preferred over ZHA for device flexibility and external debugging |
| **Plant Monitor** (built-in integration) | Per-plant health status | Aggregates sensor data, shows "problem" state when thresholds exceeded |
| **OpenPlantbook** (HACS integration) | Species data lookup | Provides min/max thresholds for Plant Monitor; free API |
| **MQTT** | Sensor data transport | Zigbee2MQTT publishes to MQTT; also future LoRaWAN path via ChirpStack |
| **Automation** | Alerts | "Bed 1 soil moisture below 30% -- time to water!" notifications to phone |
| **Lovelace Dashboard** | Visual monitoring | Flower Card (HACS) for plant status display, gauge cards for moisture |

**Note on deprecation:** Legacy template entities are being deprecated in HA 2025.12 (removed 2026.6). Use the newer template entity format from the start.

### 6. Seeds and Plants

Buy seedlings (plugplanter) for most crops since the project scope excludes indoor seed starting. Seeds only for direct-sow crops (radishes, beans, peas, herbs).

#### Recommended Danish Suppliers

| Supplier | URL | Specialty | Notes |
|----------|-----|-----------|-------|
| **Frosnapperen** | froesnapperen.dk | Curated vegetable + flower seeds | Excellent variety descriptions, EU-sourced. Good for the "choose your own seeds" activity with the child. |
| **Frobutikken** | froebutikken.dk | Broad organic seed selection | Quality-focused. |
| **Gug Planteskole** | gugplanteskole.dk | Seedlings + seeds | Good for buying started plants (plugplanter) in spring. |
| **Jespers Planteskole** | jespersplanteskole.dk | Budget seeds | Large selection, inexpensive. |
| **Plantorama / local garden center** | plantorama.dk | Seedlings in season | Walk-in with the child in April/May to pick plants. The choosing IS the activity. |

**Confidence:** HIGH -- All suppliers verified as active Danish retailers.

**Budget for seeds/seedlings: 300-600 DKK** (a mix of 10-15 seed packets at ~20-30 DKK each, plus 5-8 seedlings at ~20-40 DKK each).

### 7. Tools and Supplies

| Item | Where to Buy | Price (DKK) | Why |
|------|-------------|-------------|-----|
| **Child-sized hand trowel** | Silvan/Bauhaus | 40-80 | Sized for small hands. The tool IS the engagement. |
| **Child-sized watering can (2-3L)** | Silvan/Bauhaus/Tiger | 30-60 | Must be small enough to carry when full. Daily ritual tool. |
| **Adult watering can (10L)** | Silvan/Bauhaus | 60-100 | For the parent to supplement. |
| **Garden twine** | Silvan | 30-50 | Staking tomatoes, marking rows. |
| **Plant labels (wood or zinc)** | Bauhaus/Silvan | 30-50 | Child writes/draws the plant name. Ownership marker. |
| **Small scissors/snips** | Silvan | 40-70 | For harvesting herbs, snipping flowers. Child-safe rounded tips. |
| **Kneeling pad** | Silvan/Bauhaus | 50-80 | Comfort for extended garden time. |
| **Bucket (10L)** | Anywhere | 20-40 | Carrying harvest, mixing soil, general utility. |

**Tool budget: ~300-500 DKK**

**What NOT to buy:**
- **Full-size garden tools** -- Too heavy for a 7-year-old, creates frustration not agency.
- **Automated irrigation timer** -- Explicitly out of scope. Watering IS the routine.
- **Expensive "kids garden kit" box sets** -- Usually low quality tools in wasteful packaging. Buy individual quality pieces.
- **Pesticides/herbicides** -- Not needed in raised beds with bought soil. Companion planting handles most pest issues.

---

## Budget Summary

### Premium Path (Corten Steel)

| Category | Cost (DKK) | Notes |
|----------|-----------|-------|
| Raised beds (3x corten) | 4,400-5,000 | 2x backyard + 1x terrace with base |
| Soil (1,000 L big bag) | 1,100-1,300 | Delivered free to Jutland |
| Sensors (3x Zigbee) | 450-750 | One per bed |
| Seeds and seedlings | 300-600 | Mix of packets and started plants |
| Tools and supplies | 300-500 | Child-sized essentials |
| **Total** | **6,550-8,150** | Exceeds 5,000 DKK budget |

### Budget Path (Galvanized Steel)

| Category | Cost (DKK) | Notes |
|----------|-----------|-------|
| Raised beds (3x galvanized) | 3,100-3,500 | Zinkbakken or byJEMA |
| Soil (1,000 L big bag) | 1,100-1,300 | Same quality soil |
| Seeds and seedlings | 300-600 | Same selection |
| Tools and supplies | 300-500 | Same tools |
| **Total (no sensors)** | **4,800-5,900** | Near budget with no sensors |
| Sensors (3x Zigbee, add later) | 450-750 | Phase 2 purchase |

### Recommended Approach: Hybrid

| Category | Cost (DKK) | Notes |
|----------|-----------|-------|
| 2x backyard beds: byJEMA CUBY Corten 150x80x40 | ~3,200-3,600 | The hero pieces. Visible, beautiful, 20+ year investment. |
| 1x terrace bed: Zinkbakken galvanized 80cm WITH saucer | ~1,050-1,200 | Saves money. Terrace bed is secondary. |
| Soil big bag | ~1,200 | Grat.dk or HaveHandel.dk |
| Seeds + seedlings | ~400 | Start modest, expand year 2 |
| Tools | ~350 | Child-sized essentials only |
| **Total** | **~6,200-6,750** | Over budget, but sensors deferred to later |
| Sensors (deferred) | ~500-700 | Add after first season when data format is proven |

**Rationale for deferring sensors:** The project already specifies "not immediate, but data format should be ready." JSON schema and HA integration architecture can be defined in season 1 while the child learns manual observation. Sensors arrive in season 2 as a "level up" moment -- the garden gets its own brain.

---

## Alternatives Considered

| Category | Recommended | Alternative | Why Not Alternative |
|----------|-------------|-------------|-------------------|
| Bed material | Corten steel | Pressure-treated wood | 3-5 year lifespan, chemicals leach into soil, looks shabby after 2 winters |
| Bed material | Corten steel | Cedar/larch wood | Not readily available in Denmark, expensive when imported, still rots in 8-10 years |
| Bed material | Corten steel | Recycled plastic lumber | Looks cheap, gets brittle in Danish frost, no thermal mass for soil warming |
| Soil | Purchased hojbedsmuld | DIY mix from components | More expensive per liter when buying sand, compost, and topsoil separately at retail. Big bag is optimized. |
| Sensors | Zigbee (Haozee) | WiFi sensors | Battery dies in days. Zigbee sleeps between readings = months of battery. |
| Sensors | Zigbee | LoRaWAN | Requires gateway purchase (~1,000 DKK), ChirpStack server setup, MQTT bridge. Overkill for 10-meter range. |
| Sensors | Zigbee | Bluetooth (Xiaomi Flora) | Range too short for outdoor beds. Not reliable through walls. |
| Data format | Custom JSON + OpenPlantbook | Off-the-shelf garden app | No integration with Home Assistant. Data locked in proprietary app. |
| Seed supplier | Frosnapperen | International seed banks | Danish suppliers stock varieties proven in zone 7b. International seeds may not be climate-appropriate. |

---

## Supplier Quick Reference

### Order Online (Deliver to Vejle)

| What | Supplier | URL | Delivery |
|------|----------|-----|----------|
| Corten beds | byJEMA | byjema.dk | 2-3 week production + shipping |
| Corten beds | Gronfeld | gronfeld.com | Ships from Denmark |
| Galvanized beds | Zinkbakken | zinkbakken.dk | Ships from Denmark |
| Soil big bag | Grat.dk | grat.dk | Free to Jutland, 1-2 days |
| Soil big bag | HaveHandel.dk | havehandel.dk | Check Jutland delivery |
| Sensors | Amazon.de | amazon.de | Ship to Denmark, 3-7 days |
| Seeds | Frosnapperen | froesnapperen.dk | Standard post |

### Buy In-Store (Vejle Area)

| What | Store | Notes |
|------|-------|-------|
| LECA, perlite, soil amendments | Bauhaus Vejle | Storegade/Vejle location |
| Small soil bags (emergency top-up) | Silvan | Champost hojbedsmuld 20 L bags |
| Tools, watering cans, labels | Silvan or Bauhaus | Compare prices, both carry basics |
| Seedlings (April-May) | Plantorama or local planteskole | Take the child. Let him choose. |

---

## Sources

### Raised Bed Suppliers (Verified)
- [byJEMA -- Danish corten/galvanized beds](https://byjema.dk/collections/hoejbed-corten-eller-galvaniseret)
- [Gronfeld -- Danish corten beds](https://gronfeld.com/collections/raised-beds-corten-steel)
- [Stalhaven -- Laser-cut steel beds](https://staalhaven.dk/collections/hojbede)
- [Zinkbakken -- Galvanized budget beds](https://www.zinkbakken.dk/hojbede.html)

### Soil Products (Verified)
- [Grat.dk -- Hojbedsmuld 1000L pricing and composition](https://grat.dk/muld/724-hojbedsmuld-big-bag-ca-1000-kg.html)
- [BedMuld.dk -- Price comparison across 15+ shops](https://bedmuld.dk/)
- [Bauhaus -- GreenBio hojbedsmuld](https://www.bauhaus.dk/greenbio-hojbedsmuld-1000-l)

### Sensor Technology (Verified)
- [HA Community Zigbee soil sensor shootout](https://community.home-assistant.io/t/my-zigbee-soil-moisture-sensor-shootout/907192)
- [Third Reality sensor -- HA device page](https://home-assistant-devices.com/en/device/third-reality-3rsm0147z)
- [Haozee sensor -- HA device page](https://home-assistant-devices.com/en/device/hobeian-zg-303z)
- [Dragino LSE01 LoRaWAN sensor](https://www.dragino.com/products/lora-lorawan-end-node/item/159-lse01.html)

### Home Assistant Integration (Verified)
- [HA Plant Monitor integration](https://www.home-assistant.io/integrations/plant/)
- [OpenPlantbook HA integration](https://github.com/Olen/home-assistant-openplantbook)
- [HA Plant component (Olen)](https://github.com/Olen/homeassistant-plant)

### Food Safety of Steel Beds
- [Gardenary -- Is it safe to garden in steel raised beds?](https://www.gardenary.com/blog/is-it-safe-to-garden-in-steel-raised-beds)

### Seed Suppliers (Verified Active)
- [Frosnapperen](https://froesnapperen.dk/)
- [Frobutikken](https://froebutikken.dk/)
- [Gug Planteskole](https://shop.gugplanteskole.dk/)
