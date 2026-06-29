# 00 — Execution Mode Dispatcher

> PR Generator OS のエントリポイント。
> Claude Code は PR 開始時に必ずこのファイルを最初に読み、実行モードを決定する。
> モード選択は AI の独自判断ではなく、このファイルに定義された OS ルールに基づく。

---

## Purpose

Execution Dispatcher は以下の目的のために存在します。

1. **Claude Code の消費量削減** — PR の種類に応じて必要十分なチェック量を選ぶ
2. **安全性の維持** — 消費量削減は安全性の低下ではなく、適正化である
3. **OS ルールによるモード選択** — AI の独自判断ではなく、ルールベースで決定する
4. **Founder が毎回モード指定しなくても済む状態** — PR 情報から自動判断する

---

## Available Modes

| Mode | 用途 | 詳細 |
|------|------|------|
| `FAST_MODE` | 通常 PR（既存設計内・変更なし）| `FAST_MODE.md` |
| `STANDARD_MODE` | 重要度中（新 Domain / Service / Event など）| `STANDARD_MODE.md` |
| `FULL_MODE` | 重要度高（Architecture / Migration / Release など）| `FULL_MODE.md` |

---

## Inputs（判断に使う情報）

Dispatcher は以下の情報を参照してモードを選択する。

```
□ PR Number
□ PR Title
□ PR Type（03_PR_TYPE_MATRIX.md 参照）
□ Current Phase / Wave
□ Roadmap 上の位置（Phase 中盤 / 終了 PR か）
□ 11_PR_RESPONSIBILITY_REGISTRY.md（責務重複チェック）
□ Governing Documents の変更有無
□ Architecture 変更の有無
□ DB / Migration 変更の有無
□ Business / Legal / Regulatory 変更の有無
□ Phase / Wave 終了 PR かどうか
□ AI / Research / Release に関わる変更かどうか
□ Security / Privacy / Consent 変更の有無
```

---

## Mode Selection Rules

### FULL_MODE を使う条件

以下のいずれかに該当する場合、FULL_MODE を選択する。

```
□ Architecture 変更（レイヤー構造・依存関係の再定義）
□ Roadmap 変更
□ Governing Document 変更
□ Binding Decision 追加 / 変更
□ DB Migration 追加
□ Supabase Schema 変更
□ Security / Privacy / Consent 変更
□ AI / LLM / Medical Safety 変更
□ Research Dataset 公開・Export・License に関わる変更
□ Release Candidate
□ Beta Release
□ Official Release
□ Phase 終了 PR
□ Wave 終了 PR
□ Legacy 削除
□ 重大なリファクタリング（複数ドメイン横断）
□ Founder 判断が必要な変更
```

### STANDARD_MODE を使う条件

FULL_MODE の条件に該当せず、以下のいずれかに該当する場合、STANDARD_MODE を選択する。

```
□ 新 Domain 追加
□ 新 Service 追加
□ 新 Repository 追加
□ 新 Event 追加
□ ApiGateway 追加
□ DI 構成追加
□ Architecture Guard 追加
□ Feature Registry / Route Registry 追加
□ 既存 Domain の構造拡張（メソッド追加・依存追加）
□ 複数ファイル横断変更（3ファイル超）
□ Phase 中盤の重要 PR
```

### FAST_MODE を使う条件

FULL_MODE・STANDARD_MODE のいずれにも該当しない通常 PR。

```
✅ Roadmap 通りの実装
✅ Architecture 変更なし
✅ DB Migration なし
✅ Business / Legal / Governing Document 変更なし
✅ 既存設計内の Domain / Service 実装
✅ 軽微な Feature Registry / Route Registry 更新
✅ 通常のテスト追加
✅ Decision Log 更新条件に該当しない
```

---

## Default Rule

```
判断に迷う場合 → STANDARD_MODE

ただし以下が関係する場合は必ず FULL_MODE:
  Security / Privacy / Consent / AI / Research / Release
```

**安全側に倒す。FAST_MODE への格下げは明確な根拠がある場合のみ。**

---

## Output Format

Claude Code は PR 開始時に必ず以下を出力してから実装に入ること。

```
## Execution Mode Decision

PR: PR-XXX — [PR Title]
Mode: FAST_MODE / STANDARD_MODE / FULL_MODE
Reason: （モード選択の根拠を1〜2文で）
Required Checks:
  - [実行するチェック一覧]
Skipped Checks:
  - [省略するチェック一覧]（FAST/STANDARD のみ）
Escalation Required: yes / no
```

---

## Execution Metadata（Mode 決定後に必ず生成）

Mode 選択後、Claude Code は必ず以下の **Execution Metadata** を生成する。
この Metadata を Completion Report と Progress Registry へそのまま引き継ぐ。

```
## Execution Metadata

Mode:               FAST / STANDARD / FULL
Reason:             （1文：モード選択の根拠）
Dispatcher Version: v0.4
Escalation:         NO / YES
  Previous Mode:    （Escalation YES の場合のみ）FAST / STANDARD
  Current Mode:     （Escalation YES の場合のみ）STANDARD / FULL
  Escalation Reason:（Escalation YES の場合のみ：理由）
Generated At:       YYYY-MM-DD
```

### Escalation が発生した場合の記録例

```
## Execution Metadata

Mode:               STANDARD
Reason:             Repository Migration Required — escalated from FAST
Dispatcher Version: v0.4
Escalation:         YES
  Previous Mode:    FAST
  Current Mode:     STANDARD
  Escalation Reason: 実装中に新 Repository が必要であることが判明した
Generated At:       2026-06-29
```

### Execution Metadata の引き継ぎ先

| 引き継ぎ先 | 対応フィールド |
|-----------|-------------|
| `09_COMPLETION_REPORT_TEMPLATE.md` の `Execution Mode` セクション | Mode / Reason / Dispatcher Version / Escalation / Skipped Checks |
| `08_PROGRESS_REGISTRY.md` の Live Progress | Execution Mode Used / Dispatcher Version / Escalation |

---

## Escalation Rule

実装中に以下が判明した場合、途中で上位モードに切り替える。

```
FAST → STANDARD:
  □ 想定外の新 Repository / Service が必要になった
  □ 複数ファイル横断変更が必要になった
  □ 軽微と思っていたが構造変更が伴うことが判明した

STANDARD → FULL:
  □ 想定外の Architecture 変更が必要になった
  □ Repository / Migration が必要になった
  □ BD 違反リスクが出た
  □ Security / Privacy / Consent に触れることが判明した
  □ Scope 外実装が必要になった
  □ Pre-existing failure ではない新規失敗が発生した
  □ Founder 判断が必要になった
```

**Escalation 発生時は必ず Founder に通知し、新モードで継続する。**

---

## Quick Reference — Execution Flow

```
PR 開始
  ↓
00_EXECUTION_DISPATCHER.md を読む（このファイル）
  ↓
Mode Selection Rules を確認
  ↓
┌─────────────────────────────────────────┐
│ FULL_MODE が該当する条件に1つでも一致？  │
│   Yes → FULL_MODE                       │
│   No  ↓                                 │
│ STANDARD_MODE が該当する条件に1つでも一致？│
│   Yes → STANDARD_MODE                   │
│   No  → FAST_MODE                       │
└─────────────────────────────────────────┘
  ↓
Execution Mode Decision を出力
  ↓
Execution Metadata を生成（必須）
  ↓
対応する MODE.md を読んで実装開始
  ↓
（Escalation 発生時は Metadata を更新して上位 MODE.md へ）
  ↓
Completion Report に Execution Metadata を転記
  ↓
Progress Registry Live Progress に Execution Metadata を転記
```

---

## 関連ドキュメント

- `FAST_MODE.md` — Fast Mode の必須チェックと出力形式
- `STANDARD_MODE.md` — Standard Mode の必須チェックと出力形式
- `FULL_MODE.md` — Full Mode の必須チェックと出力形式
- `02_PR_INPUT_SHEET.md` — Input Sheet（Execution Mode フィールド追加済み）
- `08_DEFINITION_OF_DONE.md` — 完了条件（Mode 別要件追加済み）
- `founder-workflow-os/08_PROGRESS_REGISTRY.md` — Live Progress 更新
