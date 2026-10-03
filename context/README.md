# The context layer

Every skill in the Superintelligent Sales OS reads `/context/user-context.yaml` first. The skill supplies the method and the structure; this file supplies your company, your buyers, your sales process, and your voice. A skill that runs without it produces generic output.

## How to fill it in

1. Install the OS.
2. Run the Customization Onboarding skill (`rep/_onboarding/`). It asks the questions, one section at a time, and writes the answers here.
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

Keep this file out of public forks: it holds your own commercial details. The template values above are placeholders only.
