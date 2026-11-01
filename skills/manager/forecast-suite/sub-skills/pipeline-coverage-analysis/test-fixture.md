# Test Fixture: Pipeline Coverage Analysis

## Test Scenario

All names, records, amounts, and dates below are fictional test inputs, not anonymized
client material. A sales manager asks: "Do we have enough pipeline for Q2, and what do we
need to create for Q3?" The skill must test coverage against the team's own win rate,
hold out stale and undated deals, split by rep and component, and give a creation target
with a deadline.

## Test Inputs

All amounts are in thousands, bookings (contract value credited in the close month).

- Current period: Q2, April 1 to June 30. Run date: April 7. Target 1,800; closed 200;
  remaining 1,600.
- Quota components (remaining): new logo (NL) 1,100; expansion (EXP) 500.
- Rep remaining quota: Rep A 600; Rep B 500; Rep C 500.
- Next period: Q3, July 1 to September 30. Target 1,900.
- `pipeline_coverage_target`: 3.0.
- Measured win rate by value, from creation, last four quarters: 30 percent.
- Measured stage rates: Discovery 30, Solution 40, Proposal 55, Contract 85 percent.
- Stage exit limits (days): Discovery 30, Solution 30, Proposal 21, Contract 14.
- Median sales cycle, creation to close: 75 days.
- Measured creation pace, last 13 weeks: 300 per week.
- Private analysis only; no CRM writes or messages.

### Open pipeline (CRM, run date April 7)

| ID | Owner | Stage | Amount | Close date | Days in stage | Component |
|---|---|---|---|---|---|---|
| P-01 | Rep A | Contract | 200 | May 10 | 6 | NL |
| P-02 | Rep A | Proposal | 300 | Jun 5 | 12 | NL |
| P-03 | Rep A | Solution | 400 | Jun 20 | 18 | NL |
| P-04 | Rep A | Discovery | 250 | Jun 28 | 10 | EXP |
| P-05 | Rep B | Proposal | 250 | May 20 | 35 | NL |
| P-06 | Rep B | Solution | 300 | Jun 15 | 40 | NL |
| P-07 | Rep B | Discovery | 150 | (blank) | 5 | EXP |
| P-08 | Rep B | Contract | 100 | Apr 30 | 4 | EXP |
| P-09 | Rep C | Proposal | 350 | Jun 10 | 9 | NL |
| P-10 | Rep C | Solution | 200 | Jun 25 | 22 | EXP |
| P-11 | Rep C | Discovery | 300 | Jun 30 | 15 | NL |
| P-12 | Rep C | Discovery | 200 | Jul 20 | 3 | NL |

## Expected Behavior

### Pipeline groups

- Q2 dated pipeline: 2,650 (all except P-07 and P-12).
- Held out, past stage limit: P-05 (Proposal, 35 days against 21) and P-06 (Solution, 40
  days against 30), total 550.
- Held out, no close date: P-07, 150. Reported as unknown, not late.
- Q2 qualified pipeline: 2,650 minus 550 = 2,100.
- Q3 pipeline: P-12, 200.

### Team coverage, Q2

- Raw coverage: 2,650 ÷ 1,600 = 1.66.
- Qualified coverage: 2,100 ÷ 1,600 = 1.31.
- Manager's setting 3.0; required by win rate 1 ÷ 0.30 = 3.33. The output must say the
  setting is below what the data implies.
- Expected value of qualified pipeline: 200 × 0.85 + 300 × 0.55 + 400 × 0.40 + 250 × 0.30
  + 100 × 0.85 + 350 × 0.55 + 200 × 0.40 + 300 × 0.30 = 1,017.5.
- Expected shortfall: 1,600 minus 1,017.5 = 582.5.

### By rep, Q2 (qualified)

| Rep | Remaining | Qualified | Coverage | Expected value | Shortfall | Largest-deal share |
|---|---|---|---|---|---|---|
| A | 600 | 1,150 | 1.92 | 570.0 | 30.0 | 35 percent |
| B | 500 | 100 | 0.20 | 85.0 | 415.0 | 100 percent |
| C | 500 | 850 | 1.70 | 362.5 | 137.5 | 41 percent |

Rep B's raw coverage is 1.30 (650 ÷ 500) but qualified coverage is 0.20, because P-05 and
P-06 are held out and P-07 has no date. The output reads this as a hypothesis (stale
deals or limits that do not fit) and flags that Rep B's qualified coverage rests on one
deal, P-08. It must not describe Rep B's effort or honesty.

### By component, Q2 (qualified)

- New logo: 1,550 ÷ 1,100 = 1.41; expected value 777.5; shortfall 322.5.
- Expansion: 550 ÷ 500 = 1.10; expected value 240.0; shortfall 260.0.

### Creation gap

- Q2: shortfall 582.5 ÷ 0.30 = 1,941.7 to create. Deadline June 30 minus 75 days = April
  16, nine days after the run date. At the measured pace of 300 per week, the team would
  create about 386 in nine days. The output must say new pipeline is unlikely to close the
  Q2 gap and that Q2 depends on converting existing deals.
- Q3: existing pipeline expected value 200 × 0.30 = 60. Shortfall 1,900 minus 60 = 1,840.
  Creation gap 1,840 ÷ 0.30 = 6,133.3. Deadline September 30 minus 75 days = July 17.
  Weeks from April 7 to July 17: 101 days, 14.4 weeks. Required pace 425.1 per week
  against a measured 300.

### Deals to inspect (expected, up to five)

P-05 and P-06 (past stage limits), P-07 (no close date), P-08 (Rep B's only qualified deal),
and P-03 (largest qualified deal for the team, 400).

### Output checks

- Every coverage ratio appears with the required coverage of 3.33 beside it.
- No industry coverage figure appears as the answer.
- Exactly one next question.
- Calculation lines shown for coverage, expected value, and both creation gaps.
- Nothing written to the public repository.

## Boundary Cases

1. **No win rate, no target.** Remove the win rate and set `pipeline_coverage_target` to
   `[USER]`. The output shows raw coverage for reference only, says coverage cannot be
   judged, and asks one question for the win rate. It must not substitute a market rule.
2. **No stage rates.** Remove stage rates. Stage-weighted coverage is "not estimable." The
   Q2 creation gap falls back to 1,600 ÷ 0.30 minus 2,100 = 3,233.3, and the output names
   the fallback method.
3. **No stage exit limits.** Set `stage_exit_criteria` to `[USER]`. P-05 and P-06 become
   qualified (Q2 qualified 2,650, coverage 1.66), and the output says the quality check did
   not run.
4. **Missing close date.** P-07 must never be counted as late or as Q2 pipeline. It is
   listed with a request to date it.
5. **Next-period deal.** P-12 (July 20) must not count toward Q2 coverage. It counts toward Q3.
6. **Manager setting above the data.** If the win rate is 40 percent (required 2.5) and the
   setting stays 3.0, the output says the setting is more conservative than the data
   requires and reports both, without overriding the manager's setting.
