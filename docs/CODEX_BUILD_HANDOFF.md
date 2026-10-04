# Codex Build Handoff v2 — Superintelligent Sales OS Phase 1

> Self-contained brief for OpenAI Codex to build the Phase 1 repository **collaboratively with Victor**. No prior session context required. Read this end-to-end before writing any code or building any files.

---

## 0. Critical: This is a collaborative build, not autonomous

**Codex's job is to collaborate with Victor on building each skill, one at a time.**

Victor will provide, per skill or per suite:
- Existing GPT exports (instructions + knowledge base files + examples + configuration)
- Existing Claude skills as references (you have mirrored read access)
- Methodology source material from Dana Consulting's IP library
- Specific instructions on how each skill should behave, what it should output, what edge cases matter
- Sample inputs and expected outputs from real engagements
- Voice, tone, and customization guidance

**Codex synthesizes those inputs into the skill** following the architecture in this brief, then opens a PR for Victor's review.

**This is not "Codex builds autonomously from a spec."** This is **"Codex builds with Victor, one skill at a time, with Victor providing the deep IP per skill."**

Implications:
- Don't try to invent skill content from thin context. If a skill needs methodology depth Codex doesn't have, **stop and ask Victor for the source material**.
- Don't batch-build skills without Victor's input. **One skill at a time, with explicit handoff at each step.**
- Don't assume the architecture answers content questions. Architecture says "BDR Suite has a `qualification-call-prep` sub-skill." Content for that sub-skill comes from Victor.
- Use existing Claude skills (research-prospect, dana-recap-emails, extract-spiced, etc.) as the depth bar — match their substance, not the simplified PTCF+E template.

---

## 1. Quick start — paste this prompt into Codex

When starting the Codex session, paste this exact prompt:

```
You are collaborating with Victor on building Phase 1 of the
Superintelligent Sales OS — a public, MIT-licensed GitHub repo
(superintelligentsales/superintelligent-sales-os) containing methodology
files and installable Claude skills (SKILL.md format) for B2B revenue
organizations.

Your role is collaborator, not autonomous builder. Victor provides the
deep IP per skill; you synthesize it into well-architected skills.

Connect to the repo: github.com/superintelligentsales/superintelligent-sales-os

Before writing any code:

1. Read /docs/CODEX_BUILD_HANDOFF.md end to end. Pay special attention
   to §0 (collaborative model) and §5 (Suite architecture).

2. Read the reference docs in /docs/reference/:
   - superintelligent-sales-os-overview.md (architectural anchor)
   - dana-sales-management-brief-v2.md (canonical methodology)
   - skill-list-v2-rep-layer.md (Rep Layer Suite architecture)
   - skill-list-v2-manager-layer.md (Manager Layer Suite architecture)
   - superintelligent-sales-os-repo-spec.md (repo architecture)

3. Read the 7 manager methodology files in /docs/reference/methodology/

4. CRITICAL: Reference Victor's existing Claude skills as the gold-standard
   format. Mirrored read access available. Specifically study:
   - research-prospect (depth, structured framework approach)
   - dana-recap-emails (template-driven output)
   - victor-voice-filter (style enforcement patterns)
   - extract-spiced (analysis framework with scoring)
   - extract-meddpicc (multi-element scoring with evidence)
   These existing skills define the quality bar.

5. Confirm you understand:
   - You are collaborating with Victor, not autonomous building
   - Phase 1 scope: Rep + Manager Layer Suites only
   - 11 Suites + 1 Customization Onboarding Skill = 55 sub-skills total
   - Pattern B folder structure: each skill is /skills/{layer}/{suite}/{sub-skill}/
   - Customization-first architecture: every skill reads from /context/
   - Day-agnostic naming for cadence skills

6. Once confirmed, ask Victor which Suite to start with. Do not start
   building until Victor confirms which suite is first and provides
   the source materials for the first sub-skill within it.

Do not build anything tagged Phase 2 (Leader, RevOps), Phase 3 (CS),
or Phase 4 (Marketing). If unsure whether something is in scope, ask
Victor before building.
```

---

## 2. Mission

Build the Phase 1 release of the Superintelligent Sales OS — a public, MIT-licensed GitHub repository containing methodology files plus installable Claude skills (SKILL.md format) organized into Suites.

**Repo:** `github.com/superintelligentsales/superintelligent-sales-os`

**Phase 1 scope:** Rep Layer (7 Suites + 1 Onboarding) + Manager Layer (4 Suites). Pre-sale through Close & Handoff to Customer Success. Excludes post-sale execution (Phase 3) and Leader/RevOps (Phase 2).

**Target deliverables:**
- 11 Suites (7 Rep, 4 Manager) + 1 Customization Onboarding Skill
- 55 sub-skills total
- ~14 methodology files (7 already written; 7 to write)
- Bundle YAML files for layer-specific or full-OS install
- README explaining the OS, install instructions, philosophy
- LICENSE (MIT) — already in place

---

## 3. Architectural principles (non-negotiable)

Three principles govern every Suite and skill:

### Suites, not standalone skills

Each Key Moment in the sales process is a **Suite** containing related sub-skills that work together. A Suite follows the **mirror pattern**:

- **Before the moment:** research, prep, prior-context ingestion
- **During the moment:** script, talk track, real-time support
- **After the moment:** scoring, recap, handoff

Each Suite is a folder. Sub-skills are folders within. See §5 for the architecture.

### Customization-first

**Every skill in the OS requires customization to be useful.** The skill provides framework + methodology + structure. The user provides company info, ICP, methodology choices, sales process stages, voice, etc.

This lives in:
- `/context/user-context.yaml` — populated via the Customization Onboarding Skill
- Explicit "Customize this" sections in every SKILL.md
- A README that emphasizes customization as the primary onboarding step

**Skills that don't read from `/context/` are broken.** This is a hard requirement.

### GPTs are source material, not endpoints

Existing ChatGPT GPTs are **harvested** for skill content. Per GPT, Victor provides:
- Instructions (system prompt)
- Knowledge base files (PDFs, MDs, examples)
- Conversation starters
- Configuration (web search settings, capabilities)

Codex synthesizes all of this into the skill, expanding/restructuring as needed to fit the Suite architecture. **Don't just port instructions — port the full IP bundle.**

---

## 4. Workflow — GitHub-native via PRs, one skill at a time

Codex commits to the repo via branches and PRs. **One skill = one PR.** Not one suite per PR. Not one phase per PR. **One skill per PR**, because each skill is a collaborative back-and-forth with Victor.

The flow per skill:

1. Victor confirms which sub-skill within which Suite to build
2. Victor provides source materials (GPT exports, methodology, examples, instructions)
3. Codex creates a working branch (e.g., `bdr-suite/prospect-research`)
4. Codex synthesizes the source materials into a SKILL.md following the architecture in §5-7
5. Codex writes a test-fixture.md with test scenario + expected output
6. Codex commits + pushes + opens a PR titled "BDR Suite: prospect-research"
7. Victor reviews the PR on GitHub, merges or requests changes
8. After merge, Codex moves to the next sub-skill (with Victor's confirmation)

**Branch naming convention:** `{suite-name}/{sub-skill-name}` (e.g., `bdr-suite/prospect-research`, `coaching-suite/task-diagnostic`).

**Stop-and-wait between skills.** After each PR is opened, Codex stops and waits for Victor's review/merge AND confirmation of the next sub-skill before continuing.

### Suite-level setup PRs

Three exceptions where Codex opens a Suite-level (not skill-level) PR:

1. **Phase 0 — Repo initialization:** Set up folder structure, copy methodology files, scaffold suite folders. One PR.
2. **Suite scaffold PRs:** When starting a new Suite, Codex first opens a small PR creating the Suite folder structure with placeholder PACKAGE.md and customization-template.md. Then individual skill PRs follow.
3. **Phase finalization PRs:** README finalization, bundle YAML files, repo testing. One PR each.

---

## 5. Suite architecture

### Repository structure

```
superintelligent-sales-os/
├── README.md                                # FINALIZE in Phase 1 close
├── LICENSE                                  # MIT (already in place)
├── docs/                                    # Reference docs (committed by Victor pre-build)
│   ├── CODEX_BUILD_HANDOFF.md              # This file
│   └── reference/
├── methodology/                             # Flat files
│   └── ... (7 existing + 7 new = 14 files)
├── skills/
│   ├── rep/
│   │   ├── _onboarding/                    # Customization Onboarding Skill
│   │   │   ├── SKILL.md
│   │   │   └── test-fixture.md
│   │   ├── bdr-suite/
│   │   │   ├── PACKAGE.md                  # Suite overview + customization guide
│   │   │   ├── customization-template.md   # Suite-specific user inputs
│   │   │   ├── methodology-refs.md
│   │   │   └── sub-skills/
│   │   │       ├── prospect-research/
│   │   │       │   ├── SKILL.md
│   │   │       │   ├── test-fixture.md
│   │   │       │   └── references/
│   │   │       ├── list-builder/
│   │   │       └── ... (6 sub-skills total in BDR Suite)
│   │   ├── discovery-suite/
│   │   ├── demo-suite/
│   │   ├── solutioning-suite/
│   │   ├── business-case-suite/
│   │   ├── proposal-negotiation-suite/
│   │   └── close-handoff-suite/
│   └── manager/
│       ├── operating-rhythm-suite/
│       ├── coaching-suite/
│       ├── forecast-suite/
│       └── call-pattern-suite/
├── context/                                 # User customization templates
│   ├── README.md
│   └── user-context.yaml.template
└── bundles/
    ├── rep-layer.yaml
    ├── manager-layer.yaml
    └── full-os.yaml
```

### Phase 1 Suite catalog

#### Rep Layer — 7 Suites + 1 Onboarding (34 sub-skills)

**Source of truth for sub-skill list:** `/docs/reference/skill-list-v2-rep-layer.md`

| Suite | Sub-skills | Customization weight | GPT source(s) |
|---|---|---|---|
| `_onboarding` (Customization Onboarding Skill) | 1 | N/A — provides customization | Net-new |
| `bdr-suite` | 6 | Medium | research-prospect (existing skill) |
| `discovery-suite` | 6 | Medium-high | Sage Discovery, SPICED Sales Call Analyst, dana-recap-emails (existing), matching-case-studies (existing) |
| `demo-suite` | 5 | High | Net-new |
| `solutioning-suite` | 5 | Very high | Net-new |
| `business-case-suite` | 4 | High | ROI & Business Case Builder GPT |
| `proposal-negotiation-suite` | 4 | Very high | dana-proposal-writer (existing, extends) |
| `close-handoff-suite` | 3 | Medium-high | Net-new |

#### Manager Layer — 4 Suites (21 sub-skills)

**Source of truth for sub-skill list:** `/docs/reference/skill-list-v2-manager-layer.md`

| Suite | Sub-skills | Customization weight | GPT source(s) |
|---|---|---|---|
| `operating-rhythm-suite` | 5 | Medium | None (orchestrates other suites) |
| `coaching-suite` | 6 | High | Dana Sales Leadership Coach GPT |
| `forecast-suite` | 5 | Medium-high | MEDDPICC Qualifier Pro GPT |
| `call-pattern-suite` | 5 | Medium-high | MEDDPICC Cross-Deal Analyst GPT |

**Phase 1 total: 11 Suites + 1 Onboarding = 55 sub-skills.**

### Day-agnostic naming

Cadence-related skills use frequency, not days. ✅ `weekly-1on1-prep`, `biweekly-deal-review`, `bi-monthly-forecast-review`. ❌ `monday-team-meeting`, `friday-deal-review`. Days vary per company.

---

## 6. PACKAGE.md — Suite-level documentation

Every Suite has a top-level PACKAGE.md that explains:

```markdown
# {Suite Name}

> One-line description of what this suite does.

## Mirror Pattern

**Before → During → After** mapping for this Suite.

## Sub-skills in this Suite

[List with one-line descriptions and links to each sub-skill folder]

## Customization Required

What the user must provide in /context/ for this suite to work well.

## Use Cases Supported

Specific scenarios this suite handles (e.g., champion enablement,
multi-threaded deal expansion).

## Methodology Files Referenced

Links to /methodology/ files this suite draws from.

## Composition

Other suites or skills this suite composes with (especially relevant
for Operating Rhythm Suite which orchestrates other suites).

## Related Skills to Suggest

For each sub-skill in this Suite, the one next skill Claude may suggest
after it runs, and the trigger phrase the user would say to run it.
Draw candidates from this Suite and from other Suites in the catalog.

| After this sub-skill runs | Suggest | Trigger phrase |
|---|---|---|
| {sub-skill} | {next skill, within or across Suites} | "{phrase}" |

Suggestion rules (apply in every sub-skill's output):
- Suggest only when there is a genuine, specific reason from this run.
- One suggestion per run. Never a menu.
- Saying nothing is acceptable.
- Never suggest a skill already run earlier in the same conversation.

## Operating Principles

Three to five short principles that govern every output in this Suite.
Each sub-skill applies these when it writes its output. Excerpt them from
dana-sales-management-brief-v2.md and the Foundational Principles in
superintelligent-sales-os-overview.md; do not invent new ones. Choose the
principles that fit this Suite. Candidates:

- **Beneath metrics are behaviors.** Coach the activities and skills that produce the number, never the number itself.
- **Diagnose in groups, treat in 1:1s.** Never solve one rep's problem in a team setting.
- **Evidence over inference.** Every claim cites a quote, timestamp, or record. If the evidence is missing, drop the section rather than pad it.
- **The manager is the highest-leverage role and the most under-supported.** Outputs should give managers time back, not add work.
- **Customization is the moat, not the methodology.** Apply the user's /context/ values; never fall back to generic advice when context exists.
```

The Operating Principles section lives at the Suite level only. Do not repeat it inside individual SKILL.md files.

---

## 7. Skill format — match the depth of existing Claude skills

PTCF+E (Persona/Task/Context/Format/Examples) is the **structural baseline**. Existing Claude skills define the **depth bar**. Match the latter.

### Frontmatter (required)

```yaml
---
name: rep/discovery-suite/discovery-call-scoring
description: Score a discovery call transcript against SPICED with evidence requirements, red-flag detection, and coaching prescriptions.
license: MIT
suite: rep/discovery-suite
methodology_refs:
  - methodology/seven-key-moments.md
  - methodology/dana-sales-management-brief-v2.md#section-vii
context_required:
  - icp
  - methodology.qualification
  - sales_process.stages
---
```

### Body structure — required sections

1. Title
2. Brief description
3. **When to Use** — bullet list of trigger scenarios
4. **Inputs** — table: Input | Required | Description
5. **Outputs** — table: File | Format | Purpose
6. **Tool Discovery** — placed before the methodology. Tells Claude to check which tools and data sources it can reach before asking the user for anything, and lists them in priority order:
   - **Core sources:** CRM, call recordings and transcripts, email, calendar.
   - **Often-overlooked sources:** team chat, contracts, shared documents, quoting or proposal tools.
   - **Rule:** Pull real context wherever it exists. Do not ask the user to find information the skill can look up itself. If a needed source is not connected, say which one and continue with what is available.
7. **Methodology / Framework** — the structured approach. This is where depth lives.
8. **Customization** — explicit section explaining what the user must provide in `/context/` for this skill to perform well
9. **Output Format** — precise structure of the deliverable
10. **Examples** — at minimum one gold-standard input/output pair
11. **Related Skills** — composition references (which skills this calls or is called by)

### Length and depth target

- **Manager Bots / scoring skills:** 2,000-4,000 words (match extract-spiced, extract-meddpicc)
- **Rep Layer sub-skills:** 1,500-3,500 words (match research-prospect, dana-recap-emails)
- **Orchestrators (Operating Rhythm sub-skills):** 2,000-3,000 words; emphasis on composition logic
- **GPT-derived skills:** Match or exceed source GPT depth + add structured Inputs/Outputs/Customization sections

If a skill is shorter than 1,000 words, it's almost certainly under-specified. Stop and ask Victor for more source material.

### Anti-patterns to avoid

- ❌ Vague instructions ("analyze the call thoroughly") — replace with structured frameworks
- ❌ Skills that don't reference `/context/` — every skill needs a Customization section
- ❌ Generic examples — examples must be substantive enough to validate skill behavior
- ❌ Inventing methodology Codex doesn't have — stop and ask Victor for the source
- ❌ Building skills without Victor's source materials — collaborative, not autonomous

---

## 8. Test fixture format

Every skill ships with `test-fixture.md`:

```markdown
# Test Fixture: {skill-name}

## Test Scenario

[Realistic scenario description — what the user is doing, what they need]

## Test Inputs

[Concrete inputs matching the skill's Inputs table]

## /context/ State Assumed

[What's populated in /context/user-context.yaml for this test]

## Expected Output

[Structural elements, depth, and decision points the output should hit]

## Quality Criteria

- [ ] Output uses the skill's Output Format structure
- [ ] All Inputs are addressed
- [ ] /context/ values are correctly applied (customization works)
- [ ] Methodology is applied, not just acknowledged
- [ ] Edge cases handled appropriately
- [ ] Output at the depth target for the skill type
- [ ] Related skills correctly referenced
- [ ] [Skill-specific quality criteria]

## Verification Process

1. Run the skill in Claude with the test inputs
2. Compare output against quality criteria
3. If criteria fail, iterate the SKILL.md and re-test
4. Document the final passing run as the §Examples in SKILL.md
```

---

## 9. Methodology file format

The 7 new methodology files Codex writes (with Victor's source material):

```markdown
# {Methodology Name}

> One-line definition.

## Origin and Authority

Where it comes from. Empirical/theoretical basis. Cite sources.

## The Framework

Structured presentation. Sections, sub-frameworks, decision points.

## Application

How it applies in practice. Specific scenarios, before/after examples.

## Common Pitfalls

What practitioners get wrong. Failure modes.

## Related Methodology

Cross-references to other methodology files.

## Skills That Operationalize This Methodology

List of /skills/ folders that implement this methodology.

---

*Last updated: {date}. Part of Superintelligent Sales OS Phase {N}.*
```

### New methodology files to write in Phase 1

1. `superintelligent-sales-whitepaper.md` — High-level OS philosophy + math
2. `seven-key-moments.md` — Canonical Rep Layer methodology
3. `core-six-manager-responsibilities.md` — Manager Layer scope
4. `three-principles-secure-attachment.md` — Three Principles
5. `operating-rhythm.md` — Three Pillars × Four Cadences (day-agnostic)
6. `call-recording-overlay.md` — Cross-cutting overlay architecture
7. `strategic-opportunity-blueprint.md` — Blue Sheet for complex enterprise deals

**For each new methodology file, Victor provides source material.** Don't write methodology from thin context.

### Existing methodology files (already written, copy as-is from /docs/reference/methodology/ to /methodology/)

1. `champions-code-seven-elements.md` — **Note:** Includes link to Victor's externally-hosted Champion's Code app (URL provided by Victor when ready)
2. `task-coaching-diagnostic.md`
3. `managing-to-metrics-library.md`
4. `five-step-coaching-conversation.md`
5. `60-min-1on1-structure.md`
6. `forecast-triangulation-method.md`
7. `bi-monthly-forecast-cadence.md`

---

## 10. /context/ customization architecture

Every skill reads from `/context/user-context.yaml`. Template:

```yaml
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
  custom_methodology_file: null

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

manager:
  team_size: 8
  team_segments: {...}
  cadence: {...}
  coaching: {...}
  forecasting: {...}
  call_analysis: {...}

voice:
  tone: "professional, direct, results-focused"
  voice_filter_skill: "victor-voice-filter"
```

**The Customization Onboarding Skill (`rep/_onboarding/`) walks the user through populating this file.** It is the first skill a user runs after installing the OS.

---

## 11. Foundational principles (apply to every skill)

- **Shift and Lift.** Every skill removes admin burden, freeing humans for coaching/judgment.
- **80% rule.** Skills generate first 80%; humans finalize 20%.
- **CRM-first architecture.** Skills touching deal data note CRM sync requirements.
- **Day-agnostic naming.** No Monday/Friday/Tuesday hardcoded references.
- **Methodology grounding.** Every skill references methodology files in frontmatter.
- **Evidence over inference.** Analytical skills cite specific evidence (timestamps, quotes), not inferred reasoning.
- **Customization-first.** Every skill reads from `/context/`.
- **Collaborative build.** Codex never invents skill content from thin context — always ask Victor for source materials.

---

## 12. Build sequence — Suite by Suite, sub-skill by sub-skill

### Suggested build order (Victor confirms or overrides)

**Phase 0 — Repo initialization (1 PR)**
- Folder structure, methodology file copies, README v0, customization onboarding scaffold

**Phase 1 — Customization Onboarding Skill (1 PR)**
- Build `rep/_onboarding/` first; everything else depends on it
- Without this, no other skill works correctly

**Phase 2 — Manager Coaching Suite (6 PRs, one per sub-skill)**
- Highest-leverage suite, most-tested methodology
- TASK diagnostic → Development plan → Five-Step Coaching → AI Roleplay → Action tracking → Coaching orchestrator
- Build in this order; later sub-skills compose earlier ones

**Phase 3 — Manager Forecast Suite (5 PRs)**
- SPICED scoring → MEDDPICC qualifier → Deal confidence → Forecast triangulation → Pipeline coverage analysis

**Phase 4 — Manager Call & Pattern Suite (5 PRs)**
- Call scoring → Cross-deal pattern analysis → Top-performer extraction → Management analytics → Rep skill gap analysis

**Phase 5 — Manager Operating Rhythm Suite (5 PRs)**
- Composes from Coaching/Forecast/Call & Pattern Suites — built last in Manager Layer
- Weekly team meeting prep → Weekly 1:1 prep → Biweekly deal review → Biweekly skill workshop → Bi-monthly forecast review

**Phase 6 — Rep Discovery Suite (6 PRs)**
- Most foundational Rep Layer suite; many GPT sources to integrate
- Discovery prep → Discovery script → Case study recommender → Discovery call scoring → Discovery recap email → Discovery-to-demo handoff

**Phase 7 — Rep BDR Suite (6 PRs)**
- Prospect research → List builder → Customized outreach → Qualification call prep → Qualification call scoring → BDR-to-AE handoff

**Phase 8 — Rep Demo Suite (5 PRs)**
- Pain extraction → Feature/benefit matcher → Demo script → Demo scoring → Demo follow-up

**Phase 9 — Rep Solutioning Suite (5 PRs)**
- Stakeholder mapper → Executive summary → Stakeholder meeting prep → MAP builder → SE handoff brief
- Highest customization weight in Rep Layer

**Phase 10 — Rep Business Case Suite (4 PRs)**
- ROI calculator → Business case document → Persona value messaging → Executive talk tracks
- Builds on ROI & Business Case Builder GPT

**Phase 11 — Rep Proposal & Negotiation Suite (4 PRs)**
- Proposal generator → Negotiation prep → Contract redline analysis → Verbal-to-contract sequencing
- Highest customization weight overall

**Phase 12 — Rep Close & Handoff Suite (3 PRs)**
- Customer profile summary → Kickoff prep → CS handoff document

**Phase 13 — Methodology files (7 PRs, one per file)**
- Write the 7 new methodology files with Victor's source material

**Phase 14 — Bundles + Context Templates (1 PR)**
- bundle YAML files, /context/ template

**Phase 15 — README finalization + repo testing (1 PR)**
- Finalize README, test full installation flow

**Total: ~70+ PRs across Phase 1.** This is intentional. Each skill is a collaborative back-and-forth.

### Done criteria for Phase 1

- 11 Suites + 1 Onboarding Skill, all installable
- 14 methodology files
- 3 bundle YAML files
- Working README with install instructions, philosophy, layer architecture
- LICENSE (MIT) ✅
- All quality gates passed (§13)
- Victor-verified end-to-end demo: install `manager-layer.yaml`, populate `/context/`, run `manager/operating-rhythm-suite/biweekly-deal-review`, confirm output

---

## 13. Quality gates (per PR review)

Each PR must pass these gates before Victor merges:

1. **PTCF+E + Required Sections compliance.** All sections from §7 present, including Tool Discovery.
2. **Methodology grounding.** Skill references at least one methodology file in frontmatter.
3. **Customization layer.** Skill explicitly reads from `/context/` and has a Customization section.
4. **Day-agnostic.** No hardcoded day references in cadence skills.
5. **80% rule.** Output explicitly notes what humans need to finalize.
6. **Test fixture passes.** Skill produces high-quality output on synthesized test scenario.
7. **Suite consistency.** Skill fits the Suite's mirror pattern and composes with sibling sub-skills.
8. **Depth bar met.** Skill matches or exceeds the depth of relevant existing Claude skill (research-prospect, extract-spiced, etc.).
9. **No scope creep.** No skills, methodology, or features outside Phase 1 scope.
10. **Source material attribution.** If derived from a Victor-provided GPT export, the skill notes the source GPT in its frontmatter or comments.

---

## 14. Out of scope for Phase 1 — DO NOT BUILD

- Customer Success skills (`rep/qbr-execution`, `rep/csm-comms-automation`)
- QBR governance, support triage
- Use cases #16-19 (post-sale)
- Customer Success Metrics Analyst GPT port
- Any Leader Layer skills (Phase 2)
- Any RevOps Layer skills (Phase 2)
- Pricing methodology, capacity planning, sales play design, RevOps charter (all Phase 2)
- Marketing-specific skills (Phase 4)

If unsure whether something is in scope, **stop and ask Victor before building.**

---

## 15. Open questions resolved before Codex starts

| Question | Answer |
|---|---|
| GitHub org name | `superintelligentsales` ✅ |
| Repo URL | `github.com/superintelligentsales/superintelligent-sales-os` ✅ |
| Skill installation mechanism | Claude Code SKILL.md format ✅ |
| Voice consistency for client-facing outputs | Reference `victor-voice-filter` skill in skills producing client-facing language ✅ |
| Test scenarios | Codex synthesizes per skill in collaboration with Victor; documents in test-fixture.md ✅ |
| Architecture | Suites with sub-skills (not standalone skills) ✅ |
| Naming convention | "Suite" suffix; reserves "Operating System" for the whole OS ✅ |
| Customization | First-class architectural concern; every skill reads from `/context/` ✅ |
| Build mode | Collaborative with Victor, not autonomous; one skill per PR ✅ |
| Champion's Code | Methodology file + external app link, not a skill ✅ |

---

## 16. Reference: Layer architecture summary

| Layer | Persona | What it owns | Phase |
|---|---|---|---|
| **Rep** | AE / SDR / CSM | Seven Key Moments — execution per deal | Phase 1 |
| **Manager** | Frontline sales manager | Coaching reps, accurate forecasts, hitting team quota | Phase 1 |
| **Leader** | CRO / EVP Sales | GTM strategy, top-down targets, cross-functional alignment | Phase 2 |
| **RevOps** | VP RevOps | Data integrity, forecast infra, tech stack, AI change management | Phase 2 |

---

## 17. Pre-flight checklist for Victor before starting Codex

Complete these one-time setup tasks before pasting the kickoff prompt:

- [ ] **Commit `/docs/reference/` to the repo** with all canonical files:
  - [ ] `superintelligent-sales-os-overview.md`
  - [ ] `dana-sales-management-brief-v2.md`
  - [ ] `superintelligent-sales-os-repo-spec.md`
  - [ ] `superintelligent-sales-os-asset-register.md`
  - [ ] `skill-list-v2-rep-layer.md`
  - [ ] `skill-list-v2-manager-layer.md`
  - [ ] `/docs/reference/methodology/` with 7 manager methodology files
  - [ ] This file as `/docs/CODEX_BUILD_HANDOFF.md`
- [ ] **Connect Codex to the repo.** Authorize `superintelligentsales` org access.
- [ ] **Verify Codex has mirrored access to existing Claude skills.** Codex should read research-prospect, dana-recap-emails, victor-voice-filter, extract-spiced, extract-meddpicc, dana-proposal-writer, matching-case-studies, dana-sequence-builder.
- [ ] **Verify Codex can read and write to the repo.** Test: have Codex create test.md in a feature branch, open PR, close it.
- [ ] **Prepare per-skill source materials in advance.** Before kicking off each skill, have ready:
  - GPT export bundle (if applicable) — instructions + knowledge files + examples + config
  - Specific behavior instructions
  - Sample inputs from real engagements
  - Expected output examples
- [ ] **(Defer)** Export Manager GPT system prompts + knowledge bases when Coaching Suite or Forecast Suite work begins
- [ ] **(Defer)** Export Rep GPT system prompts + knowledge bases when Discovery Suite or Business Case Suite work begins
- [ ] **(Defer)** Provide Champion's Code app URL when methodology file is being written

Once pre-flight is complete, paste the kickoff prompt from §1 into Codex.

---

*Last updated: April 29, 2026. v2 supersedes April 26 Codex handoff. Aligned with Suite architecture in skill-list-v2-rep-layer.md and skill-list-v2-manager-layer.md.*
