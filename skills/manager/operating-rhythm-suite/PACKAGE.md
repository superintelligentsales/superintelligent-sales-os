# Operating Rhythm Suite

> Plans, checks and reinforces the manager's meeting cadence: weekly team meeting,
> weekly 1:1s, alternating deal review and skill workshop, bi-monthly forecast review
> and the quarterly business review.

Build status: meeting-rhythm-analysis is the first draft sub-skill. The other
catalogued sub-skills (weekly-team-meeting-prep, weekly-1on1-prep,
biweekly-deal-review, biweekly-skill-workshop, bi-monthly-forecast-review) are not
implemented by this package. This file records the shared principles; it does not
claim the whole suite is installed or accepted.

## Mirror Pattern

**Before:** meeting-rhythm-analysis measures the current calendar against the rhythm.
**During:** the prep sub-skills (not yet built) prepare each meeting.
**After:** action-tracking in the Coaching Suite holds the manager's commitments.

## Sub-skills in this Suite

- [meeting-rhythm-analysis](sub-skills/meeting-rhythm-analysis/SKILL.md): calendar
  audit against the Dana operating rhythm, with a 30-day plan that adds one rhythm at
  a time.

## Customization Required

manager.team_size, manager.direct_reports, manager.work_arrangement and
manager.cadence in /context/user-context.yaml. A set cadence value replaces the
default benchmark.

## Methodology Files Referenced

- docs/reference/dana-sales-management-brief-v2.md, section VI (The Operating Rhythm)
- docs/reference/methodology/60-min-1on1-structure.md
- docs/reference/methodology/bi-monthly-forecast-cadence.md

## Related Skills to Suggest

| After this sub-skill runs | Suggest | Trigger phrase |
|---|---|---|
| meeting-rhythm-analysis | five-step-coaching-conversation (when the first rhythm is the weekly 1:1) | "help me run a coaching conversation" |

## Operating Principles

- **Verified, not vibes.** Cite the calendar, a named default or the manager's own figure; omit unsupported claims.
- **The manager is the highest-leverage role and the most under-supported.** Outputs give managers time back, not add work.
- **Diagnose in groups, treat in 1:1s.** Keep individual development private.
- **Customization is the moat, not the methodology.** Apply the manager's own cadence when set.
