# Superintelligent Sales OS

Free, open-source Claude skills that help sales managers coach from evidence instead of instinct.

Most coaching starts with whatever felt wrong on the last call a manager heard. Sometimes that is the right place to start. Often the rep had a volume problem, not a skill problem, and weeks of call coaching change nothing. The Sales OS puts a method under that decision: check the evidence, find the real constraint, coach one thing, and track whether it happened.

Every skill follows one rule: **verified, not vibes.** When the evidence isn't there, the skill asks for it instead of guessing.

## What's in the first release

Eight skills, built for B2B sales managers and the reps they coach.

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

## Install

You do not need any technical tools. The Sales OS installs from the Claude app, and once it is on your account it works in Claude chat, Claude Cowork and Claude Code.

### In the Claude app (web or desktop) and Claude Cowork

1. **Turn on file creation.** In Claude, go to **Settings > Capabilities** and turn on **Code execution and file creation** (in the newer settings layout it is called **Create and edit files**). Skills need this to run. On Team and Enterprise plans your administrator controls this setting.
2. **Open the Plugins page.** Select **Customize** in the sidebar, then **Plugins**. You can also go straight to [claude.ai/customize/plugins](https://claude.ai/customize/plugins).
3. **Add this repository.** Select **Add**, then **Add marketplace**, and paste:

   ```
   superintelligentsales/superintelligent-sales-os
   ```

4. **Install the Sales OS.** Find **superintelligent-sales-os** in the list and select **Add**.
5. **Check that it worked.** Open the plugin from **Customize > Plugins**. Its **Skills** tab should list eight skills, including **customization-onboarding**.

The plugin is saved to your Claude account, so you install it once. It is then available in chat on the web, desktop and mobile, and in Cowork the next time you start a task. To pick a skill yourself, type `/` in the message box and look for the skills marked **superintelligent-sales-os**. You can also just describe what you want, such as "Diagnose this rep," and Claude loads the matching skill.

To get new skills as they are released, open the marketplace on the Plugins page and select **Check for updates**, or turn on **Sync automatically**.

On a Team or Enterprise plan, an owner decides whether members can add their own marketplaces. If you do not see **Add marketplace**, ask your Claude administrator.

### In Claude Code (optional)

If you already use [Claude Code](https://code.claude.com/docs/en/overview), you can install from there instead. In a Claude Code session, run these two commands:

```
/plugin marketplace add superintelligentsales/superintelligent-sales-os
/plugin install superintelligent-sales-os@superintelligent-sales
```

Or run the same steps from your terminal:

```bash
claude plugin marketplace add superintelligentsales/superintelligent-sales-os
claude plugin install superintelligent-sales-os@superintelligent-sales
```

To check that it worked, run `claude plugin details superintelligent-sales-os`. The list should show `Skills (8)`.

If you installed from the Claude app, you do not need these steps. Claude Code picks up the plugin from your account the next time you start a session.

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

This release covers onboarding, coaching and the manager's meeting rhythm. More manager suites (forecasting, deal inspection) and rep-layer skills are being built in public in this repository. Watch the repository to follow along.

## Feedback

The most useful thing you can send is a specific miss: what you asked, what the skill said, and what it should have said. [Open an issue](https://github.com/superintelligentsales/superintelligent-sales-os/issues) with that and it goes straight into the next build.

## Want help with your team?

Want this tailored to your team by a human? Dana Consulting runs a short sales diagnostic. Contact us at https://dana-consulting.com/contact.

## License

[MIT](LICENSE). Built by [Dana Consulting](https://dana-consulting.com).
