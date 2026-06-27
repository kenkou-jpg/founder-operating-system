# Development OS

## 目的

全プロダクト共通の技術方針・開発標準・品質基準を定義する。
各プロダクトリポジトリはここを参照し、逸脱がある場合はADRに理由を記録する。

**このOSが答える問い:**
- どの技術スタックを選ぶか
- コードをどう書くか
- テスト・セキュリティ・CI/CDをどう設計するか
- アーキテクチャをどう判断するか

---

## 責務

| 責務 | 内容 |
|------|------|
| 技術スタック選定基準 | なぜその技術を選ぶか・選ばないかの判断軸 |
| コーディング規約 | 言語別スタイル・命名・構造の標準 |
| アーキテクチャ原則 | 設計判断の繰り返しを防ぐ共通パターン |
| セキュリティ標準 | 認証・データ保護・依存ライブラリ管理 |
| テスト標準 | テスト種別・カバレッジ目標・禁止パターン |
| CI/CD標準 | パイプライン・品質ゲートの最低基準 |
| ドキュメント規約 | ADR・ARCHITECTURE.md・コメントの書き方 |

---

## 将来追加予定

- `TECH_STACK.md` — 技術選定の詳細と理由（ippoでの実績ベース）
- `CODING_STANDARDS.md` — TypeScript / React Native の規約
- `ARCHITECTURE_PRINCIPLES.md` — Supabase × RN の設計パターン集
- `SECURITY_STANDARDS.md` — 認証・ヘルスデータ・農業データの保護基準
- `TESTING_STANDARDS.md` — テスト戦略・禁止パターン（mockの扱い等）
- `CICD_STANDARDS.md` — GitHub Actions の標準ワークフロー

---

## 他OSとの関係

| OS | 関係 |
|----|------|
| `automation-os/` | CI/CDの自動化ルールを参照 |
| `analytics-os/` | AnalyticsスキーマのDB設計基準を提供 |
| `legal-os/` | セキュリティ基準はlegal-osのデータ保護方針と整合させる |
| `portfolio-os/` | 各プロダクトが採用する技術の記録 |
| `governance/ADR/` | 技術的重要決定はADRに記録 |

---

## 現在の標準スタック（v0.1時点）

| レイヤー | 標準技術 | 適用プロダクト |
|---------|---------|-------------|
| Mobile | React Native (Expo) | ippo, Fasting App |
| Backend/DB | Supabase (PostgreSQL) | 全プロダクト |
| 言語 | TypeScript | 全プロダクト |
| テスト | Jest + RNTL | ippo |
| CI | GitHub Actions | 全プロダクト |
