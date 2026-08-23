# Quality Checklist

Inspect each generated image before accepting it.

## Hard-Fail Checks

Reject or retry when any answer is yes:

- Did the species or character class change?
- Is a signature feature missing, relocated, or replaced?
- Did the main palette drift away from the character reference?
- Does the background violate the selected mode: non-white in `white`, or dark, saturated, low-contrast against the character, or scene-like in `soft-grain`?
- Does the image use realistic 3D volume, gradients, glossy light, fur, plush, plastic, or strong shadow?
- Is the character cropped, oversized, or filling most of the canvas?
- Is there unintended text, a logo, caption, or watermark?
- Does the output closely copy a style reference's exact scene or pose?

## Per-Image Checks

Accept only when all are true:

- The character remains recognizable without seeing the source beside it.
- The dominant silhouette and feature placement match the identity lock.
- Signature color blocks and accessories remain stable.
- The canvas matches `white` or `soft-grain` mode and keeps broad empty margins.
- The character or compact cluster is small and centered.
- Outlines are thick, black, and mildly irregular.
- Fills read as flat color blocks rather than rendered volume.
- Facial lines and interior details are sparse.
- The action is readable in one glance.
- Props support the action and do not dominate the character.
- The mood stays quiet, cute, tired, friendly, or deadpan.

## Background Mode Checks

For `white`:

- The canvas is pure or near-white with no visible grain or paper texture.

For `soft-grain`:

- The background is one high-lightness, low-saturation contextual hue and remains visually close to off-white.
- Skin, white clothing, cream fur, and signature color blocks stay clearly separated from the background.
- Grain is extremely fine, even, low contrast, and concentrated in the background.
- Character fills contain at most a barely perceptible amount of grain.
- Black outlines remain crisp, solid, and dominant.
- The background edit did not redraw, move, resize, crop, or recolor the character or props.

## Batch Checks

For batches, also verify:

- Character proportions, palette, signature anatomy, and outline language remain consistent.
- Every scene changes at least two meaningful variation axes.
- No image is a near-duplicate of an earlier image in the batch or series.
- The batch feels like one sticker set rather than unrelated illustrations.
- Background modes and contextual colors are deliberate across the batch; paired `both` outputs share the same white master.
- Every accepted output has a semantic filename and a matching entry in `prompts.md`.
- Every final file exists in the stable output directory, not only in the generated-image cache.

## Correction Strategy

Retry once with a single explicit correction while repeating the complete identity and style locks. Do not stack unrelated corrections in one retry. If the retry still fails, keep the best result only when it passes every hard-fail check and disclose the visible limitation.
