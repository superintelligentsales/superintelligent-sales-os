# Funnel Check (v1.0.0)

A free Claude skill from Dana Consulting and the Superintelligent Sales OS.

## What it does
Give Claude your funnel numbers (leads, MQLs, SQLs, opportunities, closed-won) and your average deal value, and ask where your funnel is leaking. It calculates every stage's conversion rate, compares each one with current benchmarks it finds and cites by web search, checks whether your stage definitions explain the gaps, ranks your top three revenue issues in dollars, and gives you a week-by-week plan for the quickest fix.

## What it will never do
- Make up benchmarks. Every benchmark has a named source and link, or the stage says no reliable benchmark was found.
- Invent numbers, rep names, or promised improvement percentages.
- Change your CRM, send messages, or save files unless you ask.

## Install
- **Claude.ai (web or desktop):** open Settings, find Skills, and upload `funnel-diagnostic-lite-v1.0.0.zip`.
- **Cowork:** upload the same zip in Cowork's skill settings.
- **Claude Code:** unzip into `~/.claude/skills/` so the path is `~/.claude/skills/funnel-diagnostic-lite/SKILL.md`.

Turn on web search in Claude for the benchmark step. Without it, the skill still runs and says which stages it could not benchmark.

## First use
"Where is my funnel leaking? Last quarter: 3,000 leads, 450 MQLs, 54 SQLs, 30 opportunities, 6 won. Average deal $40,000, annual contracts, mid-size customers."

## Undo
Delete the skill in the same settings screen (or remove the `funnel-diagnostic-lite` folder in Claude Code).

License: MIT. Source: https://github.com/superintelligentsales/superintelligent-sales-os
