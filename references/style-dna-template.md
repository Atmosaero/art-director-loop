# Candidate Style DNA

Copy this structure into each candidate round's `style-dna.md`. Replace prompts with concrete rules and values; use `not applicable` with a reason when appropriate. Distinguish **hypothesis**, **observed**, and **locked**. Do not silently promote intended rules into observed facts.

## Identity and priorities

- Candidate/round and benchmark version; brief constraints and identity invariants.
- One-sentence visual goal followed by ranked operational priorities, e.g. icon discrimination before surface ornament.
- Structural differences from other candidates; rationale tied to the game.
- Target viewport, logical pixels/export scale, smallest supported asset sizes, expected production volumes.

## Shared construction grammar

For each rule record **value/range**, **where it applies**, **size-dependent exception**, and **how to inspect it**. Give pixels at a stated display size or ratios with a reference dimension; “thick,” “simple,” and “stylized” alone are not specifications.

| Rule group | Required decisions |
|---|---|
| Silhouette/shape | Round/angular balance; primary/secondary masses; asymmetry; negative spaces; allowed irregularity |
| Contours | Exterior/interior weight; ratio; join/cap type; line color; interruptions; minimum-size treatment |
| Palette | Swatches with values and roles; hue/saturation/value bands; colors per asset; accents; rarity and state encoding |
| Shading | Flat/cel/other construction; tone count; light direction; shadow shape and color; cast versus form shadows |
| Gradients/highlights | Allowed locations and extent or ban; highlight geometry, intensity and material exceptions |
| Surface/detail | Texture density, stroke/grain scale, internal detail budget, smallest retained feature, quiet areas |
| Geometry | Proportion families; corner radii; bevel policy; perspective and depth cues |
| Effects | VFX shape motifs, palette, edge softness, opacity and overlap budget; UI priority during effects |

## Domain construction

- **Characters:** body/head ratios, anatomy simplification, limb/hand treatment, costume massing, face feature placement, eyes/mouth/expression ranges. Include which proportions can vary across archetypes.
- **Items/icons:** silhouette footprint, padding, view angle, material symbols, ornament budget by rarity, shape distinctions at minimum size.
- **Gameplay pieces:** family resemblance versus mechanic identity, selection/active/blocked variants, information priority.
- **UI:** panel layers, fill/border/shadow relationship to character contours, spacing grid, corner construction, typography roles, button states, slots, bars and tooltips. A deliberate UI simplification needs a shared parent rule and tested scale rationale.
- **Backgrounds:** perspective, contrast/depth layers, texture frequency, quiet gameplay zones, separation from actors and UI.
- **Composition:** gameplay/menu hierarchy, density, edge-safe zones and overlap rules.

## Production contract

- Allowed techniques and forbidden shortcuts; exceptions with reasons.
- Asset recipe from silhouette through export; reusable templates and per-asset effort allowance.
- Source/output formats, transparency, padding, naming, resolution/sampling rules, intended editability.
- Known risks and falsifiable predictions: which category or size is most likely to break this grammar?
- Reference sources and extracted principles, separated from subject-specific content.

## Round evidence

- Corresponding sheet/native paths; generation recipe/tool settings; actual cleanup effort versus allowance.
- Observed departures from rules and unresolved issue IDs.
- Changed rules since previous round; affected domains; evidence to regenerate.

Generate prompts **from** this document, not vice versa. A prompt fragment can be stored with generation logs; it is not the authoritative rule definition.
