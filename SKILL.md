---
name: gc-minimal-ip-doodle
description: Preserve an IP character's identity while redrawing it as a sparse, flat, hand-drawn sticker illustration on white or a light grainy background. Use for requests such as "把这个角色做成极简手绘风格", "生成五张不同生活场景", "做一个浅色背景轻颗粒版", "再来五张不要重复", or when a frog, capybara, fish, mascot, toy, or other character reference must become a consistent batch of cute deadpan doodles.
---

# Minimal IP Doodle

Turn one character reference into one or more consistent minimal hand-drawn illustrations. Keep the style fixed and the character replaceable.

## Rights Boundary

Use character references only when the user owns them or has permission to use them. Do not infer ownership from possession of an image. For public or commercial delivery, remind the user that generated output does not create rights in a third-party character, logo, or trademark.

## Required Resources

Before generating, read:

- `references/style-guide.md` for the fixed visual grammar.
- `references/prompt-template.md` for identity extraction and prompt construction.
- `references/quality-checklist.md` for acceptance checks.

Inspect the project-provided images in `assets/style-references/` with the image viewer before the first generation in a task. Treat them only as evidence for the specific roles documented under `Bundled Evidence` in `references/style-guide.md`; not every image teaches every style property. Never copy their character design, exact scene, pose, or prop arrangement. For white-background work, choose the smallest useful set of original white references. Use the two identity-transfer examples only when their anatomy-retention evidence is relevant, and never learn their gradients, shading, subject scale, or scene density. For `soft-grain`, include the paired white/soft-grain example so the background change is explicit. Asset provenance is documented in `ASSET_PROVENANCE.md`.

## Normalize the Request

Resolve these inputs from natural language:

- `character_reference`: required image path or attached image.
- `count`: default `1`.
- `scene`: optional explicit action or situation.
- `scene_mode`: default `auto` when no scene is supplied.
- `expression`: optional override; otherwise preserve the character's baseline mood.
- `props`: optional; keep the prop set sparse.
- `background_mode`: `white` (default), `soft-grain`, or `both`. Resolve "白底/没背景" to `white`, "有背景/浅色背景/轻颗粒" to `soft-grain`, and requests for both versions to `both`.
- `output_dir`: optional; otherwise use `outputs/gc-minimal-ip-doodle/<date>-<character-slug>/` under the current workspace.

Ask one short question only when the character reference is missing or unreadable. Make conservative defaults for every other omitted field.

## Workflow

### 1. Load and Label Images

Use the built-in image-generation path from `$imagegen`.

- Load a local character file with the image viewer before generation.
- Label the character image as `character reference`.
- Label bundled examples as `style references`.
- Treat this as reference-guided generation, not an edit that must preserve the source composition.

### 2. Build an Identity Lock

Extract and retain an internal identity lock containing:

- species or character class;
- dominant silhouette and head-to-body ratio;
- eye, mouth, ear, fin, horn, antenna, limb, and muzzle geometry;
- main, secondary, and signature color blocks;
- distinctive accessories or anatomy;
- baseline expression and emotional energy.

Do not replace uncertain anatomy with a generic animal template. When simplification conflicts with recognizability, preserve recognizability.

### 3. Plan Distinct Scenes

For `count > 1`, create an internal scene list before generation. Vary at least two of these axes between neighboring images:

- action;
- body pose or silhouette;
- prop category;
- emotional beat;
- spatial relationship between character and prop.

Keep scenes small, everyday, and readable in one glance. Prefer quiet deadpan humor over spectacle. Do not count a color swap or one replaced handheld object as a new scene.

For requests such as "再来五张", inspect the current conversation and any existing `prompts.md` in the output series. Exclude earlier scenes and near-duplicates.

### 4. Construct the Prompt

Use `references/prompt-template.md`. Put the identity lock before scene and style details. Repeat critical invariants in every prompt:

- keep the same character identity, silhouette logic, colors, and signature features;
- use the selected background mode with generous empty space;
- draw one small centered character or compact character-and-prop cluster;
- use thick, mildly irregular black hand-drawn outlines and flat fills;
- keep facial marks, props, and motion lines sparse;
- exclude realistic lighting, gradients, shadows, fur, plush, plastic, and 3D volume; allow only the controlled micro-grain defined for `soft-grain`;
- include no text, lettering, logo, or watermark unless explicitly requested.

### 5. Generate One Asset per Call

Issue one built-in image-generation call per distinct image. Do not use one multi-variant call as a substitute for separately prompted scenes.

For each call, provide the character reference and the smallest useful set of style references. Preserve the same identity-lock wording across a batch and change only the scene-specific block.

### 6. Apply the Background Mode

Generate and accept a `white` master first. Then:

- `white`: keep the pure or near-white empty background and add no grain.
- `soft-grain`: edit the accepted white master instead of redrawing the scene. Change only the background and surface treatment. Choose a high-lightness, low-saturation background hue after inspecting the character palette; keep clear separation from skin, white clothing, cream fur, and signature colors. Add very fine, low-contrast monochrome grain mainly to the background, at roughly one-quarter of a visibly grainy reference. Let only a barely perceptible amount enter character fills. Keep black outlines crisp and dominant.
- `both`: save the accepted white master, then derive a `soft-grain` version from that same master.

Do not use a dark or saturated background, gradients, vignettes, stains, coarse noise, film grain, shadows, or scenery. If the background edit changes character anatomy, pose, color blocks, or line placement, reject it and retry once with an explicit "change only background and texture" correction.

### 7. Inspect and Correct

Inspect every output against `references/quality-checklist.md`.

Retry once with one targeted correction when an output fails a hard requirement. State the failed invariant explicitly, such as:

- restore the antenna and yellow bulb;
- remove gradient shading and cast shadow;
- reduce the character scale and restore white space;
- restore the source-specific muzzle patch and half-lidded eye.

Do not silently accept a pretty image that changes the character or misses the fixed style.

### 8. Persist the Deliverables

For project-bound or batch work, copy every accepted output from the built-in generated-image location into the stable `output_dir`. Never leave final deliverables only in the generated-image cache.

Use semantic filenames:

`<character-slug>-<two-digit-index>-<scene-slug>.png`

When `background_mode` is `both`, add `-white` and `-soft-grain` before `.png`. Treat `count` as the number of scenes, so `both` produces two files per scene.

Create or append `prompts.md` with:

- source character reference;
- output filename;
- concise scene description;
- background mode and selected background color for `soft-grain`;
- final generation prompt;
- retry note, if any.

Do not overwrite an existing image unless the user explicitly requests replacement.

## Final Response

Report:

- the number of accepted images;
- the stable output directory;
- direct links to the final images and `prompts.md`;
- any identity or style limitation that remains visible.
