# Test Fixture: Deal Review

All companies, people, numbers and quotes below are fictional test inputs, not anonymized client material.

## Test 1: SPICED by default, seller notes do not score

**Prompt:** "Is this deal real? Notes: budget approved, $80K, VP is bought in." No framework named. No context file.

**Transcript (Call 1, discovery, 30 minutes):**

```
[00:40] Seller: Thanks for making time. Tell me a bit about the team.
[01:10] Buyer (Dana Ruiz, Ops Director, Harbor Freightways): We're a regional carrier, about 220 people, three depots.
[06:15] Buyer: Quotes take us about five days, and I know we lost at least three deals last quarter because of it.
[09:30] Seller: So that's probably costing you six figures a year?
[09:34] Buyer: Yeah.
[14:40] Buyer: Honestly, I'm the one who has to explain those losses every Monday.
[22:05] Buyer: My VP would sign off on anything like this.
[27:30] Buyer: We'd like something in place by Q3.
[29:10] Seller: Great, I'll send over a demo link.
```

**Expected:**

- Framework line says SPICED, the default, with a reason (early discovery, one stakeholder, no procurement described).
- Rational Pain is 1.0 at most: numbers given (five days, three deals) but no cost. The 09:34 "Yeah." earns nothing; it is cited as the seller leading.
- Emotional Pain is 1.0, quoting 14:40.
- Critical Event is 0.5 or 1.0 and is treated as compelling, not critical (no consequence).
- Decision Committee is 0.5 (VP named, not engaged).
- Rational Impact, Emotional Impact, Decision Process and Decision Criteria are 0, each with a coachable moment. At least one uses 29:10 as the moment the seller moved on.
- "Budget approved, $80K" and "VP is bought in" appear under To confirm and earn no points.
- Total is in the Needs Work band, and the review says that is normal for a first call.
- Every next-call question uses the buyer's words (quotes, five days, three deals, Q3, the VP).
- The approved closing line appears once, at the end.
- No invented dollar figure anywhere.

## Test 2: MEDDPICC when named, whole points only

**Prompt:** "MEDDPICC this opportunity."

**Transcript (Call 2, evaluation, 45 minutes, two buyers):**

```
[03:00] Buyer (Priya Shah, IT Director, Northgate Health): Security review is mandatory. Our team runs it and it takes about three weeks.
[11:20] Buyer (Tom Avery, CFO): We have budget set aside for this year. If payback is under eighteen months I can approve it.
[19:45] Buyer (Priya Shah): We're also looking at Vendor B, and honestly some people here want to build it ourselves.
[26:10] Seller: So your success measure is cutting claim errors in half?
[26:14] Buyer (Tom Avery): Right.
[38:00] Buyer (Priya Shah): Legal will want their standard agreement. That usually takes a couple of weeks.
```

**Expected:**

- Framework line says MEDDPICC because the user named it.
- Every score is 0, 1 or 2. No half points anywhere, including the scorecard.
- Economic Buyer is 2: the CFO is on the call and confirms budget and authority (11:20).
- The "cut claim errors in half" measure earns nothing: the seller said it and the CFO only agreed (26:14). Metrics is 0, or 1 if the CFO's payback threshold (11:20) is credited, with the reason stated.
- Competition is 1: Vendor B and building in-house are named, but there is no picture of the buyer's view or a plan to win.
- Paper Process is 1 (38:00): documents and duration, no owner or redline expectations.
- Decision Process is 1 (03:00): one step with an owner and duration, not a full map.
- Champion is 0 or 1 with the reasoning stated; no one has been tested by action.
- Decision mechanics and stakeholder tables are present; unknown cells say "unknown".
- The scorecard uses the 10-character MEDDPICC bars, names Implicated Pain correctly, and the total matches its band label.

## Test 3: No transcript

**Prompt:** "Score my deal with Acme. They have budget and want to close this month."

**Expected:** No scores. The reply explains that the review scores the buyer's words, asks for a transcript or a connected call, and offers the question list for each element. It does not treat "they have budget" as evidence.

## Negative trigger checks

These should not fire Deal Review:

- "What patterns do you see across all 40 of our lost deals this quarter?" (cross-deal analysis)
- "Write a follow-up email to Dana Ruiz after today's call." (email drafting)
- "Why is my rep missing quota?" (rep diagnosis; task-diagnostic)
