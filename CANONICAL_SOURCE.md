# Canonical Source — 真実の在り処マップ

> 「どこが正しい情報か」を常に明確にする。コピーではなく参照。

## What is a Canonical Source?

情報が複数の場所に存在するとき、どれが「正」かが曖昧になる。
このドキュメントは各情報の **唯一の正しい在り処（Canonical Source）** を定義する。

コピーしない。参照する。更新は一箇所で行う。

---

## OS Layer (このリポジトリ内)

| 情報の種類 | Canonical Source |
|-----------|----------------|
| 創業者の根本思想 | `FOUNDER_PHILOSOPHY.md` |
| 事業横断の運営原則 | `OPERATING_PRINCIPLES.md` |
| 技術方針・開発標準 | `development-os/README.md` |
| ブランドガイドライン | `brand-os/README.md` |
| 法務ひな形・方針 | `legal-os/README.md` |
| KPI定義（全社） | `analytics-os/README.md` |
| ポートフォリオKPI | `portfolio-os/PORTFOLIO_KPI.md` |
| 重要意思決定の記録 | `governance/DECISION_LOG.md` |
| 変更履歴 | `governance/CHANGELOG.md` |
| 拘束力のある決定 | `governance/BINDING_DECISIONS.md` |

---

## Product Layer (各プロダクトリポジトリ)

| プロダクト | Canonical Source | 場所 |
|-----------|----------------|------|
| ippo アーキテクチャ | ARCHITECTURE.md | ippo リポジトリ |
| ippo ビジネス戦略 | docs/BUSINESS_STRATEGY.md | ippo リポジトリ |
| ippo KPI | Supabase Analytics | DB + analytics-os定義 |
| AgriPath (TBD) | — | TBD |

---

## External Systems

| 情報の種類 | システム | 補足 |
|-----------|---------|------|
| タスク管理 | GitHub Issues / Projects | 各リポジトリ |
| コード | GitHub | 各リポジトリ |
| 財務記録 | `finance-os/` + 会計ソフト | ここが定義、会計ソフトが数値 |
| ユーザーフィードバック | `customer-success-os/` | 集約・分析のルール定義 |
| 競合・市場調査 | `research-os/` | インサイトの蓄積 |

---

## Rules

1. **同じ情報を2箇所に書かない** — 書く場合は「参照元」を明示する
2. **Canonical Sourceが変わったら、このファイルを先に更新する**
3. **「どこが正しいか分からない」と感じたら、このファイルを確認する**
4. **削除した情報は `governance/DECISION_LOG.md` に理由を記録する**
