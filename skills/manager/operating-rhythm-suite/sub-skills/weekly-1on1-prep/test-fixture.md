# Test Fixture: weekly-1on1-prep

All people, companies and dates are fictional. No real client data is needed.

## Test Scenario
Manager M, at a fictional mid-size software company, has a 15-minute prep block before a weekly 1:1 with Rep C on Tuesday, November 10, 2026, and asks: "Prep my 1:1 with Rep C." Private prep only; no writes.

## Test Inputs
- Rep: Rep C. Meeting date: Tuesday, November 10, 2026.
- Last 1:1 tracker (from action-tracking): one development commitment, "ask an impact question after the first stated pain on every discovery call", due November 6, status UNKNOWN, no evidence supplied.
- Open pipeline (pasted CRM export):
  - Deal Alder: discovery, $18,000, created November 4, no impact recorded.
  - Deal Birch: proposal, $42,000, 41 days in stage, one contact (a manager-level buyer), no critical event recorded.
  - Deal Cedar: demo, $25,000, 9 days in stage, full SPICED notes, two director-level contacts.
  - Deal Dune: discovery, $9,000, 12 days in stage, notes complete for its stage.
- Activity (pasted): discovery calls held 3 this week, 7 last week. No target supplied.
- Call transcripts: Wednesday discovery call (rep moves to demo at minute 8 after the first stated pain); Thursday discovery call (impact question asked at minute 11).
- Rep pre-work: CRM updated November 8; no deal report; no self-assessment received; no deals flagged by the rep.
- Career goal: none recorded.

## /context/ State Assumed
manager.direct_reports: [Rep A, Rep B, Rep C, Rep D]
manager.cadence.one_on_one_frequency: weekly
manager.coaching.priority_skill: '[USER]' (placeholder, unknown)
manager.coaching.tone: '[USER]' (placeholder, unknown)
manager.forecasting.stage_exit_criteria: '[USER]' (placeholder, unknown)
tools.crm: '[USER]' (placeholder, unknown)

## Expected Output
- Header: Week 2 topic (pipeline management and qualification) from the day-of-month rule, stated; Month 2 of the quarter emphasis (mid-stage advancement); sources reached and not reached.
- Last week: the commitment shown UNKNOWN, not done and not missed, with the transcript evidence described as partial (used Thursday, not Wednesday) and a prompt to ask the rep's own read first.
- Performance facts: 3 and 7 discovery calls as raw counts with source; no target comparison; no explanation of the drop.
- Deals: exactly two or three. Alder (newest since last 1:1) and Birch (single-threaded, no critical event) are selected with reasons; Cedar and Dune are not selected because they show no gap. Each selected deal has one evidence question from the deal-killer table.
- Coaching focus: one hypothesis at the Skill level tied to the open commitment, citing Wednesday minute 8; the focus outranks the rotation topic, which is listed as secondary.
- Career: no weekly career block; flagged as due for the quarterly conversation (none recorded this quarter), with one question.
- Agenda: five blocks, 5/10/15/20/10 minutes, in order.
- Rep pre-work: CRM received, self-assessment not received, with the one-line reschedule-not-cancel protocol and the decision left to the manager.
- Follow-up summary draft: unsent, with blanks for agreements; no pre-written commitments.
- Stage exit check skipped and the reason stated, because stage_exit_criteria is a placeholder.
- Final line is the Dana closing offer line.

## Edge Case A: nothing connected and nothing pasted
Input: "Prep my 1:1 with Rep D on Thursday, November 19." No data and no connectors.
Expected: header with Week 3 topic and Month 2 emphasis, the five-block agenda, the pre-work checklist, and one combined request for the inputs that would fill the rest. No invented deals, numbers or quotes.

## Edge Case B: "Mark the commitment done and tell me if I should put Rep C on a plan"
Expected: the skill keeps the commitment UNKNOWN (offers MANAGER-REPORTED if the manager says it is done without evidence), declines to recommend a performance plan or any employment action, and keeps the prep behavioral and factual.

## Quality Criteria
- [ ] Output uses the skill's Output Format order (header through follow-up draft).
- [ ] All Inputs are addressed; missing ones are named as gaps, not filled.
- [ ] /context/ placeholders trigger the stated defaults (stage check skipped, default tone).
- [ ] Methodology applied: five blocks in order, rotation by day of month, deal selection reasons, TASK-level hypothesis.
- [ ] Two or three deals only, each with a reason and one evidence question.
- [ ] Silence is not completion: the commitment is never marked done or missed without a statement.
- [ ] No external write; drafts offered as text with a question.
- [ ] Related skills referenced (action-tracking, five-step-coaching-conversation, task-diagnostic), at most one suggested.
- [ ] Ends with the closing offer line.
