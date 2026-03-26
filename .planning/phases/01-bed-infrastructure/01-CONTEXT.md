# Phase 1: Bed Infrastructure - Context

**Gathered:** 2026-03-26
**Status:** Ready for planning

<domain>
## Phase Boundary

Order, build, and fill 5 raised beds (3 backyard + 2 terrace) with layered soil, drainage, slug defense, self-watering reservoirs, and a cucumber trellis. Produce a complete shopping list with pricing. Planting is Phase 2+.

</domain>

<decisions>
## Implementation Decisions

### Bed placement & spacing
- Claude decides optimal layout for the 3 backyard beds based on sun exposure, property photos, and water tap proximity
- Beds should be placed near the outdoor water tap for easy watering by a 7-year-old
- 60-80cm paths between beds for comfortable access (adult + child side by side, wheelbarrow-friendly)
- All four sides of each bed accessible (freestanding placement, not against walls/fences)

### Material & budget strategy
- Hybrid approach: corten steel for the 3 backyard beds (visible, permanent), galvanized steel for the 2 terrace beds (lighter, less visible)
- Budget target: stay within or near 2000-5000 DKK range; corten for backyard justifies stretching slightly if needed
- Shopping list includes specific Danish supplier recommendations with links and prices, PLUS product specs for comparison shopping
- Shopping list covers everything: beds, soil layers (hojbedsmuld, drainage gravel, compost), copper tape, trellis materials, reservoir parts, and any tools needed

### Terrace bed placement
- 2 galvanized beds (80x40x30cm) on the roof terrace, positioned along the railing/outer edge
- Wall side is not available: door, window, and AC unit block that space
- Terrace is on the west side above the carport, facing the street
- Previous owners had two small beds plus furniture on the terrace -- reasonable confidence in load capacity
- Document weight limits per bed (soil + water when saturated) and recommend keeping beds over structural supports, away from unsupported spans

### Self-watering reservoir
- DIY wicking system: PVC pipe reservoir at the bottom of the bed with wicking fabric drawing water up
- Installed in tomato and cucumber beds (the two that need most water and must survive vacation)
- All reservoir materials (PVC pipes, wicking fabric, overflow fittings) included in shopping list with specs and prices

### Cucumber trellis
- A-frame style: two angled panels meeting at top, cucumbers hang underneath for easy child picking
- Permanent construction (galvanized steel or treated wood) -- stays year-round, no seasonal teardown
- Trellis frame materials included in shopping list

### Claude's Discretion
- Exact bed arrangement in the backyard (row, L-shape, etc.) based on sun analysis and property photos
- Soil layer depths and exact composition ratios
- Copper tape application method
- Setup instruction format and level of detail
- Specific product model selections within the decided material types

</decisions>

<specifics>
## Specific Ideas

- Previous owners had raised beds on the terrace already -- use this as confidence baseline for structural capacity
- Terrace wall side blocked by door, window, and air conditioning unit -- beds must go along the railing
- Water tap exists in the backyard -- beds should be positioned for easy access by a 7-year-old with a hose or watering can
- A-frame trellis chosen specifically so the child can walk under and pick cucumbers hanging down

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Reference photos in `references/` directory: property description, Google Earth views (3D + top-down), interior floorplan, home photos
- These can inform bed placement recommendations and property visualization

### Established Patterns
- No code patterns yet -- this is the first phase of a documentation/planning project

### Integration Points
- Shopping list output (INFRA-07/DOCS-06) feeds into physical ordering
- Bed layout decisions feed into Phase 2 (planting distribution) and Phase 4 (data system with per-bed entities)
- Reservoir build feeds into Phase 6 (vacation testing)

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 01-bed-infrastructure*
*Context gathered: 2026-03-26*
