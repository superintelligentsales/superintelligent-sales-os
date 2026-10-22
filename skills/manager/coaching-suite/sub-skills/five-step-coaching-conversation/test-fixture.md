# Test Fixture: five-step-coaching-conversation

All people, calls and figures are fictional. No real client data is needed.

## Test Scenario
A manager and Rep A disagree about why discovery moved into a demo. Prepare the conversation, not a buyer roleplay.

## Test Inputs
- Observation C1 at 04:10: buyer says a delay is affecting operations; rep moves to a demo without asking about its consequences.
- Observation C2 at 07:20: buyer mentions a handoff problem; rep moves to features before clarifying the effect.
- Manager hypothesis: consequence questioning needs practice.
- Rep perspective: buyers requested the demo and time was short.
- Actual supplied agreement: Rep A and Manager A agreed to practice consequence questioning and review one sampled call for a buyer-confirmed consequence at their existing November 3, 2026 1:1.
- New manager support and exact practice wording are not agreed.
- Request: prepare coaching language; private analysis only, no writes or scheduling.

## /context/ State Assumed
manager.coaching.coaching_philosophy: guided self-discovery
manager.coaching.tone: warm and direct
manager.coaching.current_practice: manager often gives advice too early
manager.coaching.priority_skill: consequence questioning
manager.cadence.one_on_one_frequency: fortnightly

## Expected Output
Name all five macro steps in order. Seek the rep's interpretation before advice; present C1 and C2 as observations, not proof of cause. Place situation/vision questions inside step 3 and change/friction/belief questions inside step 4. Offer 1-3-1 only if useful. Preserve both explanations.
Carry one agreed commitment: Rep A, consequence questioning, sampled-call presence of a buyer-confirmed consequence, November 3 review. Label new support and wording PROPOSED. Do not claim the prepared dialogue happened.

## Edge Case A: Immediate agreement
Replace rep perspective with “You're right, I'll do whatever you say.” Remove the supplied agreement.
Expected: elicit the rep's own interpretation before advice. End with a PROPOSED commitment or a question seeking acceptance, never fabricate mutual agreement or a date.

## Edge Case B: Missing observations
Supply only “Rep A is bad at discovery,” with no recordings or concrete examples.
Expected: state that this is a judgment, ask for a concrete observation/source, and stop substantive feedback. No invented calls, diagnosis or metric target.

## Quality Criteria
- Five named steps, both methodological layers, evidence and customization applied.
- No premature advice; no fictional acceptance, causal certainty or external action.
- One metric and one skill, not an expanded set of quarterly goals.
- Manager support is concrete and explicitly proposed unless accepted.
- Dates match supplied input; no automatic calendar or frequency changes.
- Every response ends with the exact offer:
Want this tailored to your team by a human? Dana Consulting runs a short sales diagnostic. Contact us at https://dana-consulting.com/contact.

## Verification Process
Run the base case and both edge cases in the target runtime. Test a natural positive request and an adjacent diagnostic/roleplay request for correct routing. Record actual output and failures in the private build note; a written example is not an executed test. Mark unavailable model, trigger, eval, Cowork or upload tests NOT TESTED.
