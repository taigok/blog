# ブログプロジェクト

## 概要

このプロジェクトは、Next.jsとTypeScriptを用いた静的ブログアプリケーションです。記事はMDX形式で記述され、SEOやSNSシェアにも最適化されています。

## 主な機能

- 記事の一覧表示・詳細ページ
- MDXによる記事コンテンツ
- 静的サイト生成（SSG）
- 構造化データ（JSON-LD）によるSEO強化
- OpenGraph/Twitterカード対応
- レスポンシブデザイン
- 404（記事が見つからない場合）の対応

## slug（スラッグ）とは

slug（スラッグ）は、各記事ページのURLの一部として使われる短い文字列です。記事タイトルを英語などで短く、URLに適した形（小文字・ハイフン区切り等）にしたもので、記事を一意に識別します。

例：
- 記事タイトル: 「静的型付けとは？」
- slug: `static-typing`
- URL: `/blog/static-typing`

## ディレクトリ構成

```
/app
  /blog
    /[slug]         ... 各記事ページ
      page.tsx
    /posts          ... MDX記事ファイル
      *.mdx
    page.tsx        ... 記事一覧ページ
    utils.ts        ... 記事取得・日付整形などのユーティリティ
  /components       ... 共通コンポーネント
    footer.tsx
    mdx.tsx         ... MDXレンダラー
    nav.tsx         ... ナビゲーションバー
    posts.tsx
  global.css        ... 全体スタイル
  layout.tsx        ... ルートレイアウト
  not-found.tsx     ... 404ページ
  og/               ... OG画像生成
  robots.ts         ... robots.txt生成
  sitemap.ts        ... サイトマップ生成
/public
  ...
README.md
package.json
tsconfig.json
postcss.config.js
pnpm-lock.yaml
```

## セットアップ方法

1. リポジトリをクローン

```bash
git clone [リポジトリURL]
cd blog
```

2. 依存パッケージをインストール

```bash
npm install
```

3. 開発サーバーを起動

```bash
npm run dev
```

4. ブラウザで `http://localhost:3000` を開く

## 依存関係

- Next.js
- React
- TypeScript
- MDX関連パッケージ
- その他（package.json参照）

## ライセンス

MITライセンス
