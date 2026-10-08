# 修復（RESTORATION）

使う場面：元画像に、ぶれ・ピンぼけ、色かぶり、低解像度、フラッシュの白飛びがあるとき（元画像で見えた、またはユーザーが説明した）。

## 使い方

**修復だけ（背景も照明も変えない）**
下の英文を全文そのまま使う。冒頭文・FIDELITY LOCK・env のブロックは入れない（この英文に同じ内容が含まれている）。

**加工と一緒に使う（背景や照明も変える）**
- 見出しを `[RESTORATION]` にする。最初の2文と Output の行は入れない（冒頭文・OUTPUT と重なる）。
- DO は、実際にある問題に対応する行だけを入れる。問題のない行を入れると、不要な処理が起きる（例：白飛びがないのに "Suppress ... specular clipping" を入れると、光沢のハイライトまで抑えられる）。

  | 問題 | DO の行 |
  |---|---|
  | ぶれ・ピンぼけ | 1行目（Remove blur ...） |
  | 色かぶり | 2行目（Correct the color cast ...） |
  | 低解像度 | 3行目（Upscale to 4K ...） |
  | フラッシュの白飛び | 4行目（Suppress blown-out ...） |

- DO NOT は4行とも入れ、次の2行を置き換える。元の文は背景・照明の変更、新しい影や映り込みと矛盾するため。
  - 2行目 → `- Change the camera angle or the product orientation`（CAMERA を角度変更にしたときは、この行ごと削除する）
  - 4行目 → `- Invent product details that are not visible in the source image; if a region is unreadable, keep it neutral`
- 色かぶりを直すときは、[RESTORATION] ブロックの1行目（DO の前）に次の一文を入れる。FIDELITY LOCK の「元画像の色を保つ」によって、かぶったままの色が残るのを防ぐ。FIDELITY LOCK のすぐ後に置くことで、色の基準が「実物の色」だと伝わる。`{cast}` はかぶりの色（yellow、green、blue など）、`{color}` は実物の色。
  `The {cast} tint in the reference photo is a color cast, not the product color. Render the product in its true {color}.`

## 英文

```text
Restore this product photograph. This is a technical restoration task, NOT a creative reinterpretation.

DO:
- Remove blur and motion softness; recover sharp micro-detail on edges, seams, screws, and text
- Correct the color cast to neutral white balance (D55, 5500K); remove the green/yellow/blue tint
- Upscale to 4K with clean, non-plastic detail; no AI smoothing, no waxy surfaces
- Suppress blown-out flash hotspots and reflected specular clipping; recover the underlying surface

DO NOT:
- Change the geometry, proportions, part count, or assembly of the product
- Change the background, camera angle, framing, or lighting direction
- Add, remove, or redraw any logo, printed text, model number, or label
- Invent details that are not visible in the source image; if a region is unreadable, keep it neutral

Output: the same photograph, technically repaired.
```
