# Standalone Style Bible and handoff

Use the structure below for the selected style, resolving every instruction into actual rules. The finished Bible must make sense to an artist or agent with no access to the discovery conversation. Link only to files shipped beside it; include normative values in the document and matching machine-readable tokens in the kit.

## 1. Status and scope

Style name, version, date, provisional/validated status, covered game/platform/viewport, scale convention, benchmark and transfer evidence versions, remaining limitations. Explain the game and supported asset families in a short paragraph. Identify the source DNA round and which established identity constraints remain invariant.

## 2. Visual goals and priorities

Describe intended player perception, then concrete ranked priorities. Translate adjectives into decisions: “friendly” could mean broad rounded masses, softened corners, a limited interior-line budget, and a specified face ratio. Resolve conflicts such as ornate rarity versus small-size legibility.

## 3. Line and shape system

Exterior/interior contour color, width by reference size, scaling/clamping or pixel-grid policy, joins/caps, irregularity limits, interruptions, allowed no-outline regions. Shape families, silhouette ratios, negative space, symmetry/asymmetry and corner/radius rules. Explain shared parent rules and domain/scale adaptations.

## 4. Palette and value hierarchy

Actual swatches (e.g. hex values) with semantic roles, background/foreground value separation, saturation bounds, color count per asset, accent budget, material/state/rarity encoding. Specify alternatives to color-only distinctions. Link `tokens.json` in the released kit; reconcile every shared value.

## 5. Shading, highlights, texture and materials

Light direction, tone count, shadow shape/color, cast/form shadow relationship, gradient policy, highlight geometry/intensity, texture frequency and detail budget. Define readable symbols for actual materials: metal, glass, cloth, wood, stone, skin/fur as applicable. Show how rare and mundane items share construction without identical ornament.

## 6. Characters and faces

Mass construction, proportions and allowed archetype variation, simplified anatomy, hands/feet, costume layering, silhouette priority, facial feature placement and expression rules. State animation deformation limits if tested; otherwise label animation unvalidated. Link a full-body and expression anchor with sizes.

## 7. Items, icons and gameplay pieces

Canvas footprint/padding, view angle, silhouette separation, internal-line/detail limits, rarity hierarchy, material recipe, mechanic/category/state coding. Explain what to remove at small sizes and which feature must survive. Link multiple material/category anchors and confusable-piece comparisons at native size.

## 8. UI, menus and information hierarchy

Panel layers and depth, borders/corners, spacing/grid, shadows, typography roles/sizes/line heights, font source/fallback constraints, icons versus text, inventory slots, bars, tooltips/popups. Define normal, selected/pressed and disabled states; localization/long-text handling. Link gameplay and menu examples, not just isolated buttons. Document which typography was rendered versus generated.

## 9. Backgrounds and VFX

Depth/perspective, detail and contrast by layer, quiet play zones, separation from actors, UI priority, effect shape/palette/opacity, overlap and busy-screen limits. State any effects or motion not yet tested. Link a busy composite and a background anchor.

## 10. Scale and export rules

Target logical sizes, export sizes/device scale, minimum readable dimensions, line/detail changes by scale, pixel snapping/filtering, transparency/padding, source/deliverable formats and naming. Explain actual-size inspection conditions. A mockup's resolution is not a promise of engine readiness.

## 11. Allowed, forbidden and diagnostic examples

List specific allowed/forbidden techniques and bounded exceptions. Include at least one correct/incorrect decision for contours, material shading, small icons and UI states; explain the visible consequence and repair. For example, extra texture on a 48 px tile can erase a mechanic symbol; the allowed larger portrait may retain that texture. Include images/crops when available, otherwise identify the exact anchor/cell illustrating the rule. Do not generate additional images solely to decorate this section.

## 12. Production recipes and generation guidance

Steps for a new character, item, gameplay piece, UI component and background: silhouette blockout, rule application, detail limit, composite/native-size check, export. State actual production/cleanup allowance and observed transfer effort. Identify editable sources and dependencies when they exist.

Reusable prompt skeleton:

```text
Asset: [new subject, function, pose/state].
Game style version: [version]; authoritative rules: [resolved relevant values].
Shared grammar: [shape, contour, palette, shading, detail rules].
Domain and size exceptions: [explicit rules, target logical/export dimensions].
Reference anchors: [local files, what each demonstrates].
Composition/output: [padding, view, transparency/background, file requirements].
Forbidden techniques: [applicable prohibitions].
```

Prompts supplement the Bible. A fresh maker must be able to derive them without access to hidden exploratory logs. Record model/tool/settings when known without implying exact seed reproducibility or a permanent vendor requirement.

## 13. New-asset acceptance and change control

An artist checks silhouette/semantic distinction at target size, shared contour/material rules, palette/detail budget, states, composition/background separation, output format and actual effort. Include pass/fail examples and the corresponding anchor paths. Compare in the gameplay screen, not only in isolation.

Rules are frozen per version. Document a proposed exception's reason and affected domains; changes to shared grammar require a new version, original-benchmark regression check, and new-content validation before that version is called validated. Do not quietly overwrite anchors. Link the shipped validation report and known minor limitations.

## Final audit

Open the Bible and its anchors as a new consumer would. Check every required section, value/unit, local link, token consistency, correct/incorrect example, and production recipe. Replace unresolved blanks with an explicit limitation and withhold validation if a core construction rule remains unknown. Packaging contents and final status gates are defined in [workflow.md](workflow.md); this template does not grant a lock by itself.
