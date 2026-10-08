# アルマイト（ANODIZED ALUMINIUM）

> 状態：草案（実際の生成で未確認）

- プレースホルダー：`{color}`
- 照明：DEFAULT（GLOSS ANODIZE だけ REFLECTIVE）

## 基本ブロック

```text
The surface is {color} anodized aluminium. The color is a dye sealed inside a thin, translucent oxide layer on the aluminium — it is not paint. Light passes through the tinted oxide and reflects off the metal below.

HIGHLIGHT BEHAVIOR:
- Satin metallic reflection: the softbox appears as a soft, slightly elongated bright band, not a sharp mirror image.
- Highlights are a lighter, luminous version of {color}, never pure white — except tiny pinpoint catchlights on sharp machined edges.
- The color stays saturated across the part; the highlight brightens it, it does not wash it out.

FORM DEFINITION:
- Edges and chamfers catch light as thin, crisp, bright lines. This is what makes the part read as precisely finished metal.
- Faces toward the key light read bright; faces turning away fall to a deeper {color}.

MICRO-TEXTURE:
- Follow the machining marks visible in the reference (concentric turning rings or straight milling lines), visible only inside the highlight zones. If none are visible in the reference, keep the surface a smooth, even satin.

FINISH QUALITY:
- Even, uniform color across all faces. No blotchy dye, no rainbow staining, no faded or chalky areas, no scratches, no fingerprints.
- Must read as cold, hard metal — not plastic, not paint.
```

## バリエーション

### GLOSS ANODIZE（光沢アルマイト）— 追加

```text
GLOSS ANODIZE:
- Polished before anodizing: the softbox reflection is sharper and clearer, close to tinted chrome, but always colored by the anodizing.
```

### BLACK ANODIZE（ブラックアルマイト）— 追加

`{color}` は black にする。

```text
BLACK ANODIZE:
- Black anodize reads as a deep, slightly cool charcoal with a soft metallic sheen, NOT flat pure black. Machined edges, engraving, and printed text remain legible.
```
