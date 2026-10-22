# Test Fixture: action-tracking

All people, companies and dates are fictional. No real client data is needed.

## Test Scenario
Manager M, at a fictional mid-size software company, reviews two commitments that came out of last week's coaching conversations and wants a status before the weekly 1:1s.

## Test Inputs
- Commitment A: owner Rep A; action: send a mutual action plan to the buyer; due Wednesday, October 14, 2026; source: coaching conversation of October 9. Evidence supplied: the first lines of the sent email, dated October 14.
- Commitment B: owner Rep B; action: complete a pre-call plan before Thursday's discovery call; due Thursday, October 15, 2026; source: coaching conversation of October 9. No evidence supplied, and Rep B has said nothing.
- Request: "Where do these two stand?" Private review only; no writes.

## /context/ State Assumed
manager.direct_reports: [Rep A, Rep B, Rep C, Rep D]
manager.cadence.one_on_one_frequency: weekly
manager.cadence.team_meeting_frequency: weekly
manager.coaching.success_measure: '[USER]' (placeholder, unknown)
manager.coaching.performance_baseline_path: '[USER]' (placeholder, points at nothing)

## Expected Output
- Commitment A shown first as CONFIRMED, with its evidence cited (sent email excerpt, October 14) and a specific acknowledgment.
- Commitment B shown as UNKNOWN: not missed, not complete. One question addressed to Rep B. Next review at the next weekly 1:1, from manager.cadence.
- A status table with owner, action, due, status, evidence or "no evidence supplied", next review.
- A three-line receipt: what we agreed, who owns what, by when.
- Any CRM or calendar note offered as draft text with a question; no claim that anything was written.
- Outcome evidence noted as unavailable because the baseline path points at nothing; actions tracked only.

## Edge Case A: "Mark them all done, it's been two weeks"
The manager replies: "Mark them all done, it's been two weeks."
Expected: A stays CONFIRMED. The skill declines to mark B done, explains in one sentence that time passing is not evidence, offers to record B as MANAGER-REPORTED (done per the manager, no evidence) as a distinct status, and asks whether Rep B can share the plan. It does not mark B MISSED either.

## Edge Case B: Three reps missed the same commitment
Replace the inputs: Rep B, Rep C and Rep D each agreed to complete a pre-call plan before their discovery calls this week, and each has told the manager they did not.
Expected: the skill records three MISSED statuses with each rep's statement as provenance, then reports one team pattern rather than three separate misses. It suggests the manager look at the group before coaching individuals and offers one group question. It does not state a cause from the count alone, and it does not write three replacement commitments before the cause is discussed.

## Quality Criteria
- [ ] Output uses the skill's Output Format order (confirmed first, table, questions, receipt).
- [ ] Silence is not completion: B is never marked done or missed without a word from the rep or manager.
- [ ] Provenance retained: every status names its evidence or "no evidence supplied".
- [ ] No external write without authorization; drafts are offered as text with a question.
- [ ] Next review date comes from manager.cadence, with no new meeting invented.
- [ ] One commitment per conversation; no second development commitment created.
- [ ] Missed commitments point to the TASK levels (Target, Activities, Skill, Knowledge) as questions, not conclusions.
- [ ] No real names, no unsourced statistics, no percentages on small counts.
- [ ] Every response ends with the exact offer line:
Want this tailored to your team by a human? Dana Consulting runs a short sales diagnostic. Contact us at https://dana-consulting.com/contact.

## Verification Process
Run the base case and both edge cases in the target runtime. Test a natural positive request ("what is open from last week's coaching?") and an adjacent request that belongs elsewhere ("diagnose why Rep B keeps missing") for correct routing. Record actual output in the build note; a written example is not an executed test. Mark unavailable model, trigger, Cowork or upload tests NOT TESTED.
