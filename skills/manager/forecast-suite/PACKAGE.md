# Forecast Suite

## Build Status

This package registers five forecast skills: forecast-triangulation, meddpicc-qualifier,
spiced-scoring, deal-confidence and pipeline-coverage-analysis. Each has a fictional test
fixture with expected results and boundary cases. Registration does not establish
behavioral acceptance; each skill is tested against its fixture before it is called
launch-ready.

## Forecast Skills

| Skill | Question it answers |
|---|---|
| pipeline-coverage-analysis | Is there enough pipeline to hit the target this period and the next, and how much must be created by when? |
| deal-confidence | Across the commit and best-case lists, which deals does the evidence support, and which should be inspected first? |
| spiced-scoring | For one deal, what has the buyer said about Situation, Pain, Impact, Critical Event and Decision? |
| meddpicc-qualifier | For one complex enterprise deal, what does the buyer evidence show on all eight MEDDPICC elements? |
| forecast-triangulation | What is the team's forecast as a band, comparing rep commit, stage-weighted pipeline and run-rate? |

A typical sequence moves from the whole pipeline to single deals and back:
coverage first, then confidence across the list, then a qualifier on the deals it flags,
then triangulation before the number goes to leadership. Use the team's qualification
method: SPICED by default, MEDDPICC for complex, procurement-led, enterprise-sized deals.
A recommendation to run another skill does not run it automatically.

## Operating Principles

- **A forecast is a band, not a number.** Show the range and what drives its width.
- **Buyer evidence only.** Score what the buyer said or wrote. CRM fields and rep
  confidence are claims to check, not evidence.
- **The team's numbers, not the industry's.** Use the team's measured rates and its own
  thresholds. Where the team has none, label any starting default as a default to replace.
- **Unknown is not late.** A missing close date or stage date is unknown, not late.
- **Patterns, not labels.** Describe what the numbers and transcripts show; never label a rep.
- **The manager decides.** Skills recommend a category; only the manager changes it.
  No CRM writes, no automatic messages.

These principles live here once; each sub-skill applies them without duplicating this
section. Teams replace the starting defaults in the Forecast section of
`rep/customization-onboarding`.
