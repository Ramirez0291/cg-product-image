# マット塗装（MATTE）

- プレースホルダー：`{color}`
- 照明：MATTE（SEMI-GLOSS だけ DEFAULT）

## 基本ブロック

```text
The surface is a fully matte {color} painted finish. Diffuse reflection dominates; there is no clear coat and no mirror layer.

HIGHLIGHT BEHAVIOR:
- No defined specular highlight. The light source shape is NEVER reflected.
- Instead: a broad, low-intensity brightening across the surfaces facing the key light, with completely feathered, edgeless falloff.
- Highlight zone stays well below RGB 235 — matte surfaces never approach white.
- The base color remains fully saturated inside the lit zone; it does not wash out.

FORM DEFINITION — the terminator carries the volume:
- Build three-dimensionality through a long, smooth, gradual shading gradient from the lit face into the shadow side. The terminator is soft and extended, not a sharp edge.
- This gradient, not any highlight, is what makes the object read as solid.

GRAZING SHEEN — mandatory, prevents a clay/CG look:
- At extreme grazing angles along the silhouette edges and along raised ridges, a faint, narrow sheen appears where the matte surface catches light at a shallow incidence. Subtle — a whisper of light, not a highlight.
- Without this the surface will read as unlit clay. Include it.

MICRO-TEXTURE:
- Fine, even granular powder-coat texture, visible ONLY under grazing light on the raking side. Invisible on surfaces facing the camera directly.
- Uniform and manufactured — not dusty, not scratched, not weathered, not fabric.

FINISH QUALITY:
- Even, consistent matte across the whole part. No glossy patches, no shiny wear spots, no fingerprints, no chalky bloom, no faded or sun-bleached appearance.
- Deep, rich color. Matte does not mean desaturated.
```

## バリエーション

### SMOOTH（粒のない、なめらかなマット塗装）— 置き換え：MICRO-TEXTURE

基本ブロックは粉体塗装の粒状の肌を描く。元画像で粒が見えない塗装に使うと、実物にない肌を足してしまうため、こちらに置き換える。

```text
MICRO-TEXTURE:
- Smooth, fine matte paint skin with no visible grain, even under grazing light.
- Uniform and manufactured — not dusty, not scratched, not weathered, not fabric.
```

### SEMI-GLOSS（半ツヤ・サテン）— 置き換え：冒頭の1文と HIGHLIGHT BEHAVIOR

```text
The surface is a satin (semi-gloss) {color} painted finish — an intermediate surface between matte and gloss.

HIGHLIGHT BEHAVIOR:
- A soft, broad specular reflection IS present but heavily diffused — the softbox shape is vaguely suggested as a blurred bright region, never sharply mirrored.
- Sheen level roughly 30-40 gloss units: more reflective than flat matte, clearly less than a clear-coated gloss finish.
- The base color remains fully saturated inside the lit zone; it does not wash out.
```

### MATTE METALLIC（マットメタリック）— 置き換え：冒頭の1文と MICRO-TEXTURE

```text
The surface is a matte metallic {color} finish: aluminium flake suspended beneath a matte topcoat. There is no gloss layer and no mirror reflection.

MICRO-TEXTURE:
- The flake produces a soft, diffused metallic shimmer rather than discrete pinpoint glints — the matte layer scatters the flake reflection.
- Flip-flop is present but muted compared to a gloss metallic.
- Reads as a dry, powdery metal sheen. No wet look, no mirror.
```

### SOFT-TOUCH（ラバー塗装・ソフトタッチ）— 置き換え：MICRO-TEXTURE

```text
MICRO-TEXTURE:
- Soft-touch rubberized coating: a velvety, slightly light-absorbing surface with a subtle velvet-like falloff at the edges (light scatters more at grazing angles than the center). Reads as soft and grippy rather than hard.
```

### MATTE BLACK（マットブラック）— 追加

`{color}` は black にする。

```text
MATTE BLACK:
- Matte black reads as a range of dark grays, NOT as flat pure black. Lit surfaces sit around RGB 60-85; shadow areas hold detail at RGB 25-40. Nothing crushes to 0.
- Panel lines, screw heads, edges, and surface transitions must all remain legible.
- The grazing sheen along the silhouette is what separates the part from the background — make it clearly present.
```
