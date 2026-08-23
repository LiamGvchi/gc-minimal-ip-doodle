# Prompt Construction

Build prompts from stable identity information first, then a variable scene block, then the fixed style lock.

## Identity Extraction

Write a compact internal record:

```text
Character class: <species or IP type>
Silhouette: <dominant shape and head/body ratio>
Feature geometry: <eyes, mouth, muzzle, ears, fins, antenna, limbs>
Signature colors: <main, secondary, accent color blocks>
Distinctive features: <accessory or unusual anatomy>
Baseline mood: <quiet, sleepy, friendly, deadpan, etc.>
Identity invariants: <features that must survive every scene>
```

Use observable evidence only. Do not invent hidden costume details, backstory, or anatomy.

## Background Mode Selection

- `white` is the default when the user does not request a background.
- `soft-grain` means: first accept a white master, then edit only its background and texture using the contextual block below.
- `both` means: keep the white master and derive one `soft-grain` file from the same master.

## Single-Image Prompt

```text
Use case: style-transfer
Asset type: minimal hand-drawn character sticker illustration

Primary request: Redraw the character reference in one simple scene: <scene>.

Input images:
- Image 1: character reference; preserve identity, proportions, signature colors, and distinctive anatomy.
- Images 2-N: style references only; learn line, flat color, negative space, expression economy, and prop density. Do not copy their characters, poses, or scenes.

Character identity lock:
<identity record>

Scene/action:
<one action, pose, expression, and primary prop>

Scene/backdrop:
<background mode block>. No environment or scenery.

Style/medium:
Minimal cute hand-drawn doodle and sticker illustration. Thick black outlines with slight natural wobble. Flat poster-color treatment: each enclosed region uses one uniform opaque fill with no internal tonal variation. Very few interior lines. Quiet deadpan expression.

Composition/framing:
One small centered character or compact character-and-prop cluster, broad empty margins, full silhouette visible, not filling the canvas.

Constraints:
Keep the same character class, silhouette logic, feature placement, signature color blocks, distinctive anatomy, accessories, and baseline emotional energy. Keep props subordinate. No text unless requested.

Avoid:
Photorealism, realistic animal anatomy, 3D rendering, toy, clay, plush, fur, plastic, gradients, highlights, cast shadows, ambient shadows, uncontrolled grain, coarse texture, cinematic lighting, complex background, crowded objects, vector-logo cleanliness, watermark, and extra characters.
```

## Background Mode Blocks

### White

```text
Pure or near-white empty background with broad margins. No grain, paper texture, shadow, vignette, tint, environment, or scenery.
```

### Soft Grain Edit

Use the accepted white master as the edit target:

```text
Change only the background and surface texture. Preserve the character, props, pose, composition, proportions, colors, facial expression, black outlines, and every identity feature exactly.

Replace the white canvas with one very light, low-saturation contextual hue selected from the character palette. Keep it close to off-white and clearly separated from skin, white clothing, cream fur, and signature colors. Use no gradient, vignette, shadow, or scenery.

Add extremely fine, even, low-contrast monochrome paper-like grain at roughly 20-25% of a visibly grainy reference. Keep most grain in the background; add only a barely perceptible amount inside character fills. Keep white areas clean and black outlines crisp, solid, and dominant.

Avoid dark or saturated backgrounds, coarse speckles, film grain, colored noise, stains, fuzzy outlines, redrawing, movement, cropping, new objects, text, logos, and watermarks.
```

## Batch Scene Matrix

Before generating a batch, create an internal matrix:

| Index | Action | Pose/silhouette | Main prop | Emotional beat | Similar to earlier scene? |
|---|---|---|---|---|---|
| 01 | ... | ... | ... | ... | no |

Reject a scene when it differs from another only by prop color, hand position, or a tiny facial change.

Good variation changes at least two dimensions, for example:

- waiting for an elevator while standing and holding a queue ticket;
- lying flat while charging a signature light;
- sitting on a curb with a rice ball and coffee;
- peeking into a washing machine while crouched;
- sheltering under an undersized umbrella while walking.

Do not reuse these examples automatically. Match scenes to the current character and exclude scenes already present in the conversation or `prompts.md`.

## Prompt Archive Entry

```markdown
## 01 - <scene title>

- Character reference: `<path>`
- Output: `<filename>`
- Scene: <one sentence>
- Background mode: `<white|soft-grain>`<optional selected color>
- Retry: <none or targeted correction>

```text
<final prompt>
```
```
