# REPORT_OPTIMIZATION

> Completion Report を Mode 別に最適化する。
> 長文化・重複記載・既知失敗の深掘りを排除する。
> 品質の低下ではなく、必要十分な情報密度を保つ。

---

## Purpose

- Completion Report の長さを Mode に合わせて適正化する
- 同じ内容を Report / Progress Registry / Decision Log に重複して書かない
- Pre-existing failure の長文分析を禁止する

---

## FAST_MODE Report — 最大 20 行

```
## FAST Summary

PR: PR-XXX — [タイトル]
Mode: FAST
Files:
  Created: [ファイル名 or None]
  Updated: [ファイル名]
Tests: X件追加 / 合計Y件 PASS / Build PASS
Result: COMPLETE
Progress: Current PR → PR-XXX
Decision Log: 更新不要
Next: PR-XXX — [次PRタイトル]
```

**20 行を超えない。超えた場合は削る。**

---

## STANDARD_MODE Report — 最大 50 行

```
## STANDARD Summary

PR: PR-XXX — [タイトル]
Mode Reason: [STANDARD_MODE を選択した理由、1文]
Created: [ファイル名 or None]
Updated: [ファイル名]
Event / API / DI:
  Event: [追加した Event or None]
  API: [追加した API or None]
  DI: [追加した DI Token or None]
Tests: X件追加 / 合計Y件 PASS / Build PASS
Architecture: [変更の有無と内容、1文]
BD: [適用した BD 番号 or None]
Progress: Current PR → PR-XXX
Decision Log: 更新不要 / DLOG-XXX 更新
Next: PR-XXX — [次PRタイトル]
```

**50 行を超えない。超えた場合は削る。**

---

## FULL_MODE Report — 詳細可（重複説明は禁止）

```
## FULL Summary

PR: PR-XXX — [タイトル]
Mode Reason: [FULL_MODE を選択した理由、1文]
Governing Documents: [確認した文書リスト]
Scope:
  Completed: [実装完了項目]
  Non-goals: 混入なし
Created: [ファイル名 or None]
Updated: [ファイル名]
Migration: [追加した Migration or None]
Event: [追加した Event or None]
API: [追加した API or None]
DI: [追加した DI Token or None]
Architecture: [変更の有無と内容]
BD: [適用した BD 番号] — PASS
Security / Privacy: 該当なし / [内容]
Tests: X件追加 / 合計Y件 PASS
Regression: PASS（X件）
Build: PASS
Progress Registry: Current PR → PR-XXX / Milestone: [あり or なし]
Decision Log: 更新不要 / DLOG-XXX 更新
Founder Approval: 不要 / 承認済み
Next: PR-XXX — [次PRタイトル]
```

---

## Pre-existing Failure Rule

既知の失敗テストは **1行** で報告する。長文分析・原因調査は禁止。

```
Pre-existing failures: X tests（[ファイル/モジュール名]） — unchanged, not this PR's scope
```

---

## No Duplicate Reporting

同じ内容を Completion Report / Progress Registry / Decision Log に重複して長文記載しない。

| ドキュメント | 記載する内容 |
|------------|------------|
| Completion Report | PR の作業内容・テスト結果・Mode 情報 |
| Progress Registry | 現在地（Current PR / Next PR / Completion %）のみ |
| Decision Log | 重要判断（更新条件に該当する場合のみ）|

**Progress Registry に実装詳細を書かない。Decision Log に PR 作業ログを書かない。**

---

## 関連ドキュメント

- `00_EXECUTION_DISPATCHER.md` — Mode 選択
- `TOKEN_OPTIMIZATION.md` — トークン消費の行動規範
- `09_COMPLETION_REPORT_TEMPLATE.md` — レポートテンプレート
