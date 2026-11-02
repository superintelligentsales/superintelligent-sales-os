# Test Fixture: Funnel Check

All companies and numbers below are fictional test inputs.

## Test 1: Definition issue at MQL, dollar math, cited benchmarks

**Prompt:** "Where is my funnel leaking? B2B software, mid-size customers, annual contracts, average first-year deal $40,000, about a 60-day cycle, 6 AEs. Last quarter: 3,000 leads, 450 MQLs, 54 SQLs, 30 opportunities, 6 closed-won. An MQL is anyone who downloads content. Most leads are inbound."

**Expected:**

- Conversion table shows 15%, 12%, 56%, 20% with the arithmetic.
- Benchmarks come from web search in the session with named sources, years, and links, or the stage says "no reliable benchmark found". No uncited benchmark figure anywhere.
- The definition check flags the high Lead-to-MQL and low MQL-to-SQL pattern plus the "any download" definition as a likely MQL definition issue, before any performance diagnosis.
- Value of one MQL-to-SQL point is about $20,000 a quarter, with the formula shown (450 x 1% x 56% x 20% x $40,000).
- Top three issues are ranked by dollar impact and each has a dollar line or says which number is missing.
- The deep dive has two root causes labeled likely, three fixes, a three-week plan, and a number to watch. No promised uplift percentage.
- The approved closing line appears once, at the end. No "Pro version" upsell.

## Test 2: Missing inputs

**Prompt:** "Our win rate is 18%. Is that bad?"

**Expected:** The skill explains that one rate cannot show where a funnel leaks, asks for adjacent stages, deal value, and context (five questions at most), and may give cited win-rate benchmarks for context. It does not invent the rest of the funnel or a dollar figure.

## Test 3: Rates that do not multiply out

**Prompt:** "1,000 leads, MQL rate 10%, SQL rate 30%, 40 SQLs, win rate 25%."

**Expected:** The skill notes that 1,000 x 10% x 30% = 30 SQLs, not 40, and asks which figure is right before analyzing.

## Negative trigger checks

These should not fire Funnel Check:

- "Score this discovery call transcript against SPICED." (single deal; deal-review)
- "Why is Jordan missing quota every month?" (rep diagnosis; task-diagnostic)
- "Write a LinkedIn post about lead scoring." (content writing)
