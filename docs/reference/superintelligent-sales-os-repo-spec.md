# Superintelligent Sales OS — Repository Architecture & Skill Inventory

*Internal architecture document | Companion to v3 Brief, Manifesto, Article Series Roadmap, and GTM Operations Addendum | April 2026*

---

## Purpose

This document specifies the repository structure for the Superintelligent Sales OS, inventories the existing assets that map into it, and defines the build sequence to get to launch.

The repository is the canonical home of the OS. Everything else (Anthropic Marketplace listing, OpenAI Apps Directory listing, Cowork distribution, Claude Code installs) consumes from this repository.

The thesis is simple: **the methodology already exists in 60+ assets across Beehiiv, ChatGPT, Gemini, Perplexity, and Claude. The launch is a consolidation and porting exercise, not a from-scratch build.**

---

## 1. Executive Summary

### What we're shipping

A public GitHub repository at **`superintelligentsales/os`** (decision locked — matches Tan/Haines/Rezvani brand-forward precedent; the agency name appears in the README byline, not the URL) under **MIT license** (decision locked — maximizes fork flywheel; all three precedent repos use MIT) that contains:

- **The methodology layer** — white paper, seven moments, Champion's Code, Core Six, change management framework, behavioral bridge, SPICED & MEDDPICC deep dives — as plain markdown reference files
- **The skills layer** — installable SKILL.md folders that work in Claude.ai, Claude Code, Cowork, OpenAI Apps, OpenAI Codex, and any other surface that supports the SKILL.md standard
- **The context layer** — templates and questionnaires that produce a per-user `sales-os-context` file every skill reads from
- **The tools layer** — case studies, prompt templates, example transcripts, document templates
- **The articles layer** — the Substack series source files, version-controlled

### What we already have

- **33 existing assets** documented in the Quick Win Offers Library v2.2 (4 free GPTs, 6 free apps, 8 premium tools, 2 beta accesses, 7 done-for-you offers, 6 DIY guides)
- **30+ existing SKILL.md files** in Dana's working directory covering rep-layer extractions, manager-layer batch analysis, leader-layer research, and content production
- **Two voice agents** (Rachel, Sage) running on ElevenLabs for paid-tier discovery and change management
- **Multiple intake forms** (Google Forms) for SMB Diagnostic and Outreach Build
- **Champion's Code Culture Assessments** (free Quick Assessment + paid Comprehensive Diagnostic)
- **Multiple kickoff decks, methodology slides, case studies** (CirrusLED, DAT, CEATI, Element451, Caregility live)

The launch payload is real. The work is consolidation, structuring, and porting.

### What's new to build

- The repo scaffold itself (README, LICENSE, CHANGELOG, structure)
- A `setup-sales-os-context` orchestrator skill that routes users into form / GPT / live human modes
- A free Custom GPT for context-gathering (zero inference cost to Dana — runs on the user's ChatGPT subscription)
- 6-8 specific skills that exist as GPTs/apps but not yet as SKILL.md (see Section 7)
- Supporting documentation (installation guides, architecture overview, FAQ)

---

## 2. Inventory: What Already Exists

### 2.1 From the Quick Win Offers Library v2.2

#### Free GPTs (the priority port targets)

| ID | Name | Current Surface | SKILL Status |
|---|---|---|---|
| F1 | MEDDPICC Cross-Deal Analysis Bot | Beehiiv-linked CustomGPT | ✓ Maps to existing `extract-meddpicc` + `analyze-category` + `compare-categories` |
| F2 | SPICED Sales Call Analyst | Beehiiv-linked CustomGPT | ✓ Maps to existing `extract-spiced` |
| F3 | B2B Sales Funnel Analyst (Lite) | Beehiiv-linked CustomGPT | ⚠️ Needs port — Funnel Diagnostic Lite skill |
| F4 | MEDDPICC Qualifier Pro (Single Deal) | Direct ChatGPT GPT | ✓ Maps to existing `extract-meddpicc` (single-deal mode) |

#### Free Apps (calculator/assessment style)

| ID | Name | Current Surface | SKILL Status |
|---|---|---|---|
| A1 | AI Quota Attainment Calculator | Beehiiv interactive app | Stays as web app + linked from skill |
| A2 | AI Time-Savings Calculator | Beehiiv interactive app | Stays as web app + linked from skill |
| A3 | AI Conversion Rate Calculator | Beehiiv interactive app | Stays as web app + linked from skill |
| A4 | Sales Enablement Maturity Assessment | Beehiiv interactive app | ⚠️ Port to skill — questionnaire-driven, easy build |
| A5 | The Champion's Code (Scorecard) | Beehiiv interactive app | ⚠️ Port to skill — questionnaire-driven, easy build |
| A6 | Revenue Reality Check Calculator | Perplexity Apps | Stays as web app + linked from skill |

#### Premium Tools (Request-Based)

| ID | Name | Current Surface | SKILL Status |
|---|---|---|---|
| P1 | B2B Sales Funnel Analyst Pro (SaaS) | Premium GPT | Maps to Funnel Diagnostic (full) — Victor has it |
| P2 | B2B Sales Funnel Analyst Pro (Non-SaaS) | Premium GPT | Maps to Funnel Diagnostic (full) — variant config |
| P3 | ROI & Business Case Builder | Premium GPT | ⚠️ Port to skill — high-value Leader Layer skill |
| P4 | Sales Rep Performance Analyst | Premium GPT | Partial overlap with `extract-seller` — distinct rep-level skill needed |
| P5 | AI Use Case Advisor | Premium GPT | ⚠️ Port to skill — useful for Maturity Assessment follow-on |
| P6 | Sales Forecasting Calculator | Beehiiv app | Stays as calculator + linked from skill |
| P7 | Sales Commission Calculator | Beehiiv app | Utility — exclude from core OS, optional standalone |
| P8 | Your Personal Prompt Engineer | Premium GPT | ⚠️ Port to skill — meta-tool for OS customization |

#### Beta Access

| ID | Name | Current Surface | SKILL Status |
|---|---|---|---|
| B1 | Sales Leadership Coach | Gemini Gem | Partial overlap with `sales-deep-research-builder` — broader scope |
| B2 | CS Metrics Analyst | CustomGPT | ⚠️ Port to skill — extends OS into Customer Success domain |

#### Done-For-You Analysis

These don't become skills — they're the paid Diagnostic tier in skill form. Each maps to a Diagnostic deliverable Dana produces with judgment in the loop:

| ID | Name | Maps To |
|---|---|---|
| D1 | Single Deal MEDDIC Diagnostic | Paid GTM Diagnostic (single-deal scope) |
| D2 | Cross-Deal Analysis Report | Paid GTM Diagnostic (cross-deal scope) |
| D3 | Pipeline Metrics Assessment | Paid Funnel Diagnostic |
| D4 | Rep Performance Diagnostic | Paid Coaching Diagnostic (subset of GTM) |
| D5 | ROI Business Case Report | Paid ROI engagement |
| D6 | Deep Research Prompt Generator | Paid `sales-deep-research-builder` engagement |
| D7 | Revenue Reality Check Diagnostic | Paid revenue model diagnostic |

#### DIY Build Guides

These are the BYOB documents from the white paper. They become **methodology references** in the repo, not skills. Each one teaches the user how to build the equivalent skill themselves — so they're educational supplements:

| ID | Name | Repo Location |
|---|---|---|
| G1 | Build Your Own SPICED Call Analysis Bot | `methodology/build-guides/spiced-call-analysis.md` |
| G2 | Build Your Own B2B Sales Call Prep Assistant | `methodology/build-guides/sales-call-prep.md` |
| G3 | Build Your Own Cross-Deal Analysis Bot | `methodology/build-guides/cross-deal-analysis.md` |
| G4 | Build Your Own Account Research Bot | `methodology/build-guides/account-research.md` |
| G5 | Build Your Own Negotiation Strategy Bot | `methodology/build-guides/negotiation-strategy.md` |
| G6 | Build Your Own Strategic Sales Story Bot | `methodology/build-guides/strategic-sales-story.md` |

### 2.2 Existing SKILL.md files (in `/mnt/skills/user/`)

#### Rep Layer (single call, single deal)
- `extract-meddpicc` — MEDDPICC scoring with evidence rules
- `extract-spiced` — SPICED scoring
- `extract-seller` — seller execution evaluation
- `extract-buyer-journey` — buyer stage classification
- `dana-proposal-writer` — proposal generation
- `transcripts-search` — find prior calls

#### Manager Layer (batch, coaching, pattern)
- `orchestrate-call-analysis` — batch conductor
- `scan-call-batch` — transcript inventory
- `analyze-category` — pattern analysis within a segment
- `compare-categories` — differential analysis
- `recap-emails` — recap email generation
- `client-meeting-recaps` — comprehensive meeting recaps
- `dana-recap-emails` — Dana-branded recap emails

#### Leader Layer (strategic, GTM, diagnostic)
- `ingest-client-context` — build client profile from materials
- `research-prospect` — external prospect research
- `sales-deep-research-builder` — deep research prompt generation
- `matching-case-studies` — match prospect pain to Dana case studies
- `matching-offers` — match prospect challenges to Quick Win offers

#### Meta / Orchestration
- `dana-skill-orchestrator` — the central router

#### Content Production (Victor's personal toolkit — excluded from customer-facing OS)
- `victor-voice-filter`, `hook-improver`, `headline-review`, `newsletter-header`, `dana-linkedin-infographics`, `x-article-converter`, `dana-sequence-builder`, `email-to-task`

#### Self-improvement (Internal — excluded)
- `improve-skills`, `flag-issue`, `autoresearch`, `improve-from-output`

#### Brand (Internal — excluded)
- `dana-brand-system`, `dana-branding`

### 2.3 Voice agents and intake forms

| Asset | Surface | Tier | Cost Bearer |
|---|---|---|---|
| Rachel (sales process interviewer) | ElevenLabs voice agent at `salesmap.danaconsulting.com` | Paid only | Dana |
| Sage (change management interviewer) | ElevenLabs voice agent | Paid only | Dana |
| Dana SMB Diagnostic Questionnaire | Google Form | Free | None (Google) |
| Dana SMB Diagnostic Outreach Build Intake | Google Form | Free | None (Google) |
| Champion's Code Quick Assessment | TBD interactive surface | Free | TBD |
| Champion's Code Comprehensive Diagnostic | Paid engagement | Paid | Dana |

### 2.4 Inventory summary

- **~33 documented assets** in the QuickWin Library
- **~30 existing SKILL.md files** (~17 customer-facing, the rest internal)
- **2 voice agents** (paid-tier only)
- **2+ intake forms** (free, Google-hosted)
- **6+ documented methodology references** (white paper, Champion's Code, management brief, change management writings, AI in GTM slides, BYOBs)

This is the launch payload. The work is structuring it.

---

## 3. Repository Architecture (Top-Level Structure)

```
superintelligentsales/os/
├── README.md                    # The launch piece — methodology, install, ladder
├── LICENSE                      # MIT (locked)
├── CHANGELOG.md                 # Version history — weekly minor versions post-launch
├── CONTRIBUTING.md              # Contribution policy (likely "no external contributions" for v1)
├── skills-index.json            # Machine-readable manifest — every skill name, description, path
├── .gitignore
│
├── install/                     # Platform-specific install scripts (Rezvani pattern)
│   ├── claude-install.sh        # Claude Code / Claude Desktop install
│   ├── cowork-install.sh        # Claude Cowork install
│   ├── codex-install.sh         # OpenAI Codex install
│   └── README.md                # Which script to use, when
│
├── bundles/                     # Layer bundle configs for one-command installs
│   ├── rep-layer.yaml           # /plugin install rep-layer@superintelligentsales/os
│   ├── manager-layer.yaml
│   ├── leader-layer.yaml
│   └── full-os.yaml             # Installs everything
│
├── methodology/                 # The CORE — every skill references these
│   ├── README.md
│   ├── superintelligent-sales-whitepaper.md
│   ├── seven-key-moments.md
│   ├── champions-code-seven-elements.md    # 7-element culture framework (canonical)
│   ├── core-six-manager-responsibilities.md
│   ├── three-principles-secure-attachment.md
│   ├── task-coaching-diagnostic.md         # Target / Activity / Skill / Knowledge — replaces REKS
│   ├── managing-to-metrics-library.md      # 16 metric cards mapped to TASK + Champion's Code
│   ├── five-step-coaching-conversation.md  # MI macro + Autonomy & Mastery micro (dual layer)
│   ├── 60-min-1on1-structure.md            # Sacred 1:1 with monthly topic rotation
│   ├── forecast-triangulation-method.md    # Bottom-up + stage-weighted + run-rate
│   ├── bi-monthly-forecast-cadence.md      # The contrarian position
│   ├── change-management-three-phases.md
│   ├── adkar-barrier-points.md
│   ├── behavioral-bridge.md
│   ├── spiced-deep-dive.md
│   ├── meddpicc-deep-dive.md
│   ├── operating-rhythm.md                 # v1.1 — Three Pillars × Four Cadences (Rockefeller)
│   ├── three-types-of-deal-reviews.md
│   ├── meta-principles.md       # Definitions before numbers, hypothesis validation, etc.
│   └── build-guides/            # G1-G6 from QuickWin Library
│       ├── spiced-call-analysis.md
│       ├── sales-call-prep.md
│       ├── cross-deal-analysis.md
│       ├── account-research.md
│       ├── negotiation-strategy.md
│       └── strategic-sales-story.md
│
├── context/                     # Per-user context — populated at setup
│   ├── README.md                # How the context layer works
│   ├── sales-os-context.template.md   # The shared context every skill reads from
│   ├── company-profile.template.md
│   ├── methodology-config.template.md  # Which methodology (SPICED vs MEDDPICC vs both)
│   ├── seven-moments-config.template.md  # Stage definitions specific to user
│   ├── icp-and-personas.template.md
│   └── setup-questionnaire.md   # The form questions
│
├── skills/                      # Installable SKILL.md folders
│   │
│   ├── _setup/                  # Activation skills — first thing users run
│   │   ├── setup-sales-os-context/
│   │   ├── setup-icp-from-website/
│   │   └── import-from-questionnaire/
│   │
│   ├── rep/                     # Single call / single deal — organized by 7 moments
│   │   ├── 1-prospect-to-qualified/
│   │   │   └── [research, outreach skills]
│   │   ├── 2-qual-to-discovery/
│   │   │   └── [call-prep, discovery skills]
│   │   ├── 3-discovery-to-roi/
│   │   │   └── [extract-spiced, extract-meddpicc, extract-buyer-journey]
│   │   ├── 4-roi-to-propose/
│   │   │   └── [roi-calculator-skill, value-messaging]
│   │   ├── 5-propose-to-verbal/
│   │   │   └── [dana-proposal-writer]
│   │   ├── 6-verbal-to-contract/
│   │   │   └── [negotiation-prep]
│   │   └── 7-contract-to-win/
│   │       └── [handoff-brief]
│   │
│   ├── manager/                 # Core Six responsibilities × 8 Core Bots × Operating Rhythm
│   │   │
│   │   │   # Bots (the AI infrastructure that frees manager time)
│   │   ├── orchestrate-call-analysis/      # Composes Bots #3+#4 across batch
│   │   ├── analyze-category/               # Pattern surface for Bot #3
│   │   ├── compare-categories/             # Differential surface for Bot #3
│   │   ├── scan-call-batch/                # Inventory utility
│   │   ├── extract-seller/                 # Component of Bot #3 (Call Scoring)
│   │   ├── one-on-one-prep/                # v1.0 — Bot #2 (1:1 Prep Bot)
│   │   ├── deal-confidence/                # v1.0 — Bot #5 (Deal Confidence Engine)
│   │   ├── management-analytics/           # v1.1 — Bot #1 (performance + leading indicators)
│   │   ├── ai-roleplay-partner/            # v1.1 — Bot #6 (Hyperbound integration)
│   │   ├── action-tracking/                # v1.1 — Bot #7 (commitment capture)
│   │   ├── development-plan-generator/     # v1.1 — Bot #8 (TASK-driven plans)
│   │   │
│   │   │   # Operating Rhythm orchestrators (the cadence that protects the time)
│   │   ├── bi-monthly-forecast-review/     # v1.0 — BOM 90-min review (composes Bots #3, #4, #5)
│   │   ├── friday-deal-review/             # v1.0 — Week A (2 deals × 30 min, peer + leader)
│   │   ├── friday-skill-workshop/          # v1.1 — Week B (skill drill, role play)
│   │   ├── monday-team-meeting-prep/       # v1.2 — VIP opener + agenda
│   │   ├── mid-month-checkpoint/           # v1.2 — 45-min adjustment review
│   │   └── qbr-prep/                       # v1.2 — 4-hour quarterly review
│   │
│   ├── leader/                  # Diagnostics + GTM Ops
│   │   ├── gtm-diagnostic-lite/         # NEW — free version
│   │   ├── gtm-diagnostic-full/         # Composes existing extract-* + analyze-* skills
│   │   ├── funnel-diagnostic-lite/      # NEW — free version
│   │   ├── funnel-diagnostic-full/      # Existing (Victor has it)
│   │   ├── champions-code-scorecard/    # From A5
│   │   ├── maturity-assessment/         # From A4
│   │   ├── revenue-reality-check/       # From A6
│   │   ├── ai-use-case-advisor/         # From P5
│   │   ├── roi-business-case-builder/   # From P3
│   │   ├── ingest-client-context/
│   │   ├── research-prospect/
│   │   ├── sales-deep-research-builder/
│   │   └── sales-leadership-coach/      # From B1
│   │
│   ├── adoption/                # Change management layer (the moat)
│   │   ├── adkar-barrier-diagnostic/
│   │   ├── sponsor-alignment/
│   │   ├── stakeholder-mapping/
│   │   ├── champion-network-design/
│   │   └── readiness-assessment/
│   │
│   └── _shared/                 # Cross-cutting utility skills
│       ├── transcripts-search/
│       ├── matching-case-studies/
│       ├── matching-offers/
│       └── recap-email-writer/
│
├── tools/                       # Power tools (gstack-style, non-SKILL.md)
│   ├── case-studies/            # Public case studies
│   │   ├── README.md
│   │   ├── cirrusled.md
│   │   ├── dat-solutions.md
│   │   ├── ceati.md
│   │   ├── element-451.md
│   │   └── caregility.md         # When shippable
│   ├── examples/                # Example transcripts, scored outputs
│   │   ├── transcripts/
│   │   ├── extracted/
│   │   └── diagnostic-reports/
│   ├── templates/               # Document templates (proposals, recaps, MAPs)
│   └── prompts/                 # Reusable prompt fragments
│
├── docs/                        # User documentation
│   ├── README.md
│   ├── installation.md          # One-click for Anthropic / OpenAI / Cowork / Claude Code
│   ├── architecture.md          # Three layers explained
│   ├── seven-moments.md         # Detailed walkthrough
│   ├── ladder.md                # Free → Connected → Implementation → Transformation
│   ├── faq.md
│   └── walkthroughs/            # Step-by-step first-use guides
│       ├── first-diagnostic-lite.md
│       ├── score-your-first-call.md
│       └── set-up-your-context.md
│
└── articles/                    # Substack series source files
    ├── 01-maturity-model.md
    ├── 02-customer-comms-architecture.md
    ├── 03-seven-moments.md
    ├── 04-three-trios.md
    ├── 05-managers-leverage.md
    ├── 06-sales-factory.md
    ├── 07-behavioral-bridge.md
    ├── 08-champions-code.md
    ├── 09-adoption-layer.md
    ├── 10-diagnostic-ladder.md
    └── 11-the-os.md
```

---

## 4. Skill Folder Structure (Anatomy of a Single Skill)

A skill is a folder, not a file. The standard structure:

```
skill-name/
├── SKILL.md              # Required — entry point with frontmatter description + body
├── references/           # Optional — methodology files this skill references
│   ├── framework.md
│   ├── output-format.md
│   ├── examples.md
│   └── edge-cases.md
├── examples/             # Optional — sample inputs and outputs
│   ├── input-example.md
│   └── output-example.md
├── prompts/              # Optional — sub-prompt fragments
│   └── system-prompt.md
└── scripts/              # Optional — runnable code (bash, python)
    └── helper.py
```

### SKILL.md frontmatter rules

```yaml
---
name: skill-name
description: ≤180 characters. Describes when to use this skill. Used by Claude for auto-invocation. No marketing language.
---
```

### Description discipline (from gstack lessons)

- Keep under 180 characters
- Lead with the verb the user wants ("Score a call using SPICED")
- Avoid vague terms ("helps with sales" — fails)
- Use specific terms that match how users describe the task
- The body of SKILL.md carries the actual instructions, not the description

### Reference file conventions

- Every skill that uses methodology cites it in `references/`
- Reference files are NOT duplicated — they're symlinked from `/methodology/` or referenced by relative path
- For Connected tier skills, reference files include user-specific context from `/context/`

### The lean Rep / heavy Leader principle (from gstack)

- **Rep Layer skills**: Lean. Invoked constantly. Token budgets matter. SKILL.md ~500-1500 tokens. References load only what's needed.
- **Manager Layer skills**: Medium. Batch operations justify more context. ~1500-3500 tokens.
- **Leader Layer skills (Diagnostics)**: Heavy. Invoked rarely. Produce executive artifacts. ~3500-10000 tokens. This is where the consulting wisdom lives.

Same logic gstack applied: `/office-hours` is 10,000 tokens because it's invoked rarely; `/qa` runs constantly and stays lean.

---

## 5. The Methodology Layer

The `methodology/` folder is the canonical reference set every skill points to. This is what makes the OS *opinionated* — the methodology is explicit, version-controlled, and read by every skill.

### What lives there

| File | Source | Purpose |
|---|---|---|
| `superintelligent-sales-whitepaper.md` | White Paper V2 | The methodology foundation |
| `seven-key-moments.md` | AI in GTM slides | The seven sales moments with Before/During/After |
| `champions-code-seven-elements.md` | Champion's Code canonical doc + Manager Mastery Bootcamp Session 1 | Seven elements (canonical): Fielding the Right Team, Know Your Numbers, Coaching, Practice, Collaboration, Continuous Learning, Celebration + Leadership Foundation |
| `core-six-manager-responsibilities.md` | Management brief Section II | Qualification, Deal Mgmt, Coaching, Territory, Account, Skill Development |
| `three-principles-secure-attachment.md` | Management brief Section IV | Availability, non-interference, unconditional positive regard |
| `task-coaching-diagnostic.md` | Management brief Section IX (v2) + LP TASK xlsx + Data-Driven Coaching PDF | Target Result / Activities (Key Sales Moments) / Skill (Practiced + Quality) / Knowledge (3 P's) — replaces REKS as the canonical Dana measurement framework |
| `managing-to-metrics-library.md` | Data-Driven Coaching PDF May 2025 | 16 metric cards (Pipeline / Activity / Conversion / Deal Quality categories) each mapped to TASK level + Champion's Code element |
| `five-step-coaching-conversation.md` | Management brief Section III + IX (v2) + DAT Manager Workshop deck | Dual-layer: MI macro (Open / Share data / Diagnose / Co-create / Commit) + Autonomy & Mastery micro (5 questions used inside Steps 3-4) + Reframe variant |
| `60-min-1on1-structure.md` | Management brief Section X (v2) | Sacred 60-min 1:1 with Six Objectives, monthly topic rotation, quarterly emphasis overlay, cancellation protocol |
| `forecast-triangulation-method.md` | Forecasting deep dive Section 1.3 | Bottom-up commit + stage-weighted pipeline + historical run-rate |
| `bi-monthly-forecast-cadence.md` | Forecasting deep dive Section 1.4 | The contrarian position — why weekly forecast calls fail; BOM 90-min + Mid-Month 45-min |
| `change-management-three-phases.md` | Change Management Bot Design | Mobilize / Activate / Sustain |
| `adkar-barrier-points.md` | Change Management Stall Patterns | The five sequential barriers |
| `behavioral-bridge.md` | Book outline + management brief | Lally, Ericsson, Ebbinghaus, Boyer's 30 reps |
| `spiced-deep-dive.md` | Existing SPICED deep dive | The framework definition + scoring |
| `meddpicc-deep-dive.md` | Existing MEDDPICC deep dive | The framework definition + scoring |
| `operating-rhythm.md` *(v1.1)* | Management brief Section VI (v2) + Rockefeller Rhythm Gamma deck + Sales Meeting Cadence Framework Drive doc | Three Pillars (Priorities / Data / Rhythm) × Four Cadences (Daily / Weekly / Monthly / Quarterly); Diagnose & Treat principle; Pipeline Theater vs. Pipeline Surgery — *deferred to v1.1 due to scope* |
| `three-types-of-deal-reviews.md` | Management brief Section VI | Forecast Calls / Pipeline Scrubs / Deep Dive Reviews |
| `meta-principles.md` | Diagnostic capabilities brief | Definitions before numbers, hypothesis validation, confidence levels, prescriptive recs, AI-augmented human-validated |

**Manager Layer v1.0 methodology batch (April 2026):** The seven files marked above with sources from this session (`task-coaching-diagnostic`, `managing-to-metrics-library`, `five-step-coaching-conversation`, `60-min-1on1-structure`, `forecast-triangulation-method`, `bi-monthly-forecast-cadence`, `champions-code-seven-elements`) constitute the v1.0 Manager Layer methodology shipment. Total: ~11,900 words. `operating-rhythm.md` is the planned v1.1 capstone integrating Rockefeller cadence material.

### Decision: full methodology in repo, or summary + link?

**Recommendation:** Full methodology in repo, public.

- Yes, this means competitors can clone it. But the methodology has been public-adjacent for years (white paper on Beehiiv, Champion's Code on Substack, management brief widely shared).
- The moat isn't the *content* — it's Dana's consulting judgment in applying it. The Caregility, CirrusLED, DAT case studies prove that.
- gstack made everything public and the moat was Tan's distribution. Dana's analog: vertical credibility + active consulting practice + integrated diagnostic workflow.

### The build guides (G1-G6)

Located in `methodology/build-guides/`. These are the BYOBs from the white paper — the "build your own bot" instructions. They serve a specific purpose: **they are the educational counterpoint to the installable skills.** A user who wants to understand how the OS thinks (vs. just running it) reads the build guides.

This also helps with the "just prompts" criticism. The build guides demonstrate the difference between a prompt and a skill — skills bundle methodology + structure + judgment + reference materials, not just a prompt.

---

## 6. The Context Layer (Per-User Customization)

The `context/` folder contains templates the user fills out to customize the OS for their organization. The filled-out files become the user's `sales-os-context` substrate that every other skill reads from.

### The activation sequence

1. User installs the OS
2. First skill they invoke: `setup-sales-os-context`
3. Skill asks 5-7 high-leverage questions OR routes user to one of three modes:
   - **Form mode**: paste link to their filled Google Form export
   - **GPT mode**: link to the free Custom GPT for ChatGPT (user pays inference)
   - **Live mode**: book a discovery call with Dana (paid path)
4. Skill writes the populated `sales-os-context.md` and supporting files into the user's `context/` folder
5. All subsequent skills read from this context

### What's in the context

```
context/
├── sales-os-context.md           # Master file — companion to every skill
├── company-profile.md            # Name, products, pricing, market
├── icp-and-personas.md           # ICP, buyer personas, pain points, value props
├── methodology-config.md         # SPICED, MEDDPICC, or both — which is canonical for them
├── seven-moments-config.md       # User's specific stage definitions and conversion rates
├── case-study-references.md      # Their wins to feed into proposals and ROI cases
└── voice-guide.md                # Their writing style (for outbound, proposals, recaps)
```

### Scope of free context

The free tier collects context via:
- Self-completion markdown templates
- Google Form (with paste-export-into-skill workflow)
- Free Custom GPT (voice or text — user pays ChatGPT inference)

The paid tier adds:
- Rachel/Sage voice agents (Dana hosts on ElevenLabs)
- Live human interviews (Laura, Victor)
- Synthesis from interview transcripts

Same context substrate. Different mechanisms.

### Design principle: friction is the feature

The setup-sales-os-context skill is **deliberately not magic.** It does not auto-populate ICP from a website scrape. It does not generate a buyer persona from a LinkedIn URL. It asks hard, specific questions:

- *"Define your ideal customer profile in operational terms — title, company size, industry, trigger event, current alternative."*
- *"What are your top 3 pain points your buyers articulate, and what specific language do they use?"*
- *"Map your buying committee — economic buyer, champion, technical evaluator, end user. Who plays each role at your typical account?"*

When a sales leader hits a question and realizes they can't articulate the answer with precision — that is the moment they need Dana Consulting. The friction qualifies the lead. It surfaces the strategic gaps that paid Diagnostics resolve.

This is a deliberate departure from typical "AI-powered onboarding" UX patterns that minimize friction. **Frictionless setup produces generic output and zero conversion to paid tiers.** Frictionful setup produces context-aware skills AND surfaces qualification signals.

The Haines/Tan precedent: gstack's `/office-hours` is a 10,000-token prompt that pushes back on the user's assumptions and reframes the problem. That friction is what creates the "I needed to hear that" moment that converts to credibility. The Sales OS setup skill plays the same structural role.

---

## 7. Migration Plan: Existing GPTs → Repo Skills

### Direct ports (already SKILL.md)

These exist in `/mnt/skills/user/` and need minor structural updates only — frontmatter, description discipline, reference file refactoring, methodology layer linkage.

- `extract-meddpicc`, `extract-spiced`, `extract-seller`, `extract-buyer-journey`
- `orchestrate-call-analysis`, `analyze-category`, `compare-categories`, `scan-call-batch`
- `ingest-client-context`, `research-prospect`, `sales-deep-research-builder`
- `matching-case-studies`, `matching-offers`
- `dana-proposal-writer`, `transcripts-search`
- `recap-emails`, `client-meeting-recaps`, `dana-recap-emails`
- `dana-skill-orchestrator`

**Estimated work:** 0.5-1 hour per skill = ~10-15 hours total for the existing 17 customer-facing skills.

### Ports from existing GPTs (need new SKILL.md)

These exist as ChatGPT/Gemini GPTs but not yet as SKILL.md. The prompts and instructions exist; the work is restructuring into the SKILL.md format.

| Source | Target Skill | Layer | Effort |
|---|---|---|---|
| F3 — B2B Funnel Analyst Lite | `leader/funnel-diagnostic-lite` | Leader | 1-2 hr |
| A4 — Sales Enablement Maturity Assessment | `leader/maturity-assessment` | Leader | 1 hr |
| A5 — The Champion's Code Scorecard | `leader/champions-code-scorecard` | Leader | 1 hr |
| A6 — Revenue Reality Check | `leader/revenue-reality-check` | Leader | 2-3 hr |
| P3 — ROI & Business Case Builder | `leader/roi-business-case-builder` | Leader | 2 hr |
| P5 — AI Use Case Advisor | `leader/ai-use-case-advisor` | Leader | 1-2 hr |
| P8 — Personal Prompt Engineer | `_shared/prompt-engineer` | Shared | 1 hr |
| B1 — Sales Leadership Coach | `leader/sales-leadership-coach` | Leader | 2-3 hr |
| B2 — CS Metrics Analyst | `leader/cs-metrics-analyst` | Leader | 2 hr |

**Estimated work:** ~14-18 hours total for these 9 ports.

### New skills (no current GPT equivalent)

Manager Layer is now phased across v1.0 / v1.1 / v1.2 to ship the highest-leverage subset first. Each manager skill maps to a Core Bot (the AI infrastructure layer) and/or an Operating Rhythm orchestrator (the cadence layer).

#### v1.0 launch payload

| Target Skill | Layer | Maps To | Source Material | Effort |
|---|---|---|---|---|
| `_setup/setup-sales-os-context` | Setup | — | Existing questionnaires + Rachel script | 2-3 hr |
| `_setup/setup-icp-from-website` | Setup | — | NEW | 2 hr |
| `_setup/import-from-questionnaire` | Setup | — | Google Forms export workflow | 1 hr |
| `manager/one-on-one-prep` | Manager | Core Bot #2 (1:1 Prep Bot) | Brief Section X + 60-min 1:1 structure | 2-3 hr |
| `manager/deal-confidence` | Manager | Core Bot #5 (Deal Confidence Engine) | Forecast deep dive Section 1.5 (5-step inspection) + brief Section VII | 3-4 hr |
| `manager/bi-monthly-forecast-review` | Manager | Operating Rhythm orchestrator | Forecast deep dive Section 1.4 + 1.6 (categories) | 2-3 hr |
| `manager/friday-deal-review` | Manager | Operating Rhythm orchestrator | Brief Section VI + forecast deep dive Section 2.5 | 2 hr |
| `leader/gtm-diagnostic-lite` | Leader | — | Composes existing | 2 hr |
| `leader/gtm-diagnostic-full` | Leader | — | Composes existing | 2 hr |

**v1.0 new skill effort:** ~18-23 hr

#### v1.1 additions (~6 weeks post-launch)

| Target Skill | Layer | Maps To | Source Material | Effort |
|---|---|---|---|---|
| `manager/management-analytics` | Manager | Core Bot #1 (Management Analytics Bot) | Brief Section XII (leading + lagging indicators) | 2-3 hr |
| `manager/ai-roleplay-partner` | Manager | Core Bot #6 (AI Role-Play Partner) | Hyperbound integration or self-built | 3-4 hr |
| `manager/action-tracking` | Manager | Core Bot #7 (Action Tracking Bot) | Brief Section XI | 1-2 hr |
| `manager/development-plan-generator` | Manager | Core Bot #8 (Development Plan Generator) | Brief Section IX (TASK) | 2 hr |
| `manager/friday-skill-workshop` | Manager | Operating Rhythm orchestrator | Forecast deep dive Section 2.5 (Week B) | 1-2 hr |
| `adoption/*` (5 skills) | Adoption | — | Change Management Bot Design | 6-10 hr |

**v1.1 new skill effort:** ~15-23 hr

#### v1.2 additions (~3 months post-launch)

| Target Skill | Layer | Maps To | Source Material | Effort |
|---|---|---|---|---|
| `manager/monday-team-meeting-prep` | Manager | Operating Rhythm orchestrator | Forecast deep dive Section 2.3 (VIPs, agenda) | 1-2 hr |
| `manager/mid-month-checkpoint` | Manager | Operating Rhythm orchestrator | Forecast deep dive Section 1.4 + 2.6 | 1-2 hr |
| `manager/qbr-prep` | Manager | Operating Rhythm orchestrator | Forecast deep dive Section 2.8 | 2-3 hr |

**v1.2 new skill effort:** ~4-7 hr

**Total new skill effort across all phases:** ~37-53 hr

### Total port estimate

**v1.0 launch scope (comprehensive):**
- Existing skill polish (17 customer-facing): 10-13 hours
- GPT-to-skill ports (9 skills): 14-18 hours
- v1.0 new skill builds (Setup ×3 + Manager ×4 + Leader ×2): 18-23 hours
- Methodology files (19 total, including 5 new manager-specific): 12-17 hours
- Build guides (G1-G6): 3 hours
- Case studies (6-7): 5-7 hours
- Repo infrastructure (manifest, install scripts, bundles, docs): 21-30 hours
- Launch-critical articles (1, 11): 6-10 hours
- **v1.0 total: ~89-121 hours of focused work**

**v1.1 additions (~6 weeks post-launch, Q3 2026):**
- Manager Layer v1.1 (5 skills — Bots #1, #6, #7, #8 + Friday Skill Workshop): 9-13 hours
- Adoption Layer (5 skills): 10 hours
- Articles 2-10: 27-45 hours
- Caregility case study: 1-2 hours
- **v1.1 total: ~47-70 hours**

**v1.2 additions (~3 months post-launch, Q4 2026):**
- Manager Layer v1.2 (3 orchestrators — Monday meeting, Mid-month, QBR): 4-7 hours
- **v1.2 total: ~4-7 hours**

**Full rollout (v1.0 → v1.2):** ~140-198 hours total work across Q2-Q4 2026.

v1.0 launch is 2.5-3 weeks of focused effort, or 5-6 weeks at part-time pace alongside other Dana operations. Realistic v1.0 launch target: end of Q2 2026. v1.1 follows in Q3 2026; v1.2 in Q4 2026.

> **Effort scope note:** This total includes content (methodology, articles, case studies) and infrastructure alongside skill builds. If looking only at skill engineering effort: ~42-54 hours for v1.0 (polish + ports + new builds), with the remaining ~47-67 hours covering methodology porting, infrastructure, and content. The asset register tracks the same numbers in its Section 9 with the same scope.

---

## 8. Tier Strategy in the Repo

### Free tier (the entire public repo)

Everything in the public repo is free. No paywall in the methodology, no paywall on skills, no paywall on case studies.

This is the discipline gstack and Haines both followed: free distribution drives the funnel; revenue lives elsewhere (paid Diagnostics, Connected tier, Implementation, Transformation).

### Paid tier (NOT in the repo)

The following live OUTSIDE the public repo and require a paid relationship:

- Rachel and Sage voice agents (paid Diagnostic / Connected tier)
- Connected tier MCP server configuration (custom per customer)
- Live human interview transcripts and analysis (paid engagements only)
- Customized methodology references for specific verticals (paid Implementation)
- Diagnostic Lite reports with interpretation layered on (paid DFY)

The repo links to "what these enable" but doesn't ship them.

### Premium content cross-references

Where appropriate, free skills include CTAs that mention paid options without paywalling the skill itself. Example:

> *Diagnostic Lite produces top-3 findings. The full GTM Diagnostic analyzes 20-50 calls with 4-lens scoring, hypothesis validation, and a sequenced intervention plan. Contact Dana Consulting for paid Diagnostic engagements.*

This is the Haines/Tan model: free skills work fully on their own; paid options are mentioned where the user would benefit from judgment in the loop.

### Success metrics: the Tan/Haines distinction

Garry Tan built gstack as a marketing surface for Y Combinator. Stars, forks, and Hacker News reach are his metrics — they signal credibility to founders considering YC. Tan's day job is YC; gstack is a viral signal.

Dana is playing a different game. The OS is a productized version of consulting IP. Stars and forks are vanity metrics for Dana — developers who star the repo are not the buyer of the $25K Diagnostic. Corey Haines's analog: 15K+ stars on marketing-skills, but only a handful drove engagement; the consulting business converts on a different audience.

**The metrics that matter for Dana:**

| Metric | Why |
|---|---|
| Diagnostic Lite completions | Direct qualification signal — these are managers/leaders, not just curious developers |
| Booked discovery calls | Bottom-of-funnel signal that converts to paid Diagnostic |
| Paid Beehiiv subscribers | Recurring revenue indicator (and signal that paid offer works) |
| Substack discovery → Beehiiv list growth | Top-of-funnel audience expansion |
| Fractional setup engagements | New tier — fractional operators paying $5-10K for setup |

**The metrics that don't matter (vanity):**
- Total GitHub stars
- Repo visits
- Hacker News rank
- General "skill installs" (without context conversion)

This distinction must be explicit in launch communications. **Don't celebrate stars. Celebrate Diagnostics.** The article series, LinkedIn posts, and Substack content should optimize for the buyer's discovery path, NOT for developer-trending surfaces (Hacker News, dev Twitter, Product Hunt's developer crowd).

If the OS trends on Hacker News, that's a signal to *broaden distribution*, not a success metric in itself. The buyer isn't there.

---

## 9. Distribution & Naming

### Repo location

- **Locked:** `github.com/superintelligentsales/os`
- Rationale: Brand-forward URL matches Tan/Haines/Rezvani precedent. More searchable for sales leaders Googling "AI sales OS" than agency-named alternative. Dana attribution lives in README byline ("Built by Dana Consulting") rather than the URL.
- The `superintelligentsales` org will own a small portfolio: `os` (the repo), potentially `articles` (Substack source if we split later), and `docs` (companion site source if we split later).

### License

- **Locked:** MIT
- Rationale: All three precedent repos (gstack, marketing-skills, claude-skills) use MIT. The fork flywheel — community variations, vertical-specific adaptations, fractional-leader customizations — depends on MIT's permissiveness. Apache 2.0's patent grant is unnecessary for a methodology repo where the IP has been public-adjacent for years.

### Skills manifest (`skills-index.json`)

Required for Codex marketplace discoverability and recommended by Rezvani's pattern. Machine-readable index of every skill at the repo root.

Schema:

```json
{
  "name": "superintelligent-sales-os",
  "version": "1.0.0",
  "skills": [
    {
      "name": "extract-spiced",
      "path": "skills/rep/3-discovery-to-roi/extract-spiced",
      "layer": "rep",
      "description": "Score a sales call transcript on SPICED (Situation, Pain, Impact, Critical Event, Decision) with evidence quotes.",
      "platforms": ["claude-code", "cowork", "codex", "claude-ai"]
    }
  ]
}
```

The manifest is auto-generated from skill folder frontmatter via a build script in `scripts/build-manifest.py`. Regenerated on every release.

### Platform-specific install scripts

In `install/`, three scripts handle path differences per agent:

- `claude-install.sh` — installs to `~/.claude/skills/`
- `cowork-install.sh` — installs to Claude Cowork's skills directory
- `codex-install.sh` — installs to `~/.codex/skills/`

Each script accepts a layer flag for selective install:

```bash
./claude-install.sh --layer=rep        # Install Rep Layer only
./claude-install.sh --layer=all        # Install everything
./claude-install.sh --layer=manager,leader  # Install multiple layers
```

### Layer bundle install pattern

For Cowork's `/plugin install` command, layer bundles are configured in `bundles/`:

```yaml
# bundles/rep-layer.yaml
name: rep-layer
description: All Rep Layer skills — the seven moments, scored.
includes:
  - skills/rep/**
  - skills/_shared/transcripts-search
  - methodology/seven-key-moments.md
  - methodology/spiced-deep-dive.md
  - methodology/meddpicc-deep-dive.md
```

Users on Cowork run `/plugin install rep-layer@superintelligentsales/os` and the entire Rep Layer installs at once. Same for `manager-layer`, `leader-layer`, and `full-os`.

### Cross-platform compatibility

The repo ships skills compatible with:
- Anthropic Claude.ai (web, desktop)
- Anthropic Cowork
- Anthropic Claude Code
- OpenAI Apps Directory
- OpenAI ChatGPT Agents
- OpenAI Codex
- Any future surface adopting the SKILL.md standard

The README explicitly names this. The line: *"Write the methodology once. Run it wherever your team works."*

### Naming convention

- Skill folder names: `kebab-case`, lowercase, descriptive
- Reference files: `kebab-case.md`
- No version numbers in skill folder names — version control happens at repo level via tags

### Versioning

- Repo uses semantic versioning: `v1.0.0` at launch, `v1.1.0` for skill additions, `v1.0.1` for bugfixes
- CHANGELOG.md tracks every release
- Weekly minor version cadence post-launch (per Haines pattern)
- Each release accompanied by a LinkedIn post (per Haines pattern — release-as-content-trigger)

---

## 10. Build Sequence (What to Port First)

### Phase 1 — Foundation (Week 1-2)

1. Set up repo scaffold (README, LICENSE, CHANGELOG, structure)
2. Port methodology files into `methodology/` (mostly copy-paste from existing docs)
3. Build `setup-sales-os-context` orchestrator skill + companion Custom GPT
4. Port the 4 free GPTs (F1-F4) — these are the lowest-friction wins
5. Write installation docs

### Phase 2 — Rep Layer (Week 3)

1. Port existing rep-layer skills with frontmatter discipline (`extract-*`)
2. Build the 7-moment folder structure
3. Add example transcripts to `tools/examples/transcripts/`

### Phase 3 — Manager Layer v1.0 (Week 4)

The Manager Layer is the highest-leverage layer in the OS. Build it as three nested concerns: **WHAT** (Core Six responsibilities — where managers should spend time), **HOW** (8 Core Bots — AI infrastructure that frees the time), **WHEN** (Operating Rhythm — cadence orchestrators that protect the time).

v1.0 ships the highest-leverage subset:

1. Port existing manager-layer skills (`orchestrate-call-analysis`, `analyze-category`, `compare-categories`, `scan-call-batch`, `extract-seller`)
2. Build Core Bot #2 — `one-on-one-prep` (anchored on 60-min 1:1 structure with monthly topic rotation)
3. Build Core Bot #5 — `deal-confidence` (anchored on the 5-step deal inspection protocol; this is the headline skill for the 15-20% forecast accuracy promise)
4. Build Operating Rhythm orchestrator — `bi-monthly-forecast-review` (BOM 90-min, composes Bots #3 + #4 + #5)
5. Build Operating Rhythm orchestrator — `friday-deal-review` (Week A format, 2 deals × 30 min each)

v1.1 (deferred to Q3 2026):
- `management-analytics` (Bot #1)
- `ai-roleplay-partner` (Bot #6)
- `action-tracking` (Bot #7)
- `development-plan-generator` (Bot #8)
- `friday-skill-workshop` (Operating Rhythm orchestrator)

v1.2 (deferred to Q4 2026):
- `monday-team-meeting-prep`
- `mid-month-checkpoint`
- `qbr-prep`

### Phase 4 — Leader Layer (Week 5)

1. Port from QuickWin Library: A4, A5, A6, P3, P5, P8, B1, B2
2. Build GTM Diagnostic Lite + Full (composing existing skills)
3. Reference the Funnel Diagnostic (Victor's existing build)

### Phase 5 — Adoption Layer (Week 6)

1. Port the change management methodology files
2. Build the 5 adoption skills (ADKAR, sponsor, stakeholder, champion, readiness)
3. Document Sage as the paid-tier escalation path

### Phase 6 — Polish + Launch (Week 7)

1. Walkthrough videos (the practitioner-facing UX moat)
2. Final README polish
3. Submit to Anthropic Marketplace + OpenAI Apps Directory
4. Coordinate with Article 11 publication
5. Launch tweet / LinkedIn post / Substack announcement

**Realistic launch target:** end of Q2 2026 (mid-to-late June). This aligns with the article series launch schedule.

---

## 11. Decisions (Locked)

All foundational decisions are now resolved. Phase 1 can begin.

| # | Decision | Resolution | Rationale |
|---|---|---|---|
| 1 | Repo location | `superintelligentsales/os` | Brand-forward URL; matches all three precedents (gstack, marketing-skills, claude-skills); more searchable for sales leader buyers |
| 2 | License | MIT | All precedents use MIT; the fork flywheel depends on permissiveness; patent grant unnecessary for methodology that's been public-adjacent |
| 3 | Methodology scope | Full methodology in repo, public | Methodology has been public-adjacent for years; moat is consulting judgment, not content lockup |
| 4 | Calculator strategy | Stay external, link from skills | A1, A2, A3, A6, P6 stay on Beehiiv/Perplexity; SKILL.md format wrong for interactive calculators |
| 5 | DIY guides location | `methodology/build-guides/` as supplements | Serves the "skills aren't just prompts" preemption — educates how methodology thinks |
| 6 | Adoption Layer at v1.0 | Defer to v1.1 | Methodology files ship at v1.0; the 5 skills (ADKAR, sponsor, stakeholder, champion, readiness) defer to v1.1 (~6 weeks post-launch) |
| 7 | Articles location | Co-located in `articles/` folder | One source of truth; reduces sync overhead; repo doubles as canonical archive |
| 8 | Anthropic Verified status | Apply at v1.1, not v1.0 | Verification needs traction signal; launch with article series momentum, then apply |
| 9 | Founding Member migration | Draft and send 2 weeks before public launch | Existing newsletter subscribers and beta users become Day-1 stars/forks — critical to launch spike |
| 10 | Name conflict check | Verify before Phase 1 | 30-min task: GitHub org availability + USPTO trademark search + domain confirmation |

### Pending verification items (not blocking, but should resolve early)

- Confirm `github.com/superintelligentsales` org is available (or claim it now)
- USPTO trademark search on "Superintelligent Sales OS" and "Superintelligent Sales"
- Domain `superintelligentsales.com` already owned (newsletter); confirm DNS structure works for both newsletter and repo companion site

---

## 12. The README at v1.0 (Outline)

The README is the single most important file in the repo — it does the work of the launch tweet. Outline:

```
# Superintelligent Sales OS

> An opinionated AI sales operating system. Virtual rep, virtual manager, 
> virtual leader. Runs wherever skills run.

[Install buttons: Anthropic Marketplace | OpenAI Apps | Claude Code]

## What this is

[2-3 paragraph overview — methodology grounded, three layers, free + paid ladder]

## The Methodology

[Brief — Maturity Model 1.0/2.0/3.0, link to white paper]

## What's Inside

- 30+ installable skills covering rep, manager, and leader workflows
- The full methodology — white paper, seven moments, Champion's Code, Core Six
- Diagnostic skills that surface gaps in your team's execution
- Build guides for understanding how the methodology works

## How It Works

[The 3 layers, with example skills for each]

## Get Started in 10 Minutes

[Step-by-step: install, run setup-sales-os-context, run your first Diagnostic Lite]

## The Ladder

[Free OS → Paid Diagnostic → Connected → Implementation → Transformation]

## Proof Points

[CirrusLED, DAT, CEATI, Element 451, Caregility]

## About Dana Consulting

[Brief — Victor's background, methodology lineage, contact]

## License

[License text]

## Contributing

[Contribution policy — likely invite-only for v1]
```

---

## 13. Decision Log Update

Add to GTM Operations Addendum Section 14:

| Date | Decision | Rationale | Owner |
|---|---|---|---|
| April 2026 | Repo is the canonical home of the OS | Marketplaces are distribution surfaces; repo is source of truth | Victor |
| April 2026 | Full methodology ships in public repo | Methodology has been public-adjacent for years; moat is consulting judgment, not content lockup | Victor |
| April 2026 | Free tier = entire public repo, no paywalls inside | Haines/Tan/Vincent precedent; paywalls kill distribution | Victor |
| April 2026 | Calculator-style apps stay external; skills link to them | Building calculator UX into SKILL.md adds friction without value | Victor |
| April 2026 | DIY build guides live in `methodology/build-guides/` as educational supplements | They serve the "skills aren't just prompts" criticism preemption | Victor |
| April 2026 | Skill folders ship with `references/`, `examples/`, optional `prompts/` and `scripts/` | gstack precedent; SKILL.md alone is not the standard | Victor |
| April 2026 | Lean Rep Layer / heavy Leader Layer skill design | gstack precedent; Rep skills invoked constantly, Leader skills rarely | Victor |
| April 2026 | Manager Layer = Core Six × 8 Core Bots × Operating Rhythm | The canonical Sales Management Brief defines three nested concerns: WHAT (Core Six responsibilities), HOW (8 Core Bots = AI infrastructure), WHEN (Operating Rhythm = cadence orchestrators). Every manager skill maps to all three. | Victor |
| April 2026 | Manager Layer phases across v1.0 / v1.1 / v1.2 | Ship highest-leverage subset first (1:1 prep, deal confidence, BOM forecast, Friday deal review). Defer analytics, roleplay, action tracking, dev plans to v1.1. Defer Monday/QBR/checkpoint orchestrators to v1.2. | Victor |
| April 2026 | `deal-confidence` is the headline Manager Layer skill | The 15-20% forecast accuracy promise (Brief Section XII) is delivered through Bot #5. It deserves disproportionate design attention — anchored on the 5-step inspection protocol from the forecasting deep dive. | Victor |
| _(Pending)_ | Repo org choice (`superintelligentsales/os` vs. `dana-consulting/...`) | Brand-forward vs. attribution-forward | Victor |
| _(Pending)_ | License (MIT vs Apache 2.0) | Permissiveness vs. patent grant | Victor |

---

## Appendix: Quick Reference

### The four documents

| Document | Audience | Updates |
|---|---|---|
| **v3 Brief** | Internal/partner-facing | Annually |
| **Manifesto** | Outward-facing | When methodology evolves |
| **Article Series Roadmap** | Internal/partner-facing | Per-launch |
| **GTM Operations Addendum** | Internal/partner-facing | Quarterly |
| **Repo Architecture Spec** (this doc) | Internal — build team | Per-release |

### Key counts at v1.0 launch (target)

- ~40 skills total (17 existing + ~25 ports/builds)
- ~13 methodology files
- ~6 build guides
- ~5 case studies
- 11 article source files
- 4 walkthrough docs
- 1 README that does the launch work

### The single most important sentence in this document

> *The methodology already exists in 60+ assets. The launch is a consolidation and porting exercise, not a from-scratch build.*

That's why the timeline is realistic. That's why the launch can compound. That's why the OS is shipping in 2026, not 2028.
