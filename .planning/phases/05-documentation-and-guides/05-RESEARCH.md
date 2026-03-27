# Phase 5: Documentation and Guides - Research

**Researched:** 2026-03-27
**Domain:** Garden documentation, reference guides, ASCII visualization, project continuity files
**Confidence:** HIGH

## Summary

Phase 5 produces six markdown documents: a property visualization (ASCII), a symptom-based troubleshooting guide, a difficulty-tiered crop reference, a neighbor vacation guide, a CLAUDE.md project file, and garlic autumn planting documentation. All deliverables are pure markdown -- no code, no data schemas, no external tools. The domain is technical writing with garden knowledge, not software engineering.

The primary challenge is cross-referencing accuracy: every document must reflect the actual crop positions, bed assignments, and care requirements established across Phases 1-3 and the data system from Phase 4. The secondary challenge is tone -- two different audiences (father-son pair vs. neighbor) with different knowledge levels and reading contexts.

**Primary recommendation:** Organize into 3 plans: (1) property visualization + CLAUDE.md project file (foundation documents that other docs reference), (2) troubleshooting guide + difficulty tiers (crop knowledge documents), (3) neighbor vacation guide + garlic autumn plan (externally-facing and future-facing documents).

<user_constraints>

## User Constraints (from CONTEXT.md)

### Locked Decisions
- Property visualization: ASCII art in markdown, full property overview with house, 5 beds, paths, water tap, nature corner, compass rose. Terrace as separate inset. Key dimensions included. Sun exposure as general zones.
- Troubleshooting guide: Dual structure (symptom-based main + crop index appendix). Reading level: father reads, child acts. Photo placeholders throughout. Severity system: green/yellow/red emoji + timeframe. Aphid "watch and wait" as featured entry.
- Difficulty tiers: Three tiers ("Can't fail" / "Needs care" / "Year 2 challenge"). One reference document classifying every planted crop.
- Neighbor vacation guide: Dual structure (daily checklist front page + per-bed detail cards). English with Danish plant names. Warm casual tone ("Help us keep our farm alive"). Emergency section at end. Content only -- physical delivery in Phase 6.
- CLAUDE.md project file: Comprehensive garden context + project structure. Data system pointers. Garden-adapted behavioral guardrails (vibes pattern). Living document with "Last updated" and "Current season status" sections.
- Garlic autumn plan: Document hardneck garlic planting for October 2026.

### Claude's Discretion
- Difficulty tier assignments for each crop
- Garlic documentation format and placement
- Exact troubleshooting symptom categories and which problems to cover
- Property visualization layout decisions (exact ASCII arrangement)
- How to cross-reference between documents (links, mentions, etc.)

### Deferred Ideas (OUT OF SCOPE)
None -- discussion stayed within phase scope.

</user_constraints>

<phase_requirements>

## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| DOCS-01 | Property visualization showing bed placement, sun patterns, compass orientation, and access paths | ASCII art pattern from bed-layout.md; reference photos in references/ directory; property data (~600m2, house ~120m2, terrace ~70m2, garage ~50m2) |
| DOCS-02 | Troubleshooting guide structured for father-son reference (visual, searchable, symptom-based) | Symptom categories identified from common raised bed problems; severity system defined in CONTEXT.md; crop-specific issues mapped from planting grids |
| DOCS-03 | Difficulty-tiered crop collection ("can't fail" / "needs care" / "Year 2 challenge") | All 27 crop varieties identified from Phase 2-3 grid maps and shopping lists; tier criteria based on Danish climate zone 7b conditions |
| DOCS-04 | Neighbor vacation guide with per-bed watering and harvest instructions | Bed assignments from bed-layout.md; watering frequencies derivable from crop data; Phase 6 handles physical delivery (VACN-04) |
| DOCS-05 | CLAUDE.md project file with full garden context for AI continuity | ~/book/vibes/CLAUDE.md template available; project structure established; Phase 4 data system schemas provide pointer targets |
| COOK-02 | Garlic hardneck cloves planted October 2026 for July 2027 harvest | Hardneck garlic planting timing: 4-6 weeks before ground freeze; for Denmark zone 7b this means September-October; bed assignment TBD (likely Bed D or dedicated space) |

</phase_requirements>

## Standard Stack

### Core
| Tool | Version | Purpose | Why Standard |
|------|---------|---------|--------------|
| Markdown | CommonMark | All deliverable format | Project convention -- every doc in docs/ is .md |
| ASCII art | N/A | Property visualization | Decided in CONTEXT.md -- consistent with project, no external tools needed |

### Supporting
| Resource | Purpose | When to Use |
|----------|---------|-------------|
| `docs/bed-layout.md` | Source of truth for bed positions, dimensions, orientation | Property viz, neighbor guide, CLAUDE.md |
| `docs/planting-grid-bed-[a-e].md` | Source of truth for what is planted where | Troubleshooting guide, difficulty tiers, neighbor guide |
| `docs/warm-season-shopping-list.md` | Phase 3 crop varieties and quantities | Difficulty tiers, troubleshooting guide |
| `references/*.png` | Property photos for spatial reference | Property visualization accuracy |
| `~/book/vibes/CLAUDE.md` | Template for behavioral guardrails section | CLAUDE.md project file |
| Phase 4 data schemas (when complete) | JSON schema locations, entity conventions | CLAUDE.md data system pointers |

### Alternatives Considered
| Instead of | Could Use | Tradeoff |
|------------|-----------|----------|
| ASCII art | Mermaid diagrams | Mermaid renders nicely on GitHub but loses fine spatial control; ASCII decided by user |
| Single mega-doc | Multiple focused docs | Multiple docs chosen -- each serves a different use case and audience |

## Architecture Patterns

### Recommended Project Structure
```
docs/
  property-map.md              # DOCS-01: Full property visualization
  troubleshooting-guide.md     # DOCS-02: Symptom-based plant doctor
  crop-difficulty-tiers.md     # DOCS-03: Can't fail / Needs care / Year 2
  neighbor-vacation-guide.md   # DOCS-04: "Help us keep our farm alive"
  garlic-autumn-plan.md        # COOK-02: October 2026 hardneck planting
CLAUDE.md                      # DOCS-05: Project file at repo root
```

### Pattern 1: Dual-Structure Reference Documents
**What:** Documents with a quick-access front section and detailed back section.
**When to use:** Troubleshooting guide (symptom lookup + crop index) and neighbor guide (daily checklist + per-bed cards).
**Rationale:** Users in crisis (plant dying) or time pressure (neighbor visiting) need fast answers. Detail is available but not required for action.

### Pattern 2: Cross-Reference by Filename
**What:** Reference other docs by relative path: `See docs/bed-layout.md` or `See docs/planting-grid-bed-a.md`.
**When to use:** When one document needs to point to detailed information in another.
**Rationale:** Consistent with existing project pattern (bed-layout.md already cross-references shopping-list.md). Avoids duplicating information.

### Pattern 3: Photo Placeholder Convention
**What:** `[PHOTO: description of what to capture]` markers throughout documents.
**When to use:** Troubleshooting guide (symptom photos) and neighbor guide (bed photos).
**Rationale:** Documents are created before the growing season. Real photos will be added as plants grow. Placeholders describe exactly what photo is needed.

### Anti-Patterns to Avoid
- **Information duplication across docs:** Do not copy full planting grids into the troubleshooting guide or neighbor guide. Reference the grid map docs instead. Exception: the neighbor guide SHOULD include simplified per-bed summaries since the neighbor will not have access to the full project.
- **Overly technical language in the neighbor guide:** The neighbor is assumed to have basic gardening knowledge but no context about this specific project. Write for someone seeing these beds for the first time.
- **Generic troubleshooting:** Every symptom entry should reference the specific crops in THIS garden, not generic "if you grow tomatoes..." advice.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Crop difficulty assessment | Arbitrary tier assignment | Evidence-based criteria (days to harvest, failure modes in zone 7b, care frequency, pest susceptibility) | Tiers must be defensible -- father will trust them for planning |
| Garlic planting schedule | Generic "plant in fall" advice | Zone 7b-specific timing (4-6 weeks before ground freeze, September-October for Denmark) | Danish frost timing differs from US/UK guides |
| Watering frequencies | Made-up schedules | Derive from crop water needs + bed type (reservoir vs non-reservoir) + season | Neighbor guide accuracy is critical -- overwatering or underwatering during vacation kills plants |

## Common Pitfalls

### Pitfall 1: ASCII Art That Doesn't Match Reality
**What goes wrong:** Property visualization shows beds in wrong positions relative to house, trees, or compass direction.
**Why it happens:** Rushing the spatial layout without checking reference photos.
**How to avoid:** Cross-reference every element against: (1) Google Earth top-down view, (2) bed-layout.md positions, (3) property description (house faces west, backyard extends east/northeast).
**Warning signs:** Compass rose pointing wrong way, beds on wrong side of house, terrace shown at ground level.

### Pitfall 2: Troubleshooting Guide Covers Wrong Crops
**What goes wrong:** Guide includes symptoms for crops not planted (e.g., carrot fly) or misses crops that are planted.
**Why it happens:** Using generic gardening troubleshooting instead of this garden's specific crop list.
**How to avoid:** Build the crop index first from the 5 planting grid maps, then write symptom entries only for problems that affect those specific crops.
**Warning signs:** Mentioning crops not in any bed grid, missing major planted crops from the index.

### Pitfall 3: Neighbor Guide Assumes Too Much Context
**What goes wrong:** Guide references bed letters (A, B, C...) that mean nothing to the neighbor, or uses project-internal terminology.
**Why it happens:** Author is deeply embedded in the project and forgets the neighbor has zero context.
**How to avoid:** Use physical descriptions ("the big metal bed closest to the fence") alongside bed labels. Include Danish plant names. Keep the daily checklist to 5-7 steps maximum.
**Warning signs:** References to "Phase 2 crops," bed letters without physical descriptions, English-only plant names.

### Pitfall 4: CLAUDE.md That's Too Long or Too Short
**What goes wrong:** Either a 2000-line file that no AI session will read fully, or a 20-line file that misses critical context.
**Why it happens:** No clear structure for what belongs in CLAUDE.md vs what belongs in the docs it points to.
**How to avoid:** Follow the vibes pattern: identity/context section (who, where, what), structure section (where things are in the repo), behavioral guardrails (what to push back on), current status (living section). Point to docs, don't duplicate them. Target 150-300 lines.
**Warning signs:** Duplicating full planting grids, missing behavioral guardrails, no "current status" section.

### Pitfall 5: Garlic Timing Wrong for Danish Climate
**What goes wrong:** Planting advice based on US Zone 7 (Virginia/Tennessee) instead of Danish Zone 7b (maritime climate, different frost patterns).
**Why it happens:** Most garlic planting guides are US-centric.
**How to avoid:** Use Denmark-specific frost dates. First hard frost in Vejle typically early-to-mid November. Plant 4-6 weeks before = late September to mid-October. Mulch heavily (10-15cm straw) after planting.
**Warning signs:** Recommending August planting (too early, causes excessive top growth) or November planting (too late, insufficient rooting).

## Code Examples

### ASCII Property Visualization Pattern
```
Established pattern from bed-layout.md:
- Compass directions at edges (NORTH at top)
- Dashed border for property boundary
- Box characters (+, -, |) for structures and beds
- Text labels inside boxes
- Legend below the diagram
- Dimensions in the legend, not cluttering the diagram
```

### Severity System for Troubleshooting
```markdown
## Leaves Turning Yellow

### Bottom leaves only, plant otherwise healthy
**Severity:** green No rush (cosmetic)

**What's happening:** Lower leaves naturally yellow and drop as the plant grows.
This is normal for: tomatoes, cucumbers, kale, peppers.

**What to do:** Nothing. Pick off yellowed leaves to keep the bed tidy.
**Child action:** "Can you find the yellow leaves and put them in the compost?"

[PHOTO: Yellow lower leaves on a healthy tomato plant]
```

### Neighbor Guide Daily Checklist Pattern
```markdown
## Daily Routine (10-15 minutes)

1. [ ] Water the two BIG metal beds (tomato bed + cucumber bed) --
       check reservoir indicator first, only water if dry
2. [ ] Water the two SMALL terrace beds -- these dry out fast,
       water every day in hot weather
3. [ ] Check the berry bed -- only water if soil feels dry 2cm down
4. [ ] Pick any ripe cherry tomatoes (they should be orange/red)
5. [ ] Pick any ripe cucumbers (10-12cm long)
6. [ ] Pick any ripe strawberries and raspberries
```

### CLAUDE.md Behavioral Guardrails Pattern
```markdown
## Guardrails

When working on this project, push back if I try to:
- **Add crops mid-season** -- the beds are full, new additions compete with existing plants
- **Expand beyond raised beds** -- the garden boundary is the 5 beds + mint pot, not the full property
- **Skip manual watering** -- manual watering is part of the child's agency-building routine, not a problem to solve
- **Over-automate** -- sensors inform decisions, they don't replace the child checking on plants
- **Complexify the data system** -- JSON files are reference data, not a production database
```

## Crop Difficulty Tier Research

Based on analysis of all 27 crop varieties planted across Phases 2-3 and their growing characteristics in Danish zone 7b:

### Tier 1: "Can't Fail" (low maintenance, fast results, very forgiving)
- Radish (any variety) -- 3-4 week harvest, almost impossible to kill
- Pea shoots -- 2-3 weeks, just water
- Baby lettuce (cut-and-come-again) -- 3 weeks to first cut
- Peas (Kelvedon Wonder) -- climb and produce with minimal care
- Chives -- perennial, indestructible
- Thyme -- drought tolerant, perennial
- Calendula -- self-sows, pest deterrent
- Borage -- vigorous, self-sows
- Nasturtium -- big seeds, fast growth, very forgiving
- Sunflower -- large seeds, dramatic growth, very hardy
- Lemon balm -- invasive if anything (too easy to grow)
- Lamb's ear -- drought tolerant perennial, nearly indestructible
- Viola/pansy -- cold hardy, long flowering

### Tier 2: "Needs Care" (regular attention, some failure modes)
- Strawberry Ostara/Korona -- need consistent water, slug protection, runner management
- Raspberry Autumn Bliss -- need pruning knowledge, first year is establishment
- Cherry tomato Sungold -- needs staking, consistent water, blossom end rot risk
- Cherry tomato Tumbling Tom -- less staking but still needs water consistency
- Cucumber Mini Munch -- needs warmth, trellis training, powdery mildew risk
- Sweet pepper Lipstick -- slow to ripen in Danish summers, needs warmth
- Basil -- frost sensitive, needs pinching, bolts in heat
- Spring onion White Lisbon -- easy but slow, needs consistent moisture
- Bush bean Provider -- frost sensitive, needs warm soil, relatively straightforward once established
- Mint -- easy but only because it's in a pot; without pot it would be tier 1 (invasive)

### Tier 3: "Year 2 Challenge" (long season, specific knowledge needed)
- Garlic (hardneck) -- autumn planting, 9-month cycle, scape removal, curing process
- Broccoli Calabrese -- long season, caterpillar magnet, timing-sensitive for side shoots
- Leek Musselburgh -- very long season (150+ days), needs blanching/hilling, transplant shock risk
- Kale Nero di Toscana -- technically easy but long season, caterpillar magnet, overwintering knowledge helps

**Confidence:** HIGH -- based on specific varieties chosen, Danish climate zone 7b, and raised bed growing conditions.

## Garlic Autumn Plan Research

### Timing for Vejle, Denmark (Zone 7b, Maritime Climate)
- **Plant:** Late September to mid-October 2026
- **Why this window:** 4-6 weeks before first hard frost (typically early-to-mid November in Vejle)
- **Too early risk:** Planting in August/early September causes excessive top growth that winter-kills
- **Too late risk:** Planting after late October gives insufficient rooting time

### Key Details for Documentation
- **Variety:** Hardneck (specific cultivar TBD -- common Danish options: Music, German Extra Hardy, Chesnok Red)
- **Source:** Seed garlic from garden center or online (e.g., solhaven.dk, floradania.dk). Do NOT plant supermarket garlic (treated, may carry disease)
- **Bed assignment:** Needs consideration -- Bed D (terrace) is logical if spring onions are finished, or a section of Bed C after warm-season crops clear
- **Planting depth:** 10-15cm deep, pointed end up, 15cm apart
- **Mulch:** 10-15cm straw mulch after planting, before first frost
- **Winter care:** None -- leave under mulch until spring
- **Spring emergence:** Green shoots appear March-April 2027
- **Scape removal:** June 2027 -- cut scapes when they curl (bonus harvest, edible)
- **Harvest:** July 2027 when lower leaves brown
- **Curing:** 2-3 weeks in dry, ventilated shade before storage

**Confidence:** MEDIUM -- timing is well-established for the climate zone, but specific Danish seed garlic sources need validation at purchase time.

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| Single big garden reference doc | Topic-specific reference docs with cross-references | Modern garden documentation pattern | Each doc serves one purpose, easier to find information |
| Text-only troubleshooting | Visual symptom matching with severity levels | Common in modern plant care apps (PictureThis, Greg) | Father can quickly assess urgency |
| Generic vacation watering notes | Per-bed instruction cards with photo placeholders | Best practice from community garden handoff protocols | Reduces error from neighbor unfamiliar with the garden |

## Open Questions

1. **Which bed gets garlic in October?**
   - What we know: Needs full sun, well-drained soil, 15cm spacing between cloves
   - What's unclear: Which bed will have space cleared by October (Bed C warm crops finishing? Bed D spring onions done?)
   - Recommendation: Document both options, decide at planting time based on what's cleared. Most likely Bed D (terrace, south end) where spring onions will be finished, or a section of Bed C after tomato/cucumber removal.

2. **Phase 4 completion status for CLAUDE.md**
   - What we know: CLAUDE.md should reference Phase 4 data system (JSON schemas, HA entities, weekly schedules)
   - What's unclear: Phase 4 may not be complete when Phase 5 executes (they can run in parallel)
   - Recommendation: Write CLAUDE.md with placeholder pointers to Phase 4 outputs. Use file paths from 04-01-PLAN.md and 04-02-PLAN.md (data/schemas/, data/crops/, data/schedules/). Mark as "pending Phase 4" if not yet created.

3. **Vacation timing for neighbor guide specificity**
   - What we know: Guide needs per-bed watering frequencies and harvest instructions
   - What's unclear: Exact vacation dates (affects which crops will be harvestable)
   - Recommendation: Write the guide for peak summer (July-August) when most crops are producing. This covers the most likely vacation window and the highest-maintenance period.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual validation (documentation phase -- no code to test) |
| Config file | N/A |
| Quick run command | Visual inspection of each document |
| Full suite command | Cross-reference check: verify every crop in grid maps appears in troubleshooting guide and difficulty tiers |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| DOCS-01 | Property viz shows beds, sun, compass, paths | manual-only | Visual comparison against reference photos | N/A |
| DOCS-02 | Troubleshooting guide is symptom-based, severity-labeled | manual-only | Verify all 27 crops appear in crop index appendix | N/A |
| DOCS-03 | Every crop classified into exactly one difficulty tier | manual-only | Count crops in tiers vs total planted crops (should be 27) | N/A |
| DOCS-04 | Neighbor guide has daily checklist + per-bed cards | manual-only | Verify all 5 beds have detail cards | N/A |
| DOCS-05 | CLAUDE.md captures full context with guardrails | manual-only | Verify behavioral guardrails section exists, file paths are valid | N/A |
| COOK-02 | Garlic planting documented for October 2026 | manual-only | Verify planting window, depth, spacing, mulch instructions present | N/A |

**Justification for manual-only:** This phase produces documentation, not code. Validation is content accuracy and completeness, not functional behavior. The planner should include cross-reference verification steps in task definitions.

### Sampling Rate
- **Per task commit:** Author reviews against source docs
- **Per wave merge:** Cross-reference all crop mentions against master crop list from planting grids
- **Phase gate:** All 6 documents exist, all 27 crops accounted for in tiers and troubleshooting index

### Wave 0 Gaps
None -- no test infrastructure needed for a documentation phase.

## Sources

### Primary (HIGH confidence)
- `docs/bed-layout.md` -- bed positions, dimensions, orientation, property overview
- `docs/planting-grid-bed-[a-e].md` -- all crop positions and varieties
- `docs/warm-season-shopping-list.md` -- Phase 3 crop varieties
- `references/description-of-property.png` -- property area data (~600m2 plot, ~120m2 house, ~70m2 terrace, ~50m2 garage)
- `references/google-earth-top-down.png` -- aerial view for property visualization
- `~/book/vibes/CLAUDE.md` -- behavioral guardrails template pattern
- `.planning/phases/04-data-system-and-schedules/04-01-PLAN.md` -- Phase 4 data system file paths
- `.planning/phases/05-documentation-and-guides/05-CONTEXT.md` -- all user decisions for this phase

### Secondary (MEDIUM confidence)
- [Garlic planting timing for cold regions](https://fromsoiltosoul.ca/7-easy-steps-for-planting-hardneck-garlic-in-cold-regions/) -- 4-6 weeks before freeze, verified against multiple sources
- [Old Farmer's Almanac garlic planting](https://www.almanac.com/planting-garlic-fall) -- fall planting timing
- [Garden.org Copenhagen planting calendar](https://garden.org/apps/calendar/?q=copenhagen) -- Denmark-specific dates
- [Growing in the Garden troubleshooting](https://growinginthegarden.com/garden-troubleshooting-guide-how-to-identify-solve-common-garden-problems/) -- symptom category patterns

### Tertiary (LOW confidence)
- Danish seed garlic sources (solhaven.dk, floradania.dk) -- mentioned but not verified as current suppliers

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH -- pure markdown documentation, established project patterns
- Architecture: HIGH -- document structure decisions locked in CONTEXT.md, patterns clear from existing docs
- Pitfalls: HIGH -- based on analysis of project-specific data (crop lists, bed assignments, audience needs)
- Garlic timing: MEDIUM -- well-established for zone 7b but Danish maritime climate nuances may vary

**Research date:** 2026-03-27
**Valid until:** 2026-10-31 (stable -- documentation patterns don't change; garlic timing relevant through October 2026)
