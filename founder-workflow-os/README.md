# Founder Workflow OS

> 「アイデアを思いついてから、設計・実装・運営・資産化・次のアプリへ展開するまで」の標準実行フレームワーク。

---

## 位置づけ

Founder Workflow OS は、Founder Operating System 全体を **横断する実行フレームワーク** です。

**Development OSの上位概念ではありません。**
**すべてのドメインOSを束ねる、Founderの行動順序の定義です。**

```
Founder Operating System
│
├── development-os/         ← 技術判断の基準
├── business-os/            ← 事業判断の基準
├── brand-os/               ← ブランドの基準
├── legal-os/               ← 法務の基準
├── research-os/            ← リサーチの基準
├── finance-os/             ← 財務の基準
├── analytics-os/           ← 指標の基準
├── customer-success-os/    ← CS の基準
├── automation-os/          ← 自動化の基準
├── template-business-os/   ← テンプレートの基準
│
└── founder-workflow-os/    ← ★ 上記すべてをいつ・どの順で使うかの実行フレームワーク
```

各ドメインOSは「何をどう判断するか」を定義します。
Founder Workflow OS は「それをいつ・どの順序で実行するか」を定義します。

---

## 目的

1. **再現性** — 新しいアプリを始めるたびに、同じ品質・同じ順序で進められる
2. **省略の防止** — 重要なフェーズを「ついうっかり」スキップしない
3. **意思決定の明確化** — Founderが判断すべきポイントを事前に定義する
4. **資産の蓄積** — 各アプリが資産として積み上がる設計を保証する
5. **ポートフォリオの健全化** — 複数アプリを一貫した基準で管理する

---

## 利用方法

### 新しいアプリを始めるとき

1. `01_FOUNDER_WORKFLOW.md` で現在のステージを確認する
2. `02_STAGE_GATE.md` でそのステージの Go/No-Go 条件を確認する
3. `03_DECISION_CHECKPOINTS.md` で次の判断ポイントを確認する
4. 現在のステージに対応するドメインOSを参照して実行する

### 週次ルーティンの設計

→ `05_FOUNDER_WEEKLY_SYSTEM.md`

### 複数アプリの全体管理

→ `06_PORTFOLIO_MANAGEMENT.md`

### 資産の棚卸し

→ `07_ASSET_ACCUMULATION_SYSTEM.md`

---

## 標準フロー（全体）

```
[Discovery]
Idea → Problem Discovery → Business Strategy → Growth Strategy → Regulatory Review

[Design]
Go-To-Market → Vision → 10-Year Design → 5-Year Quality → Domain Design → Architecture

[Build]
Roadmap → APP STARTER OS → PR Development

[Launch]
Release → Analytics → User Feedback → Improvement

[Asset]
Brand Asset → Research Asset → Template Asset

[Scale]
Portfolio → Next App
```

詳細は `01_FOUNDER_WORKFLOW.md` を参照。

---

## 他OSとの関係

| ステージ | 参照するOS |
|---------|----------|
| Problem Discovery | `research-os/` |
| Business Strategy | `business-os/` |
| Regulatory Review | `legal-os/` |
| Go-To-Market | `business-os/` + `brand-os/` |
| Domain Design / Architecture | `development-os/` |
| PR Development | `development-os/pr-generator-os/` |
| Release | `automation-os/` + `legal-os/` |
| Analytics | `analytics-os/` |
| User Feedback | `customer-success-os/` |
| Brand Asset | `brand-os/` |
| Research Asset | `research-os/` |
| Template Asset | `template-business-os/` |
| Portfolio | `portfolio-os/` + `finance-os/` |
| Finance全般 | `finance-os/` |
| 週次運営 | `operations-os/` |
| ナレッジ蓄積 | `knowledge-os/` |

---

## ファイル構成

```
founder-workflow-os/
├── README.md                    ← このファイル
├── 01_FOUNDER_WORKFLOW.md       ← 23ステージの標準フロー定義
├── 02_STAGE_GATE.md             ← Go/No-Go 条件
├── 03_DECISION_CHECKPOINTS.md   ← Founder判断ポイント
├── 04_APP_LIFECYCLE.md          ← アプリのライフサイクル定義
├── 05_FOUNDER_WEEKLY_SYSTEM.md  ← 週間ルーティン設計
├── 06_PORTFOLIO_MANAGEMENT.md   ← 複数アプリ管理の基準
├── 07_ASSET_ACCUMULATION_SYSTEM.md ← 資産蓄積の体系
└── examples/
    ├── IPPO_WORKFLOW.md         ← IPPO での Workflow 適用例
    └── GENERIC_APP_WORKFLOW.md  ← 汎用SaaSでの適用例
```

---

## Version

**現在: v0.1 — Foundation**

変更は `governance/CHANGELOG.md` に記録します。
