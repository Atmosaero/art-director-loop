# Comparable visual-system benchmark

## Freeze the contract

Write the project's `benchmark.md` before generating candidates. Every cell gets a stable ID, semantic description, pose/state, crop, intended display size, and comparison background. Keep subjects, counts, layout, text, scale, and negative space equivalent across candidates. Only the construction rules vary. Labels and measurement guides are neutral presentation chrome, excluded from scoring.

Default coverage (adapt subjects to the game, without dropping a category merely because it is hard):

| IDs | Required content | What it exposes |
|---|---|---|
| C01–C02 | One full-body character; portrait/expression of the same character | Silhouette, proportions, facial grammar, line hierarchy |
| I01–I04 | Potion, weapon, magical artifact, mundane object, or four equally distinct in-world categories | Organic/hard/glass/ordinary material transfer |
| G01–G06 | Six distinct match-3 tiles, resources, icons, cards, or equivalent mechanics | Small-size distinction, category/rarity encoding, state clarity |
| U01–U03 | The same button normal, selected/pressed, disabled | States without relying only on color |
| U04–U07 | Inventory slot, popup/panel, HP/mana/progress bar, tooltip/card | Reusable panel construction, hierarchy, text fit |
| B01 | Background/environment slice containing quiet and busy areas | Depth, texture/detail budget, subject separation |
| X01 | A playable-looking viewport with character, items, mechanics, background and HUD | Cross-domain consistency at real density |
| X02 | Menu/inventory screen with panel, slots, buttons and popup | Consistency beyond the gameplay scene |

If there is no character or inventory in the game, choose the closest actual equivalents, explain the adaptation, and retain comparable complexity. Label domains that the product truly does not contain; never claim evidence for untested categories. This adapts a real game, not a candidate's weaknesses.

Define target dimensions from the project. If absent, a disclosed mobile starting assumption is a 390 × 844 logical viewport, 96 × 96 item icons, and 48 × 48 mechanic icons. Define logical versus export pixels and device scale explicitly; a 2× export does not make a 48-logical-pixel icon an easier 96-pixel readability test. Preserve aspect ratios; document nearest-neighbor versus filtered sampling appropriate to the style.

## Produce evidence rather than a moodboard

A package contains a standardized overview sheet plus separate native-size crops and viewport captures. Do not shrink every test into one unreadable collage. Use the same rows, captions, canvas, and neutral surround across candidates. The main viewport uses the game's intended background, density, and HUD placement; a white-backed isolated icon cannot establish in-game readability.

Generate all domains under the DNA's shared rule block. When a sheet model mixes styles or omits cells, generate the missing/affected cells separately under the **same** DNA and assemble them without inventing extra decorative elements. Use tool-compliant image editing/compositing or a suitable UI renderer; do not assume shell-based raster editing is always permitted.

Prompt skeleton:

```text
Create a 2D GAME STYLE VALIDATION SHEET, benchmark version [N].
Visual construction rules: [resolved DNA rule block, including scale policy].
Required cells and fixed subject/pose/state: [manifest].
Fixed layout and size relationships: [grid specification].
Gameplay and menu composition: [viewport, density, exact interface content].
No new subjects, missing states, cinematic camera, beauty-shot lighting,
decorative presentation frame, or unrequested embellishment.
Use identical material/contour/shadow logic across domains; apply only the
documented small-size exceptions. Preserve the given game identity constraints.
```

If text or UI interaction is unreliable in image generation, render typography/state layouts using the project UI or a deterministic mockup, and generate only the illustration parts. Apply the same method across candidates. Record the font/renderer and any manual correction. Do not let garbled text stand in for proof of readable tooltips.

## Presence and native-size checks

Before judging, inspect and record each cell's file/crop, dimensions, presence, semantic correctness, state, and target-scale view in `manifest.md`. Metadata alone cannot show that a potion or disabled button is actually present. A repeated portrait does not count as a full-body character; an enlarged icon does not count as a native-size sample.

Required checks:

- Open native-size evidence at 100% when the viewer supports it. If automatic resizing prevents that, obtain a controlled-scale viewport/capture or mark actual-size readability unverified. Never infer it from an enlarged contact sheet alone.
- Compare mechanically confusable elements beside one another at the minimum supported size and in the busy composite. Confirm distinctions survive without color alone, using shapes/symbols/structure.
- Check that active, selected/pressed, and disabled controls are distinguishable; disabled labels remain legible. Check actual text samples, tooltip hierarchy, bars at low fill, and occlusion by popup/VFX where relevant.
- Inspect character-to-background and UI-to-background separation, attention hierarchy, outline collapse, texture noise, and material highlights. Record measured contrast when tools make it available, without inventing a compliance claim.
- Mark source resolution, resampling method, transparency/edge artifacts, and any cleanup. Verify both light and dark backing if the assets must support both.

Missing required cells or unreadable evidence makes the package invalid. A visibly complete package with indistinguishable icons or inconsistent states is valid evidence of a **failure** and should reach the judge.

## New-content transfer test

After provisional lock, choose subjects not used in generation, anchors, examples, or prior trials. Retain target sizes and production constraints; change content and composition. Include:

- A different character archetype/body plan and a new expression (e.g. a witch and an ice wolf when appropriate).
- At least three items spanning ornate/rare, mundane, and a contrasting material (e.g. a legendary weapon, bread, and a glass instrument).
- Three new mechanics icons/cards/resources with potentially confusable silhouettes.
- A new screen type such as settings or results, with fresh tooltip content and disabled/selected controls; include long text if localization matters.
- A new background region and a dense gameplay composite integrating new assets with existing anchors.

Adapt equivalents for games without these domains. The maker receives the locked Bible/anchors and this new content specification, not candidate generation history. Any rule it must invent is evidence about reproducibility. Successful visual transfer that requires excessive bespoke repainting can still fail the production gate.

Choose genuinely different subjects for a second stress attempt; swapping colors or renaming a failed item does not restore its unseen status. Preserve failed stress evidence for regression checks.
