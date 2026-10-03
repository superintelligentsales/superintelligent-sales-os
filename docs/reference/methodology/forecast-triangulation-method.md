# Forecast Triangulation Method

> Methodology reference. Loaded by `manager/deal-confidence`, `manager/bi-monthly-forecast-review`, `manager/mid-month-checkpoint`, and `manager/qbr-prep`.

## When to use this

Whenever a sales manager needs to produce a defensible forecast — beginning of month, mid-month checkpoint, leadership reporting, QBR. The method applies regardless of segment, deal size, or sales motion.

## The core thesis

A single forecasting method is always wrong. Each method has a structural blind spot that another method covers. The honest forecast is not a number — it is a **band**, produced by triangulating three independent methods and reconciling the gaps.

Managers who report a single point estimate to leadership are either overconfident or hiding the uncertainty. Managers who report a band — with the spread named as the diagnostic — build forecast credibility over time.

## The three methods

### Method 1: Bottom-Up Rep Commit

Each rep submits a list of specific deals they expect to close in the period, with deal-level commitment. Sum these.

- **Strength:** Reflects the rep's customer-facing intelligence — the human signals only the rep has seen
- **Weakness:** Subject to behavioral distortion (sandbagging when comp is generous, happy ears when rep is behind)

### Method 2: Stage-Weighted Pipeline

Apply historical win rates to all opportunities expected to close in the period.

```
Forecast = Σ (Deal Amount × Stage-Specific Win Rate × Close-Date-In-Period Probability)
```

- **Strength:** Statistically grounded; removes individual rep bias
- **Weakness:** Treats every deal as average; doesn't reflect deal-specific signals

### Method 3: Historical Run-Rate

Trailing four-quarter average, adjusted for seasonality and trend.

- **Strength:** Incorporates patterns the rep doesn't see (historical macro)
- **Weakness:** Backward-looking; misses inflection points (new product, new comp plan, market shift)

## Worked example

A team with $5M quarterly quota produces:

| Method | Output |
|---|---|
| Bottom-up rep commit | $5.2M |
| Stage-weighted pipeline | $4.6M |
| Historical run-rate | $4.8M |

The triangulated forecast is the band: **$4.6M to $5.2M, with a midpoint of ~$4.85M**. The honest message to leadership: *"we expect $4.85M with $4.6M as worst case and $5.2M as best case."* The 12% spread is the genuine uncertainty.

## Reconciliation rules

| Spread between methods | Confidence | Action |
|---|---|---|
| < 10% | High | Report midpoint; minimal investigation needed |
| 10–20% | Medium | Investigate which method has the structural advantage for this period |
| > 20% | Low | The gap is the diagnostic — investigate root cause before reporting |

When methods diverge by 20%+, three pathologies are typically at work:

1. **Reps sandbagging** — rep commit < pipeline. Typical after a quota raise or in comp accelerator structures that reward exceeding commit
2. **Reps with happy ears** — rep commit > pipeline. Typical when reps are behind and inflating weak deals
3. **Stale pipeline** — pipeline > run-rate. Old deals padding the number; the next action is a pipeline scrub

## Establishing your baseline numbers

Without baseline data, the formulas are guesses dressed up as math. Before triangulating:

1. Pull last 4 quarters of closed deals from CRM
2. Calculate stage-to-stage conversion rates
3. Calculate average days-in-stage for won deals
4. Segment by deal size, segment, and rep where volume permits
5. Update quarterly

If CRM data is bad enough that this exercise can't run, **that is the first project**. Forecasting on top of fictional data is theater.

## Reference benchmarks

Stage-to-close win rates (industry typical — establish your own):

| Entry Stage | Probability of Eventual Close |
|---|---|
| Prospecting | ~27% |
| Discovery | ~28% |
| Solution | ~34% |
| Proposal / Negotiate | ~46% |
| Contract | ~88% |

Note the discontinuity between Proposal and Contract. A deal that has actually been contractually engaged is in a fundamentally different state than one merely under proposal. "In negotiation" forecasts often miss because reps confuse activity with commitment.

Maximum days in stage (industry typical — flag deals exceeding):

| Stage | Maximum Days | Action if Exceeded |
|---|---|---|
| Prospecting | 14 | Disqualify or escalate |
| Discovery | 21 | Inspect SPICED rigorously; consider closing as no-decision |
| Solution / Demo | 30 | Validate stakeholder engagement; check critical event |
| Proposal / Negotiate | 45 | Inspect pricing, procurement engagement |
| Contract | 30 | Escalate; identify legal/security blocker |

A deal sitting longer than maximum-days-in-stage without movement is, statistically, dying.

## Reporting the triangulation to leadership

Every forecast report includes all three estimates. When they agree, point that out. When they don't, name the gap and the reason. This builds trust by showing your work.

Forecast credibility curve:

- **Quarter 1:** Forecast within ±15% — earn permission to be heard
- **Quarters 2–3:** Forecast within ±10% — earn the benefit of the doubt
- **Quarter 4+:** Forecast within ±5% — earn resources, autonomy, and the next promotion

Forecast accuracy compounds reputationally. So does forecast inaccuracy.

## Related methodology

- `bi-monthly-forecast-cadence.md` — when to run this method (BOM 90-min review + Mid-Month 45-min checkpoint)
- `three-types-of-deal-reviews.md` — distinguishes forecast calls (this method) from pipeline scrubs and deep dive reviews
- `core-six-manager-responsibilities.md` — Opportunity Qualification (Core Six #1) is the upstream input that makes triangulation possible
- `spiced-deep-dive.md` — SPICED scoring is the per-deal evidence that drives Method 1 (rep commit) integrity

## Source attribution

Synthesized from "A Comprehensive Brief on My Ideas on Sales Management" Section VIII (Forecasting Methodology) and "Deep Dive: Forecasting & Operating Rhythm" Sections 1.2 (Sales Cycle Reality) and 1.3 (Triangulation Method). Authored by Victor Adefuye, April 2026.
