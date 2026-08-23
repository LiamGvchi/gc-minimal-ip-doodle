# GC 极简 IP 手绘

[English](README.md)

这是一个用于 Codex 的视觉生成 Skill：在保留角色身份与核心识别特征的前提下，将角色重绘为留白充足、平涂、略带手绘感的贴纸小插画。

它适合吉祥物、玩具、动物角色与 IP 角色参考图，也适合需要连续生成多个统一风格生活场景的任务。

![内置原创风格参考](assets/style-references/original-pebble-sprout-white.png)

## 它能做什么

- 从用户提供的角色参考图中建立身份锁定信息。
- 保留轮廓、身体结构、标志性色块、配件和基础表情。
- 先规划有实质差异的场景，避免只替换道具或颜色。
- 支持纯白底和克制的浅色轻颗粒背景。
- 每次单独生成一张，并按照固定质量清单检查结果。
- 用语义化文件名保存成品，同时在 `prompts.md` 中记录提示词。

## 调用示例

```text
使用 $gc-minimal-ip-doodle 把这个角色做成五张不同生活场景的极简手绘插画。

把这个角色做成三张极简手绘贴纸，白底，不要文字。

保持角色身份不变，再生成五张不重复的生活场景，并同时给我白底和浅色轻颗粒版。
```

角色参考图是必需输入。其他未说明的设置会按照 [SKILL.md](SKILL.md) 中的保守默认值执行。

## 使用条件

- 具备图像生成和图像查看能力的 Codex 环境。
- 一张可读取的本地或对话附件角色参考图。
- 用户拥有角色参考图，或者已经取得相应使用许可。

## 安装方法

克隆或下载本仓库，将整个 `gc-minimal-ip-doodle` 文件夹放入 Codex Skills 目录：

```text
~/.codex/skills/gc-minimal-ip-doodle/
```

不要拆散目录结构。`SKILL.md`、`references/`、`assets/` 和 `agents/` 都属于运行时包的一部分。

如果没有立即显示，可以重启 Codex，然后通过 `$gc-minimal-ip-doodle` 调用，或者直接描述符合该能力范围的角色重绘任务。

## 项目结构

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

## 权利与素材来源

请只使用自己拥有或已经取得授权的角色参考图。生成结果不会自动赋予用户第三方角色、Logo 或商标的相关权利。

内置视觉参考图的用途和来源已经单独记录。重新分发或修改项目前，请阅读 [ASSET_PROVENANCE.md](ASSET_PROVENANCE.md)。

## 许可证

除非另有说明，本仓库当前版本采用 [PolyForm Noncommercial License 1.0.0](LICENSE)。仅允许非商业目的的使用、修改和再分发；商业使用必须另行取得维护者的书面许可。

许可证只覆盖贡献者有权许可的内容，不授予用户后来提供的角色参考图所涉及的任何权利。

许可证历史：首次公开提交 `5eab276` 采用 MIT License。当前许可证变更不会撤回已经就该历史版本授予的权利。
