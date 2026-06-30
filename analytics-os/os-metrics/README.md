# Analytics OS — OS Metrics

> Founder Operating System の成熟度・使用率・偏りを数値で管理する。
> 毎週 Claude Code が自動レビューできる仕組みを提供する。

---

## 目的

1. **Founder OS がどこまで成熟しているか** — OS Scorecard で可視化
2. **各 OS をどれだけ活用できているか** — Usage Matrix で追跡
3. **偏りなく運用できているか** — Balance Score で検出
4. **Founder Efficiency の向上** — Asset 増加を定量管理

---

## Analytics OS v1.1 — Performance Optimization

Analytics OS v1.1 では **Event Driven Update** と **Snapshot First** を導入しています。

| 原則 | 内容 |
|-----|------|
| **Snapshot First** | 最初に `CURRENT_STATE.md` だけ読む。全ファイル一括読込禁止 |
| **Event Driven Update** | 毎週すべて再計算しない。イベント発生時のみ更新 |
| **Incremental Update** | 変更があった項目だけ差分更新する |
| **Context Loader** | `CONTEXT_LOADER.md` が読むべきファイルを決定する |

---

## Claude Code 標準プロンプト

以下だけで週次レビューを実施できます。

```
Founder Operating System の週次レビューを実施してください。

Analytics OS に従ってください。

Founder Operating System のみ更新してください。
```

---

## ファイル構成

```
analytics-os/os-metrics/
├── README.md                   ← このファイル
├── CURRENT_STATE.md            ← 最初に読む。現在状態スナップショット（v1.1）
├── CONTEXT_LOADER.md           ← 読むファイルを決定するルール（v1.1）
├── METRICS_DEFINITION.md       ← KPI 定義
├── OS_SCORECARD.md             ← OS 別完成率
├── OS_USAGE_MATRIX.md          ← 週次 OS 利用回数
├── OS_BALANCE_SCORE.md         ← 利用バランス分析
├── FOUNDER_EFFICIENCY.md       ← Founder Asset 増加管理
├── WEEKLY_REVIEW_TEMPLATE.md   ← 週次レビュー記入フォーム
└── WEEKLY_REVIEW_WORKFLOW.md   ← Claude Code 実行フロー
```

---

## 更新ルール

| イベント | 更新対象 |
|---------|---------|
| PR 完了 | `CURRENT_STATE.md` の Current PR / Completion % のみ |
| 週次レビュー | CURRENT_STATE → Usage → Scorecard → Review |
| Phase 完了 | CURRENT_STATE + Milestone History + Scorecard 差分 |
| Wave 完了 | Analytics 全体 |
| Founder OS 更新 | Scorecard の該当 OS 行のみ差分更新 |

---

## 関連ドキュメント

- `founder-workflow-os/08_PROGRESS_REGISTRY.md` — 現在地管理
- `founder-workflow-os/09_DECISION_LOG.md` — Founder 判断履歴
- `development-os/pr-generator-os/00_EXECUTION_DISPATCHER.md` — PR 実行モード
