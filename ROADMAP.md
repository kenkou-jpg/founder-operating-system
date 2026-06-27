# Roadmap — Founder Operating System

> OSそのもののバージョンロードマップ。
> 各バージョンで「何が使えるようになるか」を定義する。

---

## バージョニング

| バージョン | 意味 |
|-----------|------|
| v0.x | Foundation — 骨格の構築期 |
| v1.x | Operational — 実際に使える状態 |
| v2.x | Integrated — AI・自動化との統合 |

---

## v0.1 — Foundation Skeleton
**目標:** OSの骨格を完成させる

**ステータス:** ✅ 完了（2026-06-27）

### 含まれるもの

- [x] `README.md` — OS全体の説明
- [x] `FOUNDER_PHILOSOPHY.md` — 根本思想
- [x] `OPERATING_PRINCIPLES.md` — 運営原則（18原則）
- [x] `CANONICAL_SOURCE.md` — 情報ヒエラルキー
- [x] `ROADMAP.md` — このファイル
- [x] `governance/CHANGELOG.md` — 変更履歴テンプレート
- [x] 全12ドメインOS の `README.md`（目的・責務のみ）
- [x] `portfolio-os/` のプロダクトプロファイル（骨格）
- [x] `governance/` の意思決定管理構造

### v0.1 完了基準

- OSの思想・原則・情報ヒエラルキーが文書化されている
- 全ドメインOSが存在し、目的が明確
- 新プロダクト立ち上げ時に「どこを見ればいいか」がわかる状態

---

## v0.5 — OS Content
**目標:** 各ドメインOSに実際のコンテンツを充実させる

**ステータス:** 🔄 未着手

**予定時期:** 2026 Q3〜Q4

### 含まれるもの

- [ ] `development-os/` — 技術スタック選定基準・コーディング規約・セキュリティ標準
- [ ] `business-os/` — GTMプレイブック・価格設計原則・PMF基準
- [ ] `brand-os/` — ブランドボイス・ビジュアルアイデンティティ原則
- [ ] `legal-os/` — 利用規約ひな形・プライバシーポリシーひな形
- [ ] `analytics-os/` — KPI定義辞書・ダッシュボード設計原則
- [ ] `finance-os/` — 月次財務チェックリスト・投資判断フレームワーク
- [ ] `operations-os/` — 週次・月次・四半期レビュー手順書
- [ ] `templates/APP_STARTER_TEMPLATE/` — 実用的なスターターテンプレート
- [ ] `templates/COUNCIL_TEMPLATE/` — ペルソナ会議の実用テンプレート
- [ ] ippo の知見をOSへフィードバック

### v0.5 完了基準

- 主要なドメインOSにコンテンツが存在する
- ippo の開発・運営で使ったパターンがOSに反映されている
- 新プロダクト立ち上げ時に「コピーして使えるもの」がある状態

---

## v1.0 — Operational OS
**目標:** 実際の運営で使い続けられる、完成したOS

**ステータス:** 🔄 未着手

**予定時期:** 2027 Q1〜Q2

### 含まれるもの

- [ ] 全ドメインOSのコンテンツが充実
- [ ] ippo / AgriPath での実績がOSに反映
- [ ] `templates/` が実際に使えるテンプレート集として完成
- [ ] `governance/ADR/` に重要な技術判断が蓄積
- [ ] `knowledge-os/` にナレッジが蓄積
- [ ] `research-os/` に市場調査インサイトが蓄積
- [ ] Portfolio KPI が実際に運用されている

### v1.0 完了基準

- 新プロダクトを72時間以内に「立ち上げ開始」できる
- OSを読めば、創業者の思想・基準・手順がすべて理解できる
- 2つ以上のプロダクトが実際にこのOSを参照して運営されている

---

## v2.0 — AI-Integrated OS
**目標:** AIエージェントがこのOSを読み込み、自律的に判断・実行できる状態

**ステータス:** 🔄 未着手

**予定時期:** 2028 以降（v1.0完成後に計画）

### 構想

- AIエージェントへのシステムプロンプトとしてOSを活用
- Claude / Cursor 等のAIコーディングツールがOSの原則に従って提案
- 意思決定のAI支援（Council AI）
- 自動レポーティング（KPI・財務・ポートフォリオ）

### 前提条件

- v1.0が実際の運営で検証済みであること
- AIエージェント技術が十分に成熟していること

---

## 次の優先アクション（v0.1 → v0.5へ）

1. ippo の開発で発生した技術判断を `governance/ADR/` に記録する
2. `development-os/` に実際の技術スタック標準を書く
3. `operations-os/` に週次レビュー手順を実装する
4. `analytics-os/` にKPI定義を書く（ippoのKPIから始める）
5. `portfolio-os/IMAGING_AGRICULTURE.md` を作成する
