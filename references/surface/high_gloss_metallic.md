# メタリック塗装（HIGH-GLOSS METALLIC）

- プレースホルダー：`{color}`、`{fine / medium}`（フレークの粗さ。元画像で粒が見分けられなければ fine）
- 照明：REFLECTIVE

## 基本ブロック

```text
The surface is a three-layer automotive metallic finish: an aluminium-flake metallic base coat, a {color} tinted layer, and a transparent high-gloss clear coat. Render all three layers as physically distinct.

TWO SEPARATE HIGHLIGHT LAYERS — this is critical:
- Upper layer: the clear coat's specular reflection. Sharp-ish, achromatic (white), sitting ON the surface plane, with the softbox shape suggested.
- Lower layer: a broad, colored metallic glow rising from BENEATH the clear coat, offset from the specular and softer. The color stays saturated inside this glow.

FLIP-FLOP (travel) — the source of three-dimensionality:
- Surfaces facing the key light read bright and luminous with strong flake activation.
- Surfaces angled away fall off steeply into a deep, saturated, darker tone — a stronger falloff than solid paint would produce.
- This face-to-flop contrast, not painted shading, defines the form.

FLAKE STRUCTURE:
- Fine aluminium flake, {fine / medium}, visible as discrete pinpoint glints only where direct light strikes — dense in the highlight zone, sparse and extinguished in the flop and shadow zones.
- The flakes are suspended below the clear coat, not sitting on top.
- NOT glitter, NOT sparkle overlay, NOT noise, NOT sandpaper texture.

FINISH QUALITY:
- Mirror-smooth clear coat: no orange peel, no dust nibs, no swirl marks, no haze.
- Shadow side retains color and flake structure — do not crush to black.
```

## バリエーション

### PEARL（パール塗装）— 置き換え：冒頭の段落と FLAKE STRUCTURE

> 状態：草案（実際の生成で未確認）

`{fine / medium}` は使わない。

```text
The surface is a three-layer pearl finish: a {color} base coat, a mica pearl layer, and a transparent high-gloss clear coat. Render all three layers as physically distinct.

PEARL STRUCTURE:
- Mica pearl pigment instead of aluminium flake: a soft, silky, continuous glow rather than discrete pinpoint glints.
- A subtle hue shift on faces turning away from the light, only as strong as visible in the reference.
- NOT glitter, NOT sparkle overlay, NOT an iridescent rainbow.
```
