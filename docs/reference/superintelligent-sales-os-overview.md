# Superintelligent Sales OS — Overview

> Internal canonical document. Single source of truth for the OS architecture, layers, skills inventory, methodology files, and tier strategy. External-facing pieces (Article 11, manifesto, sales decks, companion site copy) draw from this. Last revised: April 26, 2026.

---

## 1. Thesis

The Superintelligent Sales OS is an opinionated, AI-native operating system for B2B revenue organizations. It ships as installable skills (SKILL.md format) backed by canonical methodology files, organized across four layers — Rep, Manager, Leader, RevOps — that mirror the way a real revenue org actually works. The methodology is public; the consulting judgment in applying it is not.

Three principles govern everything inside it:

- **Beneath metrics are behaviors.** You cannot coach a number. You can only coach the activities and skills that produce it.
- **Methodology is free. Application is paid. Implementation is expensive. Partnership is bespoke.**
- **Shift and lift.** Every skill in the OS exists to shift administrative burden off humans so they can lift their capacity for the high-leverage work AI cannot do — coaching, judgment, building trust under uncertainty.

---

## 2. The hero illustration

| | Leads | Prospect→Qual | Qual→Disco | Disco→ROI | ROI→Propose | Propose→Verbal | Verbal→Contract | Contract→Win | Revenue |
|---|---|---|---|---|---|---|---|---|---|
| **Today** | 1,000 | 30% | 75% | 60% | 70% | 50% | 80% | 90% | **$1.7M** |
| **With OS** | 1,000 | 33% | 83% | 66% | 77% | 55% | 88% | 99% | **$3.3M** |

ACV: $50,000. Same leads. Same team. Same deal size. A 10% lift at each of seven moments compounds to roughly 2x revenue. This is the conversion proof that justifies the investment in the OS — and the math the methodology is engineered to deliver against.

---

## 3. Four-layer architecture

The OS organizes around four peer layers. Layers correspond to personas, not org charts. A small company with no dedicated RevOps still has *RevOps work* — it just gets absorbed by the senior sales executive (the fallback rule, see §8).

| Layer | Persona | Primary outputs | Time horizon | Center of gravity |
|---|---|---|---|---|
| **Rep** | AE / SDR / CSM | Closed deals, retained customers | Daily / per-deal | The Seven Key Moments |
| **Manager** | Frontline sales manager | Coached reps, accurate forecast, hit team quota | Weekly / quarterly | Core Six + 8 Bots + Operating Rhythm |
| **Leader** | CRO / EVP Sales | GTM strategy, top-down targets, cross-functional alignment | Quarterly / annual | Strategy, reconciliation, board narrative |
| **RevOps** | VP RevOps / Head of RevOps | Data integrity, forecast infra, tech stack, change adoption | Continuous | Infrastructure, systems, AI change management |

---

## 4. The Rep Layer — Seven Moment-Suites

Every B2B sale moves through seven specific moments where the rep's work converts the deal forward. Coaching at the moment level is concrete and trackable; coaching at the abstract skill level (*"improve discovery"*) is not.

**Architectural shift (April 29, 2026):** The Rep Layer is organized as **Suites of related sub-skills**, not standalone skills. Each Suite follows the mirror pattern: Before → During → After.

### Rep Layer Suite catalog

| Suite | Mirror pattern | Sub-skills | Customization weight |
|---|---|---|---|
| **BDR Suite** | Research → List Build → Outreach → Qualify → Score → Handoff | 6 | Medium |
| **Discovery Suite** | Research → Prep → Script → Run → Score → Recap → Handoff | 6 | Medium-high |
| **Demo Suite** | Pain Extraction → Feature Matching → Script → Run → Score → Follow-up | 5 | High |
| **Solutioning Suite** | Stakeholder Mapping → Engagement → Documentation → MAP | 5 | Very high |
| **Business Case Suite** | ROI Quantification → Persona Translation → Talk Tracks | 4 | High |
| **Proposal & Negotiation Suite** | Proposal → Stakeholder → Negotiation → Redlines | 4 | Very high |
| **Close & Handoff Suite** | Customer Profile → Kickoff Prep → CS Handoff | 3 | Medium-high |

**Plus the Customization Onboarding Skill** — the first skill a user runs after install, populating `/context/user-context.yaml` with company info, ICP, methodology, sales process, etc.

**Total: 7 Suites + 1 Onboarding Skill = 34 sub-skills.** Plus the cross-cutting Call Recording overlay (see §9).

Source of truth for the full sub-skill catalog: `skill-list-v2-rep-layer.md`.

### Existing Rep Layer GPTs that feed into Suites

GPTs are harvested as source material — not ported one-to-one. Each GPT's instructions + knowledge base + examples flow into the relevant Suite as Codex builds it.

| GPT | Feeds into | Specific sub-skill(s) |
|---|---|---|
| **SPICED Sales Call Analyst** | Discovery Suite | `discovery-call-scoring` |
| **Sage Discovery** | Discovery Suite | `discovery-prep`, `discovery-script` |
| **ROI & Business Case Builder** | Business Case Suite | `roi-calculator`, `business-case-document` |
| **Existing skill: `research-prospect`** | BDR Suite | `prospect-research` (port + extend) |
| **Existing skill: `dana-recap-emails`** | Discovery Suite | `discovery-recap-email` (port) |
| **Existing skill: `matching-case-studies`** | Discovery Suite | `case-study-recommender` (port) |
| **Existing skill: `dana-proposal-writer`** | Proposal & Negotiation Suite | `proposal-generator` (extend) |

### Use cases supported by Rep Layer Suites

The 20 AI use cases mapped earlier (§10) operate **within** Suites, not as standalone skills. Examples:

- **Champion enablement** — Solutioning Suite (executive summary + stakeholder meeting prep + MAP)
- **Multi-threaded deal expansion** — Solutioning Suite + Business Case Suite
- **Procurement engagement** — Solutioning Suite + Proposal & Negotiation Suite
- **Internal deal review prep** — Solutioning Suite (works with Manager Forecast Suite)
- **CRM auto-capture** — Cross-cutting capability, integrated into multiple Suites
- **Real-time call intelligence** — Cross-cutting capability tied to Call Recording overlay

---

## 5. The Manager Layer — Four Suites (Operating Rhythm, Coaching, Forecast, Call & Pattern)

The Manager Layer is the OS's center of gravity. The frontline manager is the highest-leverage role in any revenue org and the most under-supported. The methodology batch shipped in v1.0 (April 2026, ~11,900 words across 7 files) covers it end-to-end.

**Architectural shift (April 29, 2026):** Manager Layer organizes around the manager's **operating cadence** (weekly / bi-weekly / bi-monthly), not around individual bots. 4 Suites, not 8 standalone bots + orchestrators.

### Manager Layer Suite catalog

| Suite | Mirror pattern | Sub-skills | Customization weight |
|---|---|---|---|
| **Operating Rhythm Suite** | Plan cadence → Run meeting → Capture commitments → Reinforce | 5 | Medium |
| **Coaching Suite** | Diagnose → Plan → Practice → Reinforce | 6 | High |
| **Forecast Suite** | Score → Inspect → Triangulate → Reconcile | 5 | Medium-high |
| **Call & Pattern Suite** | Score → Aggregate → Pattern-match → Surface coaching opportunities | 5 | Medium-high |

**Total: 4 Suites = 21 sub-skills.**

Source of truth for the full sub-skill catalog: `skill-list-v2-manager-layer.md`.

### Core Six Manager Responsibilities (still the methodology backbone)

1. Opportunity Qualification → covered by Forecast Suite
2. Deal Management → covered by Forecast Suite + Coaching Suite
3. Call Planning & Coaching → covered by Coaching Suite + Call & Pattern Suite
4. Territory Management → covered by Operating Rhythm Suite + Forecast Suite
5. Account Management → covered by Operating Rhythm Suite
6. Team Skill Development → covered by Coaching Suite

### Operating Rhythm Suite — the orchestration layer

Operating Rhythm Suite is the **meta-suite that ties the other three together**. Its sub-skills compose from Coaching Suite, Forecast Suite, and Call & Pattern Suite into the manager's actual cadence:

- `weekly-team-meeting-prep` — composes from Forecast Suite + Call & Pattern Suite
- `weekly-1on1-prep` — composes from Coaching Suite + Forecast Suite
- `biweekly-deal-review` — composes from Forecast Suite + Coaching Suite
- `biweekly-skill-workshop` — composes from Coaching Suite
- `bi-monthly-forecast-review` — composes from Forecast Suite

This is real architectural composition, not just naming. The 1:1 prep sub-skill literally calls the TASK diagnostic from Coaching Suite plus the deal confidence sub-skill from Forecast Suite.

### Existing Manager Layer GPTs that feed into Suites

| GPT | Feeds into | Specific sub-skill |
|---|---|---|
| **MEDDPICC Qualifier Pro** | Forecast Suite | `meddpicc-qualifier` |
| **MEDDPICC Cross-Deal Analyst** | Call & Pattern Suite | `cross-deal-pattern-analysis` |
| **Dana Sales Leadership Coach** | Coaching Suite | `coaching-orchestrator` (top-level orchestrator) |

### Champion's Code — methodology, not a skill

The Champion's Code 7 elements (Recognition, Practice, Learning, Collaboration, etc.) is a **cultural methodology**, not a skill. It lives as `methodology/champions-code-seven-elements.md` and is referenced by skills in Coaching Suite and Operating Rhythm Suite. Externally, Victor maintains a Champion's Code self-assessment app; the methodology file links to it for users who want to score their team's culture against the 7 elements without installing the OS.

---

## 6. The Leader Layer — Strategy, reconciliation, board narrative

The senior sales executive (CRO / EVP Sales) is responsible for **strategy and reconciliation**, not deal inspection. The methodology assumes top-down targets get set here and bottoms-up forecasts get reconciled here. Where RevOps doesn't exist, Leader absorbs RevOps responsibilities (see §8).

| Skill | Function |
|---|---|
| `leader/gtm-strategy-design` | GTM blueprint + revenue target cascading; STP, ICP design, TAM/SAM/SOM, where-to-play / how-to-win choices |
| `leader/top-down-target-setting` | Annual/quarterly target methodology |
| `leader/forecast-reconciliation` | Top-down vs. bottoms-up gap analysis |
| `leader/cross-functional-alignment` | Sales / Marketing / CS OKR alignment; Standing Revenue Council governance |
| `leader/customer-lifecycle-metrics` | NRR / CLTV / churn dashboard (use case #16); references Bowtie, Opportunity Lifecycle, Postsale Sequence (Deliver / Develop / Confirm / Activate) |
| `leader/attribution-funnel-analysis` | Multi-touch attribution (use case #14) |
| `leader/renewal-expansion-detection` | Expansion opportunity identification (use case #18); applies Postsale Sequence (D/D/C/A) framework |
| `leader/field-engagement-tracker` | Enforces "1:1 per rep per quarter" rule |
| `leader/systemic-blocker-diagnostic` | Surfaces macro-level hurdles |
| `leader/board-narrative-builder` | Board-ready performance story; includes base/best/worst scenario planning |
| `leader/champions-code-scorecard` | Culture audit instrument |
| `leader/pricing-governance` | Pricing strategy, discount approval, deal desk rules, value metrics |
| `leader/capacity-planning` | Headcount math: ramp time, attainment, turnover, cycle length, coverage |
| `leader/sales-play-design` | Repeatable sales plays per segment/persona |
| `leader/qbr-governance-framework` | Defines QBR/EBR cadence, structure, and reconciliation standards (Rep executes via `rep/qbr-execution-framework`) — *Phase 3 (Customer Success)* |

### Existing Leader Layer GPT inventory

| GPT | Maps to |
|---|---|
| **Revenue Planning to Execution Advisor** | `leader/gtm-strategy-design` + `leader/top-down-target-setting` |
| **B2B Sales Funnel & Revenue Planning** | `leader/funnel-diagnostic` |
| **B2B Sales Funnel Analyst (Pro)** | `leader/funnel-diagnostic-deep` |
| **B2B Sales Funnel Analyst (Pro - N...)** | Variant — clarify scope before port |

---

## 7. The RevOps Layer — Infrastructure, systems, change management

RevOps is a peer layer (not a sub-layer of Leader) because nine of the 20 AI use cases sit here. RevOps owns the infrastructure that powers every other layer's analytics and AI capabilities — and owns AI change management as a differentiated capability.

### RevOps methodology files (planned)

- `revops-charter-and-scope.md` — what RevOps owns vs. Sales Ops vs. Marketing Ops
- `crm-hygiene-standards.md` — data quality framework
- `forecast-infrastructure.md` — pipeline modeling, conversion rates, capacity planning
- `tech-stack-rationalization.md` — CRM-first architecture principle
- `quota-territory-design.md` — TAM-based quota math, ramp schedules
- `comp-plan-operationalization.md` — comp design + tracking infrastructure
- `kpi-standardization.md` — definitions framework (what counts as MQL, etc.)
- `change-management-three-phases.md` — Mobilize / Activate / Sustain (moved from Leader)
- `adkar-barrier-points.md` — five sequential barriers (moved from Leader)
- `ai-change-management.md` — **AI-specific adoption playbook** (Dana differentiator)

### RevOps skills

| Skill | Use case | Function |
|---|---|---|
| `revops/intent-signal-aggregation` | #1 | Surface and act on 3rd-party buying signals (Bombora, G2) |
| `revops/data-enrichment` | #2 | Auto-enrich leads/accounts; prioritize on buying readiness |
| `revops/lead-account-scoring` | #3 | Adaptive scoring on engagement + conversion history |
| `revops/audience-segmentation` | #4 | Smart audience groups for targeted campaigns |
| `revops/campaign-optimization` | #5 | Multi-channel spend + sequencing |
| `revops/crm-hygiene-infra` | #12 (infra) | Auto-log meetings, notes, opportunity data; enforces 6 data quality dimensions (accuracy, completeness, consistency, validity, uniqueness, integrity) |
| `revops/insights-diagnostic` | #15 | AI copilot surfacing GTM inefficiencies + root causes |
| `revops/support-triage-engine` | #19 | Categorize, prioritize support tickets; flag NRR risk — *Phase 3 (Customer Success)* |
| `revops/ai-change-management` | #20 | Adaptive onboarding + contextual training for GTM |
| `revops/tech-stack-audit` | — | CRM-first architecture audit |
| `revops/quota-territory-design` | — | TAM-based quota math |
| `revops/comp-plan-operationalization` | — | Comp design + CRM tracking |
| `revops/dashboard-builder` | — | Executive + team-level GTM dashboards |
| `revops/revenue-reality-check` | — | Validate growth goal achievability against funnel math |
| `revops/hubspot-revops-diagnostic` | — | CRM portal diagnostic across data integrity / automation / tech stack / reporting |

### Existing RevOps Layer GPT inventory

| GPT | Maps to |
|---|---|
| **AI Use Case Advisor - GTM Interventions** | `revops/ai-use-case-advisor` (intake → recommendations skill) |
| **Sage Discovery** | `revops/change-readiness-discovery` — change-management discovery, surfaces adoption barriers and stakeholder readiness |

---

## 8. The three overlap zones + fallback rule

Three responsibilities legitimately span layers. The OS resolves the overlap with explicit ownership rules per zone.

| Zone | Leader owns | RevOps owns | Manager owns |
|---|---|---|---|
| **Forecasting** | Top-down target; reconciles top-down vs. bottoms-up; pipeline gap analysis | Infrastructure: pipeline models, conversion rates, capacity planning, CRM hygiene | Bottoms-up rep-level forecast; deal inspection; rep accuracy |
| **Quota & Comp** | Sets philosophy and incentive intent | Designs the math; operationalizes in CRM/comp tools; territory data | Communicates plan; coaches to plan; flags inequities |
| **Change Management** | Provides executive sponsorship and narrative | Owns the system: program design, ADKAR diagnostics, AI adoption playbooks | Reinforces at the rep level; coaches through resistance |

### The fallback rule

> **If RevOps doesn't exist, the senior sales executive absorbs RevOps responsibilities.**

Most midmarket companies under ~50 reps don't have dedicated RevOps. Practical implications:

1. Every RevOps skill is persona-flexible — works whether the user is a VP RevOps or a CRO absorbing the function.
2. Skill descriptions explicitly call this out: *"Owned by RevOps where the function exists; by the senior sales executive otherwise."*

---

## 9. Cross-cutting overlay: Call Recording

Call Recording is not a single skill — it's an architectural primitive that runs underneath the entire Rep Layer execution flow, with hooks into Manager (coaching review), RevOps (transcript data infrastructure), and Leader (funnel-level pattern analysis).

The seven moments are the conversion points; call recording is the **reinforcement, accountability, and improvement layer that runs beneath all of them.**

| Layer | Call Recording skill | Function |
|---|---|---|
| Rep | `rep/realtime-call-intelligence` | In-call assist + post-call summary |
| Manager | `manager/call-scoring` (Bot #3) | Objective SPICED scorecards on 100% of calls |
| RevOps | `revops/transcript-data-pipeline` | Data infrastructure feeding analytics |
| Leader | `leader/conversational-pattern-analysis` | Funnel-level patterns across thousands of calls |

### Methodology file (planned v1.1)

`call-recording-overlay.md` — establishes the cross-cutting architecture, integration points, and the reinforcement loop from rep behavior → manager coaching → leader strategy → RevOps measurement.

---

## 10. The 20 AI use cases mapped to layers

| # | Use case | Primary | Secondary | Stage |
|---|---|---|---|---|
| 1 | Intent Signal Aggregation & Activation | RevOps | — | Top of funnel |
| 2 | Data Enrichment & Prioritization | RevOps | — | Top of funnel |
| 3 | Intelligent Lead & Account Scoring | RevOps | — | Top of funnel |
| 4 | Audience Segmentation & Dynamic Cohorting | RevOps | — | Top of funnel |
| 5 | Multi-Channel Campaign Optimization | RevOps | — | Top of funnel |
| 6 | Personalized Content Generation | Rep | — | Top of funnel |
| 7 | Agentic Prospecting & Email Sequencing | Rep | RevOps (infra) | Top of funnel |
| 8 | Real-Time Call/Meeting Intelligence | Rep | Manager (review) | Mid-funnel |
| 9 | Playbook & Objection Handling Copilot | Rep | Manager (content) | Mid-funnel |
| 10 | Automated Account Research & Prep | Rep | — | Mid-funnel |
| 11 | Sales Content Recommendation Engines | Rep | RevOps (rules) | Mid-funnel |
| 12 | Automated CRM Capture & Update | Rep | RevOps (infra) | Pipeline mgmt |
| 13 | Pipeline Risk & Forecasting Analysis | Manager | Leader (reconcile) | Pipeline mgmt |
| 14 | Attribution & Funnel Analysis | Leader | RevOps (infra) | Full funnel |
| 15 | RevOps Insights & Diagnostic Copilots | RevOps | Leader (consume) | Full funnel |
| 16 | Customer Health Scoring | Leader | Rep (CSM execution) | Post-sale |
| 17 | CSM Email Drafting & Meeting Summaries | Rep (CSM) | — | Post-sale |
| 18 | Renewal & Expansion Opportunity Detection | Leader | Rep (AE/CSM) | Post-sale |
| 19 | Proactive Support Ticket Triage | RevOps | Rep (CSM) | Post-sale |
| 20 | AI-Powered Change Management & Training | RevOps | Manager (delivery) | Enablement |

**Distribution:** RevOps 9 / Rep 8 / Leader 4 / Manager 1. RevOps is the largest cluster — confirms the peer-layer call. Manager is small here because the Manager Layer's center of gravity is *coaching* (Core Six + 8 Bots), not *capability*.

---

## 11. Tier strategy

| Tier | What | Pricing instinct | Conversion target |
|---|---|---|---|
| **1. Free OS** (GitHub + companion site) | Methodology + complete skill code, MIT-licensed | Free | Awareness → newsletter signup → diagnostic |
| **2. Paid Substack** | Application examples, live case studies, diagnostic walk-throughs, Q&A, templates | $20-30/mo or $200-300/yr | Newsletter → paid → diagnostic referral |
| **3. Productized Engagements** | Diagnostic, Quarterly Sprint, Connected Implementation, VoiceIQ | $10-50K diagnostic; $35-50K sprint | Diagnostic → sprint → connected |
| **4. Custom Consulting** | Multi-quarter strategic, advisory board, transformation | $200K+ | Apex tier; expansion or referral |

### The principle

> **Methodology is free. Application is paid. Implementation is expensive. Partnership is bespoke.**

This is the test for any future content/asset decision. Where does it sit? That answer maps directly to free / Substack / productized / custom.

### Common mistakes to avoid

1. Don't gate methodology behind paid Substack. The methodology is the funnel.
2. Don't give away application examples free. That's the Substack value prop.
3. Don't free-tier diagnostic work. Quick-win offers can be free; structured diagnostic-with-deliverable cannot.
4. Don't blur Tiers 3 and 4. Tier 3 is productized (fixed scope, fixed price). Tier 4 is custom. Mixing them destroys margin in Tier 3.

---

## 12. Foundational principles (cross-cutting)

These principles inform every skill, every methodology file, and every consulting engagement. They show up in skill system prompts, in article series content, and in client-facing materials.

### Shift and Lift

Every skill exists to **shift administrative burden off humans** so they can **lift their capacity for the high-leverage work AI cannot do** — coaching, judgment, building trust under uncertainty. Productivity math: high-performing AI deployments report 25-30% increase in revenue-generating activity time, with strategic ambitions to reach 70-80%.

### Activity coaching beats skill coaching by 12x

Vazzana's *Crushing Quota* research: activity coaching drives ~24% of quota variance vs. ~2% from skill coaching. Twelve times the leverage. The reason is psychological — salespeople are motivated by **clarity of task**. The highest-leverage coaching converts skill goals into activity targets.

### Diagnose & Treat

Group meetings diagnose team-level patterns. Triggered 1:1s treat individual gaps. The cardinal sin is solving individual performance problems in a group setting.

### TASK over REKS

The canonical Dana measurement framework. **T**arget Result → **A**ctivities (Key Sales Moments) → **S**kill (Practiced + Quality) → **K**nowledge (Process / Product / Prospect). Activities = Key Sales Moments creates the explicit bridge from manager coaching to rep execution.

### The 80% rule

AI generates the first 80% of any deliverable; humans finalize the remaining 20%. Pursuing 100% AI output destroys quality and burns time on rework. Naming the 80% boundary protects throughput.

### CRM-first architecture

Every tool in the RevOps stack must sync directly with the CRM. Disconnected tools create data silos, slow processes, and drive up costs. SaaS sprawl is the enemy.

### Customization-first architecture

Every skill in the OS requires customization to be useful. The skill provides framework + methodology + structure. The user provides company info, ICP, methodology choices, sales process stages, voice, and other inputs through `/context/user-context.yaml`. The Customization Onboarding Skill is the first skill a user runs after install. Without customization, every skill produces generic output. **This is a competitive moat** — generic AI tools don't customize at this depth; the OS does, by design.

### Suites, not standalone skills

Each Key Moment in the sales process is a **Suite** containing related sub-skills that work together as a system, not a collection of one-trick utilities. Each Suite follows a mirror pattern (Before → During → After). Skills compose with sibling skills inside the Suite, and Suites can compose with other Suites (Operating Rhythm Suite composes from Coaching, Forecast, and Call & Pattern Suites).

---

## 13. Repository structure

```
github.com/superintelligentsales/superintelligent-sales-os/
├── README.md
├── LICENSE                                  # MIT
├── docs/
│   ├── CODEX_BUILD_HANDOFF.md
│   └── reference/                           # Canonical reference docs Codex reads
├── methodology/                             # Flat methodology files
│   ├── superintelligent-sales-whitepaper.md       🆕 Phase 1
│   ├── seven-key-moments.md                       🆕 Phase 1
│   ├── core-six-manager-responsibilities.md       🆕 Phase 1
│   ├── three-principles-secure-attachment.md      🆕 Phase 1
│   ├── champions-code-seven-elements.md           ✅ Existing (links to external app)
│   ├── task-coaching-diagnostic.md                ✅ Existing
│   ├── managing-to-metrics-library.md             ✅ Existing
│   ├── five-step-coaching-conversation.md         ✅ Existing
│   ├── 60-min-1on1-structure.md                   ✅ Existing
│   ├── forecast-triangulation-method.md           ✅ Existing
│   ├── bi-monthly-forecast-cadence.md             ✅ Existing
│   ├── operating-rhythm.md                        🆕 Phase 1
│   ├── call-recording-overlay.md                  🆕 Phase 1
│   ├── strategic-opportunity-blueprint.md         🆕 Phase 1 (Blue Sheet)
│   └── ... (Phase 2 methodology files added later)
├── skills/                                  # Pattern B: Suite folders, sub-skill folders
│   ├── rep/
│   │   ├── _onboarding/                    # Customization Onboarding Skill
│   │   ├── bdr-suite/
│   │   │   ├── PACKAGE.md
│   │   │   ├── customization-template.md
│   │   │   └── sub-skills/
│   │   │       ├── prospect-research/
│   │   │       │   ├── SKILL.md
│   │   │       │   ├── test-fixture.md
│   │   │       │   └── references/
│   │   │       └── ... (6 sub-skills)
│   │   ├── discovery-suite/                # 6 sub-skills
│   │   ├── demo-suite/                     # 5 sub-skills
│   │   ├── solutioning-suite/              # 5 sub-skills
│   │   ├── business-case-suite/            # 4 sub-skills
│   │   ├── proposal-negotiation-suite/     # 4 sub-skills
│   │   └── close-handoff-suite/            # 3 sub-skills
│   └── manager/
│       ├── operating-rhythm-suite/         # 5 sub-skills (composes other suites)
│       ├── coaching-suite/                 # 6 sub-skills
│       ├── forecast-suite/                 # 5 sub-skills
│       └── call-pattern-suite/             # 5 sub-skills
├── context/                                 # Per-user customization
│   ├── README.md
│   └── user-context.yaml.template
└── bundles/                                 # Layer-bundle install YAML
    ├── rep-layer.yaml
    ├── manager-layer.yaml
    └── full-os.yaml
```

**Phase 1 scope:** 11 Suites + 1 Onboarding Skill = 55 sub-skills + 14 methodology files. Source of truth for the catalog: `skill-list-v2-rep-layer.md` and `skill-list-v2-manager-layer.md`.

**Phase 2 expansion:** Adds `/skills/leader/` and `/skills/revops/` Suite folders (architecture TBD during Phase 2 planning).

---

## 14. Release phasing & build sequence

The OS releases in 4 phases over ~6 months. Each phase is its own launch event with complete methodology + working skills for the layers in scope. Phased rollout creates publishing rhythm and prevents launch-day scope overload.

### Phase 1 — Rep Layer + Manager Layer (Initial launch, ~Month 0)

**Scope:** Pre-sale through Close & Handoff to CS. Excludes post-sale execution.

**In scope:**
- **Rep Layer:** 7 Suites + Customization Onboarding Skill = 34 sub-skills
  - BDR Suite, Discovery Suite, Demo Suite, Solutioning Suite, Business Case Suite, Proposal & Negotiation Suite, Close & Handoff Suite
- **Manager Layer:** 4 Suites = 21 sub-skills
  - Operating Rhythm Suite, Coaching Suite, Forecast Suite, Call & Pattern Suite
- **Methodology:** 14 files (7 existing + 7 new)
- **Cross-cutting:** Call Recording overlay (referenced by skills in both layers)
- **Foundational:** All 12 architectural principles + customization-first architecture

**Total: 55 sub-skills across 11 Suites + 1 Onboarding.**

**Out of scope (deferred to Phase 3):** CSM persona work, QBR execution, use cases #16-19.

**Build mode:** Collaborative with Codex. One sub-skill per PR, with Victor providing source materials (GPT exports, methodology, examples) per skill. ~70+ PRs across Phase 1.

**Anchor article:** Combined launch announcement (originally Articles 1 + 11 collapsed) — frames the OS, announces Phase 1, and teases the upcoming series.

### Phase 2 — Sales Leader + RevOps (~Month 2)

**Scope:** Strategic and infrastructure layers around the Rep+Manager OS.

**In scope:**
- **Leader Layer:** 14 of 15 skills (defers `qbr-governance-framework`)
- **RevOps Layer:** 15 of 16 skills (defers `support-triage-engine`)
- **Methodology files:** Pricing & discount governance, capacity planning, sales play design, RevOps charter, AI change management

**Out of scope (deferred to Phase 3):** QBR governance, support triage, post-sale execution skills.

**Anchor article:** Phase 2 launch piece TBD — likely a strategic-leader-focused angle (working title: *The Sales Factory* — Article 6 in current roadmap could re-anchor here).

### Phase 3 — Customer Success (Future, ~Month 4-5)

**Scope:** Post-sale execution and strategic governance.

**In scope:**
- **Rep Layer additions:** `rep/qbr-execution-framework`, `rep/csm-comms-automation`
- **Leader Layer additions:** `leader/qbr-governance-framework`
- **RevOps Layer additions:** `revops/support-triage-engine`
- **AI use cases activated:** #16 Customer Health Scoring, #17 CSM Email Drafting, #18 Renewal & Expansion, #19 Support Triage
- **Methodology files:** `qbr-execution-framework.md`

### Phase 4 — Marketing (Future, ~Month 6+)

**Scope:** TBD. May incorporate marketing-specific skills around demand generation, brand, content strategy, channel orchestration. Some Top-of-Funnel RevOps skills (#1-5) may rebalance here at this phase.

---

### Build sequence (current state, April 29, 2026)

The Phase 1 build runs collaboratively with Codex, **one sub-skill per PR**. Total ~70+ PRs across Phase 1.

| Phase | Item | Status |
|---|---|---|
| **Foundation** | Manager Layer methodology batch (7 files, ~11,900 words) | ✅ Complete |
| **Foundation** | Brief v2 (~7,020 words) | ✅ Complete |
| **Foundation** | Repo spec + asset register | ✅ Updated |
| **Foundation** | Article roadmap (14 articles) | ⚠️ Needs update for announcement-first model |
| **Foundation** | Birds-eye doc (this file) | ✅ Updated for Suite architecture |
| **Foundation** | Skill list v2 — Rep Layer (`skill-list-v2-rep-layer.md`) | ✅ Locked |
| **Foundation** | Skill list v2 — Manager Layer (`skill-list-v2-manager-layer.md`) | ✅ Locked |
| **Foundation** | Codex Build Handoff v2 | ✅ Updated for Suite architecture + collaborative model |
| **Phase 1 — Setup** | GitHub repo + org (`superintelligentsales`) | ✅ Complete |
| **Phase 1 — Setup** | Commit `/docs/reference/` to repo | ⏳ Pre-flight |
| **Phase 1 — Setup** | Customization Onboarding Skill (`rep/_onboarding/`) | ⏳ Build first |
| **Phase 1 — Manager** | Coaching Suite (6 sub-skills) | ⏳ Build |
| **Phase 1 — Manager** | Forecast Suite (5 sub-skills) | ⏳ Build |
| **Phase 1 — Manager** | Call & Pattern Suite (5 sub-skills) | ⏳ Build |
| **Phase 1 — Manager** | Operating Rhythm Suite (5 sub-skills) | ⏳ Build last in Manager Layer |
| **Phase 1 — Rep** | Discovery Suite (6 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | BDR Suite (6 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | Demo Suite (5 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | Solutioning Suite (5 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | Business Case Suite (4 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | Proposal & Negotiation Suite (4 sub-skills) | ⏳ Build |
| **Phase 1 — Rep** | Close & Handoff Suite (3 sub-skills) | ⏳ Build |
| **Phase 1 — Methodology** | 7 new methodology files (whitepaper, seven-key-moments, core-six, three-principles, operating-rhythm, call-recording-overlay, strategic-opportunity-blueprint) | ⏳ Write with Victor's source material |
| **Phase 1 — Close** | Bundles + context templates + README finalization | ⏳ Build |
| **Phase 1 — Launch** | Combined launch announcement article | ⏳ Write |
| **Phase 2 — Build** | Leader Layer Suites (TBD) + RevOps Layer Suites (TBD) | ⏳ Architecture locked during Phase 2 planning |
| **Phase 2 — Launch** | Phase 2 launch article | ⏳ Write |
| **Phase 3 — Build** | Customer Success additions (rep CSM Suite, leader QBR governance, revops support triage) | ⏳ Build |
| **Phase 3 — Launch** | Phase 3 launch article | ⏳ Write |
| **Phase 4 — Plan** | Marketing scope TBD | ⏳ Plan |

---

## 15. Quotable principles for external use

These show up in articles, on the companion site, in sales decks, and in LinkedIn posts. Pulled from the foundational principles above for easy reuse.

> **Methodology is free. Application is paid. Implementation is expensive. Partnership is bespoke.**

> **Beneath metrics are behaviors. You cannot coach a number — only the activities and skills that produce it.**

> **Activity coaching has twelve times the leverage of skill coaching. Salespeople are motivated by clarity of task.**

> **Group meetings diagnose. Triggered 1:1s treat. The cardinal sin is solving individual problems in a group setting.**

> **Routine sets you free.** *(Verne Harnish, on the Rockefeller Rhythm — adopted as the operating rhythm principle)*

> **The seven moments are where deals are won. Call recording is the reinforcement layer that runs beneath all of them.**

> **The frontline manager is the highest-leverage role in any revenue org and the most under-supported. AI doesn't replace the manager — it gives the manager back the time to do their actual job.**

---

## 16. Article-direction mapping (writing guide)

Each article in the public series draws from specific sections of this doc. When writing, pull the structure and claims from the indicated sections — and apply the suggested angle.

| # | Article | Draws from | Angle |
|---|---|---|---|
| 1 | *The 1.0 / 2.0 / 3.0 Question* | §1 Thesis, §12 Foundational principles | The maturity model is the diagnostic frame. 1.0 = manual heroics. 2.0 = process discipline. 3.0 = AI-native operating system. Hero stat optional opener. |
| 2 | *Customer Communications Drive Sales Superintelligence* | §4 Seven Moments, §9 Call Recording overlay | Voice of customer extraction. Call recording as the data layer that powers every other capability. |
| 3 | *The Seven Moments Where Revenue Is Won or Lost* | §2 Hero stat, §4 Seven Moments, §9 Call Recording overlay | Open with $1.7M → $3.3M math. Walk through each moment with the skill catalog. Call recording as cross-cutting reinforcement. |
| 4 | *The Three Trios* | §3 Four-layer architecture, §10 20 use cases | Three diagnostic dimensions: Layer (who), Moment (when), Capability (what AI does). Diagnostic mental model for any AI investment. |
| 5 | *The Manager's Leverage* | §5 Manager Layer, §12 (TASK, Activity coaching beats skill 12x) | Manager as the highest-leverage role. Core Six. The 12x stat. The 8 Bots as redirected time, not added effort. |
| 6 | *The Sales Factory* | §6 Leader Layer, §12 (CRM-first) | The factory metaphor: inputs (leads, quota) → process (Manager Layer + RevOps) → outputs (revenue, retention). Leader as factory architect. |
| 7 | *The Behavioral Bridge — Why Most Sales Training Fails* | §12 (TASK, Diagnose & Treat), §5 (Five-Step Coaching) | Training without behavior change is theater. The bridge: manager + operating rhythm + 30-practice rule. |
| 8 | *The Champion's Code — Why Culture Sustains What Process Starts* | §5 Manager Layer (Champion's Code), `champions-code-seven-elements.md` | The 7 elements. Culture as the moat. Recognition, practice, collaboration, learning. |
| 9 | *The Adoption Layer — Why 70% of Change Initiatives Fail* | §7 RevOps Layer, §8 Change Mgmt overlap zone, §12 (AI Change Management) | Why most AI rollouts fail. ADKAR. Three phases. AI-specific change management as the Dana differentiator. |
| 10 | *The Diagnostic Ladder — How to Know Where to Start* | §6 Leader Layer diagnostics, §11 Tier strategy, §12 (Diagnose & Treat) | Diagnostic before prescription. The ladder: Quick win → Diagnostic → Sprint → Connected. |
| 11 | *The Superintelligent Sales OS* | **All sections — focused on Phase 1 (Rep + Manager)** | The Phase 1 unveiling. Architecture, Rep + Manager layers, the principle ("Methodology is free…"), the math, the offer. Phase 2-4 get their own launch articles. |
| 12 | *The Operating Rhythm* | §5 Operating Rhythm orchestrators, `operating-rhythm.md` (v1.1) | Three Pillars (Priorities × Data × Rhythm). Four Cadences. Verne Harnish framing. *"Routine sets you free."* |
| 13 | *Pipeline Surgery — From Theater to Diagnosis* | §5 (Bi-monthly forecast cadence, Three Types of Deal Reviews), §12 (Diagnose & Treat) | Pipeline Theater vs. Pipeline Surgery. The 67/73/89 stats. SPICED as the scalpel. |
| 14 | *The Five-Step Coaching Conversation — How Managers Actually Change Behavior* | §5 (Five-Step Coaching), §12 (Activity coaching beats skill 12x) | The dual-layer protocol: macro (5 steps) + micro (Autonomy & Mastery probe). Why telling fails; questioning works. |

### Future article candidates (not in v1.0 series — gaps surfaced from research)

| Working title | Draws from | Why |
|---|---|---|
| *The Pricing Lever — How B2B Companies Forfeit Margin* | `leader/pricing-governance`, `pricing-discount-governance.md` | Bain's research positions pricing as Top-2 commercial-excellence lever. Currently absent from the v1.0 series. |
| *Capacity, Not Quota — Why Most Revenue Plans Are Math-Broken* | `leader/capacity-planning`, `quota-territory-design.md` | Most "revenue plans" are quota allocations divorced from ramp/attainment/turnover math. Worth its own piece. |
| *The Sales Play Library — Repeatable Plays Beat Heroic Reps* | `leader/sales-play-design` | Bain's "repeatable sales plays" finding. Differentiates strategy-driven orgs from rep-dependent ones. |

---

## 17. What this doc is for

- **Single source of truth** for the OS architecture. When in doubt about a layer assignment, a skill location, or an overlap zone, refer here.
- **Onboarding aid** for collaborators (Jase, partners, future team members). Read this first; everything else makes sense afterward.
- **Article-roadmap input.** Article 11 (the OS launch piece) draws directly from this. Article 1 (the Maturity Model piece) sets up the architecture this doc canonicalizes.
- **Sales pitch foundation.** Any external presentation of the OS pulls structure, claims, and quotable principles from here.
- **Drift control.** Long sessions risk subtle architectural drift. This doc gets updated when architecture changes, and resumed sessions reference it before making structural decisions.

---

*Authored by Victor Adefuye. Last revised April 29, 2026 (Suite architecture revision). Companion documents: `dana-sales-management-brief-v2.md` (canonical methodology), `skill-list-v2-rep-layer.md` and `skill-list-v2-manager-layer.md` (Suite architecture source of truth), `codex-build-handoff-v2.md` (collaborative build brief for Codex), `superintelligent-sales-os-repo-spec.md` (repository architecture), `superintelligent-sales-os-asset-register.md` (build status), `superintelligent-sales-article-series-roadmap.md` (publication plan — needs update for announcement-first model).*
