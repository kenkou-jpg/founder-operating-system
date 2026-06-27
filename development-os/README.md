# Development OS

## 目的

全プロダクト共通の技術方針・開発標準・品質基準を定義する場所。
各プロダクトリポジトリはここを参照し、独自の逸脱がある場合はADRに記録する。

## 何を保存するか

- **技術スタック選定基準** — なぜその技術を選ぶか・選ばないかの判断軸
- **コーディング規約** — 言語別のスタイル・命名・構造の標準
- **アーキテクチャ原則** — 設計判断の繰り返しを防ぐ共通パターン
- **CI/CD標準** — テスト・デプロイ・品質ゲートの最低基準
- **セキュリティ基準** — 認証・データ保護・依存ライブラリ管理
- **ドキュメント規約** — ADR・ARCHITECTURE.md・コメントの書き方

## 技術スタック（現在の標準）

| レイヤー | 標準技術 | 備考 |
|---------|---------|------|
| Frontend | React Native (Expo) | モバイルファースト |
| Backend | Supabase (PostgreSQL + Edge Functions) | BaaSファースト |
| 型安全 | TypeScript | 全スタック |
| テスト | Jest + React Native Testing Library | 単体・統合 |
| CI | GitHub Actions | |
| モニタリング | TBD | |

## 開発原則

1. **型安全を妥協しない** — `any` は禁止、型推論を最大活用
2. **テストなしでマージしない** — 機能追加は必ずテストを伴う
3. **依存は最小に** — 外部ライブラリ追加は慎重に、長期メンテを考慮
4. **破壊的変更はADRを書く** — `governance/ADR/` に記録してから実施

## 今後の再利用計画

- **AgriPath** — 同じ Supabase + React Native スタックを採用予定
- **Fasting App** — 同スタック、ヘルスケアデータの扱いにセキュリティ標準を適用
- **テンプレート事業** — APP_STARTER_TEMPLATE として実装

## ファイル構成（今後追加予定）

```
development-os/
├── README.md               # このファイル
├── TECH_STACK.md           # 技術選定の詳細と理由
├── CODING_STANDARDS.md     # コーディング規約
├── ARCHITECTURE_PRINCIPLES.md
├── SECURITY_STANDARDS.md
├── TESTING_STANDARDS.md
└── CICD_STANDARDS.md
```
