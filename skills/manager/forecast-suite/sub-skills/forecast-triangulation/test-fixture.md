# Test Fixture: Forecast Triangulation

## Test Scenario

All names, records, amounts, and dates below are fictional test inputs, not anonymized
client material. A sales manager asks: "Prep my forecast for the leadership call. Is the
team going to hit 2,400 this quarter?" The skill must produce a band, not a single number,
and test the team's commit rather than accept it.

## Test Inputs

All amounts are in thousands, bookings (contract value credited in the close month).

- Period: Q1, January 1 to March 31. Run date: January 6. Target: 2,400. Closed to date: 0.
  Single quota component (new logo only). Private analysis only; no CRM writes or messages.
- RC1, rep commit submissions:
  - Rep A: D-101, Contract, 500, close February 14. D-103, Proposal, 700, close March 20.
  - Rep B: D-102, Contract, 300, close January 30. D-104, Proposal, 500, close March 6.
  - Rep C: D-106, Solution, 650, close March 28.
  - Commit total: 2,650.
- P1, open pipeline export (CRM, run date January 6):

| ID | Owner | Stage | Amount | Close date | Days in stage |
|---|---|---|---|---|---|
| D-101 | Rep A | Contract | 500 | Feb 14 | 9 |
| D-102 | Rep B | Contract | 300 | Jan 30 | 12 |
| D-103 | Rep A | Proposal | 700 | Mar 20 | 22 |
| D-104 | Rep B | Proposal | 500 | Mar 6 | 18 |
| D-105 | Rep C | Proposal | 400 | Mar 25 | 38 |
| D-106 | Rep C | Solution | 650 | Mar 28 | 41 |
| D-107 | Rep A | Solution | 550 | Mar 30 | 15 |
| D-108 | Rep B | Discovery | 560 | Mar 31 | 7 |
| D-109 | Rep C | Proposal | 450 | Apr 15 | 20 |

- B1, measured stage-to-close rates, last four quarters, 212 decided opportunities,
  team's own CRM: Contract 85 percent, Proposal 50 percent, Solution 35 percent,
  Discovery 25 percent. No close-date-in-period probability supplied.
- H1, closed bookings by quarter, last four quarters: 1,950; 2,100; 2,000; 2,150.
  No seasonality adjustment supplied. No known inflection points this quarter.
- S1, maximum days in stage from context: Discovery 21, Solution 30, Proposal 45, Contract 30.

## /context/ State Assumed

The following is private fixture context, not an addition to the public schema:

```yaml
manager:
  cadence:
    forecast_review_frequency: bi-monthly
  forecasting:
    deal_stages: [Discovery, Solution, Proposal, Contract]
    stage_exit_criteria: fixture/S1.md
    historical_conversion_rates: fixture/B1.md
    quota_structure: single new-logo bookings quota
tools:
  forecast_data_sources: [fixture/RC1.md, fixture/P1.csv]
```

Treat B1 and S1 above as the supplied contents of those paths. All other fields are
unanswered; none may be invented.

## Expected Output

- D-109 closes April 15 and is excluded from all three methods, listed as a possible pull-forward.
- Method 1: 500 + 300 + 700 + 500 + 650 = 2,650.
- Method 2: Contract 800 × 0.85 = 680; Proposal (700 + 500 + 400) 1,600 × 0.50 = 800;
  Solution (650 + 550) 1,200 × 0.35 = 420; Discovery 560 × 0.25 = 140. Total 2,040.
  In-period pipeline total is 4,160. States that close dates were taken as given.
- Method 3: (1,950 + 2,100 + 2,000 + 2,150) ÷ 4 = 2,050. States no seasonality adjustment.
- Band 2,040 to 2,650. Central estimate (2,650 + 2,040 + 2,050) ÷ 3 = 2,247 (rounded).
  Spread 610 ÷ 2,247 = 27 percent. Low confidence. Target 2,400 sits inside the band.
- Spread reading: commit exceeds stage-weighted by 610, suggesting possible happy ears,
  stated as a hypothesis about deals, not a label on any rep. Stage-weighted and run-rate
  differ by 10 (under 1 percent), so stale pipeline is not indicated.
- Deals to inspect, in this order: D-103 (700, Proposal, committed, largest amount driving the
  gap); D-106 (650, Solution, committed, 41 days against a 30-day maximum). D-105 may be listed
  as aging (38 of 45 days, not yet past maximum) but not called late.
- One first action, one draft leadership message marked as a draft, exactly one next question.

## Quality Criteria

- [ ] Six Output Format sections in order; exactly one question; draft message never sent.
- [ ] D-109 excluded from every method and listed separately.
- [ ] All arithmetic matches the Expected Output and appears in a calculation line.
- [ ] Only B1 rates used; no industry stage rates or days-in-stage figures from the reference appear.
- [ ] Band, central estimate, and spread all reported; central estimate never shown alone.
- [ ] Pathology stated as a hypothesis about deals; no rep described as having happy ears.
- [ ] D-106 flagged against S1; D-105 described as aging, not late.
- [ ] Each flagged deal cites its source record (RC1 or P1).
- [ ] No CRM writes, messages, or invented context fields.

## Additional Boundary Cases

1. Remove B1: Method 2 is not estimable. Report a two-method band (2,050 to 2,650), cap
   confidence at medium, and ask for the team's measured stage rates as the one question.
2. Replace H1 with two quarters only: run Method 3 on two periods, state the count, lower confidence.
3. Rep C submits "800 total" with no deal lines: accept it in Method 1, flag that its deals
   cannot be inspected, and do not attribute it to D-106.
4. D-104 appears under Rep B in RC1 and Rep A in P1: show both records and hold D-104 out of
   Method 2 until resolved; recompute the band without it and say so.
5. The user asks for "just one number for my CRO": give 2,247 with the band 2,040 to 2,650
   beside it and one sentence on why the band matters this quarter.
