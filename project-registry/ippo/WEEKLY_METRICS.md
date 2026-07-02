# IPPO — WEEKLY_METRICS

> IPPO の週次 KPI・Velocity・プロジェクト固有指標を管理する。
> Analytics OS（analytics-os/）にはプロジェクト固有 KPI を書かない。
> IPPO の数値指標はここに記録する。

---

## Weekly Metrics Template

```
Week: YYYY-WXX（例: 2026-W28）

Development Metrics:
  PR 完了数:    X 件
  テスト追加数: X 件
  Build 状態:   PASS / FAIL
  Bug 件数:     X 件（新規）/ X 件（修正）
  Scope Creep:  なし / あり（内容）

Velocity:
  PR Velocity:  X PR / 週
  Test Velocity:X テスト / PR

Product KPI（Beta Release 後に記録開始）:
  MAU:          — / X 人
  MRR:          — / ¥X
  7日 Retention:— / X%
  Churn Rate:   — / X%
```

---

## 週次記録（直近）

### 2026-W27（2026-06-23〜06-29）

```
Development Metrics:
  PR 完了数:    0 件（PR-044 準備中）
  テスト追加数: 0 件
  Build 状態:   PASS
  Bug 件数:     0 件（新規）/ 0 件（修正）
  Scope Creep:  なし

Velocity:
  PR Velocity:  0 PR / 週（Founder OS 構築週）
  Test Velocity:— 

Product KPI:
  MAU:          — （Beta Release 前）
  MRR:          — （Beta Release 前）
  7日 Retention:—
  Churn Rate:   —
```

---

## Milestone KPI（累積）

| Milestone | PR 数 | テスト数 | Bug 数（累積）|
|---------|------|---------|------------|
| Wave1 Complete | — | — | — |
| Wave2 Phase A 完了（予定）| 14 PRs | — | — |
| Beta Release（予定）| ~35 PRs | — | — |

---

## 更新ルール

```
PR 完了時:
  1. PR 完了数・テスト追加数・Build 状態を記録する
  2. analytics-os/ には記録しない

週次レビュー時:
  1. 当週の Development Metrics を記録する
  2. Product KPI は Beta Release 後に記録開始する
```
