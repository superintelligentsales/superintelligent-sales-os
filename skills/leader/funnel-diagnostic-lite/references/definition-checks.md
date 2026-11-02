# Definition Checks

How to tell a definition problem from a performance problem before diagnosing anything.

## Contents
- Why definitions come first
- Adjacent-stage patterns
- How definitions move each rate
- Questions to ask the user

---

## Why definitions come first

Teams drift away from standard stage definitions over time: old definitions nobody revisited, CRM settings that force whatever the system supports, and marketing and sales using different bars for "qualified". If a team's MQL-to-SQL rate looks low because every content download counts as an MQL, coaching reps to "convert more MQLs" is the wrong fix. The number is misleading, not the reps.

## Adjacent-stage patterns

| If you see | Check for |
|---|---|
| Lead to MQL very high and MQL to SQL very low | MQL bar too low: leads advance easily, then fail sales review |
| Lead to MQL very low and MQL to SQL very high | MQL bar too high: marketing is doing sales qualification, or there is no real MQL stage |
| MQL to SQL normal but SQL to Opportunity very low | SQL criteria too loose, or SQL and opportunity overlap |
| SQL to Opportunity very high and win rate very low | Opportunities created too early: pipeline inflation |
| Win rate very high and SQL to Opportunity very low | Opportunities created too late: only near-certain deals enter the pipeline |
| Every rate below benchmark | Benchmark and team may use different stage definitions |
| Every rate above benchmark | Stricter definitions: fewer, better entries |

**The adjacent-stage test.** When one stage looks wrong, look at the stage before and after it:

- Preceding stage unusually high, this stage low: the handoff definition is too loose.
- Preceding stage unusually low, this stage high: the handoff definition is too strict.
- Both neighbours normal: the issue is more likely operational.

"Very high" and "very low" mean outside the cited benchmark range for that stage, or outside the sanity ranges in `benchmark-research.md` when no benchmark was found.

## How definitions move each rate

**MQL**

| Approach | Lead to MQL | MQL to SQL |
|---|---|---|
| Any engagement (download, webinar, page visit) | Very high | Very low |
| Fit only (title and company size) | Moderate | Moderate |
| Fit plus behaviour with a score threshold | Moderate to high | Moderate |
| Intent signals plus engagement | Low to moderate | High |
| Reviewed by a person (SDR) before MQL | Low | Very high |

**SQL**

| Approach | MQL to SQL | SQL to Opportunity |
|---|---|---|
| Rep agrees to work it, few criteria | Higher | Lower |
| Qualifying conversation held | Moderate | Moderate |
| Budget or authority partly confirmed | Lower | Higher |
| Full MEDDIC-style qualification | Very low | Very high |

**Opportunity**

| Approach | SQL to Opportunity | Win rate |
|---|---|---|
| Meeting or demo booked | Higher | Lower |
| Discovery done, pain confirmed | Moderate | Moderate |
| Several stakeholders engaged | Lower | Higher |
| Proposal sent, or budget and timeline confirmed | Very low | Very high |

**Qualification method.** BANT tends to lift MQL to SQL but makes later stages less predictable. MEDDIC or MEDDPICC lowers MQL to SQL on purpose and lifts later stages. SPICED and other pain-led methods tend to strengthen SQL to Opportunity and win rate. No method at all usually shows up as wide differences between reps.

## Questions to ask the user

1. What makes a lead an MQL? Is it written down and applied the same way by everyone?
2. Is there an agreed follow-up time between marketing and sales for new MQLs?
3. What makes something an SQL: a conversation, a checkbox, or a score?
4. What creates an opportunity: a meeting, a demo, a proposal?
5. Are the exit criteria for each stage written down, and does the CRM enforce them?
6. When were the definitions last reviewed?

If the user cannot answer most of these, "stage definitions are unclear" is a finding in its own right.
