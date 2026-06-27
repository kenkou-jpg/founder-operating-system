# Founder Operating System

> 一人創業者が、複数の事業を同じ思想・同じ品質・同じ運営基準で長期運営するための共通OS。

## What is this?

このリポジトリは **Founder OS** — 創業者個人が持つ意思決定基準・運営ルール・再利用可能なテンプレートを一元管理するシステムです。

コードではなく、**思想・判断基準・手順書・テンプレート** の集合体です。
各プロジェクトリポジトリ（ippo / agripath / fasting-app 等）はこのOSの「実装例」であり、
OSそのものはここに集約されます。

## Core Philosophy

- **One founder, multiple products** — 同じ一人の人間が複数事業を動かす前提で設計
- **Canonical Source** — 真実は一箇所に存在する。コピーしない、参照する
- **Async-first** — ミーティング・口頭説明に依存しない文書中心の運営
- **Long-term compounding** — 短期の速度より、長期で積み上がる基盤を優先

## Repository Structure

```
founder-operating-system/
│
├── README.md                    # このファイル
├── FOUNDER_PHILOSOPHY.md        # 創業者としての根本思想
├── CANONICAL_SOURCE.md          # 真実の在り処マップ
├── OPERATING_PRINCIPLES.md      # 事業横断の運営原則
│
├── development-os/              # 開発標準・技術方針
├── business-os/                 # 事業戦略・GTM・収益モデル
├── brand-os/                    # ブランド・コミュニケーション基準
├── legal-os/                    # 法務・利用規約・契約ひな形
├── research-os/                 # リサーチ・競合分析・インサイト管理
├── finance-os/                  # 財務・コスト管理・投資判断
├── analytics-os/                # 指標定義・ダッシュボード・KPI管理
├── customer-success-os/         # CS・サポート・オンボーディング
├── automation-os/               # 自動化・CI/CD・Workflow設計
├── template-business-os/        # テンプレート事業の固有OS
├── operations-os/               # 日次・週次・月次の運営ルーティン
├── knowledge-os/                # 学習・ナレッジキャプチャ・メモ管理
│
├── portfolio-os/                # ポートフォリオ全体の管理
│   ├── IPPO.md
│   ├── AGRIPATH.md
│   ├── FASTING_APP.md
│   └── PORTFOLIO_KPI.md
│
├── templates/                   # 再利用可能テンプレート群
│   ├── APP_STARTER_TEMPLATE/
│   ├── COUNCIL_TEMPLATE/
│   ├── PR_TEMPLATE.md
│   ├── ARCHITECTURE_TEMPLATE.md
│   └── BUSINESS_STRATEGY_TEMPLATE.md
│
└── governance/                  # 意思決定の記録・変更ログ
    ├── ADR/
    ├── DECISION_LOG.md
    ├── BINDING_DECISIONS.md
    └── CHANGELOG.md
```

## How to Use

1. **新しい事業を始めるとき** → `templates/APP_STARTER_TEMPLATE/` から複製
2. **技術方針を決めるとき** → `development-os/` を参照し、ADRを書く
3. **ブランドに関わる判断** → `brand-os/` を参照
4. **ポートフォリオ全体を見直すとき** → `portfolio-os/PORTFOLIO_KPI.md`
5. **重要な意思決定をしたとき** → `governance/DECISION_LOG.md` に記録

## Versioning

このOSは `governance/CHANGELOG.md` でバージョン管理します。
破壊的変更（原則の変更・構造の再編）はメジャーバージョンを上げます。

## Portfolio

| プロダクト | リポジトリ | ステータス |
|-----------|-----------|-----------|
| ippo | [ippo](https://github.com/kenkou-jpg/ippo) | Active |
| AgriPath | TBD | Planning |
| Fasting App | TBD | Concept |

---

*This OS is maintained by [@kenkou-jpg](https://github.com/kenkou-jpg)*
