# はないわーるど まるごと記録帖

「はないわーるど」の配信ノート（スプレッドシート）を集計・可視化した、単一HTMLファイルのファンダッシュボードです。

- 外部依存なし（Chart.jsをファイル内に埋め込み済み）。`index.html` を開くだけで動作します。
- グラフ、五十音リアクションマップ、全話アーカイブ（検索・絞り込み・詳細モーダル）を収録。

## ローカルで確認する

`index.html` をブラウザで直接開くだけで表示できます。ビルドは不要です。

```
open index.html      # macOS
start index.html      # Windows
```

## GitHubに置く

まだGitHubリポジトリを作っていない場合は、[github.com/new](https://github.com/new) で新しいリポジトリを作成してください（Public / Private どちらでも可）。

このフォルダ（`index.html` と `README.md`）をリポジトリのルートに置いて、以下のコマンドでpushします。

```bash
git init
git add .
git commit -m "はないわーるど記録帖を追加"
git branch -M main
git remote add origin https://github.com/<あなたのユーザー名>/<リポジトリ名>.git
git push -u origin main
```

すでにリポジトリがある場合は、`index.html` をそのリポジトリのルート（または任意のフォルダ）にコピーして、通常どおり `git add` → `git commit` → `git push` してください。

## Cloudflare Pagesで公開する

1. [Cloudflare Dashboard](https://dash.cloudflare.com/) にログイン
2. 左メニューの **Workers & Pages** → **Create** → **Pages** タブ → **Connect to Git**
3. さきほどpushしたGitHubリポジトリを選択
4. ビルド設定は以下の通り（静的HTMLなのでビルド不要）
   - **Framework preset**: `None`
   - **Build command**: 空欄のまま
   - **Build output directory**: `/` （`index.html` を置いたフォルダ。サブフォルダに置いた場合はそのパスを指定）
5. **Save and Deploy** をクリック

数十秒でデプロイが完了し、`https://<プロジェクト名>.pages.dev` のようなURLが発行されます。以降はmainブランチにpushするたびに自動で再デプロイされます。

### 独自ドメインを使いたい場合

Cloudflareでドメインを管理していれば、Pagesプロジェクトの **Custom domains** タブから追加するだけで、DNS設定も自動で行われます。

## ファイル構成

```
.
├── index.html   # ダッシュボード本体（このファイルだけで完結）
└── README.md    # このファイル
```

## データの更新

内容を更新したい場合は、元のスプレッドシート（全まとめ／今週のアイスまとめ／叶えたい！キャラ一覧／リアクション統計／知ってるカナ点数計算／コーナー出現分布の6シート構成）を用意して、Claudeに再度アップロードしてもらえば `index.html` を再生成できます。
