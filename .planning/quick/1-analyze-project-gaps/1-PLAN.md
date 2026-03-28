---
phase: quick
plan: 1
type: execute
wave: 1
depends_on: []
files_modified:
  - .planning/quick/1-analyze-project-gaps/1-ANALYSIS.md
autonomous: true
must_haves:
  truths:
    - "Every gap, weakness, and oversight in the project is identified with evidence"
    - "Each finding is actionable with a concrete fix proposal"
    - "Findings are organized as potential future phases with priorities"
  artifacts:
    - path: ".planning/quick/1-analyze-project-gaps/1-ANALYSIS.md"
      provides: "Comprehensive project gap analysis with proposed fixes"
      min_lines: 150
---

<objective>
Perform a thorough audit of the entire Haven project -- all documentation, data files, schemas, schedules, HA configs, planning artifacts, and verification results -- to identify gaps, weaknesses, oversights, and inconsistencies. Produce a structured analysis document that organizes findings into actionable future phases.

Purpose: The v1.0 milestone is 93% complete with 6 phases planned/executed. Before moving to physical execution (W16 build day), surface anything that was missed, is inconsistent, or needs strengthening.

Output: A single analysis document at .planning/quick/1-analyze-project-gaps/1-ANALYSIS.md
</objective>

<execution_context>
@/Users/albair/.claude/get-shit-done/workflows/execute-plan.md
@/Users/albair/.claude/get-shit-done/templates/summary.md
</execution_context>

<context>
@CLAUDE.md
@.planning/STATE.md
@.planning/ROADMAP.md
@.planning/REQUIREMENTS.md
@.planning/PROJECT.md
</context>

<tasks>

<task type="auto">
  <name>Task 1: Full project audit -- read everything</name>
  <files>None (read-only)</files>
  <action>
Read ALL of the following files systematically. Take notes on inconsistencies, gaps, missing content, and weaknesses as you go.

**Documentation (docs/):**
- docs/bed-layout.md
- docs/property-map.md
- docs/planting-grid-bed-a.md through docs/planting-grid-bed-e.md (all 5)
- docs/planting-day-script.md
- docs/warm-season-session-scripts.md
- docs/shopping-list.md
- docs/warm-season-shopping-list.md
- docs/setup-guide.md
- docs/soil-layers.md
- docs/reservoir-build.md
- docs/trellis-build.md
- docs/slug-defense.md
- docs/bug-hotel-guide.md
- docs/crop-difficulty-tiers.md
- docs/garlic-autumn-plan.md
- docs/mulching-guide.md
- docs/neighbor-vacation-guide.md
- docs/pre-departure-checklist.md
- docs/reservoir-test-protocol.md
- docs/troubleshooting-guide.md
- docs/vacation-countdown-script.md

**Data files (data/):**
- data/schemas/crop.schema.json, bed.schema.json, week.schema.json, checklist.schema.json
- ALL 27 crop JSON files in data/crops/
- ALL 5 bed JSON files in data/beds/
- data/succession-calendar.json
- ALL 30 weekly schedule files in data/schedules/ (w15.json through w44.json)
- data/ha/alert-rules.json, customize.json, plants.json, sensors.json
- data/sensors/sensor-recommendations.md
- data/pre-departure-checklist.json

**Planning artifacts:**
- .planning/REQUIREMENTS.md
- .planning/PROJECT.md
- .planning/ROADMAP.md
- ALL 6 VERIFICATION.md files (one per phase)
- ALL SUMMARY.md files across all phases
- ALL CONTEXT.md and RESEARCH.md files across all phases

**Audit dimensions to track while reading:**

1. **Data integrity:** Do crop JSON files validate against schemas? Are bed assignments consistent between bed files and crop files? Do planting grid positions match bed JSON positions? Are succession calendar entries consistent with individual crop harvest windows?

2. **Schedule completeness:** Do weekly schedules cover every planted crop's care needs? Are there weeks with no tasks? Do schedule tasks align with crop growth stages? Is the W30-W33 vacation gap properly handled?

3. **Cross-reference consistency:** Do shopping lists match what the planting grids specify? Do session scripts reference the correct beds and crops? Does the neighbor guide match the actual bed contents? Do HA sensor thresholds match crop requirements?

4. **Documentation gaps:** Are there missing guides for predictable situations (e.g., what to do if a crop fails, end-of-season cleanup, soil amendment for year 2)? Are photo placeholders tracked? Is there a guide for the child's daily routine?

5. **Child engagement coverage:** Do all sessions account for ADHD/Autism needs? Are there enough "quick win" activities? Is the child's daily garden routine documented? Are there engagement activities between planting sessions (W18 to W21 gap)?

6. **HA integration readiness:** Are sensor entity names consistent? Do alert rules cover all critical scenarios? Is there a guide for actually setting up HA? Are dashboard mockups or configs present?

7. **Season 2 preparedness:** Is there any documentation for what happens after W44? Soil refresh? What perennials return? Garlic harvest timing? Lessons learned template?

8. **Requirement coverage:** Cross-check all 59 requirements from REQUIREMENTS.md against what was actually delivered. Are any requirements only partially met?

9. **Verification findings:** Read all 6 VERIFICATION.md files. Were any gaps identified but not closed? Are there lingering issues?

10. **Operational readiness:** Is there enough information for the father to actually execute build day without re-consulting Claude? Are tool lists complete? Are timing estimates realistic?
  </action>
  <verify>All files listed above have been read. No file was skipped.</verify>
  <done>Complete mental model of the entire project with notes on every dimension listed above.</done>
</task>

<task type="auto">
  <name>Task 2: Write comprehensive gap analysis document</name>
  <files>.planning/quick/1-analyze-project-gaps/1-ANALYSIS.md</files>
  <action>
Write .planning/quick/1-analyze-project-gaps/1-ANALYSIS.md with the following structure:

```markdown
# Haven Project Gap Analysis

**Date:** 2026-03-27
**Scope:** Full audit of v1.0 milestone (6 phases, 15 plans, 59 requirements)
**Method:** Systematic read of all docs, data, schemas, schedules, HA configs, and planning artifacts

## Executive Summary

[2-3 paragraphs: overall project health assessment, top 3 most important findings, and general recommendation]

## Findings by Category

### 1. Data Integrity
[For each finding: what the issue is, where it appears (specific files/lines), severity (critical/moderate/minor), and proposed fix]

### 2. Schedule and Calendar
[Same format]

### 3. Cross-Reference Consistency
[Same format]

### 4. Documentation Gaps
[Same format]

### 5. Child Engagement and ADHD/Autism Coverage
[Same format]

### 6. Home Assistant Integration
[Same format]

### 7. Season 2 and Long-Term Preparedness
[Same format]

### 8. Requirement Coverage
[Table showing any requirements that are partially met or have gaps, with the requirement ID, description, what was delivered, and what is missing]

### 9. Verification Debt
[Findings from VERIFICATION.md files that were not fully resolved]

### 10. Operational Readiness
[Gaps between documentation and actual physical execution readiness]

### 11. Other Findings
[Anything that does not fit the categories above]

## Proposed Future Phases

Organize actionable fixes into potential future phases, ordered by priority. Each proposed phase should include:
- **Name and goal**
- **Findings addressed** (reference finding numbers above)
- **Estimated scope** (small: 1-2 plans, medium: 3-4 plans, large: 5+ plans)
- **Priority** (critical: do before W16, high: do before W21, medium: do in-season, low: post-season)
- **Why:** Why this matters for the project's core value (child agency)

Example phases might include (but are not limited to):
- Data validation and consistency fixes
- Daily routine and mid-season engagement guide
- HA setup walkthrough and dashboard config
- End-of-season and Year 2 planning
- Operational checklists for build day

## Summary Table

| # | Proposed Phase | Priority | Scope | Findings |
|---|---------------|----------|-------|----------|
| 1 | ... | ... | ... | ... |
```

Be thorough but honest. If an area is well-covered, say so. Do not manufacture gaps. Only flag genuine issues with specific evidence (file names, line numbers, missing fields, inconsistent values).

Every finding must be specific and actionable -- not "the documentation could be better" but "docs/neighbor-vacation-guide.md references Bed B watering but does not mention the A-frame trellis that blocks access to rear plants" (or whatever the actual finding is).
  </action>
  <verify>
File exists at .planning/quick/1-analyze-project-gaps/1-ANALYSIS.md with all 11 finding categories and a proposed future phases section. Document is at least 150 lines.
  </verify>
  <done>Comprehensive analysis document exists with specific, evidence-backed findings organized by category, and actionable future phase proposals ordered by priority.</done>
</task>

</tasks>

<verification>
- 1-ANALYSIS.md exists and contains all 11 finding categories
- Each finding references specific files and evidence
- Proposed future phases are concrete and prioritized
- Document is honest -- does not inflate issues or ignore genuine gaps
</verification>

<success_criteria>
- Complete audit of all project files (docs, data, schemas, schedules, HA configs, planning)
- Analysis document with specific, evidence-backed findings across all 11 dimensions
- Proposed future phases with priorities, scope estimates, and rationale
- Findings are actionable -- a planner could turn any proposed phase into a real phase plan
</success_criteria>

<output>
After completion, create `.planning/quick/1-analyze-project-gaps/1-SUMMARY.md`
</output>
