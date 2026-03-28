# Phase 8: Child Engagement Bridge - Research

**Researched:** 2026-03-28
**Domain:** Child-facing visual routine design, ADHD/Autism-adapted daily engagement materials
**Confidence:** HIGH

## Summary

Phase 8 produces four deliverables: a printable daily routine card, structured W19-W20 gap activities, a weekly garden walk checklist, and a photo log approach. All deliverables are markdown documents targeting a 7-year-old with ADHD/Autism. The child cannot reliably read text, so all materials must be visual-first (icons, pictures, simple sequences). The project already has rich source material: crop JSON files contain `child_actions` with bilingual prompts, weekly schedule files contain themed tasks with time estimates, and the existing session scripts demonstrate the ADHD-adapted patterns (mandatory breaks, clear transitions, meltdown-resilient sequencing).

This is a content creation phase, not a technical implementation phase. There are no libraries, APIs, or code systems to build. The "stack" is markdown documents with ASCII/emoji-based visual representations suitable for printing. The key constraint is that all materials must align with the existing bed names (A-E), crop data, and weekly schedules already in the project.

**Primary recommendation:** Create 3-4 markdown documents in `docs/` that the father can print. Use the existing crop JSON `child_actions` and weekly schedule `tasks` as the source of truth for what the child does daily/weekly. Keep everything under 5 minutes for daily routine and 10 minutes for weekly activities.

<phase_requirements>
## Phase Requirements

| ID | Description | Research Support |
|----|-------------|-----------------|
| CENG-01 | Printable daily routine card with visual 5-minute checklist (check beds, water, pick, measure) | Existing crop `child_actions` define exactly which actions the child performs at each growth stage. The card maps these to a simple icon-based sequence. W16-W44 season span means the card needs seasonal variants or a generic core with swap-in seasonal items. |
| CENG-02 | Structured between-session activities for W19-W20 gap (sunflower check, germination watch, sensory walk) | W19 schedule has pea shoot harvest as hero task; W20 has radish harvest. Sunflowers are sown W18 and germinate W18-W19. The gap is between Session 1 (W18, May 1) and Session 2 (W21, May 20+). Activities already exist in schedule data -- this requirement bridges them into a child-facing format. |
| CENG-03 | Weekly garden walk checklist with 3-5 recurring quick activities (5-10 minutes) | Crop JSON `engagement.attention_minutes_per_week` fields give time budgets. Recurring activities: sensory walk (touch lamb's ear, smell mint/lemon balm, smell basil), creature check (bees on borage, aphids on nasturtium), growth measurement (sunflower ruler), harvest check (radish/strawberry/lettuce). |
| CENG-04 | Simple photo log approach documented (low friction, one photo per visit) | Needs to be zero-friction for the father. Shared album (Apple Photos, Google Photos) with a simple rule: one photo per garden visit. No journaling, no captions required. The child can participate by choosing what to photograph. |
</phase_requirements>

## Standard Stack

This phase produces documentation only -- no code libraries or frameworks.

### Core Deliverables

| Deliverable | Format | Purpose | Location |
|-------------|--------|---------|----------|
| Daily routine card | Markdown (printable) | 5-minute visual checklist for morning garden check | `docs/daily-routine-card.md` |
| W19-W20 gap activities | Markdown | Structured between-session engagement | `docs/between-session-activities.md` |
| Weekly garden walk | Markdown (printable) | 3-5 recurring quick activities | `docs/weekly-garden-walk.md` |
| Photo log guide | Markdown | Low-friction documentation approach | Can be a section within one of the above docs |

### Source Data (already exists)

| Source | What to Extract | Location |
|--------|----------------|----------|
| Crop JSON `child_actions` | Daily/weekly activities per crop per growth stage | `data/crops/*.json` |
| Weekly schedule `tasks` | Week-specific child tasks with prompts | `data/schedules/w15.json` through `w44.json` |
| Crop JSON `engagement.sensory` | Which sensory activities are available | `data/crops/*.json` |
| Session scripts | ADHD-adapted patterns, transition cues, motor skill split | `docs/planting-day-script.md`, `docs/warm-season-session-scripts.md` |

## Architecture Patterns

### Pattern 1: Visual-First, Text-Free Design

**What:** The child has ADHD/Autism and is 7 years old. He may not read fluently. All child-facing materials must work without reading.

**How to achieve in markdown:**
- Use emoji as icons for each activity type (e.g., eyes for "look", water droplet for "water", hand for "touch", ruler for "measure")
- Use numbered steps (1, 2, 3, 4, 5) with large visual markers
- Keep each step to one action
- The father reads the card once to explain it, then the child follows the icons independently

**Example daily routine card structure:**
```
## My Garden Morning (5 minutes)

1. [eyes emoji] LOOK -- Walk past all beds. What changed?
2. [hand emoji] TOUCH -- Feel the soil. Dry = water time!
3. [water emoji] WATER -- Small can, gentle pour
4. [search emoji] PICK -- Any red strawberries? Any ripe radish tops poking out?
5. [ruler emoji] MEASURE -- How tall is the sunflower today?
```

**Source:** Established pattern from the existing session scripts which already use a "What HE does" / "What FATHER does" split with simple action verbs.

### Pattern 2: Seasonal Adaptation Without Complexity

**What:** The garden changes through the season. The daily routine card should not require reprinting every week.

**How:** Create a core routine that is always the same (look, touch, water, pick, measure) with a small "This Week's Special" box that the father updates verbally or with a sticky note. The core 5 steps never change; only what you look for, pick, or measure changes.

**Why:** Children with ADHD thrive on predictable routines. Changing the card creates anxiety. A stable structure with one variable element gives predictability plus novelty.

### Pattern 3: Time-Boxing (Hard 5-Minute / 10-Minute Limits)

**What:** Every activity has a strict maximum duration. ADHD attention spans are short, and the garden engagement must not become a chore.

**Rules from existing project patterns:**
- Daily routine: 5 minutes maximum (non-negotiable)
- Weekly walk: 10 minutes maximum
- Between-session activities: 10-15 minutes maximum
- If he finishes early, he is done. If he wants to stay longer, that is his choice.
- Never extend a session past its time limit, even if there is "more to do"

### Pattern 4: Danish + English Bilingual Prompts

**What:** The crop JSON files already contain bilingual prompts (`en` and `da`). Child-facing materials should include Danish alongside English where the father would speak to the child.

**Implementation:** Include Danish prompts for verbal cues the father says aloud. The visual card itself uses icons (language-free). Verbal scripts appear as father-facing notes.

### Anti-Patterns to Avoid

- **Over-documenting:** Do NOT create a 10-page guide. The father needs printable cards, not manuals. If it does not fit on one printed page, it is too long.
- **Requiring literacy:** Do NOT write instructions the child must read. Icons and pictures only for child-facing elements.
- **Making it feel like homework:** Do NOT use checklists with checkboxes the child must tick. The routine is a walk-through, not a form to complete. (The father can use checkboxes on his own copy.)
- **Varying the routine daily:** Do NOT create day-specific routines (Monday = X, Tuesday = Y). Same routine every day. Predictability is the feature.
- **Digital-first:** Do NOT suggest apps or digital tools for the child. Printed cards, physical presence, and real plants. The photo log is the only digital element, and that is father-managed.

## Don't Hand-Roll

| Problem | Don't Build | Use Instead | Why |
|---------|-------------|-------------|-----|
| Activity data | New activity lists from scratch | Existing crop JSON `child_actions` | Already has bilingual prompts, time estimates, frequency, and who-does-what |
| Weekly task lists | New weekly task invention | Existing `data/schedules/w19.json` - `w20.json` | Already has W19-W20 tasks with child prompts |
| Sensory activity list | Guessing which plants are sensory | `data/crops/*.json` `engagement.sensory` fields | Already categorized by sight/touch/smell/taste |
| Time estimates | Guessing durations | Crop JSON `child_actions.minutes` | Already field-tested estimates in the data |

## Common Pitfalls

### Pitfall 1: The Routine Becomes a Chore
**What goes wrong:** If the daily routine feels like an obligation, the child will resist it. ADHD children abandon tasks that feel imposed.
**Why it happens:** Over-structuring, too many steps, requiring completion of every step.
**How to avoid:** Frame as "your morning garden walk" not "your garden tasks." Any step can be skipped. The walk itself is the routine, not completing every action.
**Warning signs:** Child says "do I HAVE to?" or refuses to go outside.

### Pitfall 2: The W19-W20 Gap Feels Empty
**What goes wrong:** Between planting Session 1 (W18, May 1) and Session 2 (W21, May 20+), three weeks pass. If there is nothing structured, engagement drops.
**Why it happens:** The project has activities in the schedule data (pea shoot harvest W19, radish harvest W20, sunflower germination watch) but they are not surfaced in a child-facing format.
**How to avoid:** Create a simple "treasure hunt" format for the gap weeks. Each week has ONE exciting thing to find: W19 = "Can you find the sunflower sprouts?", W20 = "Is the first radish ready to pull?"
**Warning signs:** Child has not visited the garden in 3+ days during the gap.

### Pitfall 3: Photo Log Adds Friction
**What goes wrong:** If the photo log requires captions, dates, organization, or uploads, the father will abandon it within a week.
**Why it happens:** Well-intentioned documentation systems that require too many steps.
**How to avoid:** One rule: "Take one photo per garden visit. Save it to the shared album. Done." No captions. No organization. The date metadata on the photo is sufficient. Let the child choose what to photograph -- it becomes part of his agency.
**Warning signs:** Father stops taking photos after week 2.

### Pitfall 4: Materials Reference Wrong Bed Names
**What goes wrong:** Using Bed 1-5 instead of Bed A-E, or referencing crops in wrong beds.
**Why it happens:** Phase 7 just fixed this across the project. New documents must use the corrected canonical names.
**How to avoid:** Always reference beds as A-E. Cross-check crop assignments against `data/beds/*.json` and planting grid maps.
**Warning signs:** Any mention of "Bed 1" through "Bed 5" in new documents.

## Code Examples

Not applicable -- this phase produces markdown documents, not code. See Architecture Patterns above for document structure examples.

### Key Data Extraction Examples

**Getting child actions for a specific growth stage:**
From `data/crops/sunflower.json`, the W18-W19 germination stage gives:
```json
{
  "action": "Spot the sprouts",
  "type": "observe",
  "who": "child",
  "minutes": 3,
  "frequency": "daily",
  "prompt": {
    "en": "The sunflower seeds you planted are waking up! Can you see them pushing through?",
    "da": "Solsikkefroene du plantede er ved at vaagne! Kan du se dem skyde op?"
  }
}
```

**Getting the W19 hero task:**
From `data/schedules/w19.json`:
```json
{
  "hero_task": "First pea shoot harvest for a snack",
  "theme": {
    "name": { "en": "Pea Shoot Snack Week" }
  }
}
```

These existing data structures provide the content for all four deliverables.

## State of the Art

| Old Approach | Current Approach | When Changed | Impact |
|--------------|------------------|--------------|--------|
| Session scripts only (big event days) | Daily routine + weekly walk + gap activities | Phase 8 (this phase) | Child engages every day, not just on planting events |
| Crop data has child_actions but no child-facing surface | Printable routine card surfaces the actions visually | Phase 8 | The rich data in crop JSON becomes usable by the child |
| No documentation habit | Simple photo log | Phase 8 | Season memories preserved with zero friction |

## Open Questions

1. **Print format preferences**
   - What we know: Markdown renders well for screen; printing depends on the tool used
   - What is unclear: Whether the father has a printer, what paper size (A4 assumed for Denmark)
   - Recommendation: Design for A4 portrait, single page per card. Markdown to PDF via any browser print works.

2. **Lamination / weatherproofing**
   - What we know: The daily routine card will be used outdoors
   - What is unclear: Whether the father will laminate it
   - Recommendation: Mention lamination as optional in the doc. Design the card to survive a few days of outdoor use even without lamination (black and white friendly, no fine detail that smudges).

3. **Seasonal variant cards**
   - What we know: The garden changes significantly from W16 (spring planting) to W28 (peak harvest) to W40 (wind-down)
   - What is unclear: Whether multiple seasonal cards are wanted or a single generic card
   - Recommendation: One generic card for the daily routine (the 5 steps are season-independent). Add a "seasonal highlights" one-pager that the father can update monthly with what to look for. Keep it to 2 documents maximum.

## Validation Architecture

### Test Framework

| Property | Value |
|----------|-------|
| Framework | Manual review (documentation phase, no code tests) |
| Config file | N/A |
| Quick run command | Visual inspection of markdown rendering |
| Full suite command | Print test: render each markdown file to PDF and verify single-page fit |

### Phase Requirements to Test Map

| Req ID | Behavior | Test Type | Automated Command | File Exists? |
|--------|----------|-----------|-------------------|-------------|
| CENG-01 | Daily routine card is printable, visual, 5-minute checklist | manual-only | Render markdown, verify fits A4 single page | Wave 0 |
| CENG-02 | W19-W20 gap activities structured with specific activities | manual-only | Verify activities reference correct crops/weeks from schedule data | Wave 0 |
| CENG-03 | Weekly walk has 3-5 activities, 5-10 min total | manual-only | Count activities, sum time estimates, verify range | Wave 0 |
| CENG-04 | Photo log approach documented, low friction | manual-only | Verify approach is documented, max 1 step for the child | Wave 0 |

**Justification for manual-only:** All deliverables are markdown documents for human consumption. Automated testing would be artificial. Verification is: does the document exist, does it meet the word/page constraints, and does it reference correct bed names and crop data.

### Sampling Rate
- **Per task commit:** Verify markdown renders correctly, bed names are A-E, crop references match JSON data
- **Per wave merge:** Print all documents to PDF and verify single-page fit
- **Phase gate:** All 4 requirements have corresponding documents that pass visual inspection

### Wave 0 Gaps
None -- no test infrastructure needed for a documentation-only phase. Verification is manual review against the success criteria.

## Sources

### Primary (HIGH confidence)
- `data/crops/*.json` -- 28 crop files with child_actions, engagement fields, sensory data
- `data/schedules/w19.json`, `w20.json` -- W19-W20 gap period tasks and growth events
- `docs/planting-day-script.md` -- Established ADHD-adapted session patterns (breaks, transitions, motor skill split)
- `docs/warm-season-session-scripts.md` -- Session 2 patterns with sunflower measurement and creature observation
- `.planning/REQUIREMENTS.md` -- CENG-01 through CENG-04 requirement definitions
- `CLAUDE.md` -- Project guardrails, ADHD/Autism profile constraints, no over-automation

### Secondary (MEDIUM confidence)
- ADHD/Autism routine design principles (predictability, visual-first, time-boxing, agency over compliance) -- from established project patterns in session scripts

## Metadata

**Confidence breakdown:**
- Deliverable structure: HIGH -- requirements are clearly defined, source data exists in the project
- ADHD/Autism adaptation patterns: HIGH -- the project already demonstrates these patterns extensively in session scripts
- Print/format recommendations: MEDIUM -- assumed A4 format for Denmark, browser-based markdown-to-PDF
- Photo log approach: HIGH -- simple enough that there is little to get wrong

**Research date:** 2026-03-28
**Valid until:** 2026-04-30 (stable -- content documentation, no moving technology targets)
