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

## [0.4.1] — 2026-06-29

### Added

- **Execution Metadata** — Dispatcher が Mode 決定後に必ず生成する構造化レコード
  - フィールド: `Mode / Reason / Dispatcher Version / Escalation / Generated At`
  - Escalation 発生時は `Previous Mode / Current Mode / Escalation Reason` を追記

### Changed

- `00_EXECUTION_DISPATCHER.md` — Execution Metadata 生成仕様追加、Execution Flow 更新（Dispatcher → Metadata → Implementation → Completion Report → Progress Registry）
- `FAST_MODE.md` — Execution Metadata テンプレート追加
- `STANDARD_MODE.md` — Execution Metadata テンプレート追加
- `FULL_MODE.md` — Execution Metadata テンプレート追加
- `09_COMPLETION_REPORT_TEMPLATE.md` — `Execution Metadata` セクション追加（Dispatcher から転記）
- `08_DEFINITION_OF_DONE.md` — Execution Metadata 生成・転記確認の 3項目追加
- `README.md` — Execution Flow 図追加
- `founder-workflow-os/08_PROGRESS_REGISTRY.md` — Live Progress Template に `Dispatcher Version / Escalation` フィールド追加

### Notes

- Execution Metadata は Completion Report と Progress Registry に必ず引き継ぐ
- これにより「このPRをどのModeで実装したか」が後から追跡可能になる
- Decision Log 更新条件・Progress Registry の Live/Milestone 設計は変更なし

---

## [0.4.0] — 2026-06-28

### Added

- `development-os/pr-generator-os/00_EXECUTION_DISPATCHER.md` — PR 開始時に最初に読む Mode 選択ルール
- `development-os/pr-generator-os/FAST_MODE.md` — 通常 PR 用の低コンテキスト消費モード
- `development-os/pr-generator-os/STANDARD_MODE.md` — 新 Domain / Service / Event など重要度中 PR 用モード
- `development-os/pr-generator-os/FULL_MODE.md` — Architecture / Migration / Release など完全監査モード

### Changed

- `development-os/pr-generator-os/README.md` — Execution Mode Dispatcher セクション追加、ファイル構成更新、v0.4 へバージョンアップ
- `development-os/pr-generator-os/02_PR_INPUT_SHEET.md` — Execution Mode / Mode Reason / Escalation Required フィールド追加
- `development-os/pr-generator-os/08_DEFINITION_OF_DONE.md` — Execution Mode 確認セクション追加（Mode選択・Mode固有チェック・Escalation確認）
- `development-os/pr-generator-os/09_COMPLETION_REPORT_TEMPLATE.md` — Execution Mode / Mode Reason / Skipped Checks / Escalation フィールド追加
- `founder-workflow-os/08_PROGRESS_REGISTRY.md` — Live Progress Template と IPPO Snapshot に Execution Mode Used フィールド追加

### Notes

- モード選択は AI の独自判断ではなく OS ルール（00_EXECUTION_DISPATCHER.md）に基づく
- 判断に迷う場合は STANDARD_MODE。Security / Privacy / AI / Research / Release は必ず FULL_MODE
- IPPO PR-044 以降は Execution Dispatcher を使用して実装を開始する

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
