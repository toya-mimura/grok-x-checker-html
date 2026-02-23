# Grok X Checker HTML

Grok API の `x_search` 機能を使って、指定した X（Twitter）アカウントの昨日の投稿をまとめてレポート生成するWebツール。

**ブラウザで完結。APIキーはサーバーに保存されません。**
**ソースコードは全て公開しています**

## こういう人向け

- Xの投稿は追いたいけど、TLのアルゴリズムやUIが合わない
- 特定のアカウントの投稿だけを効率よく追いたい
- SNSを開く時間を減らしたい

## 仕組み

### ローカルモード（HTMLファイル単体）
```
ブラウザ → Grok API (x_search) に直接リクエスト
```

## 使い方

1. 以下の2ファイルをダウンロード
  - `index.html`
  - `check.txt`
2. `check.txt`を編集
3. `index.html`をブラウザで開く
4. check.txt をドラッグ＆ドロップ → 「レポートを生成」

※ CORS エラーが出る場合は `npx serve .` でローカルサーバー経由で開いてください。

---

### 1. Grok API キーを取得

1. [xAI Console](https://console.x.ai/) にアクセス
2. アカウント作成 → API キーを生成
3. `xai-` で始まるキーをコピー

### 2. check.txt を作成

テキストファイルを作成し、以下の形式で記入：

```
xai-your-api-key-here
@account1
@account2
@account3
```

- 1行目: Grok API キー
- 2行目以降: チェックしたい X アカウント名（`@` 付きでも無しでもOK）
- `#` で始まる行はコメントとしてスキップされます
- 最大20アカウントまで

### 3. サイトにアクセスしてファイルをアップロード

1. index.htmlを開く
2. check.txt をドラッグ＆ドロップ
3. 「レポートを生成」ボタンをクリック
4. 30秒〜1分待つとレポートが表示される


## プロジェクト構成

```
x-digest/
├── index.html        # フロントエンド（静的HTML）
├── check.example.txt     # check.txt のサンプル
└── README.md
```

## ライセンス

MIT

## 参考リンク

- [xAI API ドキュメント](https://docs.x.ai/docs/overview)
- [x_search ツール](https://docs.x.ai/docs/guides/tools/search-tools)
- [Cloudflare Workers](https://developers.cloudflare.com/workers/)
