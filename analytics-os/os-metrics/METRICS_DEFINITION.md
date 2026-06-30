# METRICS_DEFINITION

> Analytics OS で使用するすべての KPI を定義する。
> この定義に基づいて OS_SCORECARD / OS_USAGE_MATRIX / OS_BALANCE_SCORE / FOUNDER_EFFICIENCY を更新する。

---

## 1. Completion Rate（完成率）

| 項目 | 定義 |
|-----|------|
| 対象 | 各 Domain OS・Workflow OS・PR Generator OS |
| 計算 | 実装済みファイル数 ÷ 計画ファイル数 × 100 |
| 単位 | % |
| 更新タイミング | OS にファイルが追加・完成したとき |
| 注意 | Markdown ファイルの完成度で判断（実装コードは対象外）|

---

## 2. Usage Count（週次利用回数）

| 項目 | 定義 |
|-----|------|
| 対象 | 各 Domain OS |
| 計算 | 1週間で Claude Code がその OS を参照した回数 |
| 単位 | 回 / 週 |
| 更新タイミング | 週次レビュー時 |
| カウント例 | PR Generator OS を PR-044 で使用 → +1 |

---

## 3. Usage %（OS 使用率）

| 項目 | 定義 |
|-----|------|
| 計算 | 当該 OS の Usage Count ÷ 全 OS の Usage Count 合計 × 100 |
| 単位 | % |
| 目的 | どの OS に偏っているかを可視化 |

---

## 4. Balance Score（使用バランス）

| 項目 | 定義 |
|-----|------|
| 計算 | 1回以上使用された OS 数 ÷ 対象 OS 総数 × 100 |
| 単位 | % |
| 目標 | ≥ 50%（Wave2 開発期）|
| 警告閾値 | < 30%（特定 OS への過度な集中を示す）|
| 注意 | Wave2 開発期は Development OS 中心のため低くなりやすい |

---

## 5. PR Success Rate（PR 成功率）

| 項目 | 定義 |
|-----|------|
| 計算 | Definition of Done を全項目クリアした PR 数 ÷ 完了 PR 総数 × 100 |
| 単位 | % |
| 目標 | 100%（Scope Creep・Architecture 違反なし）|
| 更新タイミング | PR 完了時 |

---

## 6. Scope Creep Count（Scope 逸脱件数）

| 項目 | 定義 |
|-----|------|
| 計算 | 当初 Non-goals に記載していたのに実装した件数（累積）|
| 単位 | 件 |
| 目標 | 0 |
| 記録先 | WEEKLY_REVIEW_TEMPLATE.md の Problems 欄 |

---

## 7. Architecture Violation Count（Architecture 違反件数）

| 項目 | 定義 |
|-----|------|
| 計算 | Architecture Checklist で違反が検出された件数（累積）|
| 単位 | 件 |
| 目標 | 0 |
| 記録先 | WEEKLY_REVIEW_TEMPLATE.md の Problems 欄 |

---

## 8. Template Reuse Count（テンプレート再利用回数）

| 項目 | 定義 |
|-----|------|
| 計算 | `templates/` または `pr-generator-os/` のテンプレートを使用した回数 |
| 単位 | 回 / 週 |
| 目標 | ≥ 3 回 / 週（開発が活発な週）|
| 目的 | テンプレート資産の活用度を可視化 |

---

## 9. Founder Efficiency（Founder 効率）

| 項目 | 定義 |
|-----|------|
| 計算 | 1週間で増加した Founder Asset の種類数 |
| 単位 | 種類数 / 週 |
| 目標 | ≥ 3 種類 / 週 |
| 詳細 | FOUNDER_EFFICIENCY.md 参照 |

---

## 10. Asset Accumulation Score（累積資産スコア）

| 項目 | 定義 |
|-----|------|
| 計算 | 各 Asset カテゴリの累積数の合計 |
| 単位 | 件（累積）|
| 目的 | 資産の積み上がりを可視化 |
| 更新タイミング | 週次レビュー時 |
