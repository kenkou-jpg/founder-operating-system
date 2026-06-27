# Founder Operating System

> One person. Multiple products. One OS.

---

## What is the Founder Operating System?

Founder Operating System (Founder OS) は、一人の創業者が複数のSaaS・アプリ・研究事業・テンプレート事業を
**同じ思想・同じ品質・同じ運営基準** で長期運営するための共通基盤です。

これはコードではありません。
これは **オペレーティングシステム** — 創業者個人の意思決定・運営・ナレッジ管理の総体です。

---

## 対象

このOSは以下のすべてのプロダクト・事業に適用されます。

| プロダクト | カテゴリ | ステータス |
|-----------|---------|-----------|
| **ippo** | ウォーキング・習慣化アプリ | Active |
| **AgriPath** | 農業キャリア・情報プラットフォーム | Planning |
| **Imaging Agriculture** | 農業×画像解析・リサーチ事業 | Research |
| **Fasting App** | 断食・食習慣管理アプリ | Concept |
| 新規SaaS（未定） | — | Future |

---

## 思想

### なぜこのOSが必要か

一人で複数事業を動かすとき、最大の敵は **判断の一貫性の欠如** と **再発明のコスト** です。

- 同じ問いに毎回ゼロから答えない
- 一つのプロダクトで学んだことを他に転用する
- ブランド・品質・倫理の基準を統一する

Founder OSはこの問題を解くための仕組みです。

### 核心思想

1. **Single Source of Truth** — 真実は一箇所に存在する
2. **Canonical over Copy** — コピーしない、参照する
3. **Long-term Compounding** — 短期の速度より長期の積み上がりを選ぶ
4. **Automation First** — 繰り返しは自動化する
5. **Quality without Compromise** — 品質は交渉の余地がない

詳細は [`FOUNDER_PHILOSOPHY.md`](FOUNDER_PHILOSOPHY.md) と [`OPERATING_PRINCIPLES.md`](OPERATING_PRINCIPLES.md) を参照。

---

## 利用方法

### 新しいプロダクトを始めるとき

1. [`portfolio-os/`](portfolio-os/) に新プロダクトのプロファイルを作成
2. [`development-os/`](development-os/) の技術標準を確認・適用
3. [`business-os/`](business-os/) の事業戦略フレームワークで計画
4. [`CANONICAL_SOURCE.md`](CANONICAL_SOURCE.md) を更新

### 重要な判断をするとき

1. [`OPERATING_PRINCIPLES.md`](OPERATING_PRINCIPLES.md) で原則に照らす
2. [`governance/DECISION_LOG.md`](governance/DECISION_LOG.md) に記録
3. 拘束力のある決定は [`governance/BINDING_DECISIONS.md`](governance/BINDING_DECISIONS.md) へ

### 各ドメインの基準を確認するとき

対応するOSディレクトリの `README.md` を参照してください。

---

## Version 管理

このOSは [`governance/CHANGELOG.md`](governance/CHANGELOG.md) でバージョン管理します。
ロードマップは [`ROADMAP.md`](ROADMAP.md) を参照。

| バージョン | 意味 |
|-----------|------|
| MAJOR | 根本思想・全体構造の変更 |
| MINOR | 新OSの追加・原則の追加・テンプレートの追加 |
| PATCH | 既存ドキュメントの修正・補足 |

**現在のバージョン: v0.1.0**

---

## OS構成

```
founder-operating-system/
│
├── README.md                    ← このファイル
├── FOUNDER_PHILOSOPHY.md        ← 創業者の根本思想
├── OPERATING_PRINCIPLES.md      ← 事業横断の運営原則
├── CANONICAL_SOURCE.md          ← 情報ヒエラルキーの定義
├── ROADMAP.md                   ← OSのバージョンロードマップ
│
├── development-os/              ← 開発・技術標準
├── business-os/                 ← 事業戦略・収益・GTM
├── brand-os/                    ← ブランド・コミュニケーション
├── legal-os/                    ← 法務・規約・コンプライアンス
├── research-os/                 ← リサーチ・市場分析
├── finance-os/                  ← 財務・コスト・投資判断
├── analytics-os/                ← 指標・KPI・データ設計
├── customer-success-os/         ← CS・サポート・オンボーディング
├── automation-os/               ← 自動化・CI/CD・Workflow
├── operations-os/               ← 日次〜年次の運営ルーティン
├── knowledge-os/                ← 学習・ナレッジキャプチャ
├── template-business-os/        ← テンプレート事業固有OS
│
├── portfolio-os/                ← プロダクトポートフォリオ管理
│   ├── IPPO.md
│   ├── AGRIPATH.md
│   ├── IMAGING_AGRICULTURE.md
│   ├── FASTING_APP.md
│   └── PORTFOLIO_KPI.md
│
├── templates/                   ← 再利用可能テンプレート
│
└── governance/                  ← 意思決定・変更管理
    ├── ADR/
    ├── DECISION_LOG.md
    ├── BINDING_DECISIONS.md
    └── CHANGELOG.md
```

---

## 将来像

**v1.0** — 全OSが充実し、新プロダクト立ち上げを72時間以内に開始できる状態

**v2.0** — AIエージェントがこのOSを読み込み、自律的に判断・実行できる状態

詳細は [`ROADMAP.md`](ROADMAP.md) を参照。

---

*Maintained by [@kenkou-jpg](https://github.com/kenkou-jpg)*
*Current Version: v0.1.0 — Foundation*
