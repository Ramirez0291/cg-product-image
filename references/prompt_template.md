# プロンプトの組み立て

## 順番

| # | ブロック | 出典 | 入れる条件 |
|---|---|---|---|
| 1 | 冒頭文 | このファイル | 常に |
| 2 | [FIDELITY LOCK — highest priority] | このファイル | 常に |
| 3 | [RESTORATION] | restoration.md | 修復が必要なとき |
| 4 | [BACKGROUND] | env | 常に |
| 5 | [SHADOW] | env | 常に |
| 6 | [CAMERA] | env | 常に |
| 7 | [LIGHTING] | env | 常に |
| 8 | [MATERIAL MAP] | このファイル | 素材が複数のとき |
| 9 | [SURFACE / MATERIAL — ...] | surface | 素材ごとに1つ。主素材が先、副素材は面積の大きい順 |
| 10 | [ADDITIONAL] | 他の指示、restoration.md | 入れる文があるとき |
| 11 | [OUTPUT] | env | 常に |
| 12 | [NEGATIVE] | env | 常に |
| 13 | [FIX] | troubleshooting.md | 生成結果を直すとき |

修復だけを行う（背景も照明も変えない）ときは、この順番を使わない。`restoration.md` の「修復だけ」に従う。

## 書き方

- 各ブロックは `[見出し]` の行と本文で作る。ブロックの間は空行1つ。
- 見出しは英語の大文字で書く。画像生成AIがブロックの区切りを認識しやすい。
- Markdown の見出し（`#`）や日本語の注記はプロンプトに入れない。
- バリエーションの英文は、その素材ブロックの中に入れる。

## 冒頭文

```text
Edit the attached reference photo into professional studio product photography — a commercial e-commerce packshot.
The goal is to reveal the true surface material of this exact product through lighting and rendering. Do not redesign or replace the product.
```

## FIDELITY LOCK

```text
[FIDELITY LOCK — highest priority]
Preserve the exact geometry, proportions, part count, surface pattern, printed text,
logos, and color of the subject in the reference image. Do not redesign, stylize,
simplify, or add any component. This must remain a truthful representation of the
physical product.
```

## MATERIAL MAP

素材が複数のときだけ入れる。部位ごとに1行。部位名は素材ブロックの見出しと同じにする。最後の1文はそのまま使う。

```text
[MATERIAL MAP]
- {部位}: {素材}
- {部位}: {素材}
Each SURFACE / MATERIAL block below applies only to its named part. Do not carry one part's color or finish onto another part.
```

## 記入例

入力：撮影環境＝商品撮影スタジオ、背景＝白、素材＝本体はマットブラック塗装（粉体塗装）・ボルト4本はクロームメッキ、他の指示＝ホコリを消す、修復なし。

`<< >>` の部分には、記載どおりモジュールの英文をそのまま入れる。実際のプロンプトに `<< >>` を残さない。

```text
Edit the attached reference photo into professional studio product photography — a commercial e-commerce packshot.
The goal is to reveal the true surface material of this exact product through lighting and rendering. Do not redesign or replace the product.

[FIDELITY LOCK — highest priority]
Preserve the exact geometry, proportions, part count, surface pattern, printed text,
logos, and color of the subject in the reference image. Do not redesign, stylize,
simplify, or add any component. This must remain a truthful representation of the
physical product.

[BACKGROUND]
Seamless pure white background, RGB 255,255,255, perfectly even, no gradient, no visible seam, no floor line.

[SHADOW]
A single soft contact shadow directly beneath the product, 20-30% opacity, tightly feathered, occupying a small footprint. No long cast shadow. The shadow must not spread across the frame or gray out the background.

[CAMERA]
Keep the camera angle, perspective, and product orientation of the reference image. 85mm macro equivalent, f/11, deep focus — the entire product is tack sharp front to back.

[LIGHTING]
- Key: very large 150cm softbox, 40 degrees front-left, positioned close to the subject for a long, gentle shading gradient across the form.
- Fill: 2 stops under key. Do NOT flatten the shading — the gradient is the only thing conveying volume on a matte surface.
- Rim: MANDATORY. A narrow strip light from behind-left creating a clear bright edge along the silhouette. Without this, the matte product loses its outline against the background.
- Grazing raker: one low-intensity light skimming across the surface at a very shallow angle to reveal the surface micro-texture on the raking side only.
- No bare hard lights. No specular hotspots anywhere on the main clamp body.
- For the mounting bolts: a strip light and a black flag positioned to create clean light-dark reflection banding.

[MATERIAL MAP]
- main clamp body: matte black powder-coated paint
- mounting bolts: mirror chrome plating
Each SURFACE / MATERIAL block below applies only to its named part. Do not carry one part's color or finish onto another part.

[SURFACE / MATERIAL — MAIN CLAMP BODY: MATTE BLACK PAINT]
The main clamp body is a fully matte black painted finish. Diffuse reflection dominates; there is no clear coat and no mirror layer.

<<matte.md 基本ブロックの HIGHLIGHT BEHAVIOR から FINISH QUALITY までをそのまま>>

MATTE BLACK:
<<matte.md の MATTE BLACK の箇条をそのまま>>

[SURFACE / MATERIAL — MOUNTING BOLTS: CHROME]
The mounting bolts are true mirror chrome. Chrome has no color of its own — its appearance is entirely the reflection of the studio environment. Build the form through reflection banding, not through painted shading.
- Keep the plating flawless: no pitting, no orange peel, no haze, no fingerprints.

[ADDITIONAL]
Remove dust. Keep machining marks, surface texture, and molded details.

[OUTPUT]
4K resolution, square 1:1, product occupies 88% of the frame, centered.
Photorealistic. Sharp micro-texture. No plastic AI smoothing.

[NEGATIVE]
No text, no watermark, no logo overlay, no props, no accessories, no hands,
no reflection of the studio, photographer, or lighting equipment as recognizable
shapes. No colored background. No vignette.
```

この例で行った調整：
- 部位名は冠詞なし（main clamp body、mounting bolts）。ボルトは複数形なので "are"。
- 主素材（本体）はモジュール全文。副素材（ボルト）は、冒頭の段落の全文と、欠点を "no ..." で並べた箇条1行（chrome.md には FINISH QUALITY の見出しがないため）。
- MATTE 照明の最後の行を本体だけに絞り、ボルト用の1行を足した。
- [ADDITIONAL] はユーザーが挙げたもの（ホコリ）だけを消し、加工跡や質感を残す一文を続けた。
