# 08 — Progress Registry

> Founder Operating System と各アプリの現在地を一元管理する。
> この文書は「現在地」を一目で分かるようにするための文書であり、開発履歴を書く文書ではありません。

---

## Purpose

Progress Registry は **「Founder が今どこにいるか」** を常に明確にするために存在します。

1. **現在地管理** — 今どのステージ・どのPRにいるかを一目で把握する
2. **マイルストーン管理** — Phase / Wave 完了などの重要節目だけを記録する
3. **迷子防止** — 70PR を超える長期開発でも現在地を失わない
4. **Portfolio管理** — 全アプリの状態を横断的に把握する

---

## Architecture（2層構造）

```
Progress Registry
│
├── Live Progress      ← 常に最新状態のみ。履歴を残さない。
└── Milestone History  ← Phase / Wave / Release 完了時のみ追記。PR単位では追加しない。
```

---

## Scope

- **Founder Operating System** — OS自体の進捗
- **IPPO** — ウォーキング習慣化アプリ
- **AgriPath** — 農業向けSaaS
- **Imaging Agriculture** — 農業×画像解析（研究フェーズ）
- **Fasting App** — ファスティング習慣化アプリ（概念フェーズ）
- **Future Apps** — 将来立ち上げる予定のアプリ

---

## Non-goals

- ❌ Product Strategy を変更しない
- ❌ Architecture を変更しない
- ❌ Roadmap を変更しない
- ❌ PR Scope を変更しない
- ❌ Binding Decision を変更しない
- ❌ IPPO の設計判断を上書きしない
- ❌ 開発履歴・PR一覧を蓄積しない（それは `11_PR_RESPONSIBILITY_REGISTRY.md` の責務）

---

## 責務分離

| ドキュメント | 責務 |
|------------|------|
| **Progress Registry（このファイル）** | 現在地 |
| `09_DECISION_LOG.md` | Founder 判断 |
| `docs/ARCHITECTURE.md`（各リポジトリ）| 設計 |
| `docs/ROADMAP.md`（各リポジトリ）| 順序 |
| `governance/BINDING_DECISIONS.md` | 仕様・拘束力のある決定 |
| `development-os/pr-generator-os/11_PR_RESPONSIBILITY_REGISTRY.md` | PR完了履歴 |

---

## ① Live Progress

> 常に最新状態だけを保持する。過去の内容は上書きする。履歴は残さない。

### Live Progress Template

```
Project:
Current Stage:          # S01〜S23（01_FOUNDER_WORKFLOW.md 参照）
Current Phase:          # Discovery / Design / Build / Launch / Asset / Scale
Current PR:             # PR-XXX
Next PR:                # PR-XXX（予定）
Completion %:           # Wave / Phase の完了率（例: 3/5 PRs = 60%）
Execution Mode Used:    # FAST_MODE / STANDARD_MODE / FULL_MODE（直近 PR で使用したモード）
Status:                 # Active / On Hold / Blocked
Last Updated:           # YYYY-MM-DD
```

### IPPO — Live Progress

*最終更新: 2026-06-28*

```
Project: IPPO
Current Stage: S14 PR Development
Current Phase: Build
Wave: Wave2 / Phase A Infrastructure Migration
Current PR: PR-044
Next PR: PR-045
Completion %: 3 / ~35 PRs (Wave2) ≈ 9%
Execution Mode Used: （PR-044 実装時に記入）
Status: Active
Last Updated: 2026-06-28
```

### Founder Operating System — Live Progress

*最終更新: 2026-06-28*

```
Project: Founder Operating System
Current Stage: —
Current Phase: —
Version: v0.3
Current Focus: Progress Registry v1.1 更新
Next: IPPO PR-044〜075 完了後に再開
Status: Active（IPPO 開発中は最小限の更新）
Last Updated: 2026-06-28
```

---

## ② Milestone History

> Phase / Wave / Release 完了など、重要節目のみ追記する。PR 単位では追加しない。

### Milestone History Template（追記用）

```
### [YYYY-MM-DD] [Project] — [Milestone Name]

- Milestone: Phase Complete / Wave Complete / Beta Release / Official Release / Major Council
- Scope: PR-XXX 〜 PR-XXX
- Notes: （任意）
```

### IPPO — Milestone History

*Wave2 開始前の状態。Wave2 Phase A 完了時に最初のエントリを追記する。*

```
（Wave2 Phase A 完了時に追記予定）
```

---

## Portfolio Table

*月次更新。Current Focus / Current Stage / Current PR のみ更新する。最終更新: 2026-06-28*

| Project | Status | Stage | Lifecycle | Current PR | Next Action | Repository | Notes |
|---------|--------|-------|-----------|-----------|-------------|-----------|-------|
| IPPO | 開発中 | S14 PR Dev | MVP | PR-044 | PR-044 実装開始 | kenkou-jpg/ippo | Wave2 Phase A |
| AgriPath | 計画中 | S01 Idea | Idea | — | IPPO 安定後に着手 | — | 農業×SaaS |
| Imaging Agriculture | 研究中 | S02 Problem Discovery | Research | — | 研究継続 | — | 学術・研究フェーズ |
| Fasting App | 概念 | S01 Idea | Idea | — | IPPO 安定後に着手 | — | ヘルスケア |
| Founder Operating System | 開発中 | — | — | — | IPPO PR-044 完了後に再開 | kenkou-jpg/founder-operating-system | Markdown only |

---

## Update Rule

### Live Progress — 更新タイミングと内容

| トリガー | 更新フィールド |
|---------|-------------|
| PR 完了時 | `Current PR` → `Next PR` へ進める、`Completion %` を更新、`Last Updated` を更新 |
| Current PR 変更時 | `Current PR` / `Next PR` を更新 |
| Stage 変更時 | `Current Stage` / `Current Phase` を更新 |
| Phase 変更時 | `Current Phase` / `Wave` を更新 |

**Live Progress に過去 PR の一覧を書かない。それは `11_PR_RESPONSIBILITY_REGISTRY.md` へ。**

### Milestone History — 更新タイミング

以下のいずれかの場合のみ追記する。PR 単位では追加しない。

```
□ Phase Complete
□ Wave Complete
□ Major Council Complete
□ Beta Release
□ Official Release
□ Lifecycle Change（MVP → PMF など）
```

### Portfolio Table — 更新タイミング

```
□ Current PR が変わったとき
□ Stage が変わったとき
□ 新しいアプリが追加されたとき
□ Status が変わったとき（開発中 → 運営中 など）
```

---

## Claude Code 運用ルール

PR 完了後、Claude Code は以下の順序で自動判断すること。

### Step 1 — Live Progress の更新

```
PR 完了 → Live Progress を更新する
  Current PR: 完了した PR → 次の PR へ
  Completion % を更新
  Last Updated を更新
```

### Step 2 — Milestone History の判断

```
Phase が完了した？
  Yes → Milestone History に追記する
  No  → 更新しない（「Milestone History 更新不要」と判断）
```

### Step 3 — Decision Log の判断

```
以下のいずれかに該当するか？
  □ Roadmap 変更
  □ Architecture 変更
  □ Governing Document 変更
  □ Business / Founder Strategy 変更
  □ 新しい OS 追加
  □ 新しいテンプレート追加
  □ Binding Decision 候補

  Yes → Decision Log を更新する
  No  → 「Decision Log 更新不要」と判断し、更新しない
```

---

## IPPO 適用例

| タイミング | Live Progress | Milestone History | Decision Log |
|-----------|-------------|-----------------|-------------|
| PR-044 完了 | Current PR → PR-045 へ更新 | 更新しない | 更新不要 |
| PR-045 完了 | Current PR → PR-046 へ更新 | 更新しない | 更新不要 |
| PR-046〜050 完了（Phase B Complete）| Current PR 更新 | Phase B Complete を追記 | 更新不要 |
| PR-075 完了（Wave2 Complete）| Current PR 更新、Completion 100% | Wave2 Complete を追記 | Wave2 完了の判断があれば記録 |

---

## 関連ドキュメント

- `01_FOUNDER_WORKFLOW.md` — Stage 定義
- `06_PORTFOLIO_MANAGEMENT.md` — Portfolio 状態定義
- `09_DECISION_LOG.md` — Founder 判断の履歴
- `development-os/pr-generator-os/11_PR_RESPONSIBILITY_REGISTRY.md` — PR 完了履歴（Append-Only）
