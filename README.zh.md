# cg-product-image

[中文](README.zh.md) | [English](README.en.md) | [日本語](README.ja.md)

**一个技能：为图像生成 AI 编写提示词，按实物原样呈现商品照片的表面材质质感。**

根据现有商品照片（原图）以及拍摄环境、背景、材质和其他要求，组装可直接粘贴到 Nano Banana、GPT Image 等工具中的英文提示词。不改变形状、颜色和 Logo，只改变打光和表面的呈现方式。

- **突出质感，不改变材质。** 哑光保持哑光，塑料保持塑料，只把材质本来的样子表现清楚。
- **忠于实物。** 每条提示词都包含 FIDELITY LOCK（锁定形状、零件数量、颜色和 Logo 的指令）。
- **附带修正方法。** 给出生成后要检查的地方，以及效果不好时追加的一行英文。

## 支持的语言

可以用中文、日语或英语提出需求。确认表、提问和检查项会使用你的语言；交给图像生成 AI 的提示词始终是英文。

## 使用方法

把本文件夹放入代理的 skills 目录，然后重启会话（Claude Code：`~/.claude/skills/cg-product-image`）。

> 用 cg-product-image 帮我写一个提升这张图质感的提示词。摄影棚，白底，主体是哑光黑漆，螺丝是电镀。

把生成的提示词和原图一起交给图像生成 AI。

## 输入

| 项目 | 内容 |
|---|---|
| 原图 | 要加工的商品照片 |
| 拍摄环境 | 商品摄影棚 |
| 背景 | 白底（Amazon 主图）／灰底（副图） |
| 材质 | 哑光漆、亮光漆、金属漆、珠光漆、电镀、阳极氧化、金属原色（拉丝、CNC 切削、抛光、喷砂）、碳纤维、塑料、橡胶、面料、皮革 |
| 其他要求 | 画面比例、商品大小、是否需要修复等（可选） |

缺少的项目会一次性集中询问。

## 输出

- 输入确认表（包括推定或假设的内容）
- 英文提示词
- 生成后的检查点，以及用于修正的一行英文

## 目录结构

```text
SKILL.md                        步骤、输入、材质对照表、输出格式
README.md                       中英双语说明（默认）
README.zh.md / .en.md / .ja.md  各语言说明
references/
  prompt_template.md            组装顺序、固定模块、示例
  restoration.md                修复模块
  troubleshooting.md            生成后的检查与修正
  env/product_photo_studio.md   背景、阴影、相机、灯光、输出、负面提示
  surface/                      材质模块（9 种）
agents/openai.yaml              Codex 显示用元数据
```

`SKILL.md` 和 `references/` 中的说明用日语书写（供 AI 代理阅读），英文提示词部分可直接使用。

## 添加模块

- **材质**：在 `references/surface/` 中新增一个文件。英文按「定义句 → HIGHLIGHT BEHAVIOR → FORM DEFINITION → MICRO-TEXTURE → FINISH QUALITY」的顺序书写，并在 `SKILL.md` 的材质对照表中加一行。
- **拍摄环境**：在 `references/env/` 中新增一个文件。参照 `product_photo_studio.md`，按背景分别写 BACKGROUND、SHADOW、OUTPUT、NEGATIVE，再写 CAMERA 和 LIGHTING。
- 在实际生成中验证之前，在文件开头标注「状態：草案」（草稿）；验证后删除。

## 注意

请务必将生成图与原图对比。如果把形状、Logo 或颜色发生变化的图片用于商品页面，展示内容就会与实物不符。

## 许可证

GNU AGPL-3.0（全文：[LICENSE](LICENSE)）。作者：Rami0291
