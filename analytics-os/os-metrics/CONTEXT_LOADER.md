# CONTEXT_LOADER

> Analytics OS v1.1 — イベント別に読むファイルを決定するルール。
> 最初に `CURRENT_STATE.md` を読んでから、このファイルでロード範囲を決定する。
> 全 Analytics ファイルの一括読込は禁止。

---

## 基本原則

```
1. CURRENT_STATE.md を読む（必須・毎回）
2. CONTEXT_LOADER.md でイベントを判定する（このファイル）
3. 必要なファイルだけ読む
4. 不要なファイルは読まない
```

---

## イベント別ロードルール

### 通常 PR 完了

```
読むファイル:
  - CURRENT_STATE.md（必須）

更新するファイル:
  - CURRENT_STATE.md（Current PR / Completion % のみ）

読まないファイル:
  - OS_USAGE_MATRIX.md（週次レビュー時のみ）
  - OS_SCORECARD.md（OS 変更がなければ不要）
  - OS_BALANCE_SCORE.md（週次レビュー時のみ）
  - FOUNDER_EFFICIENCY.md（週次レビュー時のみ）
  - METRICS_DEFINITION.md（定義変更時のみ）
```

---

### 週次レビュー

```
読むファイル（この順番で読む）:
  1. CURRENT_STATE.md
  2. OS_USAGE_MATRIX.md
  3. OS_SCORECARD.md
  4. WEEKLY_REVIEW_TEMPLATE.md
  5. FOUNDER_EFFICIENCY.md
  6. OS_BALANCE_SCORE.md

更新するファイル:
  - OS_USAGE_MATRIX.md（今週の Usage 追記）
  - OS_SCORECARD.md（変更があった OS 行のみ）
  - OS_BALANCE_SCORE.md（現在値 + 履歴）
  - FOUNDER_EFFICIENCY.md（今週の Asset 追記）
  - WEEKLY_REVIEW_TEMPLATE.md（今週分記入 + 前週アーカイブ）
  - CURRENT_STATE.md（全フィールド更新）

読まないファイル:
  - METRICS_DEFINITION.md（定義変更がなければ不要）
  - WEEKLY_REVIEW_WORKFLOW.md（フロー確認が必要な時のみ）
```

---

### Phase 完了

```
読むファイル:
  1. CURRENT_STATE.md
  2. OS_SCORECARD.md
  3. founder-workflow-os/08_PROGRESS_REGISTRY.md（Milestone History 更新のため）

更新するファイル:
  - CURRENT_STATE.md（Phase / Wave / Completion %）
  - OS_SCORECARD.md（該当 OS 差分）
  - founder-workflow-os/08_PROGRESS_REGISTRY.md（Milestone History 追記）
  - OS_BALANCE_SCORE.md（Balance Score 差分）
```

---

### Wave 完了

```
読むファイル（フル読込）:
  1. CURRENT_STATE.md
  2. OS_USAGE_MATRIX.md
  3. OS_SCORECARD.md
  4. OS_BALANCE_SCORE.md
  5. FOUNDER_EFFICIENCY.md
  6. WEEKLY_REVIEW_TEMPLATE.md
  7. founder-workflow-os/08_PROGRESS_REGISTRY.md

更新するファイル:
  - Analytics 全体（全ファイル）
  - founder-workflow-os/08_PROGRESS_REGISTRY.md（Milestone History 追記）
```

---

### Founder OS 更新（新ファイル追加・OS 完成度変化）

```
読むファイル:
  1. CURRENT_STATE.md
  2. OS_SCORECARD.md（該当 OS 行だけ確認）

更新するファイル:
  - OS_SCORECARD.md（該当 OS 行のみ差分更新）
  - CURRENT_STATE.md（OS Overview の Overall Score）

読まないファイル:
  - Usage / Balance / Efficiency（OS 更新では不要）
```

---

### METRICS_DEFINITION.md を読む条件

```
以下のいずれかに該当する場合のみ読む:
  - KPI 定義を変更したい
  - 新しい KPI を追加したい
  - 計算式に疑問がある
  
通常の週次レビュー・PR 完了では読まない。
```

---

## 一括読込禁止ルール

```
禁止: "Analytics OS の全ファイルを読む"
禁止: "毎回 METRICS_DEFINITION.md を読む"
禁止: "Wave 完了でもないのに全 Analytics ファイルを読む"

理由: Context 消費の最適化（Token Optimization）
```

---

## Claude Code 自己チェック

```
Analytics OS を使う前に以下を確認:

□ CURRENT_STATE.md を最初に読んだか？
□ CONTEXT_LOADER.md でイベントを判定したか？
□ 不要なファイルを読んでいないか？
□ 差分更新が必要なファイルのみ更新したか？
□ 全ファイル一括更新していないか？
```
