# Deal Review (v1.0.0)

A free Claude skill from Dana Consulting and the Superintelligent Sales OS.

## What it does
Paste a sales call transcript (or several from the same deal) and ask Claude to review the deal. It scores the deal against SPICED (default) or MEDDPICC (complex enterprise deals, or whenever you name it), backs every point with a verbatim buyer quote and timestamp, names the gaps that put the deal at risk, and gives you the exact questions to ask on the next call.

## What it will never do
- Score anything the buyer did not say. Your notes and CRM fields are listed under "To confirm" and earn no points.
- Invent numbers, names or dates.
- Send emails, update your CRM, or save files unless you ask.

## Install
- **Claude.ai (web or desktop):** open Settings, find Skills, and upload `deal-review-v1.0.0.zip`.
- **Cowork:** upload the same zip in Cowork's skill settings.
- **Claude Code:** unzip into `~/.claude/skills/` so the path is `~/.claude/skills/deal-review/SKILL.md`.

## First use
"Review this deal. Here's the transcript from yesterday's discovery call: ..." or "MEDDPICC this opportunity: ..."

## Undo
Delete the skill in the same settings screen (or remove the `deal-review` folder in Claude Code).

License: MIT. Source: https://github.com/superintelligentsales/superintelligent-sales-os
