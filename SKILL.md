---
name: style-loop
description: Discover, refine, and validate a coherent 2D game visual style across characters, items, gameplay elements, backgrounds, and UI. Use for art-direction exploration, cross-asset style inconsistency, style bibles, or validation of an existing visual system; not for a standalone illustration or pixel-perfect screenshot recreation.
---

# Style Loop

Treat style as a production system: one explicit visual grammar must survive multiple asset categories, actual gameplay sizes, and previously unseen content. Deliver a reusable Style Kit with evidence of its limits.

## Start and route

Read [workflow.md](references/workflow.md) for execution, persistent state, budgets, and exit gates. Choose from the user's intent:

- **Discover:** no established direction, or an explicit redesign. Compare 3–5 structurally different candidates (default 4), shortlist, refine, provisionally lock, stress-test, then finalize.
- **Refine:** preserve an existing identity. Capture current assets/screens and baseline DNA; compare that baseline with two targeted alternatives unless the user already selected a direction. Then use the same refinement and validation gates.
- **Validate/extend:** an existing Bible or locked style is the starting point. Audit its rules and evidence, run the common benchmark and new-content test, and propose changes only where failures require them. Do not reopen divergence merely because another style seems prettier.
- **Resume:** recover the phase, artifact versions, unresolved issues, and remaining budgets from the project ledger. Do not restart counters or discard failed rounds.

## Capabilities

Need project file access, visual inspection, and a way to produce visible test artifacts: image generation, existing assets, or suitable 2D rendering tools. Use available image generation for raster exploration; follow its tool/skill instructions. Code-native vector/UI work may use the project's own renderer. A text prompt is not a rendered artifact.

Use a fresh independent judge subagent when delegation and image access are available. The judge procedure and fallback are in [judge.md](references/judge.md). Tool unavailability does not justify invented inspection, scores, images, or independence. Without visual evidence, deliver an explicitly unvalidated plan/DNA and stop at the documented capability exit.

## Read at the point of use

| Work | Reference |
|---|---|
| Build equivalent test sheets and native-size evidence | [benchmark.md](references/benchmark.md) |
| Write each candidate's explicit construction rules | [style-dna-template.md](references/style-dna-template.md) |
| Prepare blind packets; score, compare, and critique | [judge.md](references/judge.md) |
| Freeze rules and package a standalone handoff | [style-bible-template.md](references/style-bible-template.md) |

Keep working artifacts in the game's `.style-loop/`, separate from this installed skill. Archive versions rather than overwriting judged evidence. The workflow document is the authority for thresholds and counters; the judge document is the authority for scoring.

Present the selected direction, comparable sheets, actionable verdicts, actual-size gameplay evidence, and linked Style Kit. Report either **validated**, **provisional**, or **unvalidated**, with the exact unmet gate when applicable. A beautiful character, a high average, or the user's preference alone cannot certify the visual system.
