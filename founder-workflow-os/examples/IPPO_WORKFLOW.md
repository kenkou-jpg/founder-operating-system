# Example: IPPO — Founder Workflow OS 適用例

> IPPO（ウォーキング習慣化アプリ）の「Ideaから Wave2 まで」を
> Founder Workflow OS に沿って説明するサンプル。

---

## プロジェクト概要

| 項目 | 内容 |
|-----|------|
| プロダクト | ippo（一歩） |
| カテゴリ | ウォーキング・健康習慣アプリ |
| 現在のフェーズ | BUILD（Wave2 / PR Development） |
| 参照ファイル | `portfolio-os/IPPO.md` |

---

## DISCOVERY フェーズ（S01〜S05）

### S01 — Idea

**課題仮説（1文）:**
「運動したいが続かない人が、ウォーキングを習慣化するための、
感情と身体状態を統合したパーソナルコーチングアプリ」

**Gate D1 確認:**
- ✅ 課題仮説が1文で言える
- ✅ `FOUNDER_PHILOSOPHY.md` の「健康×テクノロジー」と整合
- ✅ 既存ポートフォリオはゼロ → 健全性問題なし

### S02 — Problem Discovery

**実施した検証:**
- 運動習慣がない30〜40代への非公式インタビュー
- 「3日坊主」を経験した人の課題の特定
- 既存アプリ（Apple Health・Strava 等）との差別化点の発見

**発見:**
- 課題の実在: ✅
- 「感情・体調と連動したウォーキング提案」への反応: ✅

**Gate D2 確認:**
- ✅ インタビュー実施
- ✅ 課題実在の確認

### S03 — Business Strategy

**決定事項:**
- 収益モデル: フリーミアム + サブスクリプション
- ターゲット: 健康意識は高いが運動継続が難しい日本人（30〜50代）
- 差別化: 感情・月経周期・体調を統合したパーソナル提案

**CP-02（ビジネスモデル決定）:** サブスクリプション優先で決定

### S04 — Growth Strategy

**NSM:** DAU（毎日歩く人の数）
**初期獲得チャネル:** note記事・X投稿・ウォーキングコミュニティ

### S05 — Regulatory Review

**特定したリスク:**
- 健康アプリ固有: 医療効果の標榜に関する薬機法・景品表示法
- ヘルスデータ（月経周期・体調）の取り扱い → 最高水準のプライバシー保護

**対処方針:**
- 医療効果を一切謳わない
- ヘルスデータは `legal-os/` の最高基準で保護

---

## DESIGN フェーズ（S06〜S11）

### S07 — Vision

**Vision（1文）:**
「一歩踏み出す力を、すべての人へ」

### S08 — 10-Year Design

**10年間変えないもの:**
- ユーザーの感情・体調との共存
- 継続 > 強度の思想
- プッシュではなくサポートするUI

### S10 — Domain Design

**主要ドメイン:**
- NetworkSignal（感情・体調シグナルのドメイン）
- EmotionSignal（感情シグナルの生成）
- WalkingSession（ウォーキングセッション管理）
- UserProfile（ユーザープロファイル）

**CP-03（設計凍結）:** Wave2 Architecture で凍結完了

### S11 — Architecture

**技術スタック:**
- React Native（Expo）
- Supabase（PostgreSQL + Edge Functions）
- TypeScript

**Binding Decisions:** BD-001〜BD-060 で管理

---

## BUILD フェーズ（S12〜S14）

### S12 — Roadmap

**Wave 構成:**
- Wave 1: 基本ウォーキング機能（完了）
- Wave 2: Emotion Signal + Persistence 基盤
  - PR-041: Repository V2（完了）
  - PR-042: Supabase Persistence（完了）
  - PR-043: Emotion Signal Foundation（完了）
  - PR-044: MenstrualPhase Auto-Resolution（計画中）
  - PR-045〜: 継続

**`11_PR_RESPONSIBILITY_REGISTRY.md`:** PR-041〜043 のエントリ登録済み

### S13 — APP STARTER OS

**完了事項:**
- GitHub リポジトリ: `kenkou-jpg/ippo`
- GitHub Actions CI/CD: 設定済み
- Supabase プロジェクト: 設定済み
- `portfolio-os/IPPO.md`: 作成済み

### S14 — PR Development（現在地）

**現在:** PR-043 完了、PR-044 準備中

**PR Generator OS の活用:**
- `02_PR_INPUT_SHEET.md`: PR-044 用に記入中
- `11_PR_RESPONSIBILITY_REGISTRY.md`: PR-041〜043 登録済み
- `12_RESPONSIBILITY_COLLISION_CHECKLIST.md`: PR-044 で実行予定
- `13_ROADMAP_VALIDATOR.md`: PR-044 で実行予定
- `14_PR_SCOPE_VALIDATOR.md`: PR-044 で実行予定

---

## 現在のステータス（2026-06-27）

| ステージ | 状態 |
|---------|------|
| S01 Idea | ✅ 完了 |
| S02 Problem Discovery | ✅ 完了 |
| S03 Business Strategy | ✅ 完了 |
| S04 Growth Strategy | ✅ 完了 |
| S05 Regulatory Review | ✅ 完了 |
| S06 Go-To-Market | ✅ 完了（MVP後に強化予定）|
| S07 Vision | ✅ 完了 |
| S08 10-Year Design | ✅ 完了 |
| S09 5-Year Quality | ✅ 完了 |
| S10 Domain Design | ✅ 完了 |
| S11 Architecture | ✅ 完了（Wave2 Architecture）|
| S12 Roadmap | ✅ 完了（Wave2 Roadmap）|
| S13 APP STARTER OS | ✅ 完了 |
| **S14 PR Development** | **🔄 進行中（PR-044 準備中）** |
| S15〜S23 | ⬜ 未実施 |

---

## 次のアクション

1. PR-044 の Input Sheet を完成させる
2. Validation 4種を実行して PASS を確認
3. PR-044 実装
4. Wave2 MVP 完成後に S15 Release へ進む
5. Release 後に `05_FOUNDER_WEEKLY_SYSTEM.md` の運営ルーティンを開始

---

## IPPO での Founder Workflow OS 活用のポイント

| Workflow OS ファイル | IPPO での活用 |
|-------------------|-------------|
| `01_FOUNDER_WORKFLOW.md` | Wave2 は S14 PR Development フェーズ |
| `02_STAGE_GATE.md` | PR開始前に Gate B1/B2 を確認 |
| `03_DECISION_CHECKPOINTS.md` | CP-03（設計凍結）は完了済み。次は CP-05（β公開）|
| `04_APP_LIFECYCLE.md` | 現在 MVP フェーズ |
| `05_FOUNDER_WEEKLY_SYSTEM.md` | Single Product 開発期モデルで運営 |
| `06_PORTFOLIO_MANAGEMENT.md` | State 1（開発中）で管理中 |
| `07_ASSET_ACCUMULATION_SYSTEM.md` | PR Generator OS が Template資産・OS資産として蓄積中 |
