# Analytics OS

## 目的

全プロダクト共通のKPI定義・指標設計・ダッシュボード設計の基準を管理する。
「測定しないものは改善できない」を実践するためのOS。

## 何を保存するか

- **KPI定義の標準** — 指標名・計算式・測定頻度・責任者の定義方法
- **ノーススターメトリクスの選定基準** — プロダクトタイプ別の考え方
- **ファネル分析フレームワーク** — 獲得〜定着〜収益のファネル設計
- **ダッシュボード設計原則** — 何を誰が・どの頻度で見るかの設計
- **実験（A/Bテスト）のルール** — 仮説・測定・判断の手順
- **分析クエリの標準** — Supabase SQL の再利用可能なクエリ集

## コアメトリクス（全プロダクト共通）

| カテゴリ | 指標 | 頻度 |
|---------|------|------|
| 成長 | MAU / DAU / DAU率 | 週次 |
| 収益 | MRR / ARR / ARPU | 月次 |
| 定着 | 7日/30日 Retention | 週次 |
| 健全性 | Churn Rate | 月次 |
| 満足度 | NPS (optional) | 四半期 |

## 今後の再利用計画

- 各プロダクトでSupabaseのAnalyticsスキーマをこのOSに基づいて設計
- `portfolio-os/PORTFOLIO_KPI.md` にロールアップ

## ファイル構成（今後追加予定）

```
analytics-os/
├── README.md
├── KPI_DEFINITIONS.md
├── NORTHSTAR_FRAMEWORK.md
├── FUNNEL_ANALYSIS.md
├── DASHBOARD_PRINCIPLES.md
└── queries/               # 再利用可能なSQLクエリ
```
