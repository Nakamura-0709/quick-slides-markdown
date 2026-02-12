---
marp: true
theme: corporate
paginate: true
size: 16:9
header: "**スライドタイトル**"
footer: "© 2026 あなたの名前"
backgroundImage: url('../../themes/background/pasterl-light-blue.jpg')
backgroundSize: cover
---

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'default' });
</script>

# 書式リファレンス
## Marp スライドの書き方例

このファイルは新規スライド作成時の参考となる書式例です。

---

# 1. ファイル名・ディレクトリの命名規則

### 推奨パターン

| 形式 | 例 | 用途 |
| :--- | :--- | :--- |
| トピック名 | `slides/theme-name/slide.md` | 汎用・リファレンス |
| 画像同梱 | `slides/theme-name/slide.md` + `images/` | 画像を同梱する場合 |

---

# 2. 基本 Markdown

- **太字 (Bold)**: 重要なポイント
- *斜体 (Italic)*: 強調したい箇所
- ~~取り消し線~~: 不要になったタスク
- 絵文字もOK: 🎉 🐳 ⚡️ 🔧

> **Note:**
> 引用ブロックはこのように表示されます。
> 参考文献や補足情報に使えます。

---

# 3. コードブロック

シンタックスハイライトと、CSSによる「ウィンドウ風」の装飾が適用されます。

```go
package main

import (
    "fmt"
    "time"
)

func main() {
    target := "Production DB"
    fmt.Printf("Checking %s status...\n", target)
    time.Sleep(1 * time.Second)
    fmt.Println("✅ All Systems Green!")
}
```

---

# 4. Mermaid ダイアグラム (シーケンス図)

HTMLタグ `<div class="mermaid">` 内でレンダリングされます。

<div class="mermaid">
sequenceDiagram
autonumber
participant U as "User (Developer)"
participant V as "VS Code"
participant C as "Dev Container"
U->>V: Open Project
V->>C: Reopen in Container
Note over C: Docker Build & Install
C-->>V: Environment Ready!
U->>C: npm run pdf
C-->>U: Generate slides.pdf
</div>

---

# 5. Mermaid ダイアグラム (フローチャート)

複雑な分岐処理もテキストベースで管理できます。

<div class="mermaid">
graph LR
A[Start] --> B{Is Container Running?}
B -- Yes --> C[npm run preview]
B -- No --> D[Reopen in Container]
D --> C
C --> E[Browser opens]
E --> F[Happy Hacking!]
</div>

---

# 6. 2カラムレイアウト

Marpの標準機能で横並びも可能です。`<div class="columns">` で囲みます。

<div class="columns">

<div>

### 左カラム：要件

* 環境のコード化
* 再現性の担保
* 運用の自動化

</div>

<div>

### 右カラム：解決策

* Dev Containers
* Docker-in-Docker
* Marp CLI

</div>

</div>

---

# 7. 画像の挿入

画像は `images/` フォルダに配置し、相対パスで参照します。

```markdown
![説明テキスト](./images/画像名.png)
```

**テンプレートのディレクトリ構造（`tree` で確認）:**

```
templates/
├── slide.md
└── images/
    ├── image1.png
    └── image2.png
```

---

# 8. 色付きテキスト

Marp では Markdown 内に HTML を書くことで、自由に文字色を変えられます。

### 基本色クラス

- <span class="text-red">重大インシデント</span>
- <span class="text-green">正常稼働</span>
- <span class="text-blue">情報共有</span>
- <span class="text-orange">注意事項</span>
- <span class="text-gray">補足・脚注</span>

### 濃淡バリエーション

- <span class="text-red-soft">text-red-soft</span>
- <span class="text-red-strong">text-red-strong</span>
- <span class="text-green-soft">text-green-soft</span>
- <span class="text-green-strong">text-green-strong</span>

---

# 9. 色付きコード表現

`<pre><code>` + `<span>` で行単位・単語単位の色を指定できます。

<pre><code>
<span class="text-gray">// コメント例</span>
<span class="text-blue">package</span> main

<span class="text-blue">func</span> main() {
    target := <span class="text-green">"Production DB"</span>
    fmt.Printf(<span class="text-green">"Checking %s...\n"</span>, target)
    fmt.Println(<span class="text-green-strong">"✅ Done!"</span>)
}
</code></pre>

> フェンスコードではなく HTML で書くと、細かい装飾の自由度が高くなります。

---

# まとめ

### プレビュー・ビルド方法

```bash
# プレビューサーバー起動（自動更新）
npm run preview

# PDF 出力
npm run pdf

# PPTX 出力
npm run pdfx
```

`format-example/slide.md` を選択して表示を確認してください。
