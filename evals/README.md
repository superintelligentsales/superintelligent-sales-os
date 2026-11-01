# Overnight Improvement Loop

Instructions for an automated loop that tests and improves every skill in this repository
before launch. It follows the autoresearch method: run the skill for real, score the
output, make one small change, keep it only if the score improves, and repeat.

## What gets scored

Every skill is scored against `evals/skill-checklist.md` in four groups:

- **Output:** does the skill reproduce its fixture's expected results, every boundary
  case, and the same answer on three runs?
- **Evidence and safety:** are claims traceable, buyer evidence only, no outside numbers,
  no labels on people, defaults labeled, no writes or sends?
- **Methodology:** does the skill match its methodology files and its suite's principles?
- **Structure:** frontmatter, references, sections, length, plain language.

Each skill's `eval/checklist.md` points to that file and adds any skill-specific notes.

## Order

Run skills in this order. Earlier skills get rounds first each night.

1. `manager/forecast-suite/sub-skills/forecast-triangulation`
2. `manager/forecast-suite/sub-skills/pipeline-coverage-analysis`
3. `manager/forecast-suite/sub-skills/deal-confidence`
4. `manager/forecast-suite/sub-skills/meddpicc-qualifier`
5. `manager/forecast-suite/sub-skills/spiced-scoring`
6. `rep/customization-onboarding`
7. `manager/coaching-suite/sub-skills/task-diagnostic`, then the other five coaching skills
8. `manager/operating-rhythm-suite/sub-skills/meeting-rhythm-analysis`

## Rules

1. **Run the skill in Claude.** The skills are written for Claude. A run by another model
   does not count as a test of the skill.
2. **The fixture is the test case.** Fixtures are fictional on purpose, because this
   repository is public. Any run on real deal or client data happens in a private
   location, and its inputs, outputs, and logs never enter this repository.
3. **Read-only files:** `evals/skill-checklist.md`, every `test-fixture.md`, every
   `PACKAGE.md`, everything under `docs/reference/`, `context/user-context.yaml`, and
   `.claude-plugin/`.
4. **Editable files:** the wording inside a skill's `SKILL.md` sections and its
   `references/` files. Section headings, section order, and the frontmatter `name` stay
   fixed.
5. **One change, one file, per round.** Re-run the full checklist after every change. Keep
   only if the total rises, the targeted test passes, and nothing that passed now fails.
   Otherwise revert.
6. **Do not game the checklist.** If a change passes a test but makes the output worse for
   a sales manager, revert it.
7. **Methodology conflicts go to the author.** When M1 fails, do not edit the skill or the
   methodology file to make them match. Quote both texts in the log and move on.
8. **Stop a skill** when every Output, Evidence and Safety, and Structure test passes on
   three consecutive runs, or after three rounds in a row with no improvement. Log what
   is left.
9. **Limit each night to six rounds per skill.**

## Where work goes

- Branch each night from the launch branch (or from `main` once the launch branch is
  merged) as `evals/night-YYYY-MM-DD`.
- Commit kept changes with one commit per round, naming the skill and the test it fixed.
- Write the night's results to `evals/results/YYYY-MM-DD.md`.
- Open one pull request per night for review. Never push to `main` and never merge.

## Night report format

`evals/results/YYYY-MM-DD.md` starts with one table, one row per skill:

| Skill | Start score | End score | Rounds | Kept | Status | Needs the author |
|---|---|---|---|---|---|---|

Status is one of: ship-ready (passed three consecutive runs), improving, plateaued, or not
run. Below the table, list each kept change (file, before, after, test fixed) and each
item that needs the author, such as a methodology conflict or a fixture that looks wrong.
A fixture that looks wrong is reported, never edited.

## Known items at the start

- `spiced-scoring` will fail M1: the skill scores nine elements from 0 to 2, while
  `docs/reference/methodology/deal-inspection-and-qualification.md` scores five elements
  from 1 to 5. Awaiting the author's decision.
- `customization-onboarding` fails S3: it has no Error Handling section.
- `development-plan-generator` fails S5: one en dash.
- `meeting-rhythm-analysis` fails S4: about 3,900 words against a 3,000 maximum.
