# cg-product-image

[中文](README.zh.md) | [English](README.en.md) | [日本語](README.ja.md)

**为图像生成 AI 编写提示词，按实物原样呈现商品照片的表面材质质感。**
**Writes image-generation prompts that bring out the true surface material of a product photo.**

根据原图和你指定的拍摄环境、背景、材质、其他要求，生成可粘贴到 Nano Banana、GPT Image 等工具的英文提示词。不改变形状、颜色和 Logo，只改变打光和表面呈现。

From a reference photo plus your shooting environment, background, material, and other instructions, it builds an English prompt for Nano Banana, GPT Image, and similar tools. Shape, color, and logos stay the same; only lighting and surface rendering change.

## 语言 / Languages

支持中文、日语、英语提问；说明使用你的语言，提示词始终为英文。
Ask in Chinese, Japanese, or English. Explanations follow your language; the prompt is always English.

## 使用方法 / Usage

把本文件夹放入 skills 目录并重启会话（Claude Code：`~/.claude/skills/cg-product-image`）。
Put this folder in your skills directory and restart the session.

> 用 cg-product-image 帮我写提升这张图质感的提示词。摄影棚，白底，主体是哑光黑漆，螺丝是电镀。
>
> Use cg-product-image to improve the material look of this photo. Studio, white background, matte black paint body, chrome bolts.

## 输入 / Inputs

| 项目 / Item | 内容 / Options |
|---|---|
| 原图 / Reference image | 要加工的商品照片 / The product photo to edit |
| 拍摄环境 / Shooting environment | 商品摄影棚 / Product photo studio |
| 背景 / Background | 白底（Amazon 主图）、灰底（副图）/ White (main image), Gray (secondary) |
| 材质 / Material | 哑光漆、亮光漆、金属漆、电镀、阳极氧化、金属原色、碳纤维、塑料、橡胶、面料、皮革 / Matte, gloss, metallic, chrome, anodized, bare metal, carbon, plastic, rubber, fabric, leather |
| 其他要求 / Other | 比例、商品大小、修复等（可选）/ Aspect ratio, size, restoration (optional) |

## 输出 / Output

- 输入确认表 / Input summary
- 英文提示词 / English prompt
- 生成后检查与修正用的一行 / Post-generation checklist with one-line fixes

## 详细说明 / Details

- 中文：[README.zh.md](README.zh.md)
- English: [README.en.md](README.en.md)
- 日本語：[README.ja.md](README.ja.md)

## 注意 / Caution

请务必将生成图与原图对比，形状、Logo、颜色变化的图片不要用于商品页面。
Always compare the result with the reference. Don't use an image whose shape, logo, or color changed on a product page.

## 许可证 / License

GNU AGPL-3.0（[LICENSE](LICENSE)）. Author: Rami0291
