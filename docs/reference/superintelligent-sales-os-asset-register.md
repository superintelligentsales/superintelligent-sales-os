# Superintelligent Sales OS — Asset Register

*Working inventory document | Update as ports complete | Last updated: April 2026*

---

## Purpose

This is the master tracking document for every existing Dana Consulting asset that maps into the Superintelligent Sales OS. It answers: *what exists, where it lives today, where it goes in the repo, and what work is needed to port it.*

This is operationally distinct from the architecture spec. The architecture spec answers "how is the repo structured." This document answers "what's the migration backlog, and what's done."

**Use this document to:**
- Track port progress
- Estimate remaining work
- Avoid duplicating builds that already exist
- Onboard collaborators to what's available

---

## Status Legend

| Symbol | Meaning |
|---|---|
| ✓ Ready | Already in SKILL.md format; needs only structural polish (frontmatter, references, examples folder) |
| ✅ Built (Apr 2026) | Methodology file complete in canonical markdown form; ready for repo placement (Manager Layer v1.0 batch) |
| ⚠️ Needs port | Exists as GPT/app/document; needs conversion to SKILL.md with reference files |
| 🆕 New build | No current equivalent; needs to be built from source methodology |
| 📦 Stays external | Better as a web app/calculator; linked from repo, not ported into it |
| ⛔ Excluded | Not appropriate for customer-facing OS (internal tools, brand utilities) |
| 🔒 Paid only | Ships as paid-tier asset, not in public repo |

---

## 1. Quick Win Offers Library v2.2 (33 Assets)

### 1.1 Free GPTs (4)

| ID | Name | Current Surface | Status | Target | Effort |
|---|---|---|---|---|---|
| F1 | MEDDPICC Cross-Deal Analysis Bot | Beehiiv-linked CustomGPT | ✓ Ready | `skills/manager/` (composes `extract-meddpicc` + `analyze-category` + `compare-categories`) | 1 hr (orchestrator wrapper) |
| F2 | SPICED Sales Call Analyst | Beehiiv-linked CustomGPT | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-spiced/` | 0.5 hr (polish only) |
| F3 | B2B Sales Funnel Analyst (Lite) | Beehiiv-linked CustomGPT | ⚠️ Needs port | `skills/leader/funnel-diagnostic-lite/` | 1-2 hr |
| F4 | MEDDPICC Qualifier Pro (Single Deal) | Direct ChatGPT GPT | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-meddpicc/` (single-deal mode) | 0.5 hr |

### 1.2 Free Apps (6)

| ID | Name | Current Surface | Status | Target | Effort |
|---|---|---|---|---|---|
| A1 | AI Quota Attainment Calculator | Beehiiv interactive app | 📦 Stays external | Linked from `skills/leader/maturity-assessment/` and ROI-related skills | None (linked) |
| A2 | AI Time-Savings Calculator | Beehiiv interactive app | 📦 Stays external | Linked from skills | None (linked) |
| A3 | AI Conversion Rate Calculator | Beehiiv interactive app | 📦 Stays external | Linked from `skills/leader/funnel-diagnostic-lite/` | None (linked) |
| A4 | Sales Enablement Maturity Assessment | Beehiiv interactive app | ⚠️ Needs port | `skills/leader/maturity-assessment/` | 1 hr |
| A5 | The Champion's Code | Beehiiv interactive app | ⚠️ Needs port | `skills/leader/champions-code-scorecard/` | 1 hr |
| A6 | Revenue Reality Check Calculator | Perplexity Apps | ⚠️ Needs port | `skills/leader/revenue-reality-check/` (skill) + linked calculator | 2-3 hr |

### 1.3 Premium Tools (8)

| ID | Name | Current Surface | Status | Target | Effort |
|---|---|---|---|---|---|
| P1 | B2B Sales Funnel Analyst Pro (SaaS) | Premium GPT | ✓ Ready | `skills/leader/funnel-diagnostic-full/` (Victor has the build) | 0.5-1 hr (port + polish) |
| P2 | B2B Sales Funnel Analyst Pro (Non-SaaS) | Premium GPT | ✓ Ready | `skills/leader/funnel-diagnostic-full/` (variant config) | 0.5 hr (variant) |
| P3 | ROI & Business Case Builder | Premium GPT | ⚠️ Needs port | `skills/leader/roi-business-case-builder/` | 2 hr |
| P4 | Sales Rep Performance Analyst | Premium GPT | ⚠️ Needs port | `skills/manager/rep-performance-analyzer/` (related to but distinct from `extract-seller`) | 2 hr |
| P5 | AI Use Case Advisor | Premium GPT | ⚠️ Needs port | `skills/leader/ai-use-case-advisor/` | 1-2 hr |
| P6 | Sales Forecasting Calculator | Beehiiv app | 📦 Stays external | Linked from related leader skills | None (linked) |
| P7 | Sales Commission Calculator | Beehiiv app | ⛔ Excluded | Utility — not core to OS methodology | None |
| P8 | Your Personal Prompt Engineer | Premium GPT | ⚠️ Needs port | `skills/_shared/prompt-engineer/` | 1 hr |

### 1.4 Beta Access (2)

| ID | Name | Current Surface | Status | Target | Effort |
|---|---|---|---|---|---|
| B1 | Sales Leadership Coach | Gemini Gem | ⚠️ Needs port | `skills/leader/sales-leadership-coach/` (broader scope than current `sales-deep-research-builder`) | 2-3 hr |
| B2 | CS Metrics Analyst | CustomGPT | ⚠️ Needs port | `skills/leader/cs-metrics-analyst/` (extends OS into CS domain) | 2 hr |

### 1.5 Done-For-You Analysis (7)

These do NOT become free skills — they ARE the paid Diagnostic tier in skill form. Document the process internally; ship gated:

| ID | Name | Status | Notes |
|---|---|---|---|
| D1 | Single Deal MEDDIC Diagnostic | 🔒 Paid only | Wraps F4 + Victor's interpretation |
| D2 | Cross-Deal Analysis Report | 🔒 Paid only | Wraps F1 + Victor's interpretation |
| D3 | Pipeline Metrics Assessment | 🔒 Paid only | Paid Funnel Diagnostic deliverable |
| D4 | Rep Performance Diagnostic | 🔒 Paid only | Paid Coaching Diagnostic deliverable |
| D5 | ROI Business Case Report | 🔒 Paid only | Paid ROI engagement |
| D6 | Deep Research Prompt Generator | 🔒 Paid only | Paid `sales-deep-research-builder` engagement |
| D7 | Revenue Reality Check Diagnostic | 🔒 Paid only | Paid revenue model diagnostic |

### 1.6 DIY Build Guides (6)

These ship as **methodology references**, not skills. Educational supplements that explain how the methodology thinks:

| ID | Name | Status | Target |
|---|---|---|---|
| G1 | Build Your Own SPICED Call Analysis Bot | ⚠️ Needs port | `methodology/build-guides/spiced-call-analysis.md` |
| G2 | Build Your Own B2B Sales Call Prep Assistant | ⚠️ Needs port | `methodology/build-guides/sales-call-prep.md` |
| G3 | Build Your Own Cross-Deal Analysis Bot | ⚠️ Needs port | `methodology/build-guides/cross-deal-analysis.md` |
| G4 | Build Your Own Account Research Bot | ⚠️ Needs port | `methodology/build-guides/account-research.md` |
| G5 | Build Your Own Negotiation Strategy Bot | ⚠️ Needs port | `methodology/build-guides/negotiation-strategy.md` |
| G6 | Build Your Own Strategic Sales Story Bot | ⚠️ Needs port | `methodology/build-guides/strategic-sales-story.md` |

**Effort:** 0.5 hr each = 3 hr total (mostly copy-paste from existing Beehiiv articles)

---

## 2. Existing SKILL.md Files (~33 Skills)

Located in `/mnt/skills/user/`. Status reflects whether each is customer-facing for the OS or internal-only.

### 2.1 Customer-facing skills (port to repo)

#### Rep Layer

| Skill | Status | Target | Effort |
|---|---|---|---|
| `extract-meddpicc` | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-meddpicc/` | 0.5 hr |
| `extract-spiced` | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-spiced/` | 0.5 hr |
| `extract-seller` | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-seller/` | 0.5 hr |
| `extract-buyer-journey` | ✓ Ready | `skills/rep/3-discovery-to-roi/extract-buyer-journey/` | 0.5 hr |
| `dana-proposal-writer` | ✓ Ready | `skills/rep/5-propose-to-verbal/proposal-writer/` (rebrand) | 1 hr |
| `transcripts-search` | ✓ Ready | `skills/_shared/transcripts-search/` | 0.5 hr |

#### Manager Layer

| Skill | Status | Target | Effort |
|---|---|---|---|
| `orchestrate-call-analysis` | ✓ Ready | `skills/manager/orchestrate-call-analysis/` | 0.5 hr |
| `scan-call-batch` | ✓ Ready | `skills/manager/scan-call-batch/` | 0.5 hr |
| `analyze-category` | ✓ Ready | `skills/manager/analyze-category/` | 0.5 hr |
| `compare-categories` | ✓ Ready | `skills/manager/compare-categories/` | 0.5 hr |

#### Leader Layer

| Skill | Status | Target | Effort |
|---|---|---|---|
| `ingest-client-context` | ✓ Ready | `skills/leader/ingest-client-context/` | 0.5 hr |
| `research-prospect` | ✓ Ready | `skills/leader/research-prospect/` | 0.5 hr |
| `sales-deep-research-builder` | ✓ Ready | `skills/leader/deep-research-builder/` | 0.5 hr |
| `matching-case-studies` | ✓ Ready | `skills/_shared/matching-case-studies/` | 0.5 hr |
| `matching-offers` | ✓ Ready | `skills/_shared/matching-offers/` | 0.5 hr |

#### Recap / Communication (decide on repo inclusion)

| Skill | Status | Notes |
|---|---|---|
| `recap-emails` | ✓ Ready | Generic — include in `skills/_shared/recap-email-writer/` |
| `client-meeting-recaps` | ✓ Ready | Generic — include in `skills/_shared/meeting-recap-writer/` |
| `dana-recap-emails` | ⛔ Excluded | Dana-branded — internal use only |

#### Orchestration

| Skill | Status | Target | Effort |
|---|---|---|---|
| `dana-skill-orchestrator` | ⚠️ Needs port | `skills/_shared/orchestrator/` (rebrand to `os-orchestrator`) | 1-2 hr |

### 2.2 Internal-only skills (excluded from public OS)

These stay in Dana's private skills directory:

- `victor-voice-filter` — Victor's personal writing style
- `hook-improver` — Victor's content tooling
- `headline-review` — Victor's content tooling
- `newsletter-header` — Dana newsletter operations
- `dana-linkedin-infographics` — Dana brand operations
- `x-article-converter` — Victor's content tooling
- `dana-sequence-builder` — Dana sales operations
- `email-to-task` — Victor's task management
- `improve-skills` — Internal skill QA
- `flag-issue` — Internal skill QA
- `autoresearch` — Internal skill development
- `improve-from-output` — Internal skill development
- `dana-brand-system` — Dana brand operations
- `dana-branding` — Dana brand operations

**Note:** Some of these (the content production ones) might become *paid* assets later for clients who want Dana voice for their team. Not v1.0.

---

## 3. Voice Agents and Intake Forms

| Asset | Surface | Tier | Status | Notes |
|---|---|---|---|---|
| Rachel (sales process interviewer) | ElevenLabs voice agent at `salesmap.danaconsulting.com` | 🔒 Paid only | Operational | Used in Caregility engagement |
| Sage (change management interviewer) | ElevenLabs voice agent | 🔒 Paid only | Operational | Used in Caregility engagement |
| Dana SMB Diagnostic — Complete AI Opportunity Questionnaire | Google Form | Free | ⚠️ Needs port | Drive ID: `1x_fG_9JDrhpB9COUA09NYX1ti23kQhLp_94nZ8Fjxyg`. Becomes part of `setup-sales-os-context` skill. |
| Dana SMB Diagnostic — Outreach Build Intake | Google Form | Free | ⚠️ Needs port | Drive ID: `1Wo7IPTQH3hw6kHqZuN1WyjvcXFHTpjFaE9SsKT2BxLU`. Variant intake. |
| Champion's Code Quick Assessment | TBD interactive surface | Free | 🆕 New build | Free version of A5 |
| Champion's Code Comprehensive Diagnostic | Paid engagement | 🔒 Paid only | Existing | Drive ID: `1-GS2B0xAXhgWbpzGU0gUwSqc17M9CcCV9qSpZGF7vt4` |
| Custom GPT (Discovery Agent) | OpenAI GPT store | Free | 🆕 New build | Mirror of Rachel for free tier; user pays inference |

---

## 4. Methodology Documents

These ship as plain markdown reference files in `methodology/`. The Manager Layer v1.0 batch (April 26, 2026) is complete; remaining files are existing methodology assets that need port to repo.

| Document | Source (Drive ID) | Status | Target |
|---|---|---|---|
| Superintelligent Sales Whitepaper V2 | `1JyX9rqe4bSADEADJSS1-Xp5nz0KWhdq026c9SzaZ5Aw` | ⚠️ Needs port | `methodology/superintelligent-sales-whitepaper.md` |
| Superintelligent Sales Complete Framework book outline | `1M_ejKqP0yqFjysoLhdC0h8XrHOYHGShkZSKT7Ues7cE` | ⚠️ Needs port | Source for multiple methodology files |
| Champion's Code (canonical doc) | `1pZlODzOOAHpx5KIsIavfT3wBlGKlLbVwqQo-Q3bykCk` | ⚠️ Needs port | Source for `champions-code-seven-elements.md` |
| Manager Mastery Bootcamp doc | `1BcLPlEOnEXg9F1ALUjVKiUAaDR3akb3rujQvoZbXg0A` | ⚠️ Needs port | Source for Champion's Code 7 elements (canonical), Vazzana research, Operating Rhythm content |
| Change Management Bot Design | `1Xqo-MFCO4X4XqWJwI1yFsSts2hhEGNle5G39FfPeQ1k` | ⚠️ Needs port | `methodology/change-management-three-phases.md` |
| Change Management Stall Patterns | `1rI7fZfxjNI3cXyoPSJJrfGXNzuVzD93oHb4txGIXsiM` | ⚠️ Needs port | `methodology/adkar-barrier-points.md` |
| Enterprise Change Management Roles | `13sAGt_yAqsFH79pQL1VT228v7tzLeGa8sxi21Bh75As` | ⚠️ Needs port | `methodology/enterprise-change-roles.md` |
| AI in GTM Slides | `/mnt/project/...` (also Drive) | ⚠️ Needs port | Source for `seven-key-moments.md`, customer-comms architecture, three trios |
| **Comprehensive Brief on Sales Management Ideas v2** (canonical, Apr 26 2026) | `/mnt/user-data/outputs/dana-sales-management-brief-v2.md` (~7,020 words); needs Drive home | ⚠️ Needs port | Source for: `core-six-manager-responsibilities.md`, `three-principles-secure-attachment.md`, `champions-code-seven-elements.md` (7 elements), `task-coaching-diagnostic.md`, `five-step-coaching-conversation.md`, `60-min-1on1-structure.md`, `operating-rhythm.md`, `three-types-of-deal-reviews.md` |
| **Deep Dive: Forecasting & Operating Rhythm** (canonical companion) | Pasted in conversation April 2026; needs Drive home | ⚠️ Needs port | Source for: `forecast-triangulation-method.md`, `bi-monthly-forecast-cadence.md`, expanded `operating-rhythm.md` |
| The Rockefeller Rhythm Gamma deck | `https://gamma.app/docs/...mgpwusu49oau5yk` | Source asset | Source for: Three Pillars, Diagnose & Treat, Pipeline Theater vs. Surgery, Reframe — fed into `operating-rhythm.md` (v1.1) |
| Sales Meeting Cadence Framework Drive doc | `1Jbduxtybpo6mbgntnkMHGw0bNpleks15Ik2-AsGh4WQ` | Source asset | Comprehensive Rockefeller cadence; full agenda templates — primary source for `operating-rhythm.md` (v1.1) |
| DAT Manager Workshop — 1:1 Meetings deck | `1ZhDvBEFXtrvsOnLryMEWeFsEcsyeikDh1k8KuXgfkas` | Source asset | Six 1:1 Objectives, Three Principles, Autonomy & Mastery slide |
| DAT Manager Skills Coaching Session #2 transcript | `1JSd-Lc-uY8qPeloukD0TzQV1_NNOg5Sy` | Source asset | Live demonstration of dual-layer Five-Step Coaching |
| Data-Driven Coaching WGLL deck (Mar 2024) | `1D1zVZKQKjTqCQybFjOSzG-zmkyX4KQEeO872b6EKBWQ` | Source asset | TASK framework origin |
| Data-Driven Coaching PDF (May 2025) | `1qS_CX3c5XA2yTaYEbdke654lcgX5bilc` | Source asset | TASK + Leading Indicators 4×4 + 16 metric cards |
| LP TASK Manager Measurement Framework xlsx | LP Exercise file | Source asset | Canonical TASK framework — replaces REKS |
| `methodology/core-six-manager-responsibilities.md` | Brief Section II | 🆕 Build from source | Manager Layer foundation |
| `methodology/three-principles-secure-attachment.md` | Brief Section IV | 🆕 Build from source | Bowlby-derived attachment principles |
| `methodology/champions-code-seven-elements.md` | Manager Mastery Bootcamp Session 1 + Champion's Code canonical doc | ✅ Built (Apr 2026) | 7-element culture framework: Fielding the Right Team / Know Your Numbers / Coaching / Practice / Collaboration / Continuous Learning / Celebration + Leadership Foundation. ~2,230 words |
| `methodology/task-coaching-diagnostic.md` | Brief Section IX (v2) + LP TASK xlsx + Data-Driven Coaching PDF | ✅ Built (Apr 2026) | Target / Activities (Key Sales Moments) / Skill (Practiced + Quality) / Knowledge (3 P's). Replaces REKS as canonical Dana measurement framework. ~1,531 words |
| `methodology/managing-to-metrics-library.md` | Data-Driven Coaching PDF May 2025 | ✅ Built (Apr 2026) | 16 metric cards (Pipeline / Activity / Conversion / Deal Quality) each mapped to TASK level + Champion's Code element. ~2,341 words |
| `methodology/five-step-coaching-conversation.md` | Brief Section III + IX (v2) + DAT Manager Workshop deck + transcript | ✅ Built (Apr 2026) | Dual-layer: MI macro (curiosity → data → diagnose → co-create → commit) + Autonomy & Mastery micro (5 questions inside Steps 3-4) + Reframe variant. ~2,036 words |
| `methodology/60-min-1on1-structure.md` | Brief Section X (v2) + DAT 1:1 Meetings deck | ✅ Built (Apr 2026) | Six Objectives, segmented agenda, monthly rotation + quarterly emphasis overlay, cancellation protocol. ~1,693 words |
| `methodology/forecast-triangulation-method.md` | Forecasting deep dive Section 1.3 | ✅ Built (Apr 2026) | Three-source triangulation: AI confidence × MEDDPICC/SPICED × manager intuition. ~720 words |
| `methodology/bi-monthly-forecast-cadence.md` | Forecasting deep dive Section 1.4 | ✅ Built (Apr 2026) | The contrarian position — why weekly forecast calls fail; BOM 90-min + Mid-Month 45-min; 15-20% accuracy improvement claim. ~1,353 words |
| `methodology/operating-rhythm.md` *(v1.1 — deferred)* | Brief Section VI (v2) + Rockefeller Rhythm Gamma deck + Sales Meeting Cadence Framework Drive doc + Bootcamp Session 5 | 🆕 Build from source | Three Pillars (Priorities / Data / Rhythm) × Four Cadences (Daily / Weekly / Monthly / Quarterly); Diagnose & Treat principle; Pipeline Theater vs. Pipeline Surgery. **Deferred to v1.1 due to scope.** |
| `methodology/three-types-of-deal-reviews.md` | Brief Section VI | 🆕 Build from source | Forecast Calls / Pipeline Scrubs / Deep Dive Reviews |
| Behavioral Bridge content | Book outline (Ch 6) | ⚠️ Needs port | `methodology/behavioral-bridge.md` |
| Sales Factory content | Book outline (Ch 5) | ⚠️ Needs port | `methodology/sales-factory.md` |
| SPICED deep dive | Existing skills documentation | ✓ Ready | `methodology/spiced-deep-dive.md` |
| MEDDPICC deep dive | Existing skills documentation | ✓ Ready | `methodology/meddpicc-deep-dive.md` |
| Meta-principles (definitions before numbers, etc.) | Diagnostic capabilities brief | ⚠️ Needs port | `methodology/meta-principles.md` |

**Manager Layer v1.0 methodology batch — shipped April 26, 2026:** Seven canonical methodology files totaling ~11,900 words: `champions-code-seven-elements`, `task-coaching-diagnostic`, `managing-to-metrics-library`, `five-step-coaching-conversation`, `60-min-1on1-structure`, `forecast-triangulation-method`, `bi-monthly-forecast-cadence`. All in `/mnt/user-data/outputs/`. Ready for repo placement.

**Effort remaining:** ~0.5-1 hr per remaining doc = ~10-14 hr to port the remaining ⚠️ Needs port and 🆕 Build from source files into `methodology/` for v1.0 launch.

**Action item:** Land canonical source documents in Drive — Brief v2 (~7,020 words, currently in `/mnt/user-data/outputs/dana-sales-management-brief-v2.md`) and the Forecasting & Operating Rhythm companion (still in conversation only). Without persistent Drive storage, the methodology builds remain operationally fragile.

---

## 5. Case Studies

These ship in `tools/case-studies/` as standalone markdown files.

| Case Study | Status | Target | Notes |
|---|---|---|---|
| CirrusLED | Existing materials | ⚠️ Needs port | Headline: 12% → 28% win rate. Multiple decks and analyses exist. |
| DAT Solutions | Existing materials | ⚠️ Needs port | Headline: 4.5% conversion vs 15% benchmark = $2.8M opportunity gap |
| CEATI | Existing materials | ⚠️ Needs port | Headline: Time-to-productivity cut from 4-6 months to 8 weeks |
| Element 451 | Existing materials | ⚠️ Needs port | Headline: 83% of won deals had champions vs 17% of lost; 25% of pipeline misqualified |
| CM Labs | Existing materials | ⚠️ Needs port | Hunter (BDR manager) running AI-powered coaching independently — capability transfer proof |
| Caregility (LIVE) | In-engagement | 🔒 Paid only initially | Drive ID: `1Ldp9U56zXvUFynVhWeTVc0kxVUWL8xu4Rt-TangJnH8`. Becomes Article 11 case study when shippable. |
| Abre | Existing materials | ⚠️ Needs port | Mentioned in QuickWin Library cross-references |
| Schwalbe & Partners | Existing materials | Maybe — fractional-relevant | $4,200/month manual cost vs. $20/month tool |
| DMJ Studios (David Jasse) | Existing materials | Maybe — fractional-relevant | $25K avg deal size; outreach automation |
| Financial Services (CS) | Existing materials | ⚠️ Needs port | Engagement plan completion 50% → 85%; at-risk accounts identified 60 days earlier |

**Effort:** ~0.5-1 hr per case study = ~5-10 hr total for case study layer

---

## 6. Article Series Source Files

Substack articles co-located in `articles/`. Drafted as the launch progresses:

| # | Title | Status | Target |
|---|---|---|---|
| 1 | Maturity Model 1.0/2.0/3.0 | 🆕 New build | `articles/01-maturity-model.md` |
| 2 | Customer Communications Architecture | 🆕 New build | `articles/02-customer-comms-architecture.md` |
| 3 | The Seven Moments | 🆕 New build | `articles/03-seven-moments.md` |
| 4 | Three Trios | 🆕 New build | `articles/04-three-trios.md` |
| 5 | Manager's Leverage | 🆕 New build | `articles/05-managers-leverage.md` |
| 6 | The Sales Factory | 🆕 New build | `articles/06-sales-factory.md` |
| 7 | The Behavioral Bridge | 🆕 New build | `articles/07-behavioral-bridge.md` |
| 8 | Champion's Code | 🆕 New build | `articles/08-champions-code.md` |
| 9 | Adoption Layer | 🆕 New build | `articles/09-adoption-layer.md` |
| 10 | Diagnostic Ladder | 🆕 New build | `articles/10-diagnostic-ladder.md` |
| 11 | The OS (Launch Article) | 🆕 New build | `articles/11-the-os.md` |

**Drafting order (per Article Series Roadmap):** 1 → 11 → 9 → 7 → 5 → 3 → fill in 2, 4, 6, 8, 10
**Effort:** ~3-5 hr per article = ~33-55 hr across the series. Distributed over 11 weeks = manageable.

---

## 7. New Skills to Build (No Current Equivalent)

Manager Layer is structured as three concentric concepts — **Core Six (what)** × **8 Core Bots (how)** × **Operating Rhythm (when)** — and phased across v1.0 / v1.1 / v1.2. Every manager skill maps to a Core Bot and/or an Operating Rhythm orchestrator.

### v1.0 launch payload

| Skill | Maps To | Source Material | Layer | Effort |
|---|---|---|---|---|
| `_setup/setup-sales-os-context` | — | Existing questionnaires + Rachel script | Setup | 2-3 hr |
| `_setup/setup-icp-from-website` | — | Conceptual — uses research-prospect pattern | Setup | 2 hr |
| `_setup/import-from-questionnaire` | — | Google Forms export workflow | Setup | 1 hr |
| `manager/one-on-one-prep` | Core Bot #2 (1:1 Prep Bot) | Brief Section X + 60-min 1:1 structure | Manager | 2-3 hr |
| `manager/deal-confidence` | Core Bot #5 (Deal Confidence Engine) — **headline skill** | Forecast deep dive Section 1.5 (5-step inspection protocol) + Brief Section VII | Manager | 3-4 hr |
| `manager/bi-monthly-forecast-review` | Operating Rhythm orchestrator — BOM 90-min | Forecast deep dive Sections 1.3-1.6 | Manager | 2-3 hr |
| `manager/friday-deal-review` | Operating Rhythm orchestrator — Week A format | Forecast deep dive Section 2.5 (Week A) + Brief Section VI | Manager | 2 hr |
| `leader/gtm-diagnostic-lite` | — | Composes existing extract + analyze skills | Leader | 2 hr |
| `leader/gtm-diagnostic-full` | — | Composes existing extract + analyze skills | Leader | 2 hr |

**v1.0 new skill effort:** ~18-23 hr

### v1.1 additions (~6 weeks post-launch, Q3 2026)

| Skill | Maps To | Source Material | Layer | Effort |
|---|---|---|---|---|
| `manager/management-analytics` | Core Bot #1 (Management Analytics Bot) | Brief Section XII (leading + lagging indicators) | Manager | 2-3 hr |
| `manager/ai-roleplay-partner` | Core Bot #6 (AI Role-Play Partner) | Hyperbound integration or self-built | Manager | 3-4 hr |
| `manager/action-tracking` | Core Bot #7 (Action Tracking Bot) | Brief Section XI | Manager | 1-2 hr |
| `manager/development-plan-generator` | Core Bot #8 (Development Plan Generator) | Brief Section IX (TASK) | Manager | 2 hr |
| `manager/friday-skill-workshop` | Operating Rhythm orchestrator — Week B format | Forecast deep dive Section 2.5 (Week B) | Manager | 1-2 hr |
| `adoption/adkar-barrier-diagnostic` | — | Change Management Stall Patterns | Adoption | 2 hr |
| `adoption/sponsor-alignment` | — | Enterprise Change Management Roles | Adoption | 2 hr |
| `adoption/stakeholder-mapping` | — | Change Management Bot Design | Adoption | 2 hr |
| `adoption/champion-network-design` | — | Champion's Code | Adoption | 2 hr |
| `adoption/readiness-assessment` | — | Change Management Bot Design | Adoption | 2 hr |

**v1.1 new skill effort:** ~21-25 hr

### v1.2 additions (~3 months post-launch, Q4 2026)

| Skill | Maps To | Source Material | Layer | Effort |
|---|---|---|---|---|
| `manager/monday-team-meeting-prep` | Operating Rhythm orchestrator | Forecast deep dive Section 2.3 (VIPs opener + agenda + anti-patterns) | Manager | 1-2 hr |
| `manager/mid-month-checkpoint` | Operating Rhythm orchestrator | Forecast deep dive Section 1.4 + 2.6 | Manager | 1-2 hr |
| `manager/qbr-prep` | Operating Rhythm orchestrator | Forecast deep dive Section 2.8 (4-hour QBR structure) | Manager | 2-3 hr |

**v1.2 new skill effort:** ~4-7 hr

**Total new skill effort across all phases:** ~43-55 hr

---

## 8. Repo Infrastructure (Non-Skill Builds)

| Task | Status | Effort |
|---|---|---|
| Reserve `superintelligentsales` GitHub org + create `os` repo | 🆕 New build | 0.5 hr |
| Configure license (MIT) | 🆕 New build | 0.25 hr |
| Initial folder structure | 🆕 New build | 0.5 hr |
| README.md (the launch piece) | 🆕 New build | 4-6 hr |
| CHANGELOG.md scaffolding | 🆕 New build | 0.25 hr |
| CONTRIBUTING.md (likely "no external for v1") | 🆕 New build | 0.5 hr |
| `skills-index.json` manifest schema + auto-gen script | 🆕 New build | 1-2 hr |
| Platform install scripts (claude, cowork, codex) | 🆕 New build | 2 hr |
| Layer bundle YAML configs (rep, manager, leader, full-os) | 🆕 New build | 1-2 hr |
| Installation docs (per surface) | 🆕 New build | 2-3 hr |
| Architecture overview docs | 🆕 New build | 2-3 hr |
| FAQ doc | 🆕 New build | 1-2 hr |
| First Diagnostic walkthrough video | 🆕 New build | 4-6 hr |
| GitHub Actions / release tagging / manifest auto-build | 🆕 New build | 1-2 hr |

**Total infrastructure effort:** ~21-30 hr

---

## 9. Migration Status Summary

### v1.0 launch payload

| Category | Count | Effort |
|---|---|---|
| Existing SKILL.md polish | 17 customer-facing | 10-13 hr |
| GPT-to-skill ports | 9 (F1, F3, A4, A5, A6, P3, P5, P8, B1, B2) | 14-18 hr |
| New skills (Setup + Manager v1.0 + Leader) | 9 | 18-23 hr |
| Methodology files | 22 (8 new manager-specific) | 12-18 hr |
| Build guides (G1-G6) | 6 | 3 hr |
| Case studies | 6-7 (excluding Caregility) | 5-7 hr |
| Repo infrastructure | All (incl. manifest, install scripts, bundles) | 21-30 hr |
| Articles 1, 11 (launch-critical) | 2 | 6-10 hr |
| **v1.0 total** | **~80-110 assets** | **~89-122 hr focused work** |

v1.0 launch is 2-2.5 weeks of focused effort, or 5-6 weeks at part-time pace alongside other Dana operations. Realistic v1.0 target: end of Q2 2026.

### v1.1 additions (~6 weeks post-launch, Q3 2026)

| Category | Count | Effort |
|---|---|---|
| Manager Layer v1.1 skills (Bots #1, #6, #7, #8 + Friday Skill Workshop) | 5 | 10-13 hr |
| Adoption Layer skills | 5 | 10 hr |
| Articles 2-10 | 9 | 27-45 hr |
| Caregility case study | 1 (when shippable) | 1-2 hr |
| Iteration based on launch feedback | TBD | TBD |

**v1.1 total:** ~25 assets, ~48-70 hr

### v1.2 additions (~3 months post-launch, Q4 2026)

| Category | Count | Effort |
|---|---|---|
| Manager Layer v1.2 orchestrators (Monday meeting, Mid-month, QBR) | 3 | 4-7 hr |

**v1.2 total:** 3 assets, ~4-7 hr

### Full rollout total

**All phases combined:** ~108-138 assets, ~141-199 hr work distributed across Q2-Q4 2026.

---

## 10. Asset Counts at Launch

When v1.0 ships, the repo contains:

- **~40 installable skills** organized across Setup (3) / Rep (~17) / Manager v1.0 (9) / Leader (~10) / Shared (1)
- **~22 methodology files** in `/methodology/` (including 8 new manager-specific files)
- **6 build guides** in `/methodology/build-guides/`
- **6-7 case studies** in `/tools/case-studies/`
- **2 launch articles** in `/articles/` (1 and 11)
- **Comprehensive README + docs**
- **Linked external assets:** A1, A2, A3, A6, P6 (calculators stay on Beehiiv/Perplexity)

**Total touchable assets at v1.0:** ~80 files. Larger than gstack's ~30 skills + 8 power tools, with substantially deeper methodology grounding — the Manager Layer alone references 8 dedicated methodology files.

When v1.2 ships, the repo grows to:
- **~48 installable skills** (Manager Layer fully complete with all 8 Core Bots × 6 Operating Rhythm orchestrators)
- **~22 methodology files** (no additions in v1.1/v1.2 — methodology is locked at v1.0)
- **15-16 case studies + articles** in `/articles/` and `/tools/`

---

## 11. What's NOT in the Public Repo

For clarity, here's what stays out:

| Asset | Why |
|---|---|
| Rachel + Sage voice agents | Paid tier only; Dana hosts |
| Done-For-You analyses (D1-D7) | Paid Diagnostic deliverables; require human judgment |
| Connected tier MCP server | Per-customer custom config |
| Internal Dana skills (voice filter, content tools, etc.) | Internal-only |
| Calculators that work better as web apps (A1-A3, A6, P6) | Wrong format for SKILL.md |
| Sales Commission Calculator (P7) | Outside core OS methodology |
| Champion's Code Comprehensive Diagnostic | Paid engagement |
| Caregility case study (until shippable) | Live engagement |

---

## 12. Update Cadence

This document gets updated:
- **At each port completion** — change status from `⚠️ Needs port` to `✓ Ready`
- **At each new skill build completion** — change status from `🆕 New build` to `✓ Ready`
- **At each release (v1.0, v1.1, v1.2, etc.)** — capture what shipped
- **Quarterly** — review what's stayed external; reassess if anything should be ported

---

## 13. Quick Reference: Port Sequence

When porting starts, work in this order to maximize early-launch credibility. Manager Layer follows the three-nested-concerns architecture: **methodology first → bots second → operating rhythm orchestrators third**.

1. **Repo scaffold + README skeleton** (Day 1)
2. **Methodology files** (Days 2-5) — port the Manager Layer methodology cluster first since every manager skill references these:
   - Day 2: `core-six-manager-responsibilities.md`, `three-principles-secure-attachment.md`, `champions-code-seven-elements.md` ✅ (already built)
   - Day 3: `60-min-1on1-structure.md` ✅, `task-coaching-diagnostic.md` ✅, `five-step-coaching-conversation.md` ✅, `managing-to-metrics-library.md` ✅
   - Day 4: `forecast-triangulation-method.md` ✅, `bi-monthly-forecast-cadence.md` ✅, `three-types-of-deal-reviews.md` *(operating-rhythm.md deferred to v1.1)*
   - Day 5: Whitepaper, seven-key-moments, behavioral-bridge, change management cluster
3. **Existing SKILL.md polish** — port `extract-spiced` first as the template; replicate pattern across `extract-meddpicc`, `extract-seller`, `extract-buyer-journey`, orchestration skills (Days 6-9)
4. **Free GPT ports** — F1, F2, F3, F4 — these are the "marketing surface" skills (Days 10-12)
5. **Setup + context skills** — `setup-sales-os-context` + companion Custom GPT (Days 13-15)
6. **Premium GPT ports** — A4, A5, A6, P3, P5, P8, B1, B2 (Days 16-22)
7. **Manager Layer v1.0 new builds** (Days 23-28) — in this order to compose cleanly:
   - Day 23-24: `one-on-one-prep` (Bot #2)
   - Day 25-26: `deal-confidence` (Bot #5 — headline skill)
   - Day 27: `bi-monthly-forecast-review` (orchestrator — composes Bots #3, #4, #5)
   - Day 28: `friday-deal-review` (orchestrator — composes Bots #4, #5)
8. **Leader Layer new builds** — `gtm-diagnostic-lite`, `gtm-diagnostic-full` (Days 29-30)
9. **Build guides + case studies** (Days 31-35)
10. **Articles 1 + 11 + walkthrough video** (Days 36-42)
11. **Launch coordination** (Days 43-49)

That's a 7-week intensive build to launch. At 50% capacity (other Dana operations continuing), 14 weeks = end of Q2 2026.

### Deferred phases

**v1.1 (Q3 2026):** Manager Layer Bots #1, #6, #7, #8 + Friday Skill Workshop orchestrator + Adoption Layer (5 skills) + Articles 2-10 + Caregility case study

**v1.2 (Q4 2026):** Manager Layer Operating Rhythm orchestrators — `monday-team-meeting-prep`, `mid-month-checkpoint`, `qbr-prep`
