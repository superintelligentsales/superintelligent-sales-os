# Superintelligent Sales OS

Free, open-source Claude skills that help sales managers coach from evidence instead of instinct.

Most coaching starts with whatever felt wrong on the last call a manager heard. Sometimes that is the right place to start. Often the rep had a volume problem, not a skill problem, and weeks of call coaching change nothing. The Sales OS puts a method under that decision: check the evidence, find the real constraint, coach one thing, and track whether it happened.

Every skill follows one rule: **verified, not vibes.** When the evidence isn't there, the skill asks for it instead of guessing.

## What's in the first release

Thirteen skills, built for B2B sales managers and the reps they coach.

| Skill | What it does | Try asking |
|---|---|---|
| **Customization onboarding** | Learns your company, buyers, sales process and team before anything else runs. Run it first. | "Set up the OS" |
| **TASK diagnostic** | Checks a rep's Target, Activities, Skill and Knowledge so you look at volume before you coach conversion. | "Diagnose this rep" |
| **Development plan generator** | Turns an accepted diagnosis into a 30-60-90 day plan focused on one skill. | "Build this rep's development plan" |
| **Five-step coaching conversation** | Prepares an evidence-based coaching conversation that ends in a commitment the rep owns. | "Help me coach this rep" |
| **AI roleplay partner** | Plays the buyer so a rep can practice before the call that matters, then debriefs against evidence. | "Role-play the CFO" |
| **Action tracking** | Records coaching commitments and keeps what was agreed separate from what was actually done. | "What is open from last week's coaching?" |
| **Coaching orchestrator** | Looks across your team and picks each rep's next coaching action. | "What should I coach across my team?" |
| **Meeting rhythm analysis** | Reads your calendar and shows where your week goes, how 1:1 time is spread across reps, and which meetings are missing. | "Analyze my calendar" |
| **Pipeline coverage analysis** | Checks whether there is enough pipeline for this period and the next, using your own win rate, and says how much to create by when. | "Do we have enough pipeline?" |
| **Deal confidence** | Rates each commit and best-case deal on buyer evidence and deal activity, and lists the deals to inspect first. | "Which commit deals should I worry about?" |
| **SPICED scoring** | Scores one deal on what the buyer said about Situation, Pain, Impact, Critical Event and Decision, and tests its forecast category. | "Score this deal on SPICED" |
| **MEDDPICC qualifier** | Scores one complex enterprise deal on the eight MEDDPICC elements from buyer quotes, and tests its forecast category. | "Is this deal really commit?" |
| **Forecast triangulation** | Compares rep commit, stage-weighted pipeline and run-rate to give a forecast range instead of one number. | "What's my forecast?" |

## Install

### Claude Code

You need [Claude Code](https://code.claude.com/docs/en/overview). In a Claude Code session, run these two commands:

```
/plugin marketplace add superintelligentsales/superintelligent-sales-os
/plugin install superintelligent-sales-os@superintelligent-sales
```

Or run the same steps from your terminal:

```bash
claude plugin marketplace add superintelligentsales/superintelligent-sales-os
claude plugin install superintelligent-sales-os@superintelligent-sales
```

To check that it worked, run `claude plugin details superintelligent-sales-os`. The list should show `Skills (13)`.

### Claude.ai and Claude Cowork

Steps for the Claude apps are being tested now and will be posted here. If you want them as soon as they are ready, click **Watch** at the top of this page or open an issue.

## Quick start

1. **Run onboarding.** Ask "Set up the OS." The onboarding skill asks about your company, buyers, sales process and team one section at a time, shows you what it will save, and writes your answers to `context/user-context.yaml`. Every other skill reads that file first.
2. **Diagnose one rep.** Ask "Diagnose this rep" and give it what you have: the rep's target, activity numbers, conversion rates, call notes. If something is missing, it will tell you what and why it matters.
3. **Coach the one thing.** Ask "Help me coach this rep." It builds the conversation from the diagnosis, and Action tracking keeps the commitment from getting lost.

You can also call a skill by name, for example `/superintelligent-sales-os:task-diagnostic`.

**Keep your company context private.** `context/user-context.yaml` in this repository is a blank template. Run onboarding in your own private copy and never push filled-in company details to a public repository.

## How it's organized

```
skills/       the installable skills, grouped by layer (rep, manager) and suite
context/      the template your onboarding answers are saved to
docs/         the methodology behind the skills (TASK, the five-step coaching conversation, the operating rhythm)
```

The methodology in `docs/reference/` is free to read and use on its own, with or without the skills.

## What's next

This release covers onboarding, coaching, the manager's meeting rhythm and forecasting. Rep-layer skills are being built in public in this repository. Watch the repository to follow along.

## Feedback

The most useful thing you can send is a specific miss: what you asked, what the skill said, and what it should have said. [Open an issue](https://github.com/superintelligentsales/superintelligent-sales-os/issues) with that and it goes straight into the next build.

## Want help with your team?

Want this tailored to your team by a human? Dana Consulting runs a short sales diagnostic. Contact us at https://dana-consulting.com/contact.

## License

[MIT](LICENSE). Built by [Dana Consulting](https://dana-consulting.com).
