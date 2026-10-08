# 生成後のチェックと修正

## 直し方

1. 生成画像を元画像と見比べる。先に「共通」の形・部品数・ロゴ・色を見て、次に素材の見え方を見る。
2. 症状に合う1行を、プロンプト末尾の `[FIX]` ブロックに足す。一度に足すのは1〜2行まで。多く足すと、ほかの指示が弱まる。
3. 再生成は元画像から行う。生成結果を次の元画像にすると、ずれが積み重なる。
4. 形やロゴのずれが2回以上続くときは、行を足すより減らす。副素材のブロック → バリエーションの行 → [ADDITIONAL] の順に削る（MATERIAL MAP の行は残す）。プロンプトが長いほど、AIが商品を描き直す余地が増える。

`{部位}` はプロンプトで使った部位名に、`{color}` は実物の色に置き換える。

## 共通

| 見るところ | 症状 | [FIX] に足す行 |
|---|---|---|
| 形・部品数 | 形が変わった、部品が増えた・減った | Match the reference exactly: same silhouette, same proportions, same part count. Change only the lighting and surface rendering. |
| ロゴ・文字 | 崩れた、別の文字になった | Keep every logo, printed text, and engraving identical to the reference. Do not redraw or retype them. |
| 色 | 色味が変わった（色かぶりを直したときは「修復」の表を使う） | Keep the product color identical to the reference; change only the lighting. |
| 部位の色 | ある部位に、別の部位の色や仕上げが移った | Each part keeps its own color and finish: the {部位} stays {color}. |
| 質感 | ツルツルのCG、プラスチックのように見える | Real photograph, not CGI. Keep natural micro-texture; no plastic AI smoothing, no waxy surfaces. |
| 白背景 | 純白でない、グレーがかる | The background must be pure white RGB 255,255,255 across the entire frame. |
| 影 | 大きい、長い | Only a small, soft contact shadow directly beneath the product. |
| 大きさ | 商品が小さい | Scale the product so it fills 88% of the frame. |
| 黒い部分 | 真っ黒に潰れた | Lift the blacks: lit faces around RGB 60-85, shadows RGB 25-40, all edges legible. |

角度を変えたとき（ANGLE CHANGE）は、「形・部品数」の行の2文目（Change only ...）を使わない。新しい角度と矛盾するため。

## 修復（restoration.md を使ったとき）

| 症状 | [FIX] に足す行 |
|---|---|
| 色かぶりが残った | Neutral white balance across the whole image: remove every trace of the {cast} tint from the product, the shadow, and the background. |
| 実物と違う色になった | Render the product in its true {color}, with neutral white balance. |
| ぶれ・ピンぼけが残った | Recover sharp, clean edges on every seam, screw, and printed character. |

## 素材別

### マット系（matte.md 全般、BEAD-BLASTED、TEXTURED PLASTIC、RUBBER、FABRIC）

| 症状 | [FIX] に足す行 |
|---|---|
| 粘土やCGのように見える、のっぺりしている | Add a faint grazing sheen along the silhouette edges and raised ridges; keep the long, soft shading gradient. |
| テカリが出た | No specular highlight anywhere on the {部位}; matte diffuse reflection only. |
| 背景に輪郭が溶ける | Strengthen the rim light: a clear, thin bright edge along the whole silhouette. |
| 実物にない粒状の肌が出た | Smooth matte skin with no visible grain, exactly as in the reference. |

### 光沢塗装・光沢樹脂（high_gloss.md、GLOSSY PLASTIC）

| 症状 | [FIX] に足す行 |
|---|---|
| ハイライトで色が白く抜ける | Keep the {color} fully saturated inside the highlight; the gloss sits on top of the color. |
| 鏡のように映り込みが鋭い | The reflection on the {部位} is soft and diffused, not a sharp mirror. |
| 小さなテカリが散らばる | A few large, controlled reflections only; no scattered small hotspots. |
| キャンディがラメのように見える | The metallic base glows through the tint as smooth depth — NOT glitter, NOT a sparkle overlay. |

### メタリック・パール（high_gloss_metallic.md）

| 症状 | [FIX] に足す行 |
|---|---|
| ラメ・グリッターに見える | The flakes are fine and suspended below the clear coat — NOT glitter, NOT a sparkle overlay. |
| 平板で、メタリックらしさがない | Strengthen the flip-flop: bright, flake-lit faces toward the key light; deep, saturated tone on faces turning away. |

### メッキ・バフ研磨（chrome.md、POLISHED）

| 症状 | [FIX] に足す行 |
|---|---|
| 灰色の鈍い金属に見える | Stronger light-dark-light reflection banding: clean white streaks and a distinct dark band. |
| 部屋・窓・カメラが映る | Reflections show only abstract soft studio gradients; no room, window, camera, or person. |
| ハイライトが真っ白に飛ぶ | Keep highlights below RGB 250 with a visible gradient; only tiny pinpoint catchlights may reach white. |

### アルマイト・金属素地（anodized.md、BRUSHED、MACHINED）

| 症状 | [FIX] に足す行 |
|---|---|
| 塗装やプラスチックに見える | Cold, hard metal: crisp bright highlight lines on edges and chamfers. |
| ヘアラインが消えた・乱れた | Keep fine parallel brush lines in the same direction as the reference. |
| アルマイトの色が白く抜ける | Highlights stay tinted with the anodized color, never pure white. |
| 削り出し・ヘアラインがメッキのように見える | The {部位} is bare metal, not mirror chrome: softer, less contrasty reflections. |

### カーボン（carbon.md）

| 症状 | [FIX] に足す行 |
|---|---|
| 柄が変わった・歪んだ | Keep the weave pattern, scale, and direction identical to the reference. |
| 印刷のように平坦（本物のカーボンのときだけ） | The tows catch light differently by direction; the light-dark checker shifts across the curvature. |
