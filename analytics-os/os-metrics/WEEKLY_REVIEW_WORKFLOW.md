# WEEKLY_REVIEW_WORKFLOW

> Claude Code が毎週実施する Analytics OS の標準フロー。
> 「Founder Operating System の週次レビューを実施してください。Analytics OS に従ってください。」の一言で実行できる。

---

## 実行トリガー

```
Founder Operating System の週次レビューを実施してください。
Analytics OS に従ってください。
Founder Operating System のみ更新してください。
```

---

## 実行フロー（Snapshot First）

```
Step 1: CURRENT_STATE.md を読む（スナップショット取得）
  ↓
Step 2: CONTEXT_LOADER.md で読むファイルを決定
  ↓
Step 3: Progress Registry 確認（Live Progress のみ）
  ↓
Step 4: OS Usage 集計（OS_USAGE_MATRIX.md を更新）
  ↓
Step 5: Balance Score 計算（OS_BALANCE_SCORE.md を差分更新）
  ↓
Step 6: OS Scorecard 確認（変更があった OS の行だけ更新）
  ↓
Step 7: Founder Efficiency 更新（FOUNDER_EFFICIENCY.md）
  ↓
Step 8: Weekly Review 記入（WEEKLY_REVIEW_TEMPLATE.md）
  ↓
Step 9: Decision Log 更新条件確認（条件未達なら「更新不要」と明示）
  ↓
Step 10: CURRENT_STATE.md を最新状態に更新
  ↓
Step 11: 改善提案（Wave2 中は記録のみ・実装禁止）
```

---

## Step 詳細

### Step 1 — CURRENT_STATE.md を読む

`CURRENT_STATE.md` だけ読んで現在状態を把握する。
**全 Analytics ファイルの一括読込は禁止。**

### Step 2 — CONTEXT_LOADER.md で読むファイルを決定

週次レビューの場合: `CURRENT_STATE → Usage → Scorecard → Review`
それ以外の場合: `CONTEXT_LOADER.md` のルールに従う。

### Step 3 — Progress Registry 確認

`founder-workflow-os/08_PROGRESS_REGISTRY.md` の Live Progress を確認する。
Milestone History は **Phase / Wave 完了時のみ** 更新。通常週は触らない。

### Step 4 — OS Usage 集計

今週 Claude Code が参照した OS を集計して `OS_USAGE_MATRIX.md` の最新週に記入する。

### Step 5 — Balance Score 計算

```
Balance Score = 使用 OS 数 ÷ 13 × 100
```

`OS_BALANCE_SCORE.md` の現在値テーブルと履歴のみ更新。

### Step 6 — OS Scorecard 確認

今週 OS が更新・追加されていたら該当行のみ差分更新。
変更がない OS は `No Change` — 行を触らない。

### Step 7 — Founder Efficiency 更新

今週増えた Asset を `FOUNDER_EFFICIENCY.md` の最新週に記入。
Founder Efficiency（種類数）と Asset Accumulation Score（累積）を更新。

### Step 8 — Weekly Review 記入

`WEEKLY_REVIEW_TEMPLATE.md` に今週分を記入。前週分は末尾にアーカイブ。

### Step 9 — Decision Log 更新条件確認

`09_DECISION_LOG.md` の Update Rule を確認。
条件に該当しなければ **「Decision Log 更新不要」** と明示して終了。

### Step 10 — CURRENT_STATE.md 更新

すべての更新を反映して `CURRENT_STATE.md` を最新状態に上書きする。

### Step 11 — 改善提案

今週の分析から改善案を提出。**Wave2 期間中は実装禁止・Decision 候補として記録のみ。**

---

## 出力形式

```
## Weekly Review — YYYY-WXX

Step 1: CURRENT_STATE 確認 ✅
Step 3: Progress — Current PR: PR-XXX / Completion X%
Step 4: OS Usage — Total X 回 / X OS 使用
Step 5: Balance Score — X%
Step 6: Scorecard — [変更あり: XXX OS X%→X%] / 変更なし
Step 7: Founder Efficiency — X 種類 / 週 / 累積 X 件
Step 9: Decision Log — 更新不要 / DLOG-XXX 更新
Step 10: CURRENT_STATE 更新 ✅

改善提案:
1. [Wave2 完了後の候補]
```

---

## イベント別更新ルール

| イベント | 更新ステップ |
|---------|-----------|
| 通常 PR 完了 | Step 1, 3, 10 のみ（Usage/Score は週次レビュー時）|
| 週次レビュー | Step 1〜11 全部 |
| Phase 完了 | Step 1, 3（Milestone 更新）, 5, 6, 10 |
| Wave 完了 | Step 1〜11 全部（Analytics 全体をフル更新）|
| Founder OS 更新 | Step 1, 6（Scorecard 差分のみ）, 10 |

---

## 制約

- `METRICS_DEFINITION.md` は毎週読まない（定義が変わった時だけ読む）
- `FOUNDER_EFFICIENCY.md` の過去週は触らない
- Decision Log は更新条件に該当する場合のみ
- Wave2 中に新 OS を追加しない（Founder OS Freeze Rule）
- Progress Registry の Milestone History は Phase/Wave 完了時のみ
