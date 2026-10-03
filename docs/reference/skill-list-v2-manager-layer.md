# Superintelligent Sales OS — Skill List v2: Manager Layer

> Manager Layer restructured into 4 Suites following the same architectural pattern as Rep Layer.
>
> **Status:** Rep Layer LOCKED ✅ | Manager Layer LOCKED ✅ | Leader / RevOps next.

---

## Manager Layer organizing principle

**Manager Layer is different from Rep Layer.** Rep Layer follows the deal through the seven moments. Manager Layer follows the **manager's operating cadence** — weekly, bi-weekly, bi-monthly. Different organizing principle, same architectural pattern (Suites, customization-first, GPTs as source material).

Manager Layer's mirror pattern: **Diagnose → Plan → Practice → Reinforce.** Apply this to forecasting, coaching, and performance work alike.

---

## MANAGER LAYER — 4 Suites

### Suite 1: Operating Rhythm Suite

**The orchestration layer that ties the other three suites together.**

The Operating Rhythm Suite doesn't have its own methodology — it composes sub-skills from Coaching Suite, Forecast Suite, and Call & Pattern Suite into the manager's actual weekly/bi-weekly/bi-monthly cadence.

**Mirror pattern: Plan the cadence → Run the meeting → Capture commitments → Reinforce in the next cycle**

| Sub-skill | Purpose | Composes from |
|---|---|---|
| `weekly-team-meeting-prep` | Team kickoff meeting prep with VIP opener + agenda + metrics review | Forecast Suite + Call & Pattern Suite |
| `weekly-1on1-prep` | 60-min 1:1 prep snapshot per rep | Coaching Suite + Forecast Suite |
| `biweekly-deal-review` | 2 deals × 30 min, deep inspection format | Forecast Suite + Coaching Suite |
| `biweekly-skill-workshop` | Focused skill practice session for the team | Coaching Suite |
| `bi-monthly-forecast-review` | Twice-monthly forecast triangulation meeting | Forecast Suite |

**Customization required:**
- Your team size and structure
- Your meeting cadence preferences (some companies prefer weekly all-hands vs. bi-weekly)
- Your reporting up structure (do you roll up to a Director, VP, CRO?)
- Your CRM and tooling for forecast data inputs

**Methodology files referenced:**
- `60-min-1on1-structure.md`
- `bi-monthly-forecast-cadence.md`
- `operating-rhythm.md` (to be written — Three Pillars × Four Cadences)

---

### Suite 2: Coaching Suite

**The highest-leverage suite. Where Dana methodology is most differentiated.**

The full coaching workflow — diagnose what the rep needs, build a development plan, practice it, reinforce in the operating rhythm. This is the suite that turns managers from inspectors into coaches.

**Mirror pattern: Diagnose → Plan → Practice → Reinforce**

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `task-diagnostic` | Apply the TASK framework to identify rep gaps (Target / Activities / Skill / Knowledge) | Net-new |
| `development-plan-generator` | TASK-driven 30-60-90 day development plan per rep | Net-new |
| `five-step-coaching-conversation` | Run the dual-layer coaching conversation (macro + Autonomy & Mastery) | Net-new |
| `ai-roleplay-partner` | Practice with AI buyer personas before high-stakes calls | Net-new |
| `action-tracking` | Capture and track coaching commitments across cycles | Net-new |
| `coaching-orchestrator` | Top-level skill that ties all coaching activities to a manager's portfolio of reps | Builds on `Dana Sales Leadership Coach` GPT |

**Customization required (high):**
- Your team's skill rubric (which skills you grade reps on)
- Your buyer personas (for roleplay)
- Your coaching philosophy and tone
- Your development plan templates (if existing)
- Your team's current performance baseline

**Methodology files referenced:**
- `task-coaching-diagnostic.md`
- `five-step-coaching-conversation.md`
- `champions-code-seven-elements.md` (cultural foundation; not operationalized as a skill — see Champion's Code note below)

---

### Suite 3: Forecast Suite

**The deal inspection and forecast triangulation suite.**

The full forecast workflow — score deals against methodology, predict deal confidence, triangulate top-down vs. bottoms-up, and produce a defensible forecast for the leader layer above.

**Mirror pattern: Score → Inspect → Triangulate → Reconcile**

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `spiced-scoring` | Score deals against SPICED with evidence | Net-new (informed by `SPICED Sales Call Analyst` GPT) |
| `meddpicc-qualifier` | Score deals against MEDDPICC with rubric and red-flag detection | Builds on `MEDDPICC Qualifier Pro` GPT |
| `deal-confidence` | Predictive deal scoring combining methodology score + behavioral signals | Net-new |
| `forecast-triangulation` | Reconcile rep-level optimistic forecast with manager-filtered realistic | Net-new |
| `pipeline-coverage-analysis` | Coverage ratio analysis vs. quota and historical conversion | Net-new |

**Customization required (medium-high):**
- Your qualification methodology (SPICED is default; supports MEDDPICC, custom)
- Your deal stages and exit criteria
- Your historical conversion rates by stage
- Your pipeline coverage targets
- Your quota structure

**Methodology files referenced:**
- `forecast-triangulation-method.md`
- `bi-monthly-forecast-cadence.md`
- `task-coaching-diagnostic.md` (deal-coaching application)

---

### Suite 4: Call & Pattern Suite

**The call analysis and team-level pattern recognition suite.**

The systematic call-coverage workflow — score every call (or a meaningful sample), aggregate patterns across deals and reps, identify what differentiates top performers, and surface coaching opportunities.

**Mirror pattern: Score → Aggregate → Pattern-match → Surface coaching opportunities**

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `call-scoring` | Score 100% of calls vs. SPICED with evidence and red flags | Net-new |
| `cross-deal-pattern-analysis` | Aggregate scoring across deals/reps to find patterns | Builds on `MEDDPICC Cross-Deal Analyst` GPT |
| `top-performer-pattern-extraction` | Identify what top performers do differently in calls | Net-new |
| `management-analytics` | Performance dashboards + coaching opportunity surfacing | Net-new |
| `rep-skill-gap-analysis` | Cross-call analysis to identify skill gaps per rep | Net-new |

**Customization required (medium-high):**
- Your call recording infrastructure (Gong, Chorus, Fathom, etc.)
- Your scoring methodology (SPICED, MEDDPICC, custom)
- Your performance benchmarks (what does "good" look like in your context?)
- Your team segmentation (top 20%, middle, bottom 20%)

**Methodology files referenced:**
- `task-coaching-diagnostic.md` (skill gap diagnosis)
- `managing-to-metrics-library.md` (which metrics to coach to)
- `call-recording-overlay.md` (cross-cutting; to be written)

---

## Champion's Code — Methodology, Not a Skill

The Champion's Code (7 elements: Recognition, Practice, Learning, Collaboration, etc.) is a **cultural methodology**, not an operationalizable skill. It informs how managers run their operating rhythm, but it's not a bot.

**How it lives in the OS:**

- `methodology/champions-code-seven-elements.md` — full methodology file (already written)
- Referenced by skills in Coaching Suite (especially `ai-roleplay-partner` and `coaching-orchestrator`)
- Referenced by skills in Operating Rhythm Suite (especially `weekly-team-meeting-prep` and `biweekly-skill-workshop`)
- **Externally linked:** Victor's Champion's Code app — a self-assessment tool that managers can use to score their team's culture against the 7 elements, and learn what to do to improve

**The methodology file should include the link to the Champion's Code app prominently**, framed as: *"For an interactive self-assessment of your team against the Champion's Code, use the Champion's Code app at [URL]."*

This positions the app as a companion to the methodology, accessible to anyone reading the file — including non-OS users.

**Action item for Victor:** Provide the Champion's Code app URL when ready, and we'll add it to the methodology file.

---

## MANAGER LAYER SUMMARY

| Suite | Sub-skills | Customization weight | GPT source(s) |
|---|---|---|---|
| 1. Operating Rhythm Suite | 5 | Medium | None (orchestrates other suites) |
| 2. Coaching Suite | 6 | High | Dana Sales Leadership Coach |
| 3. Forecast Suite | 5 | Medium-high | MEDDPICC Qualifier Pro |
| 4. Call & Pattern Suite | 5 | Medium-high | MEDDPICC Cross-Deal Analyst |

**Total: 4 suites = 21 sub-skills**

(Down from 16 standalone skills in v1, but each is now richer and embedded in suite context with explicit methodology grounding and customization layer.)

---

## MANAGER LAYER — Customization Layer Architecture

Manager Layer reads from the same `/context/user-context.yaml` as Rep Layer, plus a Manager-specific section:

```yaml
# Additional fields for Manager Layer in /context/user-context.yaml
manager:
  team_size: 8
  team_segments:
    top_performers: ["rep-1", "rep-2"]
    middle: ["rep-3", "rep-4", "rep-5", "rep-6"]
    developing: ["rep-7", "rep-8"]
  
  cadence:
    team_meeting_frequency: "weekly"
    one_on_one_frequency: "weekly"
    deal_review_frequency: "biweekly"
    skill_workshop_frequency: "biweekly"
    forecast_review_frequency: "bi-monthly"
  
  methodology_preference: "SPICED"  # or MEDDPICC, custom
  
  coaching:
    skill_rubric_path: "/context/skill-rubric.md"
    development_plan_template_path: "/context/development-plan-template.md"
    coaching_philosophy: "Diagnose & Treat — group meetings diagnose, triggered 1:1s treat"
  
  forecasting:
    deal_stages: [...]
    stage_exit_criteria: {...}
    historical_conversion_rates: {...}
    pipeline_coverage_target: 4.0
  
  call_analysis:
    call_recording_platform: "Gong"  # or Chorus, Fathom, etc.
    scoring_methodology: "SPICED"
    coverage_target: "100%"  # or sample-based
```

The customization onboarding skill (Rep Layer) walks the user through populating all of these fields.

---

## MANAGER LAYER — LOCKED DECISIONS (April 29, 2026)

- ✅ **Architecture:** 4 Suites (Operating Rhythm, Coaching, Forecast, Call & Pattern)
- ✅ **Naming convention:** "Suite" suffix (matches Rep Layer)
- ✅ **GPT mappings confirmed:** MEDDPICC Qualifier Pro → Forecast Suite; MEDDPICC Cross-Deal Analyst → Call & Pattern Suite; Dana Sales Leadership Coach → Coaching Suite (orchestrator)
- ✅ **Champion's Code:** Stays as a methodology file in `/methodology/`, not a skill. Linked externally to Victor's Champion's Code app.
- ✅ **Operating Rhythm Suite:** Composes sub-skills from other three suites; this is real composition, not just naming
- ✅ **Detail level:** Architectural; specific skill content fleshed out by Codex + Victor per package, one at a time

---

## TOTAL OS PHASE 1 SCOPE (Rep + Manager Layers)

| Layer | Suites | Sub-skills |
|---|---|---|
| Rep Layer | 7 + onboarding | 34 |
| Manager Layer | 4 | 21 |
| **Total Phase 1** | **11 suites + 1 onboarding** | **55 sub-skills** |

Plus the methodology files (~14 in `/methodology/`).

---

## Leader / RevOps — Next

Apply the same lens to Phase 2 layers. My initial cut:

**Leader Layer — 3-4 Suites (Phase 2):**
- **Strategy Suite:** GTM design, target setting, capacity planning, pricing governance, sales play design
- **Reconciliation Suite:** Forecast reconciliation, attribution, customer lifecycle metrics, board narrative
- **Cross-Functional Suite:** Alignment, cultural audit (Champion's Code Scorecard for leaders)

**RevOps Layer — 3-4 Suites (Phase 2):**
- **Data & Infrastructure Suite:** CRM hygiene, tech stack audit, intent signals, data enrichment, lead scoring
- **Analytics & Insights Suite:** RevOps insights diagnostic, revenue reality check, dashboard builder, HubSpot diagnostic
- **Change Management Suite:** AI change management (Dana differentiator), quota/territory design, comp plan operationalization

But these are rough. Lock these when we get to Phase 2 planning, post-Phase 1 launch.

---

*Last updated: April 29, 2026. Manager Layer locked.*
