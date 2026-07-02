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

## [0.4.5] — 2026-06-30

### Added

- `BOOTSTRAP.md` — Founder Operating System の唯一の実行起点（v1.0.1）
  - 「Founder Operating System に従ってください。」の解釈を定義
  - 実行順序（BOOTSTRAP → FOUNDER_OS_REFERENCE → Dispatcher → Matrix → Optimization Pack → Implementation）
  - 禁止事項の明示（起点スキップ禁止・探索禁止・推測禁止）

### Changed

- `FOUNDER_OS_REFERENCE.md` — Repository Discovery Policy セクション追加
  - BOOTSTRAP.md → FOUNDER_OS_REFERENCE.md の起動順序を明記
  - Founder OS Invocation 定義追加（プロンプトと同義の処理を定義）
  - ヘッダーを BOOTSTRAP 起点に更新
- `00_EXECUTION_DISPATCHER.md` — Execution Flow 先頭に BOOTSTRAP ステップ追加。関連ドキュメントに BOOTSTRAP.md を追加。
- `README.md` — BOOTSTRAP.md 起点の Execution 開始・Repository Discovery 禁止を追記。Execution Flow 更新。

### Notes

- Added BOOTSTRAP.md: Execution Dispatcher now starts from BOOTSTRAP
- Repository Discovery Policy added: Claude Code no longer discovers or searches for Founder OS
- Founder OS invocation is now deterministic: single prompt triggers full OS execution
- Reduced unnecessary repository search: context efficiency further improved

---

## [0.4.4] — 2026-06-30

### Added

- `FOUNDER_OS_REFERENCE.md` — External Repository Mapping v1.0
  - Founder OS が IPPO とは独立した Repository で管理されることを明示
  - Repository Mapping テーブル（Development OS / PR Generator OS / Founder Workflow OS / Analytics OS / Execution Dispatcher / Optimization Pack ほか）
  - PR タイプ別 Loading Rules（通常 PR / FULL PR / 週次レビュー）
  - Claude Code への禁止事項（Repository 探索・推測・IPPO 内での検索）
  - IPPO と Founder OS の関係定義

### Changed

- `00_EXECUTION_DISPATCHER.md` — Execution Flow の先頭に FOUNDER_OS_REFERENCE.md 確認ステップを追加。Repository 探索禁止を明記。関連ドキュメントに追加。
- `README.md` — Execution Dispatcher 章に Founder OS 独立 Repository 管理・FOUNDER_OS_REFERENCE.md 起点参照・探索禁止を追記。Execution Flow 更新。

### Notes

- Added External Repository Mapping: Execution Dispatcher now supports external Founder OS references
- Repository discovery removed: Claude Code no longer searches for Founder OS files
- Reduced unnecessary repository search: context efficiency improved
- Claude Code execution is now deterministic from FOUNDER_OS_REFERENCE → Dispatcher → Matrix

---

## [0.4.3] — 2026-06-30

### Added

- `development-os/pr-generator-os/MODE_SELECTION_MATRIX.md` — ルールベース Mode 決定マトリクス v1.0
  - FAST / STANDARD / FULL の対象 PR タイプを網羅的に定義
  - 14 ステップ判定フロー（FULL 優先 → STANDARD → FAST）
  - 複合 PR ルール（最高リスク優先）
  - Escalation ルール（実行中の発見による上位 Mode 切替）

### Changed

- `00_EXECUTION_DISPATCHER.md` — Execution Flow を MODE_SELECTION_MATRIX 起点に更新
  - 推測禁止・ルールベース決定を明記
  - Flow: MODE_SELECTION_MATRIX → Execution Mode 決定 → SMART_DOCUMENT_LOADING → TOKEN_OPTIMIZATION → REPORT_OPTIMIZATION → PR_INPUT_SHEET → Validation → Implementation → Completion Report → Progress Registry → Decision Log判定
  - 関連ドキュメントに MODE_SELECTION_MATRIX.md 追加
- `FAST_MODE.md` — MODE_SELECTION_MATRIX で選択された場合のみ利用する旨を追記
- `STANDARD_MODE.md` — 同様に追記
- `FULL_MODE.md` — 同様に追記
- `README.md` — Mode Selection Matrix セクション追加・Execution Flow に Decision Log 判定を追加

### Notes

- Execution Dispatcher がルールベースになったことで Claude Code の実行が決定論的になった
- 推測による Mode 選択を廃止。不明な場合は上位 Mode を選択するルールを明示

---

## [0.5.1] — 2026-06-30

### Added

- `analytics-os/os-metrics/CURRENT_STATE.md` — Snapshot First の起点。PR 完了・週次レビュー時に更新（v1.1）
- `analytics-os/os-metrics/CONTEXT_LOADER.md` — イベント別ファイルロードルール。全ファイル一括読込禁止（v1.1）

### Changed

- `analytics-os/os-metrics/README.md` — v1.1 原則（Snapshot First / Event Driven / Incremental Update / Context Loader）追記
- `analytics-os/os-metrics/WEEKLY_REVIEW_WORKFLOW.md` — Snapshot First フロー・イベント別更新ルール追記

---

## [0.5.0] — 2026-06-30

### Added

- `analytics-os/os-metrics/README.md` — Analytics OS os-metrics サブシステム概要
- `analytics-os/os-metrics/METRICS_DEFINITION.md` — 10 KPI 定義（Completion Rate / Usage Count / Usage % / Balance Score / PR Success Rate / Scope Creep / Architecture Violation / Template Reuse / Founder Efficiency / Asset Accumulation）
- `analytics-os/os-metrics/OS_SCORECARD.md` — OS 別 Completion Rate（初期値 / 差分更新ルール / 履歴）
- `analytics-os/os-metrics/OS_USAGE_MATRIX.md` — 週次 OS 利用回数 / Usage % / 利用カウント基準
- `analytics-os/os-metrics/OS_BALANCE_SCORE.md` — Balance Score 計算式 / 現在値 / 偏り分析 / 閾値 / 改善提案
- `analytics-os/os-metrics/FOUNDER_EFFICIENCY.md` — 10 Asset カテゴリ / 週次記録 / 目標
- `analytics-os/os-metrics/WEEKLY_REVIEW_TEMPLATE.md` — 週次レビュー記入フォーム（前週アーカイブ込み）
- `analytics-os/os-metrics/WEEKLY_REVIEW_WORKFLOW.md` — Claude Code 実行フロー（Step 1〜11）

### Changed

- `analytics-os/README.md` — os-metrics セクション追加・週次レビュープロンプト追加
- `CANONICAL_SOURCE.md` — Founder OS 成熟度の Canonical Source として `CURRENT_STATE.md` 追記

### Notes

- Analytics OS v1.0: Founder OS 自体の定量管理を開始
- 週次レビュープロンプト1行で全指標を自動更新できる仕組みを確立

---

## [0.4.2] — 2026-06-29

### Added

- `development-os/pr-generator-os/SMART_DOCUMENT_LOADING.md` — Mode 別文書読込ルール（FAST/STANDARD/FULL + Escalation Loading）
- `development-os/pr-generator-os/REPORT_OPTIMIZATION.md` — Completion Report の Mode 別最適化（FAST:20行 / STANDARD:50行 / FULL:詳細可・重複禁止）
- `development-os/pr-generator-os/TOKEN_OPTIMIZATION.md` — トークン消費の行動規範（Must / Must Not / Test / Output 最適化）

### Changed

- `00_EXECUTION_DISPATCHER.md` — Mode 決定後の参照順序に Optimization Pack 3ファイルを追加
- `FAST_MODE.md` — Optimization Pack 必須参照セクション追加
- `STANDARD_MODE.md` — Optimization Pack 必須参照セクション追加
- `FULL_MODE.md` — Optimization Pack 必須参照セクション追加
- `09_COMPLETION_REPORT_TEMPLATE.md` — REPORT_OPTIMIZATION.md 参照注記追加
- `README.md` — Optimization Pack v0.4.2 セクション・ファイル構成・バージョン表記更新

### Notes

- 削ってよいもの: 長文要約・全文書一括読込・重複説明・毎回の全 BD 列挙・既知失敗の深掘り
- 削ってはいけないもの: Scope確認・BD重大違反確認・Architecture Guard・Test・Build・PR責務分離
- Decision Log 更新条件・Progress Registry 方針・Founder OS Freeze Rule は変更なし

---

## [0.4.1-dlog] — 2026-06-29

### Added

- `founder-workflow-os/09_DECISION_LOG.md` — DLOG-006: Founder Capability OS 構想を Append-Only で記録
  - Wave2 期間中は Founder OS Freeze Rule により実装禁止
  - Wave2 完了後（PR-075 以降）に Council + Founder 承認を経て設計候補へ昇格予定

### Notes

- Founder Capability OS の実装は行っていない
- 新ディレクトリ・新 OS・構造変更は一切行っていない
- Wave2 ロードマップ変更なし

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
