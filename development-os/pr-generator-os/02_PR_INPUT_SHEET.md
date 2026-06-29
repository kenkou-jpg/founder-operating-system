# 02 — PR Input Sheet

> PRプロンプト生成前に埋める入力シート。
> このシートを完成させてから `01_PR_PROMPT_TEMPLATE.md` に流し込む。
> Validation（11〜14）はこのシートが完成してから実行する。

---

## Execution Mode

> `00_EXECUTION_DISPATCHER.md` のルールに基づいて選択する。

```yaml
Execution Mode: ""
  # FAST_MODE / STANDARD_MODE / FULL_MODE

Mode Reason: ""
  # モード選択の根拠（1文）
  # 例: "新 Repository 追加のため STANDARD_MODE"
  # 例: "Architecture 変更なし・Migration なし → FAST_MODE"

Escalation Required: NO
  # YES / NO
  # 実装中にモードを切り替えた場合は YES に変更し、理由を記載
```

---

## Project Information

```yaml
Project Name: ""
  # 例: IPPO / AgriPath / Fasting App / Imaging Agriculture

PR Number: ""
  # 例: 044

PR Title: ""
  # 例: MenstrualPhase Auto-Resolution

Wave / Phase: ""
  # 例: Wave 2 / Phase 8 / Sprint 3

Domain: ""
  # 例: emotion-signal / user-profile / crop-analysis
```

---

## PR Chain

```yaml
Completed PRs: ""
  # 例: PR-041, PR-042, PR-043

Previous PR:
  Number: ""
  Title: ""
  # 例: PR-043 — Emotion Signal Generation Foundation

This PR:
  Number: ""
  Title: ""

Next PR:
  Number: ""
  Title: ""
  # 例: PR-045 — Emotion Signal UI Integration
```

---

## Governing Documents

> 実装前にAIに読ませる上位文書をすべてリストする。

```yaml
Governing Documents:
  - ""  # 例: docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md
  - ""  # 例: docs/WAVE2_ARCHITECTURE.md
  - ""  # 例: docs/HANDOFF_PHASE7_COMPLETE.md
  - ""  # 例: docs/BINDING_DECISIONS.md
  # 必要に応じて追加
```

---

## Binding Decisions

```yaml
Applicable BDs:
  - ""  # 例: BD-001 (Supabase as primary persistence)
  - ""  # 例: BD-015 (Event Sourcing for Domain events)

Non-applicable BDs:
  - ""  # 例: BD-030 (AI/LLM — 本PRでは使用しない)

Conflicts: none
  # 衝突するBDがあれば記載
```

---

## Scope Flags

> このPRで必要なものだけ YES にする。未必要なものは NO。

```yaml
Repository Required:    # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのRepositoryを追加するか

Event Required:         # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのEventを追加するか

API Required:           # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのAPIエンドポイントを追加するか

DI Required:            # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのTokenを追加するか

Migration Required:     # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのテーブル・カラムを変更するか

UI Required:            # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのScreenを変更するか

Architecture Guard Required:  # YES / NO
  Value: NO
  Detail: ""  # YES の場合: どのGuardを追加・更新するか
```

---

## Implementation Target

```yaml
Purpose: ""
  # このPRが解決する問題・達成する目標を1〜3文で

Implementation Target: |
  # 実装する内容を箇条書きで
  # 例:
  # - MenstrualPhaseResolver クラスを作成する
  # - EmotionSignalGenerator に MenstrualPhase を統合する
  # - 既存のNetworkSignalPersistenceServiceV2を使用して永続化する

Non-goals: |
  # このPRで実装しないことを明示する
  # 例:
  # - UI変更
  # - 新規Repository作成
  # - Supabase Migration追加
```

---

## Forbidden Changes

```yaml
Forbidden Changes:
  - ""  # 例: Repository Interface（INetworkSignalRepository）の新設
  - ""  # 例: Supabase Migration ファイルの追加
  - ""  # 例: AI/LLM の使用
  - ""  # 例: app-legacy.js の変更
  - ""  # 例: 他Domainファイルの変更
```

---

## Test Requirements

```yaml
Test Minimum Count: 10
  # このPRで追加する最低テスト件数

Required Tests:
  - ""  # 例: Unit Test: MenstrualPhaseResolver の基本動作
  - ""  # 例: Unit Test: 正常系・異常系・境界値
  - ""  # 例: Integration Test: EmotionSignalGenerator との統合
  - ""  # 例: Architecture Guard Test: レイヤー境界の確認
  - ""  # 例: Regression Test: 既存Emotion Signalへの影響なし
```

---

## Current State Description

```yaml
Current State: |
  # 現在のコードベースの状態を説明する
  # 例:
  # PR-041でRepository Interfaceが定義された。
  # PR-042でSupabase Repositoryと永続化基盤が完成した。
  # PR-043でEmotionSignalの基本Ruleエンジンが完成した。
  # 本PRでMenstrualPhaseの自動解決を追加する。
```

---

## Completion Report Required Items

```yaml
Completion Report Items:
  - Summary
  - Created Files
  - Updated Files
  - Domain Changes
  - Event Changes      # Event Required の場合
  - API Changes        # API Required の場合
  - DI Changes         # DI Required の場合
  - Tests Added
  - Total Passing Tests
  - BD Compliance
  - Known Limitations
  - Next PR Inputs
```

---

## Validation Status

> このシートを埋めた後、以下のValidationを実行して結果を記録する。

| Validation | ファイル | 結果 | 日時 |
|-----------|---------|------|------|
| Responsibility | `11_PR_RESPONSIBILITY_REGISTRY.md` | ⬜ PASS / ⬜ STOP | |
| Collision | `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` | ⬜ PASS / ⬜ STOP | |
| Roadmap | `13_ROADMAP_VALIDATOR.md` | ⬜ PASS / ⬜ STOP | |
| Scope | `14_PR_SCOPE_VALIDATOR.md` | ⬜ PASS / ⬜ STOP | |

**すべてPASSになるまで実装を開始しない。**
