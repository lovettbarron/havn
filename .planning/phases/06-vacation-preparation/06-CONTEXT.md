# Phase 6: Vacation Preparation - Context

**Gathered:** 2026-03-27
**Status:** Ready for planning

<domain>
## Phase Boundary

The garden survives 2-3 weeks of family absence in July-August with zero crop loss, and a neighbor can maintain it using a printed guide. This phase covers reservoir testing, mulching, pre-departure protocols, and physical neighbor handoff. The neighbor guide *content* is created in Phase 5; this phase handles delivery, testing, and execution of all vacation-readiness measures.

</domain>

<decisions>
## Implementation Decisions

### Reservoir testing protocol
- 5-day dry-run test: fill reservoir, stop manual watering, check soil daily for 5 consecutive days
- Pass criteria: soil at root depth (5-10cm) stays damp via finger test. Top 2-3cm drying out is acceptable.
- Daily observations logged (wet/dry + notes)
- Child is daily soil check partner -- he does the finger test each morning and reports wet or dry. Builds understanding of why we're preparing.
- If reservoir fails: increase neighbor visit frequency to every 2-3 days for those specific beds (no new hardware)
- Test must be completed before July departure

### Mulching approach
- Mixed material strategy: straw for veggie beds (moisture retention), bark chips for perennial/berry/herb beds (neater, lasts longer, stays year-round)
- All beds mulched -- backyard AND terrace. Terrace beds get bark (won't blow away in wind, neater appearance)
- 5-8cm layer depth for all beds
- Timing: 2-3 days before departure, followed by deep watering after mulching
- Child helps spread mulch -- framed as "tucking the plants in for their nap while we're away." Sensory-rich activity (texture, smell).

### Pre-departure checklist
- 3-day countdown protocol:
  - **Day -3:** Mulching all beds + deep watering. Child helps spread mulch.
  - **Day -2:** Fill all reservoirs + Big Harvest Party. Child leads harvest (his beds first). Pick everything showing color.
  - **Day -1:** Neighbor walk-through + final top-up watering + last check. Child says goodbye to each bed.
- Harvest party framed as a celebration (follows the Phase 3 "pea harvest party" pattern)
- Child has age-appropriate tasks each day of the countdown -- builds ownership and closure before leaving
- Dual format: printable checklist (one page, checkboxes, tape to fridge) + JSON version in the data system for future HA automation potential

### Neighbor handoff logistics
- Walk-through + printed guide: Day -1, walk the primary neighbor through the garden bed by bed (15-20 min). Show water tap, reservoirs, what's harvestable. Hand over printed guide as backup reference.
- One primary neighbor + one backup neighbor. Primary gets the full walk-through. Backup gets a copy of the guide and knows they're on standby.
- Visit frequency: every 2-3 days. Roughly 15 minutes per visit. Low burden, matches reservoir capacity.
- Ripe produce policy: neighbor keeps whatever they harvest -- it's their thank-you. Reduces waste, rewards the favor, and ensures they actually check for ripe produce.
- Emergency protocol already defined in Phase 5 guide: "text with a photo, most things can wait"

### Claude's Discretion
- Exact 3-day countdown task sequencing and time estimates
- Which beds need reservoir testing vs which are adequately covered by mulch + neighbor visits
- Printable checklist layout and design
- JSON schema for the pre-departure checklist data
- How to coordinate the walk-through flow (route through garden, what to emphasize)

</decisions>

<specifics>
## Specific Ideas

- "Tucking the plants in" framing for mulching makes it a nurturing activity, not a chore
- Harvest party follows the established pattern from Phase 3's pea harvest celebration -- he knows this ritual
- "Say goodbye to each bed" on Day -1 gives emotional closure and reduces anxiety about leaving
- Neighbor keeps the harvest as a thank-you -- explicitly communicated in the guide and walk-through
- Backup neighbor as insurance against illness or vacation overlap during 2-3 week absence

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Phase 1 docs: reservoir-build.md has the DIY wicking system specs (PVC pipe, wicking fabric, overflow fittings) -- testing protocol validates this build
- Phase 5 neighbor guide content (DOCS-04/VACN-04): daily checklist + per-bed detail cards, English with Danish plant names, "Help us keep our farm alive" tone -- Phase 6 handles physical delivery
- Phase 4 data system: weekly schedule JSON files cover vacation weeks -- pre-departure checklist JSON extends this pattern
- Planting grid maps (docs/planting-grid-bed-{a-e}.md): reference for which beds have which crops during testing

### Established Patterns
- Session script format (step-by-step, timing, breaks, transitions) from Phases 2-3 -- reuse for the 3-day countdown protocol
- Markdown deliverables in docs/ directory
- JSON data files in data/ directory with schemas in data/schemas/
- Celebration framing for transitions (pea harvest party pattern from Phase 3)

### Integration Points
- Reservoir build (Phase 1) must be physically complete and functional before testing
- Neighbor guide content (Phase 5) must exist before Phase 6 can print and deliver it
- Pre-departure JSON checklist extends the Phase 4 data system pattern
- Weekly schedule files (Phase 4) should flag vacation weeks with special pre-departure tasks

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 06-vacation-preparation*
*Context gathered: 2026-03-27*
