# Execution and state

## 1. Establish the brief

Inspect the project and any references before proposing styles. Record in `brief.md`:

- Game genre, player actions, emotional tone, audience, platform/orientation, viewport and actual display sizes.
- Asset families, content volume, animation needs, engine/export constraints, existing typography, and localization needs.
- Identity to preserve; allowed redesign scope; reference sources and rights/usage constraints supplied by the user.
- Production method, available tools/people, per-asset time or cleanup allowance, reusable construction requirements, and budget.
- Hard requirements versus preferences; unknowns with explicit working assumptions.

Infer reasonable defaults for noncritical gaps and continue. Ask only for missing information that changes scope or makes valid evidence impossible. Do not ask the user to design this workflow. Inspect existing screens at gameplay size; preserving identity means writing down which rules are invariant, not just keeping the same palette.

For references, distinguish transferable rules (contour hierarchy, shape rhythm, material symbols) from subject details (one costume, camera pose, background story). Resolve conflicting references into coherent hypotheses. Record why a rule transfers; do not copy every reference detail into every asset.

## 2. Establish comparable evidence and finite budgets

Read [benchmark.md](benchmark.md). Freeze benchmark content, layout, target sizes, and evaluation conditions before generating candidates. Define holdout **categories** now, but select their exact new subjects only after provisional lock.

Record these defaults in `state.json`; honor smaller user limits and adjust explicit larger limits before work begins:

| Limit | Default | What counts |
|---|---:|---|
| Initial candidates | 4 discovery; 3 refinement; 1 validation | Existing baseline counts as one |
| Refinement rounds | 6 shared across shortlisted candidates | Every attempted benchmark revision, including invalid revisions, structural rescue and post-stress repairs |
| Structural rescues | 1 per candidate | A coordinated grammar/subsystem redesign after stall |
| Stress attempts | 2 across the run | Each holdout package, including a repeat after failure |
| Sheet/package attempts | 18 across the run | Initial, revised, stress, and completion-repair packages, even if invalid |
| Generation calls | 48 across the run | Every image-generation invocation, including individual cells, retries, and stress-maker calls |
| Judge calls | 24 across the run | Initial, refinement, tournament, stress, and verdict-correction invocations |

A package may contain several images. Reserve/increment applicable counters before dispatch; reserve a refinement round when its revision begins, not only when it becomes judgeable. Child makers must receive a fixed share of the remaining call allowance and report usage; reconcile before another dispatch. Accepted or uncertain jobs remain counted; retrieve an existing result instead of blindly resubmitting. Each initial sheet, revision, or holdout gets at most one missing-cell repair. That repair consumes another package attempt plus actual generation calls, but not another refinement/stress slot; a repair cannot spawn another repair. An invalid package never earns a numerical score. Allow at most one correction of an incomplete/contradictory verdict per packet, consuming another judge call; unresolved evidence remains invalid.

Check applicable limits and any user time/cost deadline before each action. A limit blocks only actions that consume it: using the last refinement round does not prevent a funded stress test or packaging existing evidence. Finish inspection/judging of already-produced evidence within its remaining allowance. If the next necessary action would exceed a limit, stop with best available evidence; never reduce benchmark coverage, lower thresholds, or reset counters to fit. Explicit user authorization can extend a limit; append that change to history. An exhausted budget is not success.

## 3. Persistent project workspace

Use one run per project, with immutable rounds and Bible versions:

```text
.style-loop/
  brief.md
  benchmark.md
  state.json
  decisions.md
  candidates/
    c01/round-00/
      style-dna.md
      sheet.png
      native/                 # size-labelled exports and viewport captures
      manifest.md             # cells, dimensions, file paths, presence check
      generation.md           # prompts, reference IDs, tool/settings, cleanup, cost
    c01/round-01/...
    c02/round-00/...
  packets/
    p001/                     # neutral labels, allowlisted copied evidence
      input.md
      current/...
      previous/...            # only during refinement
  verdicts/
    p001.md
    tournament-01.md
  locked/
    v01/
      style-bible.md
      anchors/                # character, items, UI, gameplay, background
  stress/
    attempt-01/
      brief.md
      maker-log.md
      sheet.png
      native/...
      manifest.md
  kit/
    v01/                      # self-contained release; contents below
```

`sheet.png` is a convention; use lossless equivalent formats if necessary and record actual paths. Create only artifacts that exist. Do not leave fake image files or empty success placeholders.

Keep bulky intermediate media out of version control using project conventions; do not automatically ignore the Bible/Kit the team needs to share. Do not overwrite existing work or modify the source game merely to make a mockup.

Minimum ledger shape (example for a newly started discovery run):

```json
{
  "schema_version": 1,
  "mode": "discover",
  "phase": "brief",
  "status": "working",
  "benchmark_version": 1,
  "limits": {"candidates": 4, "refinements": 6, "rescues_per_candidate": 1, "stress": 2, "packages": 18, "generation_calls": 48, "judge_calls": 24},
  "used": {"refinements": 0, "stress": 0, "packages": 0, "generation_calls": 0, "judge_calls": 0},
  "candidates": {},
  "packet_map": {},
  "locked_version": null,
  "pending_jobs": [],
  "history": [],
  "next_action": "freeze benchmark"
}
```

For each candidate track round paths, score components/total, blocker IDs, best eligible round, rescue count, and comparison epoch. History entries include timestamp, action, input/output paths, usage changes, verdict path, and outcome. Update after each action, retaining pending-job IDs. Store candidate-to-blind-label mapping only in the coordinator's ledger. Judges receive packets, not this ledger or selection commentary.

On resume, inspect pending jobs and referenced files, reconcile counters, and resume the next incomplete action. Missing evidence invalidates its verdict; it does not reset consumption. Changes to content, target sizes, rubric, or hard constraints start a new comparison epoch: rerender all still-compared candidates under the new conditions and retain old scores as incomparable history. Budgets and rescue counts survive the change.

## 4. Diverge and compare

Read [style-dna-template.md](style-dna-template.md). Write each DNA **before** generation. In discovery, build a short matrix showing at least three structural differences between each pair: contour construction, shapes/proportions, shading/material language, or detail/UI construction. Palette-only variants are not independent discovery hypotheses.

For refinement mode, list baseline invariants and keep alternatives within them; targeted alternatives may change just one failing subsystem and do not need discovery's three-axis divergence. For validation mode, use one baseline; a tournament is unnecessary.

Generate each candidate with the frozen benchmark and the same production allowance. Save prompts, inputs, cleanup effort, and observed departures from DNA. Check every manifest cell visually, including native-size exports; repair missing content within the retry limit. A complete sheet that violates its style rules is judgeable and should score poorly; a sheet missing required categories is invalid.

Prepare neutral packets as described in [judge.md](judge.md). Have fresh judges score valid candidates independently before the comparison judge sees them together. The comparison judge receives those same sheets/verdicts in randomized order, the brief constraints, and a neutral candidate matrix. Retain raw verdicts and full tradeoff reasoning.

Shortlist at most two. Prefer candidates without major blockers, then those with stronger weakest dimensions and plausible production effort. A high total does not offset a hard constraint failure. If scores are within 0.25 or tradeoffs dominate, use brief priorities and production burden, explaining the choice. Do not use repeated judging to shop for a higher score. If none is promising, allocate the available rescue to the strongest recoverable candidate; do not silently start another divergence batch.

## 5. Refine with continuity

Each round:

1. Name the highest-impact issue IDs and predicted cross-domain consequences in `decisions.md`. Keep content and test conditions fixed.
2. Update DNA and regenerate affected assets, then recompose the **complete** sheet and native-size composite. Reuse unchanged cells only when their rules truly remain unchanged. A global contour/palette/shading change requires rerendering every affected domain.
3. Validate presence, then submit current evidence/DNA plus previous evidence/DNA/verdict to a fresh judge. If it exists, also include the best prior eligible round for regression context.
4. Store the verdict and component scores. Recalculate the sum; resolve missing evidence or contradictory judgments, not unfavorable opinions.
5. Evaluate gates and stall rules below. Keep the best **eligible** version recoverable; the latest file is not automatically the winner.

Do not solve a mismatch merely by rewriting DNA to bless an accidental defect. Explain the benefit of a rule change, apply it to all affected domains, and retest. High scores are not monotonic: a regression means a lower score or newly blocking issue even if other dimensions improve.

### Stall and structural rescue

Compare only valid scored rounds of the same candidate and epoch. Let `B(t)` be the best total through round `t`, including the initial round. Once two scored revisions exist, a numerical stall is `B(t) - B(t-2) < 0.5`. Also trigger a stall if the same unresolved **major** root-cause issue appears in two consecutive verdicts; track stable issue IDs even if wording changes. Neither missing-cell repairs nor invalid sheets count as scored progress.

If a candidate passes the provisional-lock gates, proceed to lock rather than rescuing merely because its score plateaued. Otherwise, on stall:

- Diagnose the structural cause: e.g. the contour cannot scale to icons, UI construction follows a different grammar, materials require bespoke painting, or character-specific tricks fail on objects.
- Spend at most one rescue for that candidate. State the failed assumption and make one coordinated art-direction revision across the affected system. It consumes a normal refinement round and generation allowance.
- Judge the rescue. Success requires **all three**: (a) resolves the targeted major root cause **or** improves the previous best by at least 0.5; (b) introduces no new major blocker; (c) regresses no rubric component by 0.5 or more. Otherwise stop work on that candidate.
- After a successful rescue, a later stall stops that candidate; no second rescue. Continue another already-shortlisted candidate only within existing budgets. If none remains, present the unresolved tradeoff for user review.

This bounds both endless small tweaks and endless reinvention. User preference may select a provisional candidate but cannot relabel failed evidence as validated.

## 6. Provisional lock and independent transfer test

Provisional lock requires a complete benchmark, satisfied hard constraints and production allowance, no major blockers, and these scores:

| Dimension | Minimum |
|---|---:|
| Total | 8.5 / 10 |
| Cross-domain consistency | 2.5 / 3 |
| Visual grammar | 1.5 / 2 |
| Gameplay readability | 1.5 / 2 |
| Generalization | 1.5 / 2 |
| Reproducibility | 0.75 / 1 |

Read [style-bible-template.md](style-bible-template.md). Freeze `locked/vNN/` as **provisional**, with a standalone Bible and multi-domain anchors from the selected judged round. Audit the Bible for concrete rules, scale exceptions, production recipe, and contradictions with those anchors. Every required section must contain an actionable rule or a reasoned non-applicability statement. A missing definition remains an issue, not implicit context.

Now choose new subjects and screen content under the holdout coverage in [benchmark.md](benchmark.md). Prefer a fresh maker subagent that receives only the frozen Bible, anchor files, holdout brief, relevant tool instructions, and allocated budget—never exploratory prompts or coaching from earlier rounds. This skill explicitly requests independent maker/judge delegation when available. The maker logs missing rules, inferred decisions, generation retries, manual cleanup, and cost/time. Do not help it conceal missing specifications.

When a fresh maker is unavailable, use the same locked-only input packet in the main agent and disclose the weaker transfer evidence. The final independence status follows [judge.md](judge.md).

Judge the holdout with the same rubric and threshold table, against the locked Bible and anchors. Supply the selected benchmark verdict for calibration **after** initial visual inspection; subject equality with the benchmark is not expected. Cross-domain grammar and actual-size behavior must still hold. Generalization and reproducibility now require observed evidence from the maker, not predictions.

On any failed gate, invalidate provisional lock, preserve its version, and return to refinement if budgets permit. Classify whether generation execution or the style rules failed; both require repaired evidence. Fixing the Bible creates a new lock version. Rejudge the complete original benchmark after changes before locking again. Failed holdout subjects are now seen and may be used for regression checks, but the next transfer test must use different subjects and a new composition. Never reset stress/round/rescue budgets after failure.

## 7. Finalize or stop

**Validated:** the same frozen Bible version passes the original benchmark and an unseen-content test; every gate in section 6 passes on both; no major issue or unresolved hard constraint remains; the Bible audit passes; transfer effort fits the recorded allowance; independent judging and independent maker evidence are available. Cite the exact evidence versions. Changes after validation require revalidation of affected evidence and a new kit version.

**Provisional:** visible evidence exists, but independence, transfer evidence, a gate, budget, or user review remains unresolved. Say which. **Unvalidated:** visual inspection/evidence is unavailable; supply useful brief, rules, benchmark specification, and prompts without a numerical verdict or lock claim.

Stop on success, a limit/deadline blocking the next necessary action, failed rescue with no remaining candidate, two failed stress attempts, user stop, or unavailable required capability. Record status, best candidate, exact unmet gates, consumed budget, and the next useful decision. Do not keep looping while awaiting user input. Ask for a tradeoff decision only after providing the concrete comparison and failure evidence.

Create `kit/vNN/` for a validated result, or clearly mark a requested draft kit provisional. It must work outside `.style-loop/` and the original conversation:

- `style-bible.md` with local relative links, status/version, and actual rule values.
- `anchors/` for characters, items, UI states, gameplay composite, and background; native-size companions and size metadata.
- `tokens.json` for actual palette values/roles, line weights by size, spacing/radii, typography roles, and shading steps. Check it agrees with the Bible; never fill missing values with guesses labelled final.
- `recipes.md` with cross-domain production steps, reusable prompt skeletons, export rules, negative constraints, and a new-asset acceptance checklist.
- `validation.md` with benchmark/holdout coverage, verdicts, scores, evidence filenames, production observations, independence limitations, and known minor issues.
- `evidence/` containing final sheets, native views, manifests, and corresponding verdicts so validation links travel with the kit.

Preview representative evidence and present the direction, score breakdown, strongest tradeoff, stress outcome, and kit path. Distinguish validated style guidance from production-ready assets: mockups do not certify animation, engine integration, font licensing, or editable source files unless actually checked.
