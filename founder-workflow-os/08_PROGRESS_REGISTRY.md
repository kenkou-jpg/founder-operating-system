# 08 — Progress Registry

> Founder Operating System と各アプリの現在地を一元管理する。
> この文書は「状態管理」のための文書であり、設計変更を行う文書ではありません。

---

## Purpose

Progress Registry は以下の目的のために存在します。

1. **現在地管理** — 今どのステージ・どのPRにいるかを常に明確にする
2. **PR進捗管理** — 完了・進行中・次のPRを記録する
3. **Stage管理** — Founder Workflow OS の23ステージ上のどこにいるかを記録する
4. **Founder OS進捗管理** — Founder Operating System 自体の開発状況を記録する
5. **Portfolio管理** — 全アプリの状態を横断的に把握する
6. **迷子防止** — 長期開発・複数プロジェクト並走時に「どこまでやったか」を失わない

---

## Scope

Progress Registry が扱う対象:

- **Founder Operating System** — OS自体の進捗
- **IPPO** — ウォーキング習慣化アプリ
- **AgriPath** — 農業向けSaaS
- **Imaging Agriculture** — 農業×画像解析（研究フェーズ）
- **Fasting App** — ファスティング習慣化アプリ（概念フェーズ）
- **Future Apps** — 将来立ち上げる予定のアプリ

---

## Non-goals

Progress Registry は以下を行いません。

- ❌ Product Strategy を変更しない
- ❌ Architecture を変更しない
- ❌ Roadmap を変更しない
- ❌ PR Scope を変更しない
- ❌ Binding Decision を変更しない
- ❌ IPPO の設計判断を上書きしない
- ❌ Governing Documents の代替にはならない

**これは記録文書です。設計・判断文書ではありません。**

---

## Progress Snapshot Template

新規プロジェクトまたは状態更新時は以下のテンプレートを使用してください。

```
Project:
Current Stage:        # S01〜S23（01_FOUNDER_WORKFLOW.md 参照）
Current Phase:        # Discovery / Design / Build / Launch / Asset / Scale
Current PR:           # PR-XXX
Previous PR:          # PR-XXX（完了済み）
Next PR:              # PR-XXX（予定）
Completion:           # X / Y PRs completed in current Wave/Phase
Status:               # Active / On Hold / Ready to Resume / Blocked
Last Updated:         # YYYY-MM-DD
Blocking Issues:      # なし or 内容
Next Action:          # 次にすべき具体的なアクション
```

---

## IPPO — Current Snapshot

*最終更新: 2026-06-28*

```
Project: IPPO
Current Stage: S14 PR Development
Current Phase: Build
Lifecycle: MVP
Wave: Wave2
Phase: Phase A Infrastructure Migration

Completed PRs:
  - PR-041: NetworkSignal Repository V2 — Interface / Adapter / Factory / Persistence / Migration
  - PR-042: Supabase Persistence Foundation — NetworkSignal + EventStore
  - PR-043: Emotion Signal Generation Foundation — Rule Engine + initializeSession

Current PR: PR-044 (planning)
Next PR: PR-045

Status: Ready to resume IPPO development

Blocking Issues: なし

Founder OS Support:
  - PR Generator OS: completed (v0.2)
  - Founder Workflow OS: completed (v0.1)
  - Progress Registry: created (v0.3)
  - Decision Log: created (v0.3)

Next Action: PR-044 の Input Sheet を完成させ、Validation 4種を実行して実装開始
```

---

## Founder Operating System — Current Snapshot

*最終更新: 2026-06-28*

```
Founder Operating System

Version: v0.3

Completed:
  - Foundation (v0.1)
    - README.md / FOUNDER_PHILOSOPHY.md / OPERATING_PRINCIPLES.md
    - CANONICAL_SOURCE.md / ROADMAP.md
    - 12 Domain OS READMEs
    - Portfolio OS
    - Templates / Governance

  - PR Generator OS (v0.2)
    - 14ファイル (01〜14) + 2 examples
    - 責務衝突防止の Validation 4種

  - Founder Workflow OS (v0.1)
    - README / 01〜07 / examples (IPPO / Generic)

  - Progress Registry (v0.3)       ← NOW
  - Decision Log (v0.3)            ← NOW

Now: v0.3 — Progress Registry / Decision Log

Later (after IPPO PR-044〜075):
  - Workflow Automation
  - Council Generator OS
  - Architecture Generator OS
```

---

## Portfolio Table

*月次更新。最終更新: 2026-06-28*

| Project | Status | Stage | Lifecycle | Current Focus | Next Action | Repository | Notes |
|---------|--------|-------|-----------|--------------|-------------|-----------|-------|
| IPPO | 開発中 | S14 PR Dev | MVP | Wave2 PR-044 | PR-044 実装開始 | kenkou-jpg/ippo | Wave2 Phase A |
| AgriPath | 計画中 | S01 Idea | Idea | 概念段階 | IPPO安定後に着手 | — | 農業×SaaS |
| Imaging Agriculture | 研究中 | S02 Problem Discovery | Research | リサーチ | 研究継続 | — | 学術・研究フェーズ |
| Fasting App | 概念 | S01 Idea | Idea | 概念段階 | IPPO安定後に着手 | — | ヘルスケア |
| Founder Operating System | 開発中 | — | — | v0.3 Progress Registry / Decision Log | IPPO PR-044完了後に再開 | kenkou-jpg/founder-operating-system | Markdown only |

---

## Update Rule

Progress Registry は以下のタイミングで更新してください。

| トリガー | 更新内容 |
|---------|---------|
| **PR完了時** | Completed PRs に追加、Current PR / Next PR を更新 |
| **Council完了時** | 関連するプロジェクトの Status・Next Action を更新 |
| **Stage変更時** | Current Stage / Current Phase を更新 |
| **Founder判断時** | Status / Blocking Issues / Next Action を更新 |
| **次アプリ開始時** | Portfolio Table に新プロジェクトを追加 |

**更新は追記・上書きのいずれでも可。ただし Portfolio Table は現在値で管理すること。**

---

## 関連ドキュメント

- `01_FOUNDER_WORKFLOW.md` — Stage 定義
- `06_PORTFOLIO_MANAGEMENT.md` — Portfolio 状態定義
- `09_DECISION_LOG.md` — Founder 判断の履歴
- `development-os/pr-generator-os/11_PR_RESPONSIBILITY_REGISTRY.md` — PR 完了記録
