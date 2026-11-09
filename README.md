# vscode-md-css

[Geb's Lab](https://geb1024.com/articles/shared-component-sculpture) の記事スタイルをベースにした、VS Code Markdown Preview用のCSSです。

本文には落ち着いたグレー、見出しと太字には濃紺を使用しています。段落やリストの余白、横罫線だけの表、引用、コード、リンクなども読みやすく調整しています。

## 設定方法

VS Codeのユーザー設定（JSON）を開きます。

1. コマンドパレットを開く
2. `Preferences: Open User Settings (JSON)` を実行する
3. 次の設定を追加する

```json
{
  "markdown.styles": [
    "https://cdn.jsdelivr.net/gh/Geb-algebra/vscode-md-css@main/markdown-preview.css"
  ],
  "markdown.preview.fontSize": 16
}
```

すでにほかの設定がある場合は、外側の `{}` を重複させず、`markdown.styles` と `markdown.preview.fontSize` の項目だけを追加してください。

設定後、Markdownファイルを開き、コマンドパレットから `Markdown: Open Preview to the Side` を実行するとスタイルを確認できます。

### 文字サイズを変更する

全体の文字サイズは `markdown.preview.fontSize` で変更できます。CSS内の文字サイズや余白は `rem` を基準にしているため、この値に合わせて全体が拡大・縮小します。

```json
{
  "markdown.preview.fontSize": 14
}
```

## 反映されない場合

まず、コマンドパレットから `Markdown: Refresh Preview` を実行してください。それでも反映されない場合は、次の項目を確認します。

- 現在のワークスペースが「信頼済み」になっているか
- `settings.json` のJSONにカンマ抜けなどのエラーがないか
- `markdown.styles` にGistのページURLやRaw URLではなく、上記のjsDelivr URLを指定しているか
- Markdown Previewを一度閉じ、再度開いても変化しないか

CDNのキャッシュにより、リポジトリ側のCSS更新がすぐに反映されない場合があります。少し時間を置いてからPreviewを更新するか、次の節の方法でタグまたはコミットハッシュを指定してください。

## バージョンを固定する

常に最新版を使う場合は `@main` を指定します。表示を固定したい場合は、`@main` をタグ名またはコミットハッシュへ置き換えてください。

```json
{
  "markdown.styles": [
    "https://cdn.jsdelivr.net/gh/Geb-algebra/vscode-md-css@v1.0.0/markdown-preview.css"
  ]
}
```

バージョンを固定すると、リポジトリ側のCSSが更新されてもプレビューの表示は変わりません。

## ローカルファイルとして使う

外部URLを使わず、リポジトリを取得して使用することもできます。ワークスペース直下に `markdown-preview.css` がある場合は、`.vscode/settings.json` に次のように指定します。

```json
{
  "markdown.styles": ["markdown-preview.css"],
  "markdown.preview.fontSize": 16
}
```

相対パスは、VS Codeで開いているワークスペースを基準に解決されます。

## スタイルの概要

- 本文色: `#63676b`
- 見出し・太字: 濃紺 `#002538`
- リンク: blue-800、常時下線
- 本文の行高: `1.75rem`
- 段落間: `1.5rem`
- リスト項目間: `0.75rem`
- 表: 縦罫線なし、横罫線のみ
- 引用: 薄い背景色とグレーの左罫線

各書式の表示確認には、リポジトリ内の [`preview-sample.md`](./preview-sample.md) を利用できます。

