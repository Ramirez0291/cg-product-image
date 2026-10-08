---
name: cg-product-image
license: "AGPL-3.0"
description: 既存の商品写真を画像生成AI（Nano Banana、GPT Image など）で加工し、表面素材の質感（マット塗装、光沢塗装、メタリック、メッキ、アルマイト、金属素地、カーボン、樹脂・ゴム、布・レザー）を実物どおりに引き出すための英語プロンプトを作る。ユーザーが指定する撮影環境・背景・素材・その他の指示から、形・色・ロゴを変えない加工プロンプトを組み立て、生成後のチェック項目と修正用の1行も出す。「商品画像の質感を上げて」「素材感を出して」「白背景のメイン画像に加工して」「商品写真を修復して」「マットの質感」「メッキをきれいに」「Nano Banana 用の加工プロンプト」など、既存の商品写真を画像生成AIで仕上げたいときは、素材名が出なくても使う。元画像なしの新規生成、文字入りの宣伝画像、動画には使わない。
---

# cg-product-image

既存の商品写真（以下「元画像」）を画像生成AIで加工し、表面素材の質感を実物どおりに、よりはっきり見せるためのプロンプトを作る。

- プロンプトは英語で書く（画像生成AI向け）。ユーザーへの説明は日本語で書く。
- 成果物はプロンプト。ユーザーが元画像を添付し、プロンプトを貼り付けて生成する。このセッションで画像生成ツールが使える場合は、ユーザーに確認してから実行してよい。
- 元画像なしで商品画像を新しく作る依頼は対象外。実物と違う画像になるため。

## 基本方針

- **質感は「引き出す」もので、「変える」ものではない。** 照明と表面の描き方で、その素材本来の見え方をはっきりさせる。樹脂を金属に、マットをツヤありに、合皮を本革に見せるような変更はしない。実物と違う商品画像は、返品・クレーム・Amazon の規約違反につながる。
- **形・部品数・色・ロゴ・文字は変えない。** プロンプトには必ず FIDELITY LOCK を入れ、最優先と明記する。
- **モジュールの英文は言い回しを変えない。** `references/` の英文は表現を調整済み。行ってよい作業は次の5つだけ。
  1. プレースホルダーを埋める
  2. 部位名を入れる（"The surface is" → "The {部位} is"。部位が複数形なら are）
  3. 副素材に使う行を選ぶ（手順4のルールどおり）
  4. 矛盾する行を削除・置き換えする（このファイルと各モジュールに書いた方法で）
  5. 他の指示に合わせて OUTPUT の比率・商品の大きさを書き換える
- **矛盾する指示を残さない。** 指示が矛盾すると、画像生成AIはどちらかを無視するか、中途半端に混ぜる。

## 入力

| 項目 | 選択肢 | 指定がないとき |
|---|---|---|
| 元画像 | 加工する商品写真 | 添付をお願いする（任意）。見られなくてもプロンプトは作れる。色と部位はユーザーの説明で決める |
| 撮影環境 | 商品撮影スタジオ | 選択肢が1つなので、スタジオを使い、入力の確認表に書く |
| 背景 | 白（Amazon メイン画像）、グレー（サブ画像） | ユーザーに聞く。推奨は白 |
| 素材 | 下の「素材の対応表」 | ユーザーに聞く。元画像から推定できるときは、推定を示して確認する |
| 他の指示 | 比率、商品の大きさ、修復の要否など | なしで進める |

- 足りない項目は、まとめて1回だけ聞く。選択肢を示し、推奨を先頭に置く。
- 素材は、対応表の「ユーザーの言い方」のどれかに当てはまれば指定済みとみなす（例：キャンディ塗装、アルマイト）。「マットブラック」「黒いツヤあり」のように色とツヤだけで材質が分からないときは、材質を聞く（例：マット塗装、シボ樹脂、ブラックアルマイト）。
- 元画像が見られず、ほかに聞くことがあるときは、ほかの素材の部位があるかも同じ質問で聞く。これだけのために質問はしない。ユーザーが挙げていない部位は FIDELITY LOCK に任せ、推定・仮定に書く。
- 対応表にない素材・撮影環境を指定されたら、既存モジュールと同じ構成で新しいブロックを書き、出力で「草案」と伝える。

## 素材の対応表

モジュールはすべて `references/surface/` にある。照明は `references/env/product_photo_studio.md` の LIGHTING から選ぶ。

| ユーザーの言い方 | モジュール | バリエーション | 照明 |
|---|---|---|---|
| マット塗装、つや消し、粉体塗装 | matte.md | — | MATTE |
| マット塗装（粒のない、なめらかな肌） | matte.md | SMOOTH | MATTE |
| 半ツヤ、サテン、3〜5分ツヤ | matte.md | SEMI-GLOSS | DEFAULT |
| マットメタリック | matte.md | MATTE METALLIC | MATTE |
| ラバー塗装、ソフトタッチ | matte.md | SOFT-TOUCH | MATTE |
| マットブラック、つや消し黒 | matte.md | MATTE BLACK | MATTE |
| 光沢塗装、ツヤあり、ソリッド塗装 | high_gloss.md | — | REFLECTIVE |
| グロスブラック、ツヤ黒 | high_gloss.md | GLOSS BLACK | REFLECTIVE |
| キャンディ塗装 | high_gloss.md | CANDY | REFLECTIVE |
| メタリック塗装 | high_gloss_metallic.md | — | REFLECTIVE |
| パール塗装 | high_gloss_metallic.md | PEARL | REFLECTIVE |
| メッキ、クロームメッキ | chrome.md | — | REFLECTIVE |
| ブラックメッキ、スモークメッキ | chrome.md | BLACK CHROME | REFLECTIVE |
| アルマイト | anodized.md | — | DEFAULT |
| 光沢アルマイト | anodized.md | GLOSS ANODIZE | REFLECTIVE |
| ブラックアルマイト | anodized.md | BLACK ANODIZE | DEFAULT |
| ヘアライン | bare_metal.md | BRUSHED | REFLECTIVE |
| 削り出し（無塗装） | bare_metal.md | MACHINED | DEFAULT |
| バフ研磨、鏡面仕上げ | bare_metal.md | POLISHED | REFLECTIVE |
| ブラスト、梨地 | bare_metal.md | BEAD-BLASTED | MATTE |
| カーボン（ツヤあり） | carbon.md | — | REFLECTIVE |
| マットカーボン | carbon.md | MATTE CARBON | MATTE |
| カーボン調（印刷・水圧転写・シート） | carbon.md | CARBON-LOOK | ツヤあり＝REFLECTIVE、マット＝MATTE |
| 樹脂（シボ・つや消し） | plastic_rubber.md | TEXTURED PLASTIC | MATTE |
| 樹脂（光沢） | plastic_rubber.md | GLOSSY PLASTIC | REFLECTIVE |
| ゴム、エラストマー | plastic_rubber.md | RUBBER | MATTE |
| ナイロン・ポリエステル生地 | textile_leather.md | FABRIC | MATTE |
| 本革、合皮 | textile_leather.md | LEATHER | DEFAULT |

バリエーションの使い方は、各モジュールの見出しに書いてある：
- **追加**：基本ブロックの末尾に足す。
- **置き換え：X**：基本ブロックの X を、バリエーションの英文と差し替える。
- **1つ選ぶ**：基本ブロックがないモジュール。選んだブロックの全文を使う。

**草案**（実際の生成でまだ確認していないもの）：REFLECTIVE 照明、anodized.md、bare_metal.md、carbon.md、plastic_rubber.md、textile_leather.md、PEARL、BLACK CHROME。使ったときは出力の「注意」に書く。

## 手順

### 1. 入力をそろえる

「入力」の表に従う。足りない項目はまとめて1回だけ聞く。

### 2. 元画像を確認する

元画像が見られるときは、次を確認する。見られないときは、ユーザーの説明から判断する。
- 部位ごとの素材と色。ユーザーの指定と食い違えば、確認してから進める。
- 修復が必要か：ぶれ・ピンぼけ、色かぶり、低解像度、フラッシュの白飛び。元画像で見えたもの、またはユーザーが説明したものがあれば、修復ブロックを入れる。
- 加工で崩れやすい要素：ロゴ、型番、細かい文字、刻印、目盛り。生成後のチェックに使う。

### 3. モジュールを選ぶ

| ブロック | 参照先 | 選び方 |
|---|---|---|
| 冒頭文、FIDELITY LOCK | `references/prompt_template.md` | 常に入れる |
| 修復 | `references/restoration.md` | 手順2で修復が必要と判断したとき |
| 背景・影・出力・NG | `references/env/product_photo_studio.md` | 指定された背景のもの |
| カメラ | 同上の CAMERA | 常に入れる。角度変更の指示があるときだけ1文目を ANGLE CHANGE に |
| 照明 | 同上の LIGHTING | 主素材の「照明」列 |
| 素材 | `references/surface/*.md` | 素材の対応表 |

### 4. 組み立てる

`references/prompt_template.md` の順番で並べ、次のルールで仕上げる。

**プレースホルダーを埋める。**
- `{color}`：一般的な英語の色名（black、red、blue、gunmetal gray など）。凝った色名は色ずれの原因になる。
  - 色かぶりがあるときは、かぶりを除いた実物の色を書く。
  - gold、silver、bronze、champagne など金属名でもある色は、"-colored" を付ける（例：gold-colored）。付けないと、その金属そのものとして描かれることがある。
- そのほかのプレースホルダー（`{metal}`、`{weave}` など）は、各モジュールの説明に従う。

**素材ブロックを書く。**
- 素材が1つ：見出しは `[SURFACE / MATERIAL — {素材}]`。本文の "The surface is" はそのまま。
- 素材が複数：部位ごとに1ブロック。見出しは `[SURFACE / MATERIAL — {部位}: {素材}]`。本文の "The surface is" を "The {部位} is" に変える（部位が複数形なら are）。
  - 部位名は元画像を見て分かる英語で、冠詞を付けずに書く（例：main clamp body、pivot bolt）。
  - 同じモジュールでも色が違う部位は、別のブロックにする。
  - ブロックは3つまで。それ以上の部位は FIDELITY LOCK に任せる。
- 見出しの {素材} は、英語で短く書く（例：MATTE BLACK PAINT、GOLD-COLORED ANODIZED ALUMINIUM）。

**主素材と副素材を分ける（素材が複数のとき）。**
- 主素材：ユーザーが「ここの質感を見せたい」と指定した部位。指定がなければ、面積が最も大きい部位。照明は主素材で選ぶ。
- 主素材はモジュールの全文を使う。
- 副素材は、次の行だけをそのまま使う（「1つ選ぶ」モジュールも同じ）。全文を重ねるとプロンプトが長くなり、主素材の指示が弱まるため。
  1. 冒頭の段落（定義文）の全文
  2. バリエーションを使うなら、その英文の全文（bare_metal.md は選んだ FINISH の全文）。バリエーションは、その素材を他と見分ける要点なので削らない
  3. FINISH QUALITY の最初の箇条1行。FINISH QUALITY の見出しがないモジュールは、欠点を "no ..." で並べた箇条1行（chrome.md は "Keep the plating flawless: ..."、high_gloss.md は "Perfectly smooth: ..."）
  - バリエーションが冒頭の段落や FINISH QUALITY を置き換えるときは、置き換えた後の文を使う。
- 副素材のブロックは、面積の大きい順に並べる。
- 素材ブロックの前に [MATERIAL MAP] を入れる（書き方は `references/prompt_template.md`）。部位をまたいだ色や質感の移りを防ぐ。

**照明を素材に合わせる。**
- 主素材がマット系で副素材が反射系（メッキ・バフ研磨・光沢塗装など）：MATTE 照明の最後の行 "No specular hotspots anywhere on the product." を "No specular hotspots anywhere on the {主素材の部位}." に変える。
- 照明が REFLECTIVE 以外で、副素材がメッキ・バフ研磨：LIGHTING の末尾に次の1行を足す。
  `- For the {部位}: a strip light and a black flag positioned to create clean light-dark reflection banding.`

**他の指示を反映する。**

| 指示の例 | 対応 |
|---|---|
| 比率 | OUTPUT の比率を書き換える。出力の「注意」に「画像生成AIの設定でも同じ比率を選ぶ」と書く |
| 商品の大きさ | OUTPUT の割合を書き換える。白背景のメイン画像は、商品が画面の85%以上を占めるようにする |
| ホコリ・指紋・小キズを消す | [ADDITIONAL] に入れる。ユーザーが挙げたものだけを書き、加工跡や質感を消さない一文を続ける（例：Remove dust and fingerprints. Keep machining marks, surface texture, and molded details.） |
| 角度を変える | CAMERA の1文目を ANGLE CHANGE の英文に置き換える。「もう少し斜めに」「やや上から」のように具体的な指示なら、その内容を英語の1文にして置き換える（例：Rotate the view slightly further toward a three-quarter angle.）。出力の「注意」に「元画像に写っていない面はAIの想像になり、実物と違う可能性が高い」と書く（確認は待たない） |
| ロゴ・文字を崩したくない | [ADDITIONAL] に troubleshooting.md「共通」のロゴ・文字の行を入れる |
| 色を変える、ロゴや文字を足す、小物や手を入れる | 実物と違う画像になる、またはAmazon メイン画像の規定に反する。理由を伝え、ユーザーが了承したときだけ入れる |
| その他 | 短い英語の命令文にして [ADDITIONAL] に入れる |

**矛盾をなくす。** 書き終えたら全文を読み、矛盾を直す。よくあるもの：
- 修復と背景・照明の変更を同時に行う：`restoration.md` の「加工と一緒に使う」に従う。
- 色かぶりを直す：FIDELITY LOCK の「色を保つ」と食い違う。`restoration.md` の説明どおり、[RESTORATION] の1行目に色かぶりの一文を入れる。
- 他の指示の比率・大きさと OUTPUT：他の指示を優先し、OUTPUT を書き換える。

### 5. 出力する

次の形式で返す。

````markdown
## 入力の確認

| 項目 | 内容 |
|---|---|
| 撮影環境 | 商品撮影スタジオ |
| 背景 | 白（Amazon メイン画像） |
| 素材 | 本体：マットブラック塗装（主素材）／ボルト：クロームメッキ |
| 照明 | MATTE |
| 修復 | なし |
| 他の指示 | ホコリを消す |
| 推定・仮定 | 色は元画像から black と判断 |

注意：（草案のモジュール・照明、角度変更、比率の設定など。なければこの行を省く）

## プロンプト

画像生成AIに元画像を添付し、下の英文を貼り付けてください。

```text
（組み立てたプロンプト）
```

## 生成後に見るところ

うまくいかないときは、プロンプトの末尾に `[FIX]` の見出しを作って → の1行を足し、元画像から生成し直してください。一度に足すのは1〜2行までです。

- 形・部品数・ロゴ・色が元画像と同じか（色かぶりを直したときは、実物の色と比べる）
  → `Match the reference exactly: same silhouette, same proportions, same part count. Change only the lighting and surface rendering.`（角度を変えたときは2文目を除く）
- （崩れやすい要素があれば：ダイヤルの目盛り、刻印など）
  → `（troubleshooting.md の対応する1行）`
- （修復を入れたとき：ぶれ・色かぶりが残っていないか）
  → `（troubleshooting.md「修復」の対応する1行）`
- （使った素材に合う項目を troubleshooting.md から2〜4個）
  → `（対応する1行）`
````

- 「推定・仮定」には、ユーザーが指定せず、こちらで推定して決めたこと（色、主素材、部位名、修復の有無など）を「、」で区切って書く。スキルの既定値（カメラ角度を保つ、比率 1:1 など）は書かない。なければ「なし」。
- 元画像が見られないときは、崩れやすい要素の項目に「（あれば）」を付ける。

### 6. 生成結果を直す

ユーザーが生成結果や不具合を伝えてきたら、`references/troubleshooting.md` を読む。
- 生成画像が見られるときは、まず元画像と見比べ、形・部品数・ロゴ・色が変わっていないか確認する。次に素材の見え方を確認する。
- 症状に合う1行を、プロンプト末尾の [FIX] ブロックに足す。一度に足すのは1〜2行まで。
- 返すのは、原因の説明（1〜2文）と、足す [FIX] ブロックだけ。プロンプトの他の部分を変えたときは、プロンプト全文を返し直す。
- 同じ症状が2回以上続いたら、行を足すより減らす（troubleshooting.md の「直し方」4）。
- 再生成は元画像から行うよう伝える。生成結果を次の元画像にすると、ずれが積み重なる。

## 参照ファイル

- `references/prompt_template.md`：組み立ての順番、冒頭文・FIDELITY LOCK・MATERIAL MAP の英文、記入例。
- `references/restoration.md`：修復ブロックと、修復だけを行うときの使い方。
- `references/env/product_photo_studio.md`：背景（白・グレー）ごとの BACKGROUND・SHADOW・OUTPUT・NEGATIVE、共通の CAMERA、照明3種。
- `references/surface/`：素材モジュール。matte、high_gloss、high_gloss_metallic、chrome、anodized、bare_metal、carbon、plastic_rubber、textile_leather。
- `references/troubleshooting.md`：生成後のチェック項目と、修正用の1行。
