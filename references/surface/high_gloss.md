# 光沢塗装（HIGH-GLOSS PAINTED）

- プレースホルダー：`{color}`
- 照明：REFLECTIVE

## 基本ブロック

```text
The surface is a two-layer automotive-grade finish: a deeply saturated {color} base coat beneath a transparent high-gloss clear coat. Render both layers distinctly.

- The base color must stay rich and saturated even inside the highlight — the gloss layer sits ON TOP of the color, it does not wash it out.
- Specular highlight: a broad, soft-edged softbox reflection with feathered falloff. Unlike chrome, this reflection is diffused — the light source shape is suggested, not mirrored sharply.
- Add a subtle Fresnel sheen along the silhouette edges, where the clear coat catches grazing light.
- Wet-look depth: the clear coat should read as having physical thickness.
- Perfectly smooth: no orange peel, no dust nibs, no swirl marks, no matte patches.
- Shadow side retains color and detail — do not crush to black.
```

## バリエーション

### GLOSS BLACK（グロスブラック・ツヤ黒）— 追加

`{color}` は black にする。

```text
GLOSS BLACK:
- Gloss black reads as dark charcoal gray with a single controlled highlight, not as flat pure black. Preserve edge and panel detail in the shadow areas.
```

### MIXED MATTE AREAS（一部がマット）— 追加

光沢塗装の中に、マットの部分がある商品に使う。`{部位}` にマット部分を英語で書く。マット部分が大きいときは、matte.md を副素材として使う。

```text
MIXED MATTE AREAS:
- The {部位} is matte powder-coated: broad, low-intensity diffuse reflection with no distinct light-source shape. Fine granular micro-texture visible under grazing light.
```

### CANDY（キャンディ塗装）— 置き換え：冒頭の段落と最初の箇条

基本ブロックの最初の箇条は "base color" を色の層として書いている。キャンディでは base が下地の金属層を指すため、ここで置き換える。

```text
The surface is a candy finish: a transparent {color}-tinted layer over a bright metallic base, under a high-gloss clear coat. Color depth increases with layer thickness — edges and curved falloff areas read deeper and more saturated than the flat facing surfaces.

- The {color} tint must stay rich and saturated even inside the highlight — the gloss layer sits ON TOP of the color, it does not wash it out.
- The metallic base glows through the tint as smooth, luminous depth — NOT glitter, NOT a sparkle overlay.
```
