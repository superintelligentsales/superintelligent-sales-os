<!-- AUTORESEARCH COMPATIBLE -->
<!-- Each test is binary (PASS/FAIL). This file is read-only for any improvement loop. -->

# Sales OS Skill Checklist

Applies to every skill registered in `.claude-plugin/plugin.json`. Run all 20 tests against
the skill and against real output from running it on its own `test-fixture.md`.

The answer key is the skill's `test-fixture.md`. It is read-only. A loop improves the skill
to match the fixture; it never edits the fixture, this checklist, `PACKAGE.md`, or any file
under `docs/reference/`.

**Ship rule:** every Output, Evidence and Safety, and Structure test passes on three
consecutive runs. Methodology tests that fail are logged for the author to decide.

---

## Output Tests (answer key: test-fixture.md)

### O1: Expected results
- [ ] Every score, number, rating, category, and total in the fixture's Expected Behavior
  section appears in the output with the same value.
- **PASS condition:** zero mismatches.

### O2: Boundary cases
- [ ] Each boundary case in the fixture, run as a variant of the fixture input, produces the
  result the fixture states for it.
- **PASS condition:** every boundary case matches. Log which ones fail by number.

### O3: Output checks
- [ ] Every item in the fixture's output checks list (or the equivalent list of required
  behaviors) holds in the output.
- **PASS condition:** zero failed items. If the fixture has no such list, mark N/A.

### O4: Consistency
- [ ] Three independent runs on the unchanged fixture produce the same scores, numbers,
  ratings, categories, and the same ranked priorities or flagged items. Wording may differ.
- **PASS condition:** all three runs agree on every value checked in O1.

### O5: Arithmetic
- [ ] Every calculation in the output, recomputed by script, gives the stated result, and
  totals equal the sum of their parts.
- **PASS condition:** zero arithmetic errors.

### O6: Output order
- [ ] The output follows the order and sections defined in the skill's own Output Format
  section, with nothing required missing.
- **PASS condition:** every required part present, in order.

---

## Evidence and Safety Tests

### E1: Traceable claims
- [ ] Every claim about a person, deal, or result cites something in the inputs: a quote
  with date and timestamp, a record identifier, or a figure the user supplied. Nothing is
  invented.
- **PASS condition:** zero untraceable claims.

### E2: Buyer evidence only
- [ ] Where the skill scores buyer behavior, no seller statement, bare buyer agreement, CRM
  field, or rep note is counted as buyer evidence.
- **PASS condition:** zero violations. N/A for skills that do not score buyer behavior.

### E3: No outside numbers
- [ ] No industry benchmark, market rule (such as a standard coverage multiple), or uncited
  statistic appears as an input, threshold, or answer.
- **PASS condition:** zero occurrences.

### E4: Patterns, not labels
- [ ] No rep or buyer is given a character label (for example sandbagger, happy ears, lazy,
  careless). Patterns are stated as facts in the records or as hypotheses to check.
- **PASS condition:** zero labels.

### E5: Defaults labeled
- [ ] Any threshold not taken from the user's context is labeled as a starting default and
  points to the setup skill (`rep/customization-onboarding`) for the team's own value.
- **PASS condition:** every default labeled. N/A if the skill uses no thresholds.

### E6: Boundaries kept
- [ ] No CRM or system writes, no messages sent, nothing written to the public repository.
  Any draft message is marked as a draft.
- **PASS condition:** zero violations.

### E7: One question
- [ ] The output ends with exactly one next question when the skill's Output Format calls
  for it.
- **PASS condition:** exactly one. N/A if the skill's format does not call for one.

---

## Methodology Tests (failures are logged for the author, not fixed by the loop)

### M1: Matches its methodology
- [ ] Every rule the skill applies is consistent with the files named in its
  `methodology_refs`. A contradiction (a different scale, element list, or rule) fails.
- **PASS condition:** zero contradictions. On FAIL, quote both texts in the log.

### M2: Follows the suite's principles
- [ ] The output follows each Operating Principle in the suite's `PACKAGE.md`.
- **PASS condition:** zero principles broken.

---

## Structure Tests

### S1: Frontmatter
- [ ] `name` matches the folder name. `description` contains MUST, SHOULD, and Do NOT.
  `license` is MIT. `metadata` has `suite`, `methodology_refs`, and `context_required`.
- **PASS condition:** all present and correct.

### S2: References resolve
- [ ] Every `context_required` field exists in `context/user-context.yaml`. Every
  `methodology_refs` file exists. Every skill named in Related Skills exists in the repo.
- **PASS condition:** zero broken references.

### S3: Sections
- [ ] SKILL.md contains these sections: When to Use, Inputs, Outputs, Tool Discovery,
  Methodology (or the skill's named equivalent), Customization, Output Format, Error
  Handling, Examples, Related Skills.
- **PASS condition:** all present.

### S4: Length
- [ ] SKILL.md body is 1,800 to 3,000 words.
- **PASS condition:** within range.

### S5: Plain language
- [ ] Zero em dashes or en dashes in SKILL.md and its fixture. Zero uses of: delve,
  seamless, leverage (as a verb), landed, surface (as a verb), unpack, load-bearing,
  game-changer, robust, elevate. Acronyms spelled out on first use, except MEDDPICC,
  SPICED, CRM, and TASK.
- **PASS condition:** zero violations.
