# Phase 3: Warm Season Planting - Context

**Gathered:** 2026-03-26
**Status:** Ready for planning

<domain>
## Phase Boundary

Transplant all frost-tender seedlings after May 20 and complete the garden's full planting plan. This includes cherry tomatoes, cucumbers, sweet peppers, sunflowers, nasturtiums, basil, mint (potted), bush beans, leeks, broccoli, and positioning borage/dill for pollinator attraction. Direct-sow crops go in early May (Session 1), transplants go in after last frost (Session 2). The continuous harvest engine starts once everything is planted.

</domain>

<decisions>
## Implementation Decisions

### Warm crop bed assignments
- Tomatoes and cucumbers share one backyard bed with the A-frame trellis and self-watering reservoir. Basil planted alongside tomatoes as companion.
- Sweet peppers go in the second backyard bed (shared/family bed), not his dedicated bed.
- Bush beans and broccoli in the second backyard bed with peppers (companion planting). Leeks in a terrace bed (compact, upright, suited to shallow 30cm beds).
- Mint pot placed next to his bed -- adds another crush-and-smell sensory plant to his daily check route alongside lamb's ear and lemon balm.
- Claude assigns exact positions within beds based on spacing, sun needs, and companion planting research.

### Planting session structure
- **Two sessions**, not three or one:
  - **Session 1 (~W18, May 1):** Direct sow sunflowers, nasturtiums, and bush beans. Quick, fun, seeds-in-soil day.
  - **Session 2 (~W21, May 20+):** Big transplant day for tomatoes, cucumbers, peppers, basil, broccoli, leeks. Mint pot setup.
- Same Phase 2 pattern for Session 2: his bed first (mint pot, any additions), snack break, then shared beds (peppers, beans transplants, broccoli, leeks).
- **No painted markers this time** -- he's already done the craft once in Phase 2. Save energy for new activities.
- **Pea-to-cucumber handoff:** Harvest celebration first -- pick all remaining peas together as a "harvest party" before clearing the trellis for cucumbers. Frame the transition as an achievement, not a loss.
- Session scripts follow the same format established in Phase 2 (step-by-step, timing estimates, break points, transition cues).

### Sunflower measurement activity
- **Ruler stake** next to the sunflower(s) -- a tall marked stake in the ground. He reads the height where the sunflower top reaches.
- **Weekly measurement**, same day each week. Visible growth between weekly checks keeps it exciting; daily would show too little change.
- **2-3 sunflowers** planted in a small cluster so he can compare which grows tallest -- adds a race element without dominating bed space.
- **Recording:** Claude's discretion -- the child likes counting/systems, so a simple wall chart or similar may add value, but don't force it if it becomes a chore.

### Creature observation setup
- **Nasturtiums positioned on his daily route** -- trailing from the edge of a bed he already checks (his bed or the tomato/cucumber bed). He'll notice aphids and ladybugs naturally during routine checks.
- **Light framing only:** "These flowers are bee magnets -- let's see how many come!" Sets expectation without lecturing. He discovers the rest on his own.
- **No new creature infrastructure** -- Phase 2 already established bug hotel, 2 water dishes, and creature habitats. Phase 3 adds the plants (nasturtiums, borage, dill) but the observation setup is already in place.
- **Aphid response: watch and wait.** "The ladybugs will come -- let's check tomorrow." Teaches patience and natural pest control. Only intervene if aphids spread from nasturtiums to food crops.

### Claude's Discretion
- Exact crop positions within each bed (spacing, companion planting layout)
- Sunflower height recording method (wall chart vs no record -- judge based on engagement value)
- Session 1 script timing and flow details
- Where exactly sunflowers go (which bed edge, how much space)
- Borage and dill exact positions for pollinator attraction

</decisions>

<specifics>
## Specific Ideas

- Pea harvest party before cucumber transplant -- makes the trellis handoff feel like a celebration
- Sunflower race between 2-3 plants -- "which one will be tallest?" gives a reason to measure weekly
- Mint pot next to his bed extends the sensory plant collection along his daily route
- Light framing for creature plants -- no lecturing, just "let's see what shows up" curiosity
- Nasturtiums on his daily route so aphid-ladybug dynamic is discovered naturally, not as a separate stop

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Reference photos in `references/` directory: property views useful for bed position planning
- Phase 1 context (01-CONTEXT.md): bed dimensions (120x60x40cm backyard, 80x40x30cm terrace), A-frame trellis spec, reservoir placement
- Phase 2 context (02-CONTEXT.md): bed assignments, grid map format, session script structure, creature habitat placement

### Established Patterns
- Grid map format (blueprint with positions and spacing in cm) -- reuse for warm crop additions to existing beds
- Session script format (step-by-step, timing, breaks, transitions) -- reuse for both Session 1 and Session 2
- No code patterns -- documentation/planning project producing markdown deliverables

### Integration Points
- Warm crop positions must align with Phase 2 spring layout (same beds, available gaps)
- Pea trellis handoff at W21 is a critical timing dependency
- Crop data feeds into Phase 4 (JSON database needs entries for all warm-season crops)
- Sunflower measurement activity could feed into Phase 4 weekly schedule files
- Nasturtium/aphid response feeds into Phase 5 troubleshooting guide

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 03-warm-season-planting*
*Context gathered: 2026-03-26*
