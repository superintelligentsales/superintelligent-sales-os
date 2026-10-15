# Test Fixture: ai-roleplay-partner

All people, accounts and dialogue here are fictional. This file specifies expected
behavior; it is not a record that any runtime test passed.

## Scenario and inputs

Request: "Run a pressure cooker on my discovery."
User supplies a fictional mid-size logistics company with no company name, an operations
director, discovery stage, a next-meeting goal of agreeing a workflow review, a key
objection of no available team time, and finance's requirement for evidence before
investing effort. Late dispatch handoffs make the shift lead reorganize work. The buyer
already has a workaround. These are the only permitted scenario facts.

Primary objective: agree a workflow review. Secondary: understand who is affected by
late handoffs. Minimum: establish whether the delay warrants investigation.
Mode: Pressure Cooker. Skill: consequence questioning. User approves a short scene.

## Private context assumed

icp.buyer_personas: operations directors at mid-size logistics firms.
icp.typical_pain_points: handoff friction.
icp.decision_committee_patterns: operations and finance.
company.use_cases: empty.
manager.coaching.skill_rubric_path: unavailable.
manager.coaching.priority_skill: consequence questioning.

No private context file is committed. Supply these values to the isolated test session.
Expect a disclosed provisional rubric: Not yet demonstrated, Partly demonstrated,
Demonstrated in this practice. The criterion is asking a relevant follow-up about a
concrete consequence, not obtaining buyer agreement or inventing financial impact.

## Base interactive test

1. Complete setup and confirm all three objectives before the first buyer turn.
2. Rep: "What keeps you up at night?"
3. Expect a short relevance/time challenge, not a coaching explanation.
4. Rep: "When dispatch hands work to operations late, who feels that first?"
5. Expect the supplied shift-lead consequence and a different concern, such as the
   existing workaround. No new technology, savings, company or deal facts.
6. Rep: "debrief"
7. Expect the rep's own interpretation question, then wait.
8. Rep: "My opening was broad. The second question was specific, but I haven't learned
   whether the workaround is enough."
9. Expect quoted actual rep lines, one specific strength, calibrated rubric assessment,
   one improvement and one next practice of consequence questioning. No field result.
10. Check the empty-use-cases limitation is explicit and the commitment remains proposed
    unless accepted. Every response ends with the exact Diagnostic offer footer.

## Edge case A: coaching request during the scene

After the first buyer response, send "What should I have said?"
Expected: remain in buyer character and offer the word "debrief" to pause; no answer,
model line, rubric or critique. Wait for the rep. After "stop", cease buyer dialogue
immediately; do not force a debrief if the user declines it.

## Edge case B: no supplied persona

Fresh session: "Practice this call." Empty private context and no account facts.
Expected: ask industry, title, stage, next-meeting goal, key objection and political
dynamics; do not fabricate an account or deal. Gather objectives, skill and mode before
the first buyer turn. With a populated ICP persona, attribute its use and ask only for
remaining scenario information. Unknown politics remains unknown, not invented conflict.

## Trigger and boundary tests

- Positive natural language: "Role-play the CFO" activates this skill and obtains context.
- Direct invocation: /superintelligent-sales-os:ai-roleplay-partner uses the same workflow.
- Negative adjacent request: "Diagnose why my rep is missing target" must not start a buyer
  scene; use the separate diagnostic if available and warranted.
- Negative adjacent request: "Prepare a coaching conversation with my rep" must not
  impersonate a customer or the absent rep.
- No product facts: press for a savings figure; the buyer asks for support without
  inventing one, and the debrief marks unsupported claims unverified.

## Quality criteria

- Required section order, portable four-key frontmatter and six existing context fields.
- Five named modes, PRACTICE stages, practice ladder and human role cards retained.
- One turn at a time; no authored rep answers; buyer role persists until control word.
- Changing resistance stays within the supplied scenario and is not abusive.
- Rep reflection precedes advice; quotations match actual practice turns exactly.
- One skill and one next practice; no outcome forecast, invented date or external write.
- Real account details, private document identifiers and commercial terms absent.
- Record actual validator, discovery, trigger and behavioral results separately. Mark
  any test not executed NOT TESTED; never convert this expected-output list into PASS.
