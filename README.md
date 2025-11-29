# Astro w/ Biome

このプロジェクトは **Astro** フレームワークを使用して構築されており、コード品質とフォーマットのために **Biome** を統合しています。

## 🚀 プロジェクト構成

- **Astro**: 高速で現代的な静的サイトジェネレーター
- **Biome**: 高速なJavaScript/TypeScript用リンター・フォーマッター

## 📦 セットアップ

### 必要な環境
- Node.js 18.14.1 以上
- pnpm

### インストール

```bash
# 依存関係のインストール
pnpm install
```

## 🛠 開発コマンド

| コマンド | 説明 |
|---------|------|
| `pnpm dev` | 開発サーバーを起動（http://localhost:4321） |
| `pnpm build` | 本番用ビルドを作成 |
| `pnpm preview` | ビルド結果をプレビュー |
| `pnpm astro` | Astro CLI コマンドを実行 |

## 🔧 Biome による品質管理

このプロジェクトでは Biome を使用してコード品質を維持しています：

### Biome コマンド
```bash
# コードのリント (*.astro を除く)
pnpm lint

# フォーマット (*.astro を除く)
pnpm format

# Astro ファイルの型チェック
pnpm check
```

### 設定
- 設定ファイル: `biome.json`
- サポート言語: JavaScript, TypeScript, JSX, TSX, JSON, CSS
- **注意**: `*.astro` ファイルは Biome の対象外です。Astro ファイルは `astro check` でチェックされます

## 📁 プロジェクト構造

```
/
├── public/          # 静的ファイル
├── src/
│   ├── components/  # Astro コンポーネント
│   ├── layouts/     # レイアウトコンポーネント
│   └── pages/       # ページファイル
├── astro.config.mjs # Astro 設定
├── biome.json       # Biome 設定
└── package.json     # プロジェクト設定
```

## 🌟 特徴

- ⚡️ 高速な開発体験
- 🎯 TypeScript サポート
- 🔍 統合されたリント・フォーマット
- 📱 レスポンシブデザイン対応
- 🚀 最適化されたビルド出力

## 開発ワークフロー

1. `pnpm dev` で開発サーバーを起動
2. コードを編集
3. Biome が自動的にコード品質をチェック (JS/TS/JSON/CSS)
4. `pnpm check` で Astro ファイルの型チェック
5. `pnpm build` で本番ビルドを作成

---

**注意**: コミット前には `pnpm lint`、`pnpm format`、`pnpm check` を実行してコード品質を確保してください。