# Test Fixture: TASK Coaching Diagnostic

## Test Scenario

All names, records, counts, quotations, and files below are fictional test inputs,
not anonymized client material. A manager asks: "Fix Rep A's discovery skill."
The diagnostic must test that starting explanation rather than accept it.

## Test Inputs

- Scope: Rep A, new-logo seller, annual remaining plan. Expansion does not apply.
  Authorized private analysis only, using these supplied excerpts. No messages or CRM writes.
  Private output folder is supplied for a real run; this fixture's response stays in chat.
- P1, planning worksheet: remaining target 20 equal-unit bookings, no prior bookings
  included in that remainder; 160 qualified opportunities expected to decide in period;
  assumed planning win rate one in four; projected annual wins 40. No current coaching
  commitment or numeric improvement target has been agreed.
- B1, matched decided-history baseline: Rep A 24 wins and 96 losses, peer cohort 30 wins
  and 90 losses. Same prior annual period, new-logo motion, opportunity admission rules,
  segment, and equal deal units. No undecided opportunities included. No industry source.
- R1, supplied rubric: after a buyer describes a problem, validate a business consequence
  and attempt one quantified impact probe before proposing a demo. Mark each behavior
  observed, contradicted, or not observed in the supplied excerpt. No numeric rating scale.
- Call A, excerpt 04:10–04:30: Buyer: "The handoffs keep slipping." Rep: "Let me show you
  our workflow screen." No consequence validation or quantified impact probe appears
  in this excerpt. The rest of the call is unavailable.
- Call B, excerpt 07:20–07:45: Buyer: "Managers spend time correcting the records."
  Rep: "A demo will make this easier to understand." The same two behaviors are not
  observed here. The rest of the call is unavailable.
- K1, knowledge check: Rep A explains: "First I would ask what a delayed handoff affects.
  Then I would ask how often that happens and what time or cost it creates, and check
  my understanding with the buyer." This supports conceptual understanding, not execution.
- C1, CRM sample: impact field blank. No inference of ability or actual omission is allowed.
- No evidence about economic-buyer engagement or paper process is supplied. Do not invent it.

## /context/ State Assumed

The following is private fixture context, not an addition to the public schema:

```yaml
manager:
  team_segments: fictional equal-unit new-logo cohort
  top_challenges:
    - understanding discovery quality
  coaching:
    skill_rubric_path: fixture/R1.md
    performance_baseline_path: fixture/B1.md
    priority_skill: discovery
    success_measure: observe the R1 behaviors in the next authorized discovery
```

Treat R1 and B1 above as the supplied contents of those paths. All other context fields
are unanswered; none may be invented. Permission and current commitments are run inputs.

## Expected Output

Use all six Output Format sections. First calculate 40 projected wins versus 20 needed,
then compare measured 24/120 to 30/120. A descriptive five-point difference does not
establish significance or cause. Report a tentative execution hypothesis supported by
Call A and Call B; do not infer low ability from C1. K1 argues against a demonstrated
knowledge deficit. Quote exact excerpt identifiers. Give one practice-and-observation
action, proposed rather than accepted, and exactly one next question. No related-skill
suggestion is necessary because the hypothesis is not yet validated.

## Quality Criteria

- [ ] Six sections, exactly one question, one first action, human finalization explicit.
- [ ] Volume checked before conversion before skill; target and assumptions visible.
- [ ] No invented expansion requirement or recommendation for more leads.
- [ ] R1 and B1 applied; observed behavior described without invented numeric scores.
- [ ] Each TASK observation cites P1, B1, R1, Call A/B, K1, or C1 as applicable.
- [ ] Missing CRM data is not evidence of low ability; absent excerpts remain unknown.
- [ ] Skill distinguished from knowledge; causal confidence is tentative.
- [ ] No industry benchmark invented or causal inference from the five-point gap.
- [ ] No internal routing cut-offs printed in the response.
- [ ] Current commitments and permission limits respected; no writes or messages.

## Additional Boundary Cases

1. Replace P1 with projected 16 against 20: lead with the four-deal volume gap in the
   same channel; retain call observations but do not prescribe skill training first.
2. Replace P1 with projected 19 against 20: state "just short, still need more volume"
   and the one-deal gap before inspecting conversion.
3. A channel projects eight annual wins: one observable behavior, counts first, no
   numeric rate target. If new-logo target is four, inspect named fictional opportunities
   before general lead volume. No fractional weekly deal target.
4. Replace B1 with two wins and eight losses: quote counts, not a rep win-rate percentage;
   the original planning assumption remains an assumption, not measured history.
5. Remove R1 and calls, leaving C1: no skill diagnosis or zero score; one question for
   a relevant observed behavior or authorized call. Volume findings can still stand.
6. Tool access fails or a rubric path resolves outside approved scope: report the exact
   unavailable input, avoid unauthorized retrieval, and keep only supported conclusions.

## Verification Process

1. Read SKILL.md and the internal calibration reference, then run this scenario.
2. Preserve the actual output and compare it to each quality criterion above.
3. Record any failures, revise the skill, and rerun only affected cases.
4. Check the boundary cases separately from the main example.
5. A same-context execution is SELF-CHECKED. An independent reviewer must run the
   fixture against the exact PR head; a written expected output is not execution proof.
6. Record runtime/tool activation checks separately. A text execution does not establish
   that the skill loads or routes correctly in a different assistant environment.
