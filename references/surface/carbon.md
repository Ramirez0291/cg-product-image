# カーボン（CARBON FIBER）

> 状態：草案（実際の生成で未確認）

- プレースホルダー：`{weave}`（元画像の柄が斜めなら 2x2 twill weave、市松なら plain weave）。CARBON-LOOK は `{base}` と `{gloss / matte}`
- 照明：ツヤあり＝REFLECTIVE、マット＝MATTE

本物のカーボンか、カーボン調（印刷・水圧転写・シート）かを必ず区別する。カーボン調を本物として描くと、実物と違う画像になる。分からなければユーザーに聞く。

## 基本ブロック（本物のカーボン・ツヤあり）

```text
The surface is genuine {weave} carbon fiber under a high-gloss clear resin coat.

WEAVE:
- Keep the weave pattern, scale, and direction exactly as in the reference. Do not resize, straighten, or redraw the pattern.
- Each fiber bundle (tow) has a fine directional sheen: tows running one way catch the light while the crossing tows stay darker. This light-dark checker shifts across the curvature of the part — it is what makes real carbon read as three-dimensional, not as a printed pattern.

DEPTH:
- The weave sits beneath a thick, glass-clear resin layer. The clear coat carries its own broad, soft specular reflection on top, separate from the weave sheen below.
- Dark tows read as deep charcoal with visible fiber detail — not crushed to pure black.

FINISH QUALITY:
- No wavy or distorted weave, no pinholes, no dry spots, no resin pooling, no yellowing, no haze.
```

## バリエーション

### MATTE CARBON（マットカーボン）— 置き換え：冒頭の1文と DEPTH

```text
The surface is genuine {weave} carbon fiber under a matte clear coat.

DEPTH:
- The matte clear coat scatters light: no mirror reflection, no wet look. The tow sheen is softer and diffused, but the light-dark checker is still visible.
- Dark tows read as charcoal with visible fiber detail — not crushed to pure black.
```

### CARBON-LOOK（カーボン調：印刷・水圧転写・シート）— 置き換え：基本ブロック全体

本物のカーボン用の文（繊維束の光り方、樹脂の厚み、樹脂だまり）は使わない。このブロックだけで完結する。`{base}` は下地（plastic、metal など）、`{gloss / matte}` は仕上げのツヤ。

```text
The surface is a carbon-pattern finish (printed, hydrographic, or an applied film) on a smooth {base}, under a {gloss / matte} clear coat. It is not genuine carbon fiber.

PATTERN:
- Keep the pattern, scale, and direction exactly as in the reference. Do not resize, straighten, or redraw it.
- The pattern is flat: it does not show the directional tow sheen of real carbon fiber. The only reflection comes from the clear coat — a broad, soft reflection for gloss, a diffused low sheen for matte.
- If the reference shows a film edge or a step at the border, keep it.

FINISH QUALITY:
- No distorted or smeared pattern, no bubbles, no peeling edges, no haze.
```
