# The context layer

Every skill in the Superintelligent Sales OS reads `/context/user-context.yaml` first. The skill supplies the method and the structure; this file supplies your company, your buyers, your sales process, and your voice. A skill that runs without it produces generic output.

## How to fill it in

1. Install the OS.
2. Run the Customization Onboarding skill ([`customization-onboarding`](../skills/rep/_onboarding/SKILL.md)). It asks the questions, one section at a time, and writes the answers here.
3. Or edit `user-context.yaml` by hand. Keep the keys; replace the placeholder values.

Put your standard agreement at `/context/standard-agreement.md` if you want the contract redline skills to compare against it.

## What is in here

| Section | Used by |
|---|---|
| `company` | every skill |
| `icp` | BDR, Discovery, Demo, Solutioning |
| `methodology` | Discovery, call scoring, Coaching, Call & Pattern |
| `sales_process` | Solutioning (mutual action plans), Forecast, Operating Rhythm |
| `financial` | Business Case, Proposal & Negotiation |
| `cs_handoff` | Close & Handoff |
| `manager` | every Manager layer Suite |
| `voice` | every skill that writes something a buyer reads |

The tracked `user-context.yaml` is a public template. All unconfirmed values are marked `[USER]`; they are not defaults. Run onboarding in a private working copy, and never commit or push populated company context to a public repository. Adding a tracked file to `.gitignore` does not untrack it.

Onboarding preserves existing answers and custom keys, shows proposed changes and asks the user to confirm the facts before saving. An unknown mapping may use the quoted scalar `"[USER]"` until a confirmed mapping replaces it; an unknown list uses `["[USER]"]`. Empty lists and null mean explicitly confirmed absence, not missing answers.

`manager.enabled` selects whether the Manager interview applies. A non-manager retains the unanswered manager schema without completing it. Manager-specific cadence, coaching, forecasting and call analysis remain nested under `manager`.

The template includes library paths for cases, features, demos, proposals, contracts, ROI inputs and handoff materials, plus `tools` for CRM, sequencing and forecast sources. The skill's coverage table maps every suite requirement. A placeholder makes a gap visible; it does not make that suite ready.

The onboarding skill supports form exports, GPT conversations and live-conversation notes. Companion GPT and human-booking links are not configured in this release; onboarding works in the current conversation without them. The Diagnostic offer line remains a pre-merge wording decision for Victor.
