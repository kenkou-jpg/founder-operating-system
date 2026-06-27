# App Starter Template

## 目的

新しいプロダクトを立ち上げるときの初期セットアップテンプレート。
`development-os/` の標準に基づいたボイラープレート。

## 含まれるもの（予定）

```
APP_STARTER_TEMPLATE/
├── README.md               # このファイル
├── .github/
│   ├── workflows/
│   │   ├── test.yml        # テスト自動実行
│   │   └── deploy.yml      # デプロイ
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/
│   ├── ARCHITECTURE.md     # ARCHITECTURE_TEMPLATEのコピー
│   └── BUSINESS_STRATEGY.md
├── src/                    # React Native / Expo の基本構造
│   ├── components/
│   ├── screens/
│   ├── hooks/
│   ├── services/
│   │   └── supabase.ts
│   ├── types/
│   └── utils/
├── supabase/
│   └── migrations/
├── .env.example
├── package.json
├── tsconfig.json
└── app.json
```

## 使い方

1. このディレクトリをコピーして新リポジトリを作成
2. `docs/ARCHITECTURE.md` を記入
3. `docs/BUSINESS_STRATEGY.md` を記入
4. `portfolio-os/` に新プロダクトのファイルを作成
5. `CANONICAL_SOURCE.md` にプロダクトを追加

## Status

このテンプレートは今後実装予定です。
現時点では構造定義のみ。
