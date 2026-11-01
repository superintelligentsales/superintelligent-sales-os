# Test Fixture: Deal Confidence

## Test Scenario

All names, companies, records, amounts, quotes, and dates below are fictional test inputs,
not anonymized client material. A sales manager asks: "Prep my deal list for Thursday's
forecast review. Which commit deals are real, and which should I dig into first?" The
skill must rate every Commit and Best Case deal, recommend a category for each, rank the
at-risk deals by amount, and write one question per deal for each rep's 1:1.

## Test Inputs

Amounts are in thousands, bookings. Run date: November 2. Period: Q4, October 1 to
December 31. Private analysis only; no CRM writes or messages.

Context:

- `methodology.qualification`: SPICED; MEDDPICC for deals above 150.
- `manager.forecasting.stage_exit_criteria`: maximum 30 days in Solution, Proposal, and
  Contract. Exit criteria: Solution, demo held with two or more buyer stakeholders;
  Proposal, buyer confirmed a budget range and a decision date; Contract, order form sent
  and buyer legal engaged. No other thresholds are set, so the activity, close date,
  contact, next step, and mutual action plan checks use the starting defaults.
- `manager.cadence.forecast_review_frequency`: bi-monthly.

### CRM deal list

| ID | Rep | Account | Amount | Stage | Category | Close date | Stage entered | Close date changes | Last buyer activity | Buyer contacts (director or above) | Next step date | Mutual action plan |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D-201 | A | Northfield Logistics | 180 | Proposal | Commit | Nov 21 | Oct 8 | 0 | Oct 14 | 1 (yes) | none | No |
| D-202 | A | Halvorsen Foods | 95 | Contract | Commit | Nov 14 | Oct 21 | 0 | Oct 30 | 3 (yes) | Nov 5 | Yes |
| D-203 | B | Brightline Clinics | 140 | Proposal | Commit | Dec 12 | Oct 11 | 2 | Oct 28 | 2 (yes) | Nov 6 | Yes |
| D-204 | B | Corvel Partners | 60 | Solution | Best Case | Dec 20 | Oct 15 | 0 | Oct 31 | 2 (yes) | Nov 10 | Yes |
| D-205 | C | Ashgrove Bank | 220 | Proposal | Best Case | Dec 18 | Oct 13 | 1 | Oct 29 | 4 (yes) | Nov 8 | Yes |
| D-206 | C | Pinecrest Schools | 45 | Solution | Commit | (blank) | (blank) | 0 | Oct 25 | 2 (yes) | Nov 12 | Yes |
| D-207 | A | Kestrel Freight | 70 | Contract | Best Case | Dec 5 | Sep 22 | 1 | Nov 1 | 3 (yes) | Nov 4 | Yes |

All seven deals have more than one approver. D-201's only buyer contact is Priya Raman,
VP Operations.

### Qualifier output and transcripts

- D-201 has `meddpicc-qualifier` JSON from November 1: total 7.5 of 16, supported category
  Best Case. Its quotes show no critical event (October 14, 19:10, "As soon as possible,
  honestly") and quantified impact (September 9, 09:40, "Overtime on the dispatch desk is
  running about forty thousand a month"). Proposal exit criteria not met: no budget range
  or decision date confirmed by the buyer.
- D-202, D-203, D-205, D-206, and D-207 have transcripts. Each shows a buyer-stated
  critical event and a buyer-stated number for impact. The light check finds buyer
  evidence for every element of the team's method on each (MEDDPICC for D-205, SPICED for
  the others). Example, D-202: "Our new warehouse opens January 6, and we can't open it on
  the old system." Each meets its stage exit criteria.
- D-204 has no recordings; the recording platform was not connected for that rep's calls.
  CRM shows a demo with two buyer stakeholders, so Solution exit criteria are met.

## Expected Behavior

### Ratings

| ID | Major findings | Minor findings | Rating | Recommended | Status |
|---|---|---|---|---|---|
| D-201 | Critical event Fail; multi-threading Fail (1 contact) | Qualifier supports Best Case; last buyer activity 19 days ago; no dated next step; no mutual action plan; Proposal exit criteria not met | Low | Pipeline | At risk, 180 |
| D-202 | None | None | High | Commit | Supported |
| D-203 | None | Close date changed 2 times | Medium | Best Case | At risk, 140 |
| D-204 | None | Critical event Unknown; quantified impact Unknown | Low | Pipeline | At risk, 60 |
| D-205 | None | None | High | Commit | Possible upgrade |
| D-206 | None | Commit deal with no close date | Medium | Best Case | At risk, 45 |
| D-207 | None | 41 days in Contract against a 30-day maximum | Medium | Best Case | Supported |

Counts: 2 High, 3 Medium, 2 Low.

Days in stage (run date November 2): D-201 25, D-202 12, D-203 22, D-204 18, D-205 20,
D-207 41. D-206 is not checked; its stage date is blank.

D-201: the rating supports Pipeline and the qualifier supports Best Case; the lower,
Pipeline, is recommended. The output must explain that the deal-killers drive the
difference from the qualifier's result.

### Totals

- Amount at risk: 180 + 140 + 60 + 45 = 425.
- Commit as recorded: 180 + 95 + 140 + 45 = 460. As recommended: 95.
- Best Case as recorded: 60 + 220 + 70 = 350. As recommended: 140 + 45 + 220 + 70 = 475.
  D-205 stays in Best Case in this total because upgrades are not counted.
- Pipeline as recommended: 180 + 60 = 240.
- Check: 460 + 350 = 810 recorded; 95 + 475 + 240 = 810 recommended.

### Deals to inspect first

1. D-201, 180: no critical event and one buyer contact.
2. D-203, 140: close date changed twice.
3. D-204, 60: no recordings, so critical event and impact cannot be checked.
4. D-206, 45: Commit with no close date.

D-205 is listed separately as a possible upgrade, with a question, and not added to Commit.

### Questions by rep (examples of acceptable form)

- Rep A, D-201: "What date does Northfield need this live, and what happens if they miss it?"
- Rep A, D-207: "What is holding the contract, and who on their side owns it?"
- Rep B, D-203: "What moved the close date the last two times, and what would move it again?"
- Rep B, D-204: "What date is Corvel working toward, and what have they said the problem costs them?"
- Rep C, D-206: "When does Pinecrest expect to sign, and what has to happen first?"
- Rep C, D-205: "Is there anything that keeps Ashgrove out of Commit?"

### Output checks

- Rules used section marks the 30-day maximum and exit criteria as the team's, and the
  activity, close date, contact, next step, and mutual action plan thresholds as starting
  defaults, with a pointer to the Forecast section of `rep/customization-onboarding`.
- The verbatim line "a missing close date or stage date is unknown, not late" applies to
  D-206; it is never called late or stale.
- Multi-threading for D-201 is counted once, as a deal-killer, not again as hygiene.
- No rep is labeled. Any pattern is stated as a fact in the records.
- Exactly one next question in the human finalization section.
- No industry benchmarks or close percentages appear.

## Boundary Cases

1. **Unknown is not Fail.** D-204 must be Low through two Unknown minors, not through a
   Fail. A run that marks D-204's critical event as Fail fails this test.
2. **Upgrade not counted.** A run that adds D-205's 220 to recommended Commit (giving 315)
   fails. Upgrades are listed separately.
3. **One flag in Commit.** D-203 has a single minor finding. It is Medium, which supports
   Best Case, so it is at risk from Commit. A run that keeps it in Commit fails.
4. **Days in stage without a team maximum.** Remove the 30-day maximum from context. D-207
   becomes High and supports Commit, a possible upgrade; the output says days in stage
   was not checked because the team has not set a maximum.
5. **Stale qualifier output.** Add a D-201 call on November 2, after the November 1
   qualifier run. The output uses the November 1 result, says it may be out of
   date, and suggests re-running the qualifier for D-201 only.
6. **Missing titles.** If D-203's contact titles are blank, multi-threading becomes
   Unknown, a minor finding. D-203 then has two minors and becomes Low, recommended
   Pipeline.
