# 布・レザー（TEXTILE / LEATHER）

> 状態：草案（実際の生成で未確認）

基本ブロックはない。下から1つ選び、全文を使う。ファスナー・バックル・ベルトなどは副素材として別に指定する。

- プレースホルダー：`{color}`、`{genuine leather / synthetic leather}`（LEATHER のみ）
- 照明：FABRIC＝MATTE、LEATHER＝DEFAULT

### FABRIC（ナイロン・ポリエステル生地）— 1つ選ぶ

```text
The surface is {color} woven synthetic fabric (nylon / polyester).

WEAVE:
- Fine weave texture visible across the surface, with the same pattern and scale as the reference (plain weave, ripstop grid, or ballistic weave). Do not change the weave scale.

HIGHLIGHT BEHAVIOR:
- Soft, low sheen. Nylon shows a faint silky sheen along folds and padded curves. No sharp reflections.

FORM DEFINITION:
- Volume comes from padding, panel shape, and soft folds. Keep the silhouette exactly as in the reference.
- Seams and stitching are crisp: individual stitches visible, stitch lines straight.

FINISH QUALITY:
- New and clean: no lint, no dust, no loose threads, no pilling.
- Smooth out temporary packing creases, but keep structural folds and the padding shape.
- Dark fabric holds weave detail — not crushed to pure black.
```

### LEATHER（本革・合皮）— 1つ選ぶ

`{genuine leather / synthetic leather}` は実物に合わせる。合皮を本革として書かない。

```text
The surface is {color} {genuine leather / synthetic leather}.

HIGHLIGHT BEHAVIOR:
- Soft, broad sheen on raised areas and curves; the grain valleys stay slightly darker.

MICRO-TEXTURE:
- Grain pattern as in the reference. Genuine leather: irregular, natural grain. Synthetic leather: uniform, regular grain with a slightly higher sheen.

FORM DEFINITION:
- Edges, piping, and stitching are crisp. Padding volume comes from soft gradients.

FINISH QUALITY:
- No scuffs, no dust, no storage creases, no cracking, no plastic-like shine.
```
