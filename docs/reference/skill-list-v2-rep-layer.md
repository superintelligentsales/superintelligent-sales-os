# Superintelligent Sales OS — Refined Skill List (v2)

> Restructured from v1 (April 29) based on architectural shift to **moment-packages with customization-first design**.
> 
> **Status:** Rep Layer LOCKED ✅ | Manager Layer next | Leader / RevOps after.

---

## Architectural principles

Three principles that govern every package in the OS:

### 1. Moment-packages, not standalone skills

Each Key Moment in the sales process becomes a **package** of related sub-skills that work together as a system, not a collection of one-trick utilities. A package follows the **mirror pattern**:

- **Before the moment** — research, prep, prior-context ingestion
- **During the moment** — script, talk track, real-time support
- **After the moment** — score the call, write the recap, hand off to the next stage

This matches how revenue work actually flows: discovery doesn't end when the call ends, and prospecting isn't a single action.

### 2. Customization is the architectural through-line

**Every skill in the OS requires customization to be useful.** The skill provides the framework, methodology, and structure. The user provides:

- Company info, products, value proposition
- ICP and personas
- Methodology preferences (SPICED, MEDDPICC, custom)
- Sales process stages and average cycle times
- Standard contract terms (for redline work)
- ROI model assumptions

This lives in the OS as:

- A `/context/` template (per-user customization file at the repo root)
- An onboarding skill that walks the user through setup
- Explicit "Customize this" sections in every SKILL.md
- A README that emphasizes customization upfront, not as an afterthought

**This is a competitive moat.** Generic AI tools don't customize at this depth. The OS does, by design.

### 3. GPTs become source material, not endpoints

Existing ChatGPT GPTs are **harvested** for skills, not linked to. The instructions, knowledge files, and examples from each GPT become the foundation for the skills that replace them. Skills are platform-agnostic, composable, methodology-grounded, and version-controllable. GPTs are kept live as a parallel distribution channel that points users back to the OS, but the skills are the canonical product.

---

## REP LAYER — 7 Moment-Packages

Each package is a folder under `/skills/rep/` containing a top-level package SKILL.md, sub-skill SKILL.md files, methodology references, and customization templates.

### Package structure

```
/skills/rep/{package-name}/
├── PACKAGE.md                    # Overview + customization guide
├── customization-template.md     # Inputs the user provides
├── sub-skills/
│   ├── {skill-1}/
│   │   ├── SKILL.md
│   │   ├── test-fixture.md
│   │   └── references/
│   ├── {skill-2}/
│   └── ...
└── methodology-refs.md           # Pointers to /methodology/ files used
```

---

### Package 1: BDR Suite

**Mirror pattern: Research → List Build → Outreach → Qualify → Score → Handoff**

The complete BDR/SDR workflow, from cold prospect to qualified handoff. Designed to be operated by a BDR or by an AE doing self-service prospecting.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `prospect-research` | Deep research on target prospect — business, sales motion, leadership | Existing skill: `research-prospect` |
| `list-builder` | Build prospect lists matching ICP from input criteria | Net-new |
| `customized-outreach` | Multi-touch outreach sequences personalized to research | Net-new |
| `qualification-call-prep` | Pre-call brief drawing on research + outreach context | Net-new |
| `qualification-call-scoring` | Score the qualification call vs. methodology | Net-new |
| `bdr-to-ae-handoff` | Structured handoff document with context, qualification status, next steps | Net-new |

**Customization required:**
- Your ICP definition
- Your qualification framework (BANT, SPICED, custom)
- Your outreach voice/tone
- Your tech stack (which CRM, sequencer, etc.)

**Customer Success persona note:** This same package shape applies to CSM-driven account expansion research, deferred to Phase 3.

---

### Package 2: Discovery Suite

**Mirror pattern: Research → Prep → Script → Run → Score → Recap → Handoff**

The complete discovery workflow. Operated by AEs after BDR handoff or self-sourced opportunities.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `discovery-prep` | Pre-call prep drawing on BDR handoff + fresh research | Builds on `Sage Discovery` GPT |
| `discovery-script` | SPICED-driven discovery script tailored to prospect | Builds on `Sage Discovery` GPT |
| `case-study-recommender` | Match relevant case studies to prospect's pain | Existing skill: `matching-case-studies` |
| `discovery-call-scoring` | Score discovery vs. SPICED with evidence and red flags | Builds on `SPICED Sales Call Analyst` GPT |
| `discovery-recap-email` | Recap email + lock-in next steps | Existing skill: `dana-recap-emails` |
| `discovery-to-demo-handoff` | Internal brief setting up demo prep | Net-new |

**Customization required:**
- Your discovery methodology (SPICED is default; supports MEDDPICC, custom)
- Your case study library
- Your ICP and persona definitions
- Your typical pain points and use cases

---

### Package 3: Demo Suite

**Mirror pattern: Pain Extraction → Feature Matching → Script → Run → Score → Follow-up**

The demo workflow, anchored in pain points surfaced during discovery.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `pain-extraction` | Pull articulated pain points from discovery transcripts + research | Net-new |
| `feature-benefit-matcher` | Match pain to product features and quantified benefits | Net-new |
| `demo-script-generator` | Personalized demo script with talk tracks per moment | Net-new |
| `demo-call-scoring` | Score demo execution + buyer engagement signals | Net-new |
| `demo-followup-email` | Follow-up email + objection-prep ahead of next call | Net-new |

**Customization required (heavy):**
- Your product's features and benefits library
- Your competitive differentiators
- Your demo flow and standard talk tracks
- Buyer persona library

This is one of the most customization-dependent packages. The methodology is generic; the value is in personalization.

---

### Package 4: Solutioning Suite

**Mirror pattern: Stakeholder Mapping → Engagement → Documentation → MAP**

The multi-stakeholder, multi-meeting work that bridges discovery to proposal. Includes the Mutual Action Plan as a central artifact.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `stakeholder-mapper` | Identify stakeholders + decision committee from research + calls | Net-new |
| `executive-summary-generator` | Multi-persona executive summary (same content, different framings) | Net-new |
| `stakeholder-meeting-prep` | Agenda + slides + narrative for stakeholder meetings | Net-new |
| `mutual-action-plan-builder` | MAP generator — heavily customized to user's sales process | Net-new |
| `se-handoff-brief` | Sales engineer handoff with technical context | Net-new |

**Customization required (very heavy):**
- Your sales process stages and average cycle time (for MAP)
- Your buyer personas + decision-committee patterns
- Your standard meeting templates
- SE engagement playbook

The Mutual Action Plan sub-skill is one of the most user-input-heavy in the entire OS. The user must input their sales process before MAP generation works.

**Use cases supported by this suite:**
- **Champion enablement** — building a champion's internal case via the executive summary, equipping them with stakeholder meeting materials, creating MAPs they can drive forward, giving them talk tracks per stakeholder. The combination of stakeholder-mapper + executive-summary-generator + stakeholder-meeting-prep + mutual-action-plan-builder is what champion enablement looks like in practice.
- **Multi-threaded deal expansion** — moving from single-contact deals to multi-stakeholder consensus
- **Procurement engagement** — bringing procurement into the deal early via stakeholder mapping
- **Internal deal review prep** — when an AE has to defend a deal to their manager (also references Manager Layer)

---

### Package 5: Business Case Suite

**Mirror pattern: ROI Quantification → Persona Translation → Talk Tracks**

The financial case + persona-specific framing. ROI is foundational; persona messaging derives from it.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `roi-calculator` | Customized ROI model based on customer inputs | Builds on `ROI & Business Case Builder` GPT |
| `business-case-document` | Full business case document with quantified value | Builds on `ROI & Business Case Builder` GPT |
| `persona-value-messaging` | Per-persona value framings derived from ROI | Net-new |
| `executive-talk-tracks` | Executive-level talk tracks for each persona | Net-new |

**Customization required (heavy):**
- Your ROI model assumptions (variables, formulas, default ranges)
- Your value drivers per persona
- Your typical financial KPIs by persona

---

### Package 6: Proposal & Negotiation Suite

**Mirror pattern: Proposal → Stakeholder → Negotiation → Redlines**

The proposal-through-contract sequence. Includes negotiation as a first-class skill (NEW — was missing from v1).

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `proposal-generator` | Generate proposal from deal data and standard template | Existing skill: `dana-proposal-writer` (extends) |
| `negotiation-prep` | Negotiation strategy + concession framework + talk tracks | Net-new |
| `contract-redline-analysis` | Compare incoming redlines against your standard agreement; surface implications | Net-new |
| `verbal-to-contract-sequencing` | Steps from verbal commitment to signed contract | Net-new |

**Customization required (very heavy):**
- Your standard proposal template
- Your standard contract terms (essential for redline analysis)
- Your discount/concession authority and policies
- Your legal review process

The contract-redline-analysis sub-skill is high-effort to set up (requires standard agreement loaded into customization layer) but high-value once configured. Worth flagging this as a heavier-lift skill in the package's README.

---

### Package 7: Close & Handoff Suite

**Mirror pattern: Customer Profile → Kickoff Prep → CS Handoff**

The transition from won deal to active customer. Less about closing tactics (that's in Package 6) and more about handoff quality.

| Sub-skill | Purpose | GPT source (if any) |
|---|---|---|
| `customer-profile-summary` | Comprehensive customer profile drawn from full sales cycle | Net-new |
| `kickoff-prep` | Kickoff meeting agenda + narrative | Net-new |
| `cs-handoff-document` | Detailed handoff doc tailored to CS team's intake needs | Net-new |

**Customization required:**
- Your CS team's intake requirements (varies wildly per company)
- Your kickoff meeting format
- Your customer onboarding process

This package is intentionally lean. The handoff is a critical moment but most of the artifacts are templates that need heavy customization rather than complex methodology.

---

## Cross-cutting: Customization Onboarding Skill

A standalone skill that runs *before* any moment-package is used. Walks the user through the customization template:

| Sub-skill | Purpose |
|---|---|
| `customization-onboarding` | Interactive setup that captures all the user-specific inputs the OS needs (ICP, methodology, products, sales process, etc.) and writes them to `/context/` |

This skill is the **first thing a user runs** after installing the OS. Without it, all other skills produce generic output.

---

## REP LAYER SUMMARY

| Package | Sub-skills | Customization weight | GPT source(s) |
|---|---|---|---|
| 1. BDR Suite | 6 | Medium | research-prospect (existing) |
| 2. Discovery Suite | 6 | Medium-high | Sage Discovery, SPICED Call Analyst, dana-recap-emails, matching-case-studies |
| 3. Demo Suite | 5 | High | Net-new |
| 4. Solutioning Suite | 5 | Very high | Net-new |
| 5. Business Case Suite | 4 | High | ROI & Business Case Builder |
| 6. Proposal & Negotiation Suite | 4 | Very high | dana-proposal-writer (existing, extends) |
| 7. Close & Handoff Suite | 3 | Medium-high | Net-new |
| Customization Onboarding | 1 | N/A — provides customization | Net-new |

**Total: 7 packages + 1 onboarding skill = 34 sub-skills**

(Down from 27 standalone skills in v1, but each is now richer and embedded in a package context. Net effect: more bundled methodology, fewer isolated utilities, easier to install and use as a system.)

---

## REP LAYER — Customization Layer Architecture

Every Rep Layer package reads from `/context/` for personalization. The `/context/` template includes:

```yaml
# /context/user-context.yaml
company:
  name: "Your Company"
  products: [...]
  value_propositions: [...]
  competitors: [...]

icp:
  primary_segments: [...]
  buyer_personas: [...]
  decision_committee_patterns: [...]
  typical_pain_points: [...]
  excluded_segments: [...]

methodology:
  qualification: "SPICED"  # or MEDDPICC, BANT, custom
  custom_methodology_file: null  # path if using custom

sales_process:
  stages: [...]
  average_cycle_days: 90
  stage_definitions: {...}

financial:
  acv_range: "30000-100000"
  pricing_model: "annual_subscription"
  discount_authority_levels: {...}
  standard_contract_path: "/context/standard-agreement.md"

cs_handoff:
  required_fields: [...]
  intake_format: "..."
  cs_team_owner: "..."

voice:
  tone: "professional, direct, results-focused"
  voice_filter_skill: "victor-voice-filter"  # or your own
```

The customization onboarding skill walks the user through populating this file. Without it, packages will prompt for the inputs at runtime, but performance suffers.

---

## REP LAYER — LOCKED DECISIONS (April 29, 2026)

- ✅ **Architecture:** 7 moment-packages (Suites) + Customization Onboarding Skill
- ✅ **Naming convention:** "Suite" suffix (BDR Suite, Discovery Suite, etc.) — reserves "Operating System" for the whole OS
- ✅ **GPT mappings confirmed:** Sage Discovery → Discovery Suite, SPICED Sales Call Analyst → Discovery Suite, ROI & Business Case Builder → Business Case Suite
- ✅ **Champion enablement:** Lives in Solutioning Suite as a use case, not a separate sub-skill (combines executive-summary-generator + stakeholder-meeting-prep + mutual-action-plan-builder)
- ✅ **Procurement, reference calls, internal review prep:** Use cases supported by Solutioning Suite, no new sub-skills needed
- ✅ **Detail level:** Architectural; specific skill content fleshed out by Codex + Victor per package, one at a time

---

## Manager / Leader / RevOps — Next

Once we lock Rep Layer, I'll apply the same lens to:

1. **Manager Layer** — likely 4 packages: Operating Rhythm, Coaching, Forecast, Call & Skill (rough cut)
2. **Leader Layer** — Phase 2; package boundaries TBD
3. **RevOps Layer** — Phase 2; package boundaries TBD

---

*Last updated: April 29, 2026. Supersedes `skill-list-for-review.md` v1.*
