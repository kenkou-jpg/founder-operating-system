# Analytics OS

## 目的

全プロダクト共通のKPI定義・指標設計・ダッシュボード設計の基準を管理する。
「測定しないものは改善できない」を実践するためのOS。

**このOSが答える問い:**
- 何を測定するか（しないか）
- KPIをどう定義し、どこに記録するか
- データをどう収集・保存・分析するか
- ダッシュボードをどう設計するか

---

## 責務

| 責務 | 内容 |
|------|------|
| KPI定義の標準 | 指標名・計算式・測定頻度の定義方法 |
| ノーススターメトリクスの選定基準 | プロダクトタイプ別のNSM選定の考え方 |
| ファネル分析フレームワーク | 獲得〜定着〜収益のファネル設計 |
| ダッシュボード設計原則 | 何を誰が・どの頻度で見るかの設計 |
| 実験（A/Bテスト）ルール | 仮説・測定・判断の手順 |
| データ収集の設計基準 | イベント設計・スキーマ・命名規則 |
| 分析クエリの標準 | 再利用可能なSQLクエリの管理 |

---

## コアメトリクス（全プロダクト共通）

| カテゴリ | 指標 | 測定頻度 |
|---------|------|---------|
| 成長 | MAU / DAU / DAU率 | 週次 |
| 収益 | MRR / ARR / ARPU | 月次 |
| 定着 | 7日・30日 Retention | 週次 |
| 健全性 | Churn Rate | 月次 |
| 品質 | Crash Rate / Error Rate | 日次 |

---

## os-metrics — Founder OS 自己分析（v1.0/v1.1 追加済み）

Founder Operating System 自体の成熟度・使用率・Founder Efficiency を定量管理するサブシステム。

```
analytics-os/os-metrics/
├── CURRENT_STATE.md            ← 最初に読む（Snapshot First）
├── CONTEXT_LOADER.md           ← 読むファイルをイベント別に決定
├── README.md
├── METRICS_DEFINITION.md       ← 10 KPI 定義
├── OS_SCORECARD.md             ← OS 別 Completion Rate
├── OS_USAGE_MATRIX.md          ← 週次 OS 利用回数
├── OS_BALANCE_SCORE.md         ← 利用バランス分析
├── FOUNDER_EFFICIENCY.md       ← Founder Asset 増加管理
├── WEEKLY_REVIEW_TEMPLATE.md   ← 週次レビュー記入フォーム
└── WEEKLY_REVIEW_WORKFLOW.md   ← Claude Code 実行フロー
```

**週次レビュープロンプト:**
```
Founder Operating System の週次レビューを実施してください。
Analytics OS に従ってください。
Founder Operating System のみ更新してください。
```

---

## 将来追加予定（プロダクト Analytics）

- `KPI_DEFINITIONS.md` — 全指標の定義辞書（計算式・集計期間・除外条件）
- `NORTHSTAR_FRAMEWORK.md` — プロダクトタイプ別NSMの選定ガイド
- `FUNNEL_ANALYSIS.md` — 獲得〜収益ファネルの設計手順
- `DASHBOARD_PRINCIPLES.md` — ダッシュボード設計の原則
- `EXPERIMENT_FRAMEWORK.md` — A/Bテストの設計・判定手順
- `queries/` — Supabase SQL 再利用クエリ集

---

## 他OSとの関係

| OS | 関係 |
|----|------|
| `business-os/` | KPIは事業判断の根拠として使用する |
| `finance-os/` | MRR・ARR・コスト系KPIはfinance-osの数値と整合 |
| `development-os/` | データ収集の実装基準はdevelopment-osのセキュリティ基準に従う |
| `legal-os/` | データ収集範囲はlegal-osのプライバシー方針に従う |
| `portfolio-os/` | ポートフォリオKPIはPORTFOLIO_KPI.mdへロールアップ |
| `operations-os/` | KPIレビューはoperations-osのルーティンに組み込む |
