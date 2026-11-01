# Test Fixture: SPICED Scoring

## Test Scenario

All names, companies, records, amounts, quotes, and dates below are fictional test inputs,
not anonymized client material. A sales manager asks: "Is D-305 real? Jordan has
Brightline in Commit for the 26th." The skill must score the deal from buyer evidence
only, test the Commit category against that score, and name the CRM fields that run
ahead of the evidence.

## Test Inputs

Amounts are in thousands. Run date: November 1. Private analysis only; no CRM writes or
messages. `manager.forecasting.stage_exit_criteria` is `[USER]`, so the starting rules in
Step 5 apply. `methodology.qualification` is SPICED.

- CRM record, D-305: Brightline Property Management. Owner Rep B (Jordan Pike). Stage
  Proposal. Amount 42, annual subscription. Expected close November 26. Forecast category
  Commit. Critical event field: "Winter freeze, must be live Dec 1". Decision maker field:
  "Ray Okafor (COO), engaged".
- Call 1: September 30, discovery, 34 minutes. Buyer: Alicia Moreno, Director of Operations.
- Call 2: October 22, demo, 31 minutes. Buyer: Alicia Moreno.
- No buyer emails supplied. No prior scoring run.

### Transcript excerpts

Call 1, September 30:

- (03:10) Alicia: "We manage about nineteen hundred units across fourteen buildings, and everything maintenance-related runs through email and a shared spreadsheet."
- (08:25) Alicia: "Work orders sit for an average of six days. We paid out about twelve thousand in rent credits last quarter because of it."
- (09:50) Alicia: "Honestly, I'm the one tenants call when things slip, and I'm tired of apologizing."
- (15:40) Jordan: "So if you cut that to two days, you'd save most of those credits?" Alicia: "Right."
- (16:30) Alicia: "That would be a nice change for the team."
- (21:00) Alicia: "We'd like it in before winter."
- (25:10) Alicia: "It has to work on phones for our techs and connect to our accounting system."

Call 2, October 22:

- (12:05) Alicia: "If we got work orders closed in two days, I think the credits mostly go away."
- (19:15) Jordan: "When do you need this running?" Alicia: "ASAP, really."
- (23:40) Alicia: "I'd take it to our COO, Ray, and he'd want to see pricing."
- (24:30) Alicia: "Ray signs off on anything over twenty-five thousand."
- (29:50) Jordan: "Perfect. I'll get the proposal over to you this week."

Neither call includes contact with Ray, a consequence tied to winter or December 1, or
timing for the COO review.

## Expected Behavior

### Scores

| Element | Score | Strongest buyer evidence | Why not higher |
|---|---|---|---|
| Situation | 1 | Sep 30, 03:10, units, buildings, current tools | No budget, leadership, or strategic plan. |
| Rational Pain | 1.5 | Sep 30, 08:25, six-day wait and rent credits | Two measures; not a full cost picture. |
| Emotional Pain | 1 | Sep 30, 09:50, "tired of apologizing" | Personal only; no team or standing at stake. |
| Rational Impact | 1 | Oct 22, 12:05, two days and credits go away | One measure. The 15:40 "Right" adds nothing. |
| Emotional Impact | 0.5 | Sep 30, 16:30, "a nice change for the team" | Vague positive, not explored. |
| Critical Event | 1 | Sep 30, 21:00, "before winter" | Preferred timing, no consequence. "ASAP" at 19:15 adds nothing. |
| Decision Process | 1 | Oct 22, 23:40, take it to the COO with pricing | Steps named, no timing. |
| Decision Criteria | 1 | Sep 30, 25:10, phones and accounting connection | Specific, but no priority or deal-breaker. |
| Decision Committee | 1 | Oct 22, 24:30, Ray and the signing threshold | Named with authority; not engaged. |

Total: 1 + 1.5 + 1 + 1 + 0.5 + 1 + 1 + 1 + 1 = 9 of 18. Label: Partial (6.5 to 10).

Expected headline: "Partial, 9 of 18. Marked Commit; evidence supports Best Case."

### Forecast category test (starting rules)

| Gate | Requirement | D-305 | Result |
|---|---|---|---|
| Commit: Critical Event | 1.5 or higher | 1 | Fail |
| Commit: Decision Process | 1.5 or higher | 1 | Fail |
| Commit: Decision Committee | 1.5 or higher | 1 | Fail |
| Commit: Rational Pain | 1 or higher | 1.5 | Pass |
| Commit: Rational Impact | 1 or higher | 1 | Pass |
| Commit: no element at 0 | None at 0 | Lowest is 0.5 | Pass |
| Best Case: Rational Pain | 1 or higher | 1.5 | Pass |
| Best Case: Critical Event | 1 or higher | 1 | Pass |
| Best Case: Decision Committee | 1 or higher | 1 | Pass |

Supported category: Best Case. The output must label these as starting rules because
`stage_exit_criteria` is `[USER]`, and point to the Forecast section of
`rep/customization-onboarding`.

### CRM field conflicts

- Critical event field "Winter freeze, must be live Dec 1" versus Critical Event 1, with
  the 21:00 and 19:15 quotes. No buyer stated December 1 or a consequence.
- Decision maker field "engaged" versus Decision Committee 1; no call shows contact with Ray.
- Both phrased as questions for the 1:1, not as errors by the rep.

### Cost of doing nothing

Not calculated. Rational Pain is 1.5 but Rational Impact is 1, so the condition (both
1.5 or higher) is not met. The output states this.

### Coachable moments

Required for every element below 1.5: Situation, Emotional Pain, Rational Impact,
Emotional Impact, Critical Event, Decision Process, Decision Criteria, and Decision
Committee. Not required for Rational Pain. Decision Committee uses the 29:50 moment,
where the rep moved to sending the proposal instead of asking to meet Ray.

### Top three priorities (expected order and reasons)

1. **Critical Event.** The close date is 25 days out and rests on a deadline no buyer has
   stated. Asking what happens if this is not live before winter tests the date.
2. **Decision Committee.** The deal is above Ray's 25 thousand threshold and no one has
   spoken with him. Asking Alicia to bring Ray into the pricing conversation also tests
   her as a champion.
3. **Decision Process.** With Ray named, the steps and timing between proposal and
   signature are still unknown.

### Output checks

- Exactly one next question in the human finalization section.
- Every quote carries call date and timestamp; no seller quote appears as evidence.
- Score bars: ten characters, five per point, half points rounded down to a whole
  character, the same rule as `meddpicc-qualifier` (0.5 is `==--------`, 1 is
  `=====-----`, 1.5 is `=======---`). The score number beside each bar is exact.
- No characterization of Jordan's honesty or judgment.
- Output written to a private location or returned in the conversation; nothing in the
  public repository.

## Boundary Cases

1. **Bare agreement.** At 15:40 Alicia says "Right" to the rep's savings estimate.
   Rational Impact must stay at 1 from the 12:05 quote. A run that scores it 1.5 on the
   15:40 exchange fails.
2. **"ASAP" is not a critical event.** "ASAP, really" at 19:15 must not raise Critical
   Event above 1.
3. **CRM as evidence.** If the run scores Critical Event 1.5 or higher because the CRM
   field says December 1, it fails.
4. **Situation is not Pain.** The 03:10 quote about buildings and spreadsheets scores
   Situation only. A run that uses it to raise Rational Pain fails.
5. **Consequence added later.** Add a third call where Alicia says, "If this isn't live
   by December 1, the winter backlog lands on me and the owners see it in the January
   report." Critical Event moves to 1.5 and Emotional Pain to 1.5. Commit still fails on
   Decision Process and Decision Committee. The output must show that the category does
   not move on one element.
6. **Exploratory call.** If Alicia had said on Call 1, "We're just exploring for next
   year," and nothing later contradicted it, Critical Event scores 0, the Commit gate
   also fails on "no element at 0," and Best Case fails on Critical Event, so the deal
   is Pipeline.
