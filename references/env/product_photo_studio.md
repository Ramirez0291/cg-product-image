# 商品撮影スタジオ（Amazon.co.jp 向け）

背景を1つ選び、その背景の BACKGROUND・SHADOW・OUTPUT・NEGATIVE を使う。CAMERA は共通。LIGHTING は主素材で選ぶ（SKILL.md の素材の対応表）。

| 背景 | 用途 |
|---|---|
| 白（WHITE） | Amazon メイン画像。背景は純白（RGB 255）、商品は画面の85%以上 |
| グレー（GRAY） | サブ画像。周辺を暗くして商品に視線を集め、質感を見せる |

## 白背景（WHITE）

### BACKGROUND

```text
Seamless pure white background, RGB 255,255,255, perfectly even, no gradient, no visible seam, no floor line.
```

### SHADOW

```text
A single soft contact shadow directly beneath the product, 20-30% opacity, tightly feathered, occupying a small footprint. No long cast shadow. The shadow must not spread across the frame or gray out the background.
```

### OUTPUT

細長い商品（レバー、マフラー、ケーブルなど）は、"product occupies 88% of the frame" を "the product's longest side spans 88% of the frame" に置き換える。面積で88%は埋まらないため。

```text
4K resolution, square 1:1, product occupies 88% of the frame, centered.
Photorealistic. Sharp micro-texture. No plastic AI smoothing.
```

### NEGATIVE

```text
No text, no watermark, no logo overlay, no props, no accessories, no hands,
no reflection of the studio, photographer, or lighting equipment as recognizable
shapes. No colored background. No vignette.
```

## グレー背景（GRAY）

### BACKGROUND

```text
Clean neutral gray seamless backdrop. Center tone around RGB 90,90,92, falling off smoothly to RGB 38,38,40 at the corners — a stylized dark vignette that draws the eye to the product. No texture, no pattern, no props.
```

### SHADOW

```text
Soft directional shadow falling to the lower-right on the gray surface, grounding the product. Subtle surface reflection beneath the product, 15% opacity, fading out within a short distance.
```

### OUTPUT

`{1:1 / 4:5}` は、他の指示がなければ 1:1 にする。

```text
4K resolution, {1:1 / 4:5}. Product occupies 75% of the frame.
Photorealistic, magazine-grade commercial quality.
```

### NEGATIVE

```text
No text overlay, no watermark, no colored gels, no smoke, no water splash,
no unrelated props, no studio equipment visible.
```

## CAMERA（共通）

元画像の角度を保つ。角度を変えると、元画像に写っていない面をAIが想像で描くため。

```text
Keep the camera angle, perspective, and product orientation of the reference image. 85mm macro equivalent, f/11, deep focus — the entire product is tack sharp front to back.
```

### ANGLE CHANGE

他の指示で角度の変更を求められたときだけ使う。上の1文目（Keep the camera angle ...）と置き換える。2文目（85mm ...）は残す。具体的な角度の指示があるときの書き方と、出力の注意は SKILL.md の「他の指示を反映する」に従う。

```text
Slight three-quarter angle showing the primary face and one side to convey depth. Eye-level to 15 degrees above.
```

## LIGHTING

主素材で1つ選ぶ。どれを選ぶかは SKILL.md の素材の対応表の「照明」列に従う。

### DEFAULT

```text
- Key: large 120cm softbox, 45 degrees front-left, high position
- Fill: white bounce card at front-right, 1.5 stops under key
- Rim: narrow strip light from behind-left for edge separation from the background
- Negative fill: black flag on the right to carve out the form
- Overall: high-key but NOT flat. Retain a full tonal range on the product.
```

### MATTE

マット系の素材用。影のグラデーションとリムライトで立体感を出す。

```text
- Key: very large 150cm softbox, 40 degrees front-left, positioned close to the subject for a long, gentle shading gradient across the form.
- Fill: 2 stops under key. Do NOT flatten the shading — the gradient is the only thing conveying volume on a matte surface.
- Rim: MANDATORY. A narrow strip light from behind-left creating a clear bright edge along the silhouette. Without this, the matte product loses its outline against the background.
- Grazing raker: one low-intensity light skimming across the surface at a very shallow angle to reveal the surface micro-texture on the raking side only.
- No bare hard lights. No specular hotspots anywhere on the product.
```

### REFLECTIVE

> 状態：草案（実際の生成で未確認）

光沢塗装・メタリック・メッキなど、映り込みで形が見える素材用。少数の大きな光源と黒い板で、明暗の帯を作る。

```text
- Key: large strip softbox above the product, slightly front-left, running along its length — creates one clean, elongated highlight streak along the upper curvature.
- Edge lights: two tall, narrow strip softboxes behind the product, left and right — they trace the silhouette with thin bright edges.
- Negative fill: black flags on both sides and below the camera axis — they appear in the surface only as soft dark bands that define the form, never as recognizable equipment shapes.
- Fill: large white bounce card in front, low intensity, to lift the lower reflection band.
- Few, large, controlled reflections. No bare point lights, no scattered small hotspots.
- How sharp these reflections look depends on the surface — follow the SURFACE / MATERIAL block.
```
