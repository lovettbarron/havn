# Phase 6: Vacation Preparation - Research

**Researched:** 2026-03-27
**Domain:** Garden vacation survival protocols, mulching, pre-departure logistics, neighbor handoff
**Confidence:** HIGH

## Summary

Phase 6 is a logistics and execution phase, not a technology phase. All infrastructure (reservoirs, beds, plantings) and documentation (neighbor guide) already exist from earlier phases. This phase validates that the reservoir system works as designed, executes mulching across all beds, runs a 3-day pre-departure countdown with the child, and delivers the printed neighbor guide with a walk-through.

The reservoir build doc claims 2-4 days of water autonomy per fill, extendable to 3-5 days with a full reservoir plus top watering. The CONTEXT.md specifies a 5-day dry-run test, which is deliberately beyond the documented 3-5 day claim -- this tests worst-case performance. If the reservoir fails the 5-day test, the fallback is increasing neighbor visit frequency (every 2-3 days instead of every 3 days), not adding hardware.

The primary deliverables are: (1) a tested and validated reservoir system, (2) mulched beds, (3) a completed harvest of everything showing color, (4) a printed neighbor guide handed off with a walk-through, and (5) a pre-departure checklist document (printable + JSON).

**Primary recommendation:** Structure this phase as a 3-wave execution: Wave 1 creates the pre-departure checklist document and reservoir test protocol. Wave 2 covers mulching and harvest protocols. Wave 3 handles neighbor handoff logistics and the final countdown session script.

<user_constraints>
## User Constraints (from CONTEXT.md)

### Locked Decisions
- **Reservoir testing protocol:** 5-day dry-run test. Fill reservoir, stop manual watering, check soil daily for 5 consecutive days. Pass criteria: soil at root depth (5-10cm) stays damp via finger test. Top 2-3cm drying out is acceptable. Daily observations logged. Child is daily soil check partner. If reservoir fails: increase neighbor visit frequency to every 2-3 days (no new hardware). Must be completed before July departure.
- **Mulching approach:** Mixed material strategy -- straw for veggie beds, bark chips for perennial/berry/herb beds. All beds mulched (backyard AND terrace). 5-8cm layer depth. Timing: 2-3 days before departure, followed by deep watering. Child helps spread mulch -- framed as "tucking the plants in for their nap."
- **Pre-departure checklist:** 3-day countdown protocol. Day -3: Mulching + deep watering. Day -2: Fill reservoirs + Big Harvest Party. Day -1: Neighbor walk-through + final top-up + last check. Dual format: printable checklist (one page, checkboxes, tape to fridge) + JSON version in data system.
- **Neighbor handoff logistics:** Day -1 walk-through with primary neighbor (15-20 min). One primary + one backup neighbor. Visit frequency every 2-3 days, ~15 min per visit. Neighbor keeps harvested produce as thank-you. Emergency protocol: "text with a photo, most things can wait."

### Claude's Discretion
- Exact 3-day countdown task sequencing and time estimates
- Which beds need reservoir testing vs which are adequately covered by mulch + neighbor visits
- Printable checklist layout and design
- JSON schema for the pre-departure checklist data
- How to coordinate the walk-through flow (route through garden, what to emphasize)

### Deferred Ideas (OUT OF SCOPE)
None -- discussion stayed within phase scope.
</user_constraints>

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| VACN-01 | Self-watering reservoirs installed and tested in tomato and cucumber beds before July | Reservoir build doc specifies 2-4 day autonomy per fill, 3-5 days with full reservoir + top watering. 5-day dry-run test protocol defined in CONTEXT.md. Only beds with reservoir features need testing (Bed C has reservoir per data files; CLAUDE.md says Beds A and B). |
| VACN-02 | Mulching protocol (5-8cm straw/bark) for all beds before each absence | Mixed material strategy locked: straw for veggie beds, bark for perennial/berry/herb beds. All 5 beds + terrace beds included. Applied Day -3 of countdown. |
| VACN-03 | Pre-vacation harvest protocol (pick everything showing color) | Harvest party on Day -2. Child leads harvest. Follows established "pea harvest party" celebration pattern from Phase 3. |
| VACN-04 | Neighbor guide delivered as printable document with photos, per-bed instructions, and emergency contacts | Neighbor guide content exists at `docs/neighbor-vacation-guide.md` (created Phase 5). Phase 6 handles printing, photo insertion, and physical delivery via Day -1 walk-through. |
</phase_requirements>

## Standard Stack

This phase produces markdown documents and JSON data files, consistent with all prior phases.

### Core
| Tool | Purpose | Why Standard |
|------|---------|--------------|
| Markdown in `docs/` | Session scripts, checklists, protocols | Established project convention |
| JSON in `data/` | Pre-departure checklist data | Extends Phase 4 data system pattern |
| JSON Schema in `data/schemas/` | Schema for checklist data | Matches existing crop/bed/week schemas |

### Supporting
| Asset | Location | Purpose |
|-------|----------|---------|
| `docs/reservoir-build.md` | Existing | Reference for reservoir capacity (15-20L per bed, 2-4 day autonomy) |
| `docs/neighbor-vacation-guide.md` | Existing | Content for printed guide -- needs photo placeholders filled and printing |
| `docs/warm-season-session-scripts.md` | Existing | Template for session script format (timed steps, prep checklists, ADHD breaks) |
| `data/schedules/w30.json` | Existing | Already references vacation prep tasks -- may need updates |

## Architecture Patterns

### Recommended Deliverable Structure
```
docs/
  vacation-countdown-script.md        # 3-day countdown session script (ADHD-adapted)
  pre-departure-checklist.md           # Printable one-page checklist (checkbox format)
  reservoir-test-protocol.md           # 5-day test procedure with daily log template
  mulching-guide.md                    # Per-bed mulching instructions (material, depth)
  neighbor-vacation-guide.md           # EXISTING -- add photos, finalize for print
data/
  pre-departure-checklist.json         # JSON version of countdown checklist
  schemas/
    checklist.schema.json              # Schema for checklist data (optional)
```

### Pattern 1: Session Script Format (Established)
**What:** Step-by-step scripts with timing, who does what, prep checklists, and ADHD-adapted breaks/transitions.
**When to use:** The 3-day countdown is effectively three mini-sessions. Each day follows the session script pattern.
**Source:** `docs/planting-day-script.md` and `docs/warm-season-session-scripts.md`

Key elements from established format:
- Pre-session prep checklist (father, ~15 min before)
- Motor skill split table (who does what)
- Timed steps with minute estimates
- Transition cues between activities
- Mandatory breaks after high-effort segments
- Weather check / abort criteria
- Clear "done" signals

### Pattern 2: Printable Checklist (New for this phase)
**What:** A one-page, checkbox-format document designed to be printed and taped to the fridge.
**When to use:** The pre-departure checklist needs to be physically accessible during the 3-day countdown.
**Design principles:**
- One page maximum (print-friendly)
- Large checkboxes for physical ticking
- Grouped by day (Day -3, Day -2, Day -1)
- Each item is a concrete action, not a category
- No ambiguity -- "Fill reservoir in Bed C through the white pipe" not "Check reservoirs"

### Pattern 3: JSON Data Extension
**What:** The pre-departure checklist as structured data, following the week schedule JSON pattern.
**When to use:** For potential future HA automation (dashboard showing countdown status).
**Schema approach:** Simple -- array of tasks with day, action, who, and completed fields. Does not need to be as complex as the weekly schedule schema.

### Anti-Patterns to Avoid
- **Over-documenting the reservoir test:** The test is a 5-day physical activity, not a complex procedure. The protocol doc should fit on one page with a daily log grid.
- **Duplicating neighbor guide content:** The guide already exists. Phase 6 adds photos and handles delivery -- do not rewrite the guide.
- **Creating automation for a manual process:** The 3-day countdown is a family activity. The JSON version is for reference, not for driving automation this season.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Neighbor guide content | New guide from scratch | Existing `docs/neighbor-vacation-guide.md` | Already complete with per-bed cards, emergency contacts, harvesting instructions |
| Session script format | New format | Established format from `docs/planting-day-script.md` | Proven ADHD-adapted structure with breaks, transitions, motor skill splits |
| Weekly schedule updates | Manual edits to all W28-W34 files | Targeted updates to W29-W30 only (pre-departure weeks) | Only the weeks immediately before vacation need countdown tasks |
| Mulching material research | Research optimal mulch types | Locked decision: straw for veggies, bark for perennials | User has already decided materials |

## Common Pitfalls

### Pitfall 1: Reservoir Test Timing
**What goes wrong:** Testing too close to departure leaves no time for fallback planning if the reservoir fails the 5-day test.
**Why it happens:** Procrastination or schedule conflicts push the test into late June.
**How to avoid:** The protocol should specify "complete by W26 (late June) at latest" -- this leaves 2-3 weeks before a typical W29-W31 departure to adjust neighbor visit frequency if needed.
**Warning signs:** If the test has not started by mid-June, escalate.

### Pitfall 2: Mulch Depth Inconsistency
**What goes wrong:** 2-3cm of mulch provides negligible moisture retention. 10cm+ smothers small plants.
**Why it happens:** Eyeballing depth without measuring, or running out of material partway through.
**How to avoid:** Pre-calculate mulch volume needed. For 5-8cm depth across all beds: roughly 180-290 liters total (3 large beds at 120x60cm + 2 small beds at 80x40cm). Buy a known quantity. Use a ruler or stick marked at 5cm and 8cm to check depth.
**Warning signs:** Material runs out before all beds are covered.

### Pitfall 3: Neighbor Walk-Through Too Detailed
**What goes wrong:** A 45-minute walk-through overwhelms the neighbor. They forget everything and default to "just water everything."
**Why it happens:** Wanting to cover every edge case.
**How to avoid:** Keep the walk-through to 15-20 minutes (locked decision). Focus on: where is the water tap, how to fill reservoirs, what is ripe, where is the printed guide. The guide handles the details -- the walk-through builds confidence.
**Warning signs:** Walk-through exceeds 20 minutes.

### Pitfall 4: Harvest Party Runs Long
**What goes wrong:** The Day -2 harvest party takes too long, causing meltdown or loss of engagement.
**Why it happens:** Too many beds, too much to pick, transitions between beds are slow.
**How to avoid:** Pre-scout which beds have harvestable produce. Start with "his beds" (highest engagement). Set a 30-minute cap. If there is more to pick after 30 minutes, father finishes while child does a different activity.
**Warning signs:** Child loses interest or becomes distressed after 20 minutes.

### Pitfall 5: Forgetting Terrace Beds
**What goes wrong:** Terrace beds (D and E) get overlooked in vacation prep because they are physically separate from backyard beds.
**Why it happens:** Out of sight, out of mind. The countdown script focuses on backyard beds.
**How to avoid:** Explicit terrace steps in every countdown day. The neighbor guide already covers terrace beds but emphasize their fast-drying nature (small, exposed to wind).
**Warning signs:** Mulching plan only mentions 3 beds instead of 5.

## Code Examples

### Pre-Departure Checklist JSON Structure
```json
{
  "checklist_type": "pre-departure",
  "departure_date": "2026-07-XX",
  "return_date": "2026-08-XX",
  "days": [
    {
      "day": -3,
      "label": "Mulching & Deep Water Day",
      "tasks": [
        {
          "id": "D3-01",
          "action": "Spread straw mulch on Beds A, B, C (5-8cm depth)",
          "who": "together",
          "minutes": 30,
          "completed": false
        },
        {
          "id": "D3-02",
          "action": "Spread bark mulch on Beds D, E (5-8cm depth)",
          "who": "together",
          "minutes": 15,
          "completed": false
        },
        {
          "id": "D3-03",
          "action": "Deep water all 5 beds after mulching",
          "who": "child",
          "minutes": 15,
          "completed": false
        }
      ]
    },
    {
      "day": -2,
      "label": "Reservoir Fill & Harvest Party",
      "tasks": [
        {
          "id": "D2-01",
          "action": "Fill all reservoirs completely via fill tubes",
          "who": "father",
          "minutes": 10,
          "completed": false
        },
        {
          "id": "D2-02",
          "action": "Harvest everything showing color (tomatoes, cucumbers, berries, beans)",
          "who": "child",
          "minutes": 30,
          "completed": false
        }
      ]
    },
    {
      "day": -1,
      "label": "Neighbor Walk-Through & Final Check",
      "tasks": [
        {
          "id": "D1-01",
          "action": "Walk primary neighbor through garden bed by bed (15-20 min)",
          "who": "father",
          "minutes": 20,
          "completed": false
        },
        {
          "id": "D1-02",
          "action": "Hand printed guide to primary neighbor",
          "who": "father",
          "minutes": 2,
          "completed": false
        },
        {
          "id": "D1-03",
          "action": "Deliver backup copy to second neighbor",
          "who": "father",
          "minutes": 5,
          "completed": false
        },
        {
          "id": "D1-04",
          "action": "Final top-up watering all beds",
          "who": "child",
          "minutes": 10,
          "completed": false
        },
        {
          "id": "D1-05",
          "action": "Child says goodbye to each bed",
          "who": "child",
          "minutes": 5,
          "completed": false
        }
      ]
    }
  ]
}
```

### Reservoir Test Daily Log Template (Markdown)
```markdown
## 5-Day Reservoir Test Log

**Bed:** [Bed letter]
**Start date:** [date]
**Reservoir filled:** [time]
**Last manual watering:** [date/time]

| Day | Date | Soil Surface | Root Depth (5-10cm) | Notes | Tester |
|-----|------|-------------|---------------------|-------|--------|
| 1   |      | Dry / Damp  | Dry / Damp          |       | Child  |
| 2   |      | Dry / Damp  | Dry / Damp          |       | Child  |
| 3   |      | Dry / Damp  | Dry / Damp          |       | Child  |
| 4   |      | Dry / Damp  | Dry / Damp          |       | Child  |
| 5   |      | Dry / Damp  | Dry / Damp          |       | Child  |

**Result:** PASS / FAIL
**Action if FAIL:** Increase neighbor visit frequency to every 2-3 days for this bed.
```

### Session Script Day Structure (Following Established Pattern)
```markdown
## Day -3: Mulching Day ("Tucking the Plants In")

**Duration target:** 45-60 minutes including break
**Vibe:** Sensory, nurturing, "we're taking care of them before we go"

### Prep Checklist (Father, ~20 min before)
- [ ] Straw bales/bags positioned near backyard beds
- [ ] Bark chip bags positioned near terrace beds
- [ ] Depth-check stick marked at 5cm and 8cm
- [ ] Watering can and hose ready for post-mulch soak
- [ ] Snack and drink ready for break

### Step 1: Backyard Beds -- Straw Mulch (20 min)
**Who:** Together
**What:** Spread straw around plants in Beds A, B, C
**Say:** "We're tucking the plants in for their nap while we're away..."
[...]
```

## Mulch Volume Calculations

Mulch volume needed per bed (at 5-8cm depth):

| Bed | Dimensions (cm) | Area (m2) | Volume at 5cm (L) | Volume at 8cm (L) | Material |
|-----|-----------------|-----------|--------------------|--------------------|----------|
| A   | 120 x 60        | 0.72      | 36                 | 58                 | Straw    |
| B   | 120 x 60        | 0.72      | 36                 | 58                 | Straw    |
| C   | 120 x 60        | 0.72      | 36                 | 58                 | Straw    |
| D   | 80 x 40         | 0.32      | 16                 | 26                 | Bark     |
| E   | 80 x 40         | 0.32      | 16                 | 26                 | Bark     |
| **Total** |           | **2.80**  | **140**            | **226**            |          |

**Straw (Beds A, B, C):** 108-174 liters. One standard straw bale (~100L loose) covers 1-2 beds. Buy 2 bales.
**Bark chips (Beds D, E):** 32-52 liters. One 50L bag of bark chips covers both terrace beds.

## Bed Identity Note

There is a mapping discrepancy between CLAUDE.md (Bed A = tomato, Bed B = cucumber) and the JSON data files (bed-a = strawberry/His Bed at backyard east, bed-c = tomato+cucumber at backyard center with reservoir). The neighbor guide uses the data file mapping. For Phase 6 deliverables:

- **Reservoir testing applies to:** Whichever physical beds have reservoirs installed. Per the data files, this is `bed-c` (Shared Bed, backyard center, with tomato + cucumber + trellis). The reservoir build doc references "Bed 1" and "Bed 2" (physical positions).
- **Use the canonical bed-letter identifiers (A-E)** in all new documents, consistent with data files and neighbor guide.
- **The neighbor guide is already written using physical descriptions** ("the big rusty-brown metal box in the center"), so the letter discrepancy does not affect the neighbor's experience.

This discrepancy should be noted but not fixed in Phase 6 -- it is a documentation cleanup issue, not a vacation preparation issue.

## State of the Art

| Old Approach | Current Approach | Impact |
|--------------|------------------|--------|
| Single neighbor, no backup | Primary + backup neighbor | Insurance against illness or scheduling conflicts during 2-3 week absence |
| Verbal instructions to neighbor | Printed guide with photos + walk-through | Neighbor has reference after family leaves; does not need to remember everything |
| Manual watering only | Reservoir + mulch + reduced neighbor visits | Reservoir extends watering interval; mulch reduces evaporation; neighbor visits drop to every 2-3 days |

## Open Questions

1. **Exact vacation dates (W29-W31 or W30-W33?)**
   - What we know: July-August, 2-3 weeks. W30 schedule already references vacation prep.
   - What is unclear: Exact departure and return dates.
   - Recommendation: Design the countdown protocol to work with any departure date. The checklist uses "Day -3, Day -2, Day -1" relative dating, not absolute dates. Leave departure_date as a placeholder in JSON.

2. **Which beds actually have reservoirs?**
   - What we know: CLAUDE.md says Beds A and B. Data files show only bed-c. Reservoir build doc says Bed 1 (west) and Bed 2 (center).
   - What is unclear: Whether the letter mapping was corrected or whether one reservoir was dropped.
   - Recommendation: The test protocol should cover all beds that physically have reservoirs. Write the protocol generically ("for each reservoir bed") and let the user confirm which beds on test day.

3. **Photo insertion in neighbor guide**
   - What we know: The guide has `[PHOTO: description]` placeholders throughout.
   - What is unclear: Whether photos will be taken before or during the countdown (plants need to look like their summer selves, not spring selves).
   - Recommendation: Add "take bed photos" as a task in the pre-departure countdown (Day -3 or Day -2, when beds are freshly mulched and looking their best). Insert into the printed copy before the Day -1 walk-through.

## Validation Architecture

### Test Framework
| Property | Value |
|----------|-------|
| Framework | Manual validation (physical garden activities) |
| Config file | None -- no automated test infrastructure for this phase |
| Quick run command | Manual checklist review |
| Full suite command | Physical walkthrough of all deliverables |

### Phase Requirements to Test Map
| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| VACN-01 | Reservoir tested and confirmed for 5+ days | manual-only | N/A -- physical 5-day test with daily finger check | N/A |
| VACN-02 | All beds mulched 5-8cm straw/bark | manual-only | N/A -- physical measurement with depth stick | N/A |
| VACN-03 | Pre-vacation harvest protocol executed | manual-only | N/A -- physical harvest of everything showing color | N/A |
| VACN-04 | Neighbor received printed guide with walk-through | manual-only | N/A -- physical delivery and walk-through | N/A |

**Justification for manual-only:** All four requirements involve physical garden activities (filling reservoirs, spreading mulch, picking produce, walking a neighbor through the garden). There is no code to test. Validation is confirmed by completing the printable checklist.

### Sampling Rate
- **Per task commit:** Review markdown for formatting, completeness, and consistency with established patterns
- **Per wave merge:** Cross-reference all deliverables for consistency (bed letters, timing, material quantities)
- **Phase gate:** All checklist items accounted for, neighbor guide photo placeholders addressed, JSON validates against schema

### Wave 0 Gaps
None -- no test infrastructure needed. This phase produces documentation and physical activity protocols, not code.

## Sources

### Primary (HIGH confidence)
- `docs/reservoir-build.md` -- reservoir capacity (15-20L), autonomy (2-4 days per fill, 3-5 with top watering), testing procedure
- `docs/neighbor-vacation-guide.md` -- complete neighbor guide content with per-bed cards and emergency contacts
- `docs/warm-season-session-scripts.md` -- established session script format (ADHD-adapted)
- `docs/planting-day-script.md` -- session script pattern with prep checklists, motor skill splits, timing
- `data/schemas/week.schema.json` -- weekly schedule schema for extending data system
- `data/schedules/w30.json` -- existing vacation prep task reference
- `data/beds/bed-c.json` -- confirms reservoir feature on shared bed

### Secondary (MEDIUM confidence)
- CLAUDE.md bed mapping (Beds A/B for reservoirs) -- may not match data file mapping
- Mulch volume calculations -- based on standard geometry, actual volume depends on mulch compression

### Tertiary (LOW confidence)
- None

## Metadata

**Confidence breakdown:**
- Standard stack: HIGH -- all deliverable types established in prior phases
- Architecture: HIGH -- follows proven session script and JSON data patterns
- Pitfalls: HIGH -- based on project-specific decisions and established patterns
- Mulch calculations: MEDIUM -- geometry is exact but real-world compression varies

**Research date:** 2026-03-27
**Valid until:** 2026-07-01 (stable -- physical protocols do not change)
