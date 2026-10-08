# cg-product-image

[中文](README.zh.md) | [English](README.en.md) | [日本語](README.ja.md)

**A skill that writes image-generation prompts to bring out the true surface material of a product photo.**

From an existing product photo (the reference image) plus your shooting environment, background, material, and any other instructions, it assembles an English prompt to paste into Nano Banana, GPT Image, and similar tools. Shape, color, and logos stay the same; only the lighting and surface rendering change.

- **Reveal the material, don't change it.** Matte stays matte, plastic stays plastic — the material just reads more clearly.
- **True to the product.** Every prompt includes a FIDELITY LOCK that protects shape, part count, color, and logos.
- **Fixes included.** You get a checklist for the generated image and a one-line fix to add when something goes wrong.

## Languages

Ask in English, Chinese, or Japanese. The summary, questions, and checklist come back in your language; the prompt for the image AI is always in English.

## Usage

Put this folder in your agent's skills directory and restart the session (Claude Code: `~/.claude/skills/cg-product-image`).

> Use cg-product-image to write a prompt that improves the material look of this photo. Studio, white background, matte black paint body, chrome bolts.

Give the resulting prompt to the image AI together with the reference image.

## Inputs

| Item | Options |
|---|---|
| Reference image | The product photo to edit |
| Shooting environment | Product photo studio |
| Background | White (Amazon main image) / Gray (secondary images) |
| Material | Matte paint, gloss paint, metallic and pearl paint, chrome, anodized aluminium, bare metal (brushed, machined, polished, bead-blasted), carbon fiber, plastic, rubber, fabric, leather |
| Other instructions | Aspect ratio, product size, restoration, etc. (optional) |

Missing items are asked for together, once.

## Output

- Input summary, including anything the skill assumed
- The English prompt
- What to check after generation, with a one-line fix for each issue

## Structure

```text
SKILL.md                        Workflow, inputs, material table, output format
README.md                       Chinese + English overview (default)
README.zh.md / .en.md / .ja.md  Per-language overviews
references/
  prompt_template.md            Assembly order, fixed blocks, worked example
  restoration.md                Restoration block
  troubleshooting.md            Post-generation checks and fix lines
  env/product_photo_studio.md   Background, shadow, camera, lighting, output, negative
  surface/                      Material modules (9)
agents/openai.yaml              Codex display metadata
```

The instructions in `SKILL.md` and `references/` are written in Japanese for the agent; the English prompt blocks can be used as-is.

## Adding modules

- **Material**: add one file to `references/surface/`. Write the English in this order: definition → HIGHLIGHT BEHAVIOR → FORM DEFINITION → MICRO-TEXTURE → FINISH QUALITY. Then add a row to the material table in `SKILL.md`.
- **Shooting environment**: add one file to `references/env/`. Like `product_photo_studio.md`, give BACKGROUND, SHADOW, OUTPUT, and NEGATIVE for each background, plus CAMERA and LIGHTING.
- Until a module has been checked in real generations, mark it with 「状態：草案」 (draft) at the top. Remove the mark once verified.

## Caution

Always compare the generated image with the reference. Using an image whose shape, logo, or color has changed on a product page misrepresents the product.

## License

GNU AGPL-3.0 (full text: [LICENSE](LICENSE)). Author: Rami0291
