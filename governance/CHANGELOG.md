# Changelog — Founder Operating System

> このファイルはFounder OSの変更履歴を記録します。
> バージョニング: `MAJOR.MINOR.PATCH`

---

## How to Write

```markdown
## [X.Y.Z] — YYYY-MM-DD

### Added
- 新しく追加された文書・原則・テンプレート

### Changed
- 変更された内容（以前との違いを明記）

### Deprecated
- 今後削除予定のもの

### Removed
- 削除されたもの（なぜ削除したかを必ず書く）

### Fixed
- 誤り・矛盾の修正
```

---

## [0.3.0] — 2026-06-28

### Added

- `founder-workflow-os/08_PROGRESS_REGISTRY.md` — Founder OS と各アプリの現在地管理
  - Progress Snapshot Template
  - IPPO Current Snapshot（Wave2 / PR-044 準備中）
  - Founder OS Progress Snapshot（v0.3）
  - Portfolio Table（IPPO / AgriPath / Imaging Agriculture / Founder OS）
  - Update Rule（PR完了時・Stage変更時など）

- `founder-workflow-os/09_DECISION_LOG.md` — Founder 判断の Append-Only 記録
  - Decision Log Template
  - DLOG-001: Founder OS を独立リポジトリで管理する
  - DLOG-002: PR Generator OS を全アプリ共通の Development OS として管理する
  - DLOG-003: Council Generator OS / Architecture Generator OS は後回しにする
  - DLOG-004: Progress Registry / Decision Log 作成後に IPPO 開発へ戻る
  - DLOG-005: Progress Registry / Decision Log は IPPO Governing Documents ではない

### Changed

- `founder-workflow-os/README.md` — Progress Registry / Decision Log の説明と IPPO PR-044 への戻り方を追記
- `CANONICAL_SOURCE.md` — Progress Registry / Decision Log のエントリを追加、権限定義（記録のみ / Binding Authority なし）を明文化

### Notes

- Progress Registry と Decision Log は IPPO の設計・ロードマップ・Architecture を変更しない
- これらは状態管理と意思決定記録のための Founder OS 側ドキュメント
- 次のアクション: IPPO PR-044 の実装に戻る

---

## [0.2.0] — 2026-06-27

### Added

**PR Generator OS** (`development-os/pr-generator-os/`)
- `README.md` — v0.2、フロー図、Validation 前提条件
- `01_PR_PROMPT_TEMPLATE.md` 〜 `14_PR_SCOPE_VALIDATOR.md`（14ファイル）
- `examples/IPPO_PR044_EXAMPLE.md`
- `examples/GENERIC_DOMAIN_PR_EXAMPLE.md`

**Founder Workflow OS** (`founder-workflow-os/`)
- `README.md` — 水平オーケストレーターとして位置づけ
- `01_FOUNDER_WORKFLOW.md` 〜 `07_ASSET_ACCUMULATION_SYSTEM.md`（7ファイル）
- `examples/IPPO_WORKFLOW.md`
- `examples/GENERIC_APP_WORKFLOW.md`

---

## [0.1.0] — 2026-06-27

### Added

**Core Documents**
- `README.md` — OS全体の説明・構造・利用方法・将来像
- `FOUNDER_PHILOSOPHY.md` — 根本思想（Operating Philosophy / Long-term Thinking / 永続設計 / One Person Company / Customer First / No Sales First / Automation First / Knowledge Asset First / Research Integrity / Founder Health）
- `OPERATING_PRINCIPLES.md` — 18の運営原則
- `CANONICAL_SOURCE.md` — 情報ヒエラルキーと更新ルール
- `ROADMAP.md` — v0.1〜v2.0のロードマップ

**Domain OSes（README.mdのみ）**
- `development-os/README.md`
- `business-os/README.md`
- `brand-os/README.md`
- `legal-os/README.md`
- `research-os/README.md`
- `finance-os/README.md`
- `analytics-os/README.md`
- `customer-success-os/README.md`
- `automation-os/README.md`
- `operations-os/README.md`
- `knowledge-os/README.md`
- `template-business-os/README.md`

**Portfolio OS**
- `portfolio-os/IPPO.md`
- `portfolio-os/AGRIPATH.md`
- `portfolio-os/FASTING_APP.md`
- `portfolio-os/PORTFOLIO_KPI.md`

**Templates（骨格のみ）**
- `templates/PR_TEMPLATE.md`
- `templates/ARCHITECTURE_TEMPLATE.md`
- `templates/BUSINESS_STRATEGY_TEMPLATE.md`
- `templates/APP_STARTER_TEMPLATE/README.md`
- `templates/COUNCIL_TEMPLATE/README.md`

**Governance**
- `governance/DECISION_LOG.md`
- `governance/BINDING_DECISIONS.md`
- `governance/CHANGELOG.md`（このファイル）
