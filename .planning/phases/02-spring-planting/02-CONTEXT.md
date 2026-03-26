# Phase 2: Spring Planting - Context

**Gathered:** 2026-03-26
**Status:** Ready for planning

<domain>
## Phase Boundary

Plant all cold-hardy crops, perennials, edible flowers, sensory plants, and creature habitats into the 5 raised beds built in Phase 1. Produce a bed-by-bed planting layout with exact positions. The child experiences his first planting sessions. Warm-season crops (tomatoes, cucumbers, peppers, sunflowers, nasturtiums, basil, mint, beans, leeks, broccoli) are Phase 3 (post-frost W21+).

</domain>

<decisions>
## Implementation Decisions

### Bed assignment
- 1 dedicated backyard bed is "his bed" — strawberries, pea shoots, edible flowers (viola, calendula), sensory edge plants (lamb's ear, thyme, lemon balm)
- 1 separate backyard bed for raspberries (Autumn Bliss canes) — companion planted with chives at the base
- Remaining backyard bed + 2 terrace beds are shared/family beds for cooking crops (kale, peas, spring onion), remaining flowers (borage), and succession sowing slots
- Claude assigns specific crops to specific beds based on companion planting, sun needs, and spacing constraints

### Within-bed layout
- Sensory plants concentrated on his bed edges + along the main walking path between beds (not every bed)
- Edible flowers scattered as functional companion plants across all beds (calendula near veg for pest deterrent, borage near future tomato/cucumber beds for bees, viola at bed edges for color) — not grouped in one section
- Peas use the A-frame cucumber trellis first (W16) — cut back when cucumbers transplant in W21. Peas fix nitrogen as pre-crop for cucumbers.
- Layout document format: grid map with exact positions and spacing in cm for each bed — like a blueprint to follow while planting

### Child's planting sessions
- Big planting day on a weekend (W16) — his bed first as the main event, then shared beds. Follow-up sessions W17-W18 for succession sowing and remaining plantings
- Task involvement varies by motor skill: big seeds (peas) and seedlings he handles fully; tiny seeds (lettuce, radish) father sprinkles, he covers soil and waters
- Painted plant markers: he paints/decorates wooden markers for his bed as a pre-planting indoor craft activity. Names or draws on them — doubles as garden labels
- Session script included: step-by-step planting day plan with timing estimates, break points (snack after his bed), and transition cues. Helps manage energy and attention across the day.

### Creature habitat placement
- Dedicated "nature corner" away from the beds — log pile, stones, pinecones, hollow stems in a bug hotel style structure
- Bug hotel built as a separate weekend activity (W17 or W18), not part of planting day — gives him something to look forward to after the big day
- Two pollinator water dishes: one at the bug hotel corner, one near the flower-heavy beds — two observation points for creature activity
- Materials: logs, stones, pinecones, hollow bamboo/stems — can collect from the garden and nearby

### Claude's Discretion
- Exact crop-to-bed assignments for shared/family beds (based on companion planting research)
- Spacing calculations within the grid maps
- Succession sowing schedule slots within the layout
- Session script timing and break structure details
- Bug hotel construction instructions and material specs

</decisions>

<specifics>
## Specific Ideas

- Peas as nitrogen-fixing pre-crop on the A-frame trellis before cucumbers arrive in Phase 3
- Painted plant markers as an indoor craft activity before planting day — builds anticipation
- Planting day structured as: his bed first (the big event), snack break, then shared beds, finish with watering together
- Bug hotel as a separate "building project" weekend — keeps the garden exciting across multiple weeks
- Two water dishes gives him two places to check for bees, butterflies, and birds

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Reference photos in `references/` directory: property views, floorplan — useful for placing the "nature corner" and understanding garden layout
- Phase 1 context (01-CONTEXT.md): bed dimensions, placement decisions, trellis spec, reservoir placement

### Established Patterns
- No code patterns — this is a documentation/planning project producing markdown deliverables
- Grid map format is new for this phase — will set the pattern for Phase 3 warm-season layout

### Integration Points
- Bed layout feeds directly into Phase 3 (warm season transplanting positions must align with spring layout)
- Bed layout feeds into Phase 4 (data system needs per-bed, per-plant entries)
- Pea trellis timing must coordinate with Phase 3 cucumber transplant (W21 handoff)
- Session script format could be reused for Phase 3 planting sessions

</code_context>

<deferred>
## Deferred Ideas

None — discussion stayed within phase scope

</deferred>

---

*Phase: 02-spring-planting*
*Context gathered: 2026-03-26*
