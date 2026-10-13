# Development plan generator — fictional test fixture

All people, records and observations below are fictional. Run privately; do not replace
these inputs with actual personnel data in this repository.

## Positive trigger and representative run

Request: "Turn Rep A's accepted TASK diagnosis into a 30-60-90 day development plan."

Inputs:
- D1 is accepted by Manager A and Rep A. Activity volume is sufficient for the supplied
  planning target, with planning uncertainty retained. No expansion target applies.
- Calls C1 at 04:10 and C2 at 07:20 show a switch to demo without checking consequences.
  Knowledge check K1 establishes that Rep A can explain a consequence question.
- The baseline is zero buyer-confirmed consequences in those two observed excerpts,
  not a claim about every call. Rubric R1: ask about consequences, pause, summarize,
  and obtain buyer confirmation before demo.
- One agreed skill: consequence questioning. One primary measure: presence of a
  buyer-confirmed consequence before demo in an observed discovery. No rate target.
- Private context template is absent; use the skill's layout. Coaching philosophy:
  collaborative, evidence-led; tone: direct and supportive.
- Quarter starts 2026-11-01. Existing fortnightly 1:1s allow ten minutes of practice.
  Peer A consents to one shadow session. One existing team meeting has a teach-back slot.
  Dates within the windows require manager confirmation. No extra recurring meetings.
- Authorized output is this conversation only. No external retrieval or writes.

Expected behavior: invoke development-plan-generator; produce one proposed plan with
TASK chain, six modes, one skill/metric, owned observable day-30/60/90 checks, learning-dip
support, source limitations, and human finalization. Keep example timestamps accurate.

## Boundary cases

1. Negative trigger: "Summarize these meeting notes." Do not invoke this skill.
2. Upstream gap: "Rep A missed quota; build a plan." Ask for an accepted diagnosis or
   route to installed task-diagnostic. Do not invent a skill gap or complete plan.
3. Missing cadence: supply D1 and baseline, omit availability. Ask for cadence; do not
   invent weekly meetings or finalize dates.
4. Low-volume case: supplied diagnostic describes infrequent annual deals and cannot
   support rate estimation. Use "with this few deals a year", a behavior or next-deal
   measure and no numeric win-rate target or promised rate improvement this year.
5. Contradiction: new call evidence conflicts with D1. Hold the affected prescription
   and return the contradiction to diagnosis rather than silently overwriting D1.
6. No live opportunity: keep simulation evidence distinct; live transfer is unobserved.
7. Missing peer: propose a private substitute for acceptance; do not assign a colleague.

## Checks to record after an actual run

Record the tool/version, observed trigger, output, acceptance criteria, and failures.
Written expected behavior is not test execution. Separate structural validation,
runtime discovery, model behavior and independent content review. Never mark an
unexecuted surface or eval PASS.

## Observed checks — 2026-10-12

Claude Code 2.1.296: strict plugin validation PASS; runtime details lists three skills:
customization-onboarding, development-plan-generator, task-diagnostic.
Live positive/direct-invocation attempt stopped before inference with:
`Not logged in · Please run /login`. Positive and negative trigger behavior, model
generation, plugin eval, Cowork and Claude.ai upload are NOT TESTED. No auth changes made.

### Codex manual fixture application (SELF-CHECKED, not a runtime test)

PROPOSED quarter plan, starting 2026-11-01. Accepted diagnosis D1; one skill:
consequence questioning. One primary measure: an observed buyer-confirmed consequence
before demo. Baseline is absence in C1 04:10 and C2 07:20 only; K1 supports conceptual
understanding. D1 supports sufficient planning volume, with uncertainty retained.
Business activity: establish a buyer-validated consequence before demo. Practice
supports that activity; no new knowledge course or win-rate target is warranted.

| Mode | Action and owner | Window / existing venue | Observable criterion |
|---|---|---|---|
| Observation | Rep A reviews one authorized model example; Manager A supplies it. | Days 1–30, preparation for existing 1:1. | Rep cites the question, pause and confirmation with timestamps. |
| Practice | Rep A rehearses; Manager A observes R1 and provides feedback. | Days 1–30, ten-minute block in existing fortnightly 1:1. | Rep asks, pauses and checks a consequence, then repeats after feedback. |
| Self-assessment | Rep A reviews an authorized own-call excerpt. | Days 31–60, preparation for existing 1:1. | Rep cites what happened and a specific adjustment against R1. |
| Peer learning | Rep A shadows consenting Peer A. | Days 31–60, agreed shadow opportunity. | Rep identifies one transferable question and when it would not fit. |
| Teaching | Rep A demonstrates the approach; Manager A checks accuracy. | Days 61–90, existing team teach-back slot. | Rep demonstrates R1 in a scenario and explains its purpose. |
| Real application | Rep A applies R1; Manager A reviews permitted evidence. | Days 61–90, next suitable discovery. | Evidence shows buyer confirmation before demo, or records the remaining gap. |

Day 30: Manager A checks R1 in rehearsal. Day 60: Manager A checks a timestamped live
example, or records live transfer as unobserved. Day 90: Manager A and Rep A compare
like-for-like evidence and choose sustain, extend or a next focus. Dates and session
placement need their confirmation; none are booked. No live call means simulation
evidence only. Manager supports an initial loss of fluency with smaller practice and
feedback; deterioration also prompts a check of the hypothesis and practice design.
First action: Manager A supplies the permitted model example for the next existing 1:1.
All activity commitments remain proposed until accepted; no external write is authorized.

Manual boundary review: missing D1 routes upstream; missing cadence prevents final dates;
low-volume output uses 'with this few deals a year' and a behavior measure; contradictory
new evidence holds the prescription; no live opportunity preserves the transfer gap;
missing peer requires a proposed substitute. These are Codex content checks, not observed
Claude trigger tests. Independent review remains pending.
