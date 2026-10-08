# 金属素地（BARE METAL）

> 状態：草案（実際の生成で未確認）

塗装もメッキもない金属。ヘアライン、削り出し、バフ研磨、ブラストに使う。

- プレースホルダー：`{metal}`（aluminium / stainless steel / steel / titanium から1つ）、`{FINISH}`（下の仕上げから必ず1つ選び、英文と置き換える）
- 照明：SKILL.md の素材の対応表に従う（仕上げで変わる）

## 基本ブロック

```text
The surface is uncoated {metal}. There is no paint and no colored layer — the appearance comes from the bare metal and the studio light it reflects.

{FINISH}

FORM DEFINITION:
- Edges, chamfers, and machined steps catch thin, crisp highlight lines that trace the shape.
- Faces turning away from the light fall off to a darker, cool gray. Keep the high value contrast typical of metal.

FINISH QUALITY:
- Clean metal: no fingerprints, no water spots, no oxidation, no rust, no random scratches.
- Must read as cold, hard metal — not gray plastic, not gray paint.
```

## 仕上げ（1つ選ぶ）

### BRUSHED（ヘアライン）

```text
FINISH — BRUSHED:
- Fine, parallel brush lines run in one direction, following the direction in the reference.
- Anisotropic reflection: highlights stretch into long, soft streaks perpendicular to the brush lines.
- Neutral, cool mid-gray base tone. Not a mirror, not matte.
- The lines are fine and uniform — not scratches, not random swirls.
```

### MACHINED（削り出し）

```text
FINISH — MACHINED:
- Freshly machined metal: bright and fairly reflective, with tool paths that follow the reference (concentric rings on turned faces, straight passes on milled faces).
- Tool paths are visible inside the highlights and fade in the shadow areas.
```

### POLISHED（バフ研磨・鏡面）

```text
FINISH — POLISHED:
- Mirror-like polished metal, slightly softer and warmer than chrome. Reflections are clear but slightly less crisp.
- Define the form with light-dark-light reflection banding: a clean bright streak, a darker band, then a lighter band near the lower edge.
- Reflected environment shows only abstract soft studio gradients. No room, window, camera, or person.
```

### BEAD-BLASTED（ブラスト・梨地）

```text
FINISH — BEAD-BLASTED:
- Uniform, fine satin grain over the whole surface. A broad, soft sheen with no defined reflection.
- Even light-to-mid gray, slightly lighter on faces toward the key light.
```
