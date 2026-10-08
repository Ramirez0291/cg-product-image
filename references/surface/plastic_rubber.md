# 樹脂・ゴム（PLASTIC / RUBBER）

> 状態：草案（実際の生成で未確認）

基本ブロックはない。下から1つ選び、全文を使う。

- プレースホルダー：`{color}`
- 照明：TEXTURED PLASTIC＝MATTE、GLOSSY PLASTIC＝REFLECTIVE、RUBBER＝MATTE

### TEXTURED PLASTIC（シボ・つや消し樹脂）— 1つ選ぶ

```text
The surface is {color} injection-molded plastic with a fine textured (grained) finish.

HIGHLIGHT BEHAVIOR:
- Broad, low-contrast diffuse sheen on faces toward the key light. No sharp reflection, no light-source shape.

FORM DEFINITION:
- Form comes from a smooth shading gradient and from crisp molded edges and corners, which catch a faint, narrow highlight.

MICRO-TEXTURE:
- Fine, uniform molded grain, visible under grazing light. Follow the grain in the reference; do not add texture to areas that are smooth in the reference.

FINISH QUALITY:
- Clean and new: no dust, no lint, no scratches, no stress whitening, no fingerprints.
- Dark plastic holds detail in dark grays — not crushed to pure black.
```

### GLOSSY PLASTIC（光沢樹脂）— 1つ選ぶ

```text
The surface is smooth, glossy {color} injection-molded plastic.

HIGHLIGHT BEHAVIOR:
- A clear, slightly soft reflection of the softbox, sitting directly on the surface — no deep wet layer like a painted clear coat.
- A few large, controlled reflections. No scattered small hotspots.

FORM DEFINITION:
- Highlights follow the curvature and trace the edges. The shadow side keeps its color.

FINISH QUALITY:
- No dust, no fine scratches, no swirl marks, no fingerprints, no flow lines.
- Dark plastic holds detail in dark grays — not crushed to pure black.
```

### RUBBER（ゴム・エラストマー）— 1つ選ぶ

```text
The surface is {color} molded rubber (elastomer).

HIGHLIGHT BEHAVIOR:
- Very low, wide sheen. Rubber absorbs light; its brightest areas stay well below any plastic or metal parts.

FORM DEFINITION:
- Soft, dense volume through a gentle gradient. A faint, slightly broader sheen at grazing edges gives it a soft, grippy feel.

MICRO-TEXTURE:
- Fine matte skin. Molded patterns (grip ribs, knurling, logos) are crisp and identical to the reference.

FINISH QUALITY:
- No white bloom, no dust, no lint, no cracks, no shiny wear spots.
- Black rubber holds detail in dark grays — not crushed to pure black.
```
