# Phase 5: Documentation and Guides - Context

**Gathered:** 2026-03-26
**Status:** Ready for planning

<domain>
## Phase Boundary

Create reference documents for every garden situation: property visualization, troubleshooting guide, difficulty-tiered crop collection, neighbor vacation guide, and a CLAUDE.md project file for AI-assisted continuity. Document garlic hardneck planting (October 2026) for Year 2 harvest. Phase 6 handles physical delivery and testing of the vacation guide.

</domain>

<decisions>
## Implementation Decisions

### Property visualization
- ASCII art in markdown, consistent with all other project deliverables
- Full property overview: house footprint, all 5 beds (3 backyard + 2 terrace), paths, water tap, nature corner, compass rose
- Terrace shown as separate inset diagram within the same document
- Key dimensions included: bed sizes (120x60cm, 80x40cm), path widths (70cm), approximate distances
- Sun exposure shown as general zones: full sun / partial shade / shade (not time-of-day splits)
- Based on existing reference photos (Google Earth views, property description, floorplan in references/)

### Troubleshooting guide
- Dual structure: symptom-based main guide + crop-specific index appendix
- Symptom-based sections organized by what you SEE: "Leaves turning yellow", "Holes in leaves", "Plant wilting", etc.
- Crop index appendix lists each planted crop with its most common issues as quick cross-reference
- Reading level: father reads, child acts -- written for an adult to read and explain, action steps concrete enough for the child to execute ("go get the watering can", "look under the leaves")
- Photo placeholders throughout: [PHOTO: description] markers to be replaced with real garden photos during the season
- Severity system: combined emoji + timeframe labels for each problem
  - 🟢 No rush (cosmetic/minor)
  - 🟡 This week (needs attention soon)
  - 🔴 Today (plant at risk)
- Incorporates Phase 3 decisions: aphid response is "watch and wait for ladybugs" -- included as a troubleshooting entry

### Difficulty-tiered crop collection
- Claude's discretion on format -- one reference document classifying every planted crop into tiers:
  - "Can't fail" (radishes, pea shoots, lettuce, herbs)
  - "Needs care" (tomatoes, cucumbers, peppers)
  - "Year 2 challenge" (garlic, broccoli, leeks)
- Tier assignment based on the specific varieties chosen in Phases 2-3 and Danish climate factors

### Neighbor vacation guide
- Dual structure: daily checklist front page + per-bed detail cards
  - Front page: numbered daily routine checklist for quick visits
  - Back pages: one section per bed with photo placeholder, contents, watering frequency, harvest instructions
- Language: English with Danish plant names (so neighbor recognizes what they're looking at)
- Tone: warm and casual -- "Help us keep our farm alive" title energy. Friendly, grateful, light humor
- Assumed knowledge: basic gardening (knows how to water, can identify plants). Focus on frequency, amounts, and what to harvest
- Emergency section at the end: "If something looks seriously wrong, text [number] with a photo. Don't worry -- most things can wait until we're back."
- Content created in Phase 5; physical delivery and reservoir testing handled in Phase 6

### CLAUDE.md project file
- Comprehensive: full garden context + project structure in one file
- Garden context: property details, bed layout, what's planted where, child's profile and engagement patterns, seasonal timing, maintenance approach
- Project structure: where docs live, file conventions, what each phase delivered, how to navigate
- Data system pointers: JSON schema locations, havn_ entity convention, weekly schedule file paths, HA config references
- Garden-adapted behavioral guardrails (vibes CLAUDE.md pattern): "Don't let me add crops mid-season", "Challenge scope creep beyond raised beds", "Remind me that manual watering is intentional"
- Living document: "Last updated" field + "Current season status" section designed for updates as things change
- Future Claude sessions get full context without re-explaining the project

### Garlic autumn plan
- Document hardneck garlic planting for October 2026 (COOK-02)
- Claude's discretion on format -- can be a section in an existing doc or standalone

### Claude's Discretion
- Difficulty tier assignments for each crop
- Garlic documentation format and placement
- Exact troubleshooting symptom categories and which problems to cover
- Property visualization layout decisions (exact ASCII arrangement)
- How to cross-reference between documents (links, mentions, etc.)

</decisions>

<specifics>
## Specific Ideas

- Troubleshooting guide should feel like a "plant doctor" reference -- look up the symptom, get a diagnosis and action
- Neighbor guide title: "Help us keep our farm alive" -- sets the warm, casual tone
- CLAUDE.md should follow the ~/book/vibes CLAUDE.md spirit but adapted for a garden project, not a software project
- Photo placeholders in troubleshooting guide and neighbor guide allow real-season photos to be added incrementally
- The aphid "watch and wait" philosophy from Phase 3 should be a featured troubleshooting entry, not buried

</specifics>

<code_context>
## Existing Code Insights

### Reusable Assets
- Reference photos in `references/`: property description, Google Earth views (3D + top-down), interior floorplan, home photos -- primary source for property visualization
- Phase 1 docs: bed dimensions, placement, soil layers, shopping list -- reference data for all Phase 5 documents
- Phase 2 docs: planting grids (5 beds), session script, bug hotel guide -- format patterns and crop positions
- ~/book/vibes/CLAUDE.md: template for the project file's behavioral guardrails section

### Established Patterns
- All deliverables are markdown files in docs/ directory
- Detailed, actionable format with tables, step-by-step instructions
- Grid map format (blueprint with cm positions) from Phase 2 -- potential reuse for property visualization
- Session script format (step-by-step, timing, transitions) from Phase 2

### Integration Points
- Property visualization references bed placements from Phase 1 (bed-layout.md)
- Troubleshooting guide references crop data from all phases + Phase 4 JSON database
- Neighbor guide content feeds into Phase 6 (VACN-04: physical delivery and testing)
- CLAUDE.md references Phase 4 data system (JSON schemas, HA entities) -- depends on Phase 4 completion
- Difficulty tiers reference crop selections from Phases 2-3

</code_context>

<deferred>
## Deferred Ideas

None -- discussion stayed within phase scope

</deferred>

---

*Phase: 05-documentation-and-guides*
*Context gathered: 2026-03-26*
