# Canonical Source

> どの文書が上位文書か。どこを更新すれば良いか。
> 情報のヒエラルキーを定義する。

---

## なぜCanonical Sourceが必要か

情報が複数の場所に存在するとき、どれが「正」かが曖昧になる。
Canonical Source = **唯一の正しい在り処** を定義することで、
「どこを見れば正しいか」「どこを更新すれば良いか」を常に明確にする。

**ルール:**
- 同じ情報を2箇所に書かない
- 書く場合は「参照元はどこか」を明示する
- コピーではなくリンクで参照する
- Canonical Sourceが変わったら、このファイルを先に更新する

---

## Document Hierarchy（文書ヒエラルキー）

```
Level 0: 根本思想（変更コスト最大）
├── FOUNDER_PHILOSOPHY.md
└── OPERATING_PRINCIPLES.md

Level 1: OS定義（半年〜年単位で変化）
├── CANONICAL_SOURCE.md       ← このファイル
├── ROADMAP.md
└── governance/BINDING_DECISIONS.md

Level 2: ドメインOS（四半期単位で変化）
├── development-os/README.md
├── business-os/README.md
├── brand-os/README.md
├── legal-os/README.md
├── research-os/README.md
├── finance-os/README.md
├── analytics-os/README.md
├── customer-success-os/README.md
├── automation-os/README.md
├── operations-os/README.md
├── knowledge-os/README.md
└── template-business-os/README.md

Level 3: プロダクト定義（月単位で変化）
└── portfolio-os/
    ├── IPPO.md
    ├── AGRIPATH.md
    ├── IMAGING_AGRICULTURE.md
    ├── FASTING_APP.md
    └── PORTFOLIO_KPI.md

Level 4: テンプレート・ガバナンス（随時更新）
├── templates/
└── governance/
    ├── ADR/
    ├── DECISION_LOG.md
    └── CHANGELOG.md
```

**上位レベルの変更は下位に影響する。**
Level 0を変更するときは、すべての下位文書への影響を検討する。

---

## OS Layer — Canonical Source 一覧

| 情報の種類 | Canonical Source | 更新頻度 |
|-----------|----------------|---------|
| 創業者の根本思想 | `FOUNDER_PHILOSOPHY.md` | 年次 |
| 事業横断の運営原則 | `OPERATING_PRINCIPLES.md` | 四半期 |
| 情報のヒエラルキー | `CANONICAL_SOURCE.md`（このファイル） | 随時 |
| OSバージョン計画 | `ROADMAP.md` | 四半期 |
| 技術方針・開発標準 | `development-os/README.md` | 四半期 |
| ブランドガイドライン | `brand-os/README.md` | 年次 |
| KPI定義（全社） | `analytics-os/README.md` | 四半期 |
| ポートフォリオKPI | `portfolio-os/PORTFOLIO_KPI.md` | 月次 |
| 法務方針 | `legal-os/README.md` | 随時 |
| 重要意思決定の記録 | `governance/DECISION_LOG.md` | 随時 |
| 変更履歴 | `governance/CHANGELOG.md` | 随時 |
| 拘束力のある決定 | `governance/BINDING_DECISIONS.md` | 随時 |

---

## Product Layer — Canonical Source 一覧

| プロダクト | 情報の種類 | Canonical Source |
|-----------|-----------|----------------|
| ippo | プロダクト概要・ブランド | `portfolio-os/IPPO.md` |
| ippo | アーキテクチャ | ippoリポジトリ `docs/ARCHITECTURE.md` |
| ippo | 事業戦略 | ippoリポジトリ `docs/BUSINESS_STRATEGY.md` |
| ippo | KPI数値 | Supabase Analytics（定義は `analytics-os/`） |
| AgriPath | プロダクト概要 | `portfolio-os/AGRIPATH.md` |
| Imaging Agriculture | 研究概要 | `portfolio-os/IMAGING_AGRICULTURE.md` |
| Fasting App | プロダクト概要 | `portfolio-os/FASTING_APP.md` |

---

## External Systems — Canonical Source 一覧

| 情報の種類 | システム | 補足 |
|-----------|---------|------|
| ソースコード | GitHub（各リポジトリ） | |
| タスク管理 | GitHub Issues / Projects | 各リポジトリ |
| 財務数値 | 会計ソフト | 方針はfiance-osが定義 |
| ユーザーデータ | Supabase | スキーマ定義はリポジトリ内 |
| 競合・市場データ | `research-os/` | インサイトの蓄積 |

---

## 更新ルール

### Canonical Sourceを変更するとき

1. このファイル（CANONICAL_SOURCE.md）を先に更新する
2. 変更が重要な場合は `governance/DECISION_LOG.md` に記録する
3. 参照していた文書があれば、リンクを更新する

### 「どこに書くべきか」判断フロー

```
この情報は特定のプロダクトだけに関係する？
  Yes → そのプロダクトのリポジトリ
  No  ↓
複数プロダクトで共通の方針・基準か？
  Yes → 該当するドメインOS（development-os等）
  No  ↓
創業者の思想・判断基準か？
  Yes → FOUNDER_PHILOSOPHY または OPERATING_PRINCIPLES
  No  ↓
情報の在り処の定義か？
  Yes → CANONICAL_SOURCE.md（このファイル）
```
