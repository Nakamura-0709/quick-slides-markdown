# quick-slides-markdown

Marp ベースの Markdown スライド作成環境です。

## スライドの作成手順

1. `slides/<スライド名>/` ディレクトリを作成
2. スライドの md ファイルを `slide.md` として配置
3. 画像を使う場合は `images/` フォルダを同ディレクトリに作成し、画像を配置
4. md 内で `![説明](./images/画像名.png)` の形式で参照

### 書式リファレンスから新規作成する場合

1. `slides/_format-example/` を `slides/<新規スライド名>/` にコピー（slide.md と images/ を含む）
2. 内容を編集し、画像を `images/` に追加・差し替え

## 書式

書式は `themes/corporate.css` で一元管理されています。デザインを変更する場合はこのファイルを編集してください。

## コマンド

```bash
npm run preview   # プレビュー起動
npm run pdf       # PDF 出力
npm run pdfx      # PPTX 出力
```
