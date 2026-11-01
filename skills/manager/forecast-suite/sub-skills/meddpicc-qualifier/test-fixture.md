# Test Fixture: MEDDPICC Qualifier

## Test Scenario

All names, companies, records, amounts, quotes, and dates below are fictional test inputs,
not anonymized client material. A sales manager asks: "Is D-201 really commit? The rep
says Northfield signs by the 21st." The skill must score the deal from buyer evidence only,
test the Commit category against that score, and name the CRM fields that run ahead of
the evidence.

## Test Inputs

Amounts are in thousands. Run date: November 1. Private analysis only; no CRM writes or
messages. `manager.forecasting.stage_exit_criteria` is `[USER]`, so the starting rules in
Step 5 apply. `methodology.qualification` is MEDDPICC.

- CRM record, D-201: Northfield Logistics. Owner Rep A (Marcus Hale). Stage Proposal.
  Amount 180, annual contract. Expected close November 21. Forecast category Commit.
  Champion field: "Confirmed (Priya Raman)". Economic buyer field: "Tom Becker, engaged".
- Call 1: September 9, discovery, 38 minutes. Buyer: Priya Raman, VP Operations.
- Call 2: October 14, follow-up, 30 minutes. Buyer: Priya Raman.
- No buyer emails supplied. No prior qualifier run.

### Transcript excerpts

Call 1, September 9:

- (06:12) Priya: "Our dispatchers rebuild routes by hand every morning. It takes the four of them most of the first two hours."
- (09:40) Priya: "Overtime on the dispatch desk is running about forty thousand a month, and late deliveries cost us credits on two of our biggest contracts."
- (14:05) Marcus: "So you'd want to see ROI inside twelve months?" Priya: "Yeah."
- (17:30) Priya: "What we want is less time spent rebuilding routes. That's the win."
- (22:18) Priya: "Anything we buy has to integrate with our TMS and pass IT's security review."
- (27:50) Priya: "We're also talking to RouteWise, and honestly the other option is we keep patching our spreadsheet."
- (31:02) Priya: "This is my project. I'll push it with whoever I need to."

Call 2, October 14:

- (04:20) Priya: "Tom Becker, our CFO, signs anything over a hundred thousand."
- (11:45) Priya: "It goes to IT for the security review, then to Tom."
- (19:10) Marcus: "When are you hoping to have this live?" Priya: "As soon as possible, honestly."
- (24:30) Marcus: "Would you be up for introducing me to Tom?" Priya: "Let me see how the next couple of weeks go."
- (28:40) Marcus: "Great, I'll send over the proposal tonight."

Neither call mentions legal review, contract documents, procurement, or signatures.

## Expected Behavior

### Scores

| Element | Score | Strongest buyer evidence | Why not higher |
|---|---|---|---|
| Metrics | 1 | Sep 9, 17:30, "less time spent rebuilding routes" | Direction with no target. The 14:05 "Yeah" adds nothing. |
| Economic Buyer | 1 | Oct 14, 04:20, CFO named with signing threshold | No one has spoken with Tom. |
| Decision Criteria | 1 | Sep 9, 22:18, TMS integration and security review | Technical only; no priority or economic criteria. |
| Decision Process | 1 | Oct 14, 11:45, IT security review then CFO | No owner for IT review, no timing. 19:10 is not a timeline. |
| Paper Process | 0 | None | Never discussed. |
| Implicated Pain | 1.5 | Sep 9, 09:40, overtime and contract credits | Quantified in two dimensions; no consequence or leadership pressure. |
| Champion | 1 | Sep 9, 31:02, "This is my project" | Stake only. Declined the introduction at 24:30. |
| Competition | 1 | Sep 9, 27:50, RouteWise and the spreadsheet | Alternatives named; her view of them unknown. |

Total: 1 + 1 + 1 + 1 + 0 + 1.5 + 1 + 1 = 7.5 of 16. Label: Partial (4.5 to 8).

Expected headline: "Partial, 7.5 of 16. Marked Commit; evidence supports Best Case."

### Forecast category test (starting rules)

| Gate | Requirement | D-201 | Result |
|---|---|---|---|
| Commit: Economic Buyer | 1.5 or higher | 1 | Fail |
| Commit: Champion | 1.5 or higher | 1 | Fail |
| Commit: Decision Process | 1.5 or higher | 1 | Fail |
| Commit: Paper Process | 1 or higher | 0 | Fail |
| Commit: no element at 0 | None at 0 | Paper Process at 0 | Fail |
| Best Case: Implicated Pain | 1 or higher | 1.5 | Pass |
| Best Case: Champion | 1 or higher | 1 | Pass |
| Best Case: Economic Buyer | 1 or higher | 1 | Pass |

Supported category: Best Case. The output must label these as starting rules because
`stage_exit_criteria` is `[USER]`.

### CRM field conflicts

- Champion field "Confirmed" versus Champion 1, with the 24:30 quote.
- Economic buyer field "engaged" versus Economic Buyer 1; no call shows contact with Tom.
- Both phrased as questions for the 1:1, not as errors by the rep.

### Cost of doing nothing

Not calculated. Implicated Pain is 1.5 but Metrics is 1, so the condition (both 1.5 or
higher) is not met. The output states this.

### Coachable moments

Required for Metrics, Economic Buyer, Decision Criteria, Decision Process, Paper Process,
Champion, and Competition (every element below 1.5). Not required for Implicated Pain.
Paper Process uses the 28:40 moment as the missed opportunity.

### Top three priorities (expected order and reasons)

1. **Economic Buyer.** The deal is above Tom's 100 thousand signing threshold and no one
   has spoken with him. Asking Priya to arrange the meeting also tests her as a champion.
2. **Paper Process.** Twenty days remain to the November 21 close date and the contract
   steps are unknown.
3. **Metrics.** Tom will need a number. Priya's own figures (overtime, credits) can anchor
   a target if she states one.

### Output checks

- Exactly one next question in the human finalization section.
- No quote used for both Decision Process and Paper Process.
- Every quote carries call date and timestamp; no seller quote appears as evidence.
- Score bars: ten characters, five per point (1 is `=====-----`, 1.5 is `=======---`).
- No characterization of Marcus's honesty or judgment.
- Output written to a private location or returned in the conversation; nothing in the
  public repository.

## Boundary Cases

1. **Bare agreement.** At 14:05 Priya says "Yeah" to a 12-month ROI. Metrics must stay at 1.
   A run that scores Metrics 1.5 on this quote fails.
2. **No timeline.** "As soon as possible" at 19:10 must not raise Decision Process or Paper
   Process.
3. **CRM as evidence.** If the run scores Champion 1.5 or higher because the CRM field says
   "Confirmed," it fails.
4. **Economic buyer engaged later.** Add a third call where Tom says, "The budget is there.
   If it pays back inside a year, I'll approve it." Economic Buyer moves to 2. Commit still
   fails on Champion, Decision Process, and Paper Process. The output must show that the
   category does not move on one element.
5. **Team gates supplied.** If `stage_exit_criteria` defines Commit as Economic Buyer 1 or
   higher and Paper Process 0.5 or higher, the team's gates replace the starting rules,
   and the output names which gates the team set.
6. **Missing speaker labels.** If Call 2 has no speaker labels, its quotes are not scored;
   Economic Buyer and Decision Process fall to 0, and the output lowers confidence and
   asks for a labeled transcript.
