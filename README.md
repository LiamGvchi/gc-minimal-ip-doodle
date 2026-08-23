# GC Minimal IP Doodle

[中文说明](README.zh-CN.md)

A Codex Skill that preserves a character's recognizable identity while redrawing it as a sparse, flat, hand-drawn sticker illustration.

It is designed for mascot, toy, animal, and IP-character references that need consistent visual treatment across multiple small everyday scenes.

![Bundled original style reference](assets/style-references/original-pebble-sprout-white.png)

## What it does

- Builds an identity lock from the supplied character reference.
- Keeps silhouette, anatomy, signature colors, accessories, and baseline expression recognizable.
- Plans genuinely distinct scenes instead of producing simple prop or color swaps.
- Supports pure white and restrained soft-grain background modes.
- Generates one image per call and checks every result against a fixed quality gate.
- Saves accepted files with semantic names and records prompts in `prompts.md`.

## Example requests

```text
Use $gc-minimal-ip-doodle to turn this character into five different everyday scenes.

把这个角色做成三张极简手绘贴纸，白底，不要文字。

保持角色身份不变，再生成五张不重复的生活场景，并同时给我白底和浅色轻颗粒版。
```

The character reference image is required. Other omitted settings use conservative defaults defined in [SKILL.md](SKILL.md).

## Requirements

- Codex with image-generation and image-inspection capabilities.
- A readable local or attached character-reference image.
- Permission to use the supplied character reference.

## Installation

Clone or download this repository and place the complete `gc-minimal-ip-doodle` folder in your Codex Skills directory:

```text
~/.codex/skills/gc-minimal-ip-doodle/
```

Keep the directory structure intact. `SKILL.md`, `references/`, `assets/`, and `agents/` are all part of the runtime package.

Restart Codex if the Skill does not appear immediately, then invoke it as `$gc-minimal-ip-doodle` or describe a matching character-redraw request naturally.

## Package structure

```text
gc-minimal-ip-doodle/
├── README.md
├── README.zh-CN.md
├── SKILL.md
├── LICENSE
├── ASSET_PROVENANCE.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── prompt-template.md
│   ├── quality-checklist.md
│   └── style-guide.md
└── assets/
    ├── source-svg/
    └── style-references/
```

## Rights and provenance

Only use character references you own or have permission to use. Generated output does not create rights in a third-party character, logo, or trademark.

The bundled visual references have documented roles and provenance. See [ASSET_PROVENANCE.md](ASSET_PROVENANCE.md) before redistributing or modifying the package.

## License

Except where otherwise noted, the current version of this repository is licensed under the [GNU Affero General Public License v3.0 only (AGPL-3.0-only)](LICENSE). Commercial use is permitted, but redistribution and modified network-interactive deployments must comply with the AGPL source-code and license obligations.

The license applies only to material the contributors have the right to license. It does not grant rights in character references later supplied by users.

License history: the initial public commit `5eab276` was released under the MIT License, and commit `8d2ee44` changed the then-current version to PolyForm Noncommercial 1.0.0. Those earlier grants are not withdrawn for copies received under their respective terms. The current `main` branch uses AGPL-3.0-only.
