# Example: IPPO PR-044 — MenstrualPhase Auto-Resolution

> PR Generator OSを使って生成されるPR-044の例。
> 実装指示ではなく「PR Generator OSがどう機能するか」を示すサンプル。

---

## Step 1: 02_PR_INPUT_SHEET.md を埋めた状態

```yaml
# [Project Information]
Project Name: "IPPO"
PR Number: "044"
PR Title: "MenstrualPhase Auto-Resolution"
Wave / Phase: "Wave 2 / Phase 8"
Domain: "emotion-signal / menstrual-phase"

# [PR Chain]
Completed PRs: "PR-041, PR-042, PR-043"
Previous PR:
  Number: "043"
  Title: "Emotion Signal Generation Foundation — Rule Engine + initializeSession"
This PR:
  Number: "044"
  Title: "MenstrualPhase Auto-Resolution"
Next PR:
  Number: "045"
  Title: "Disease Signal Integration"

# [Governing Documents]
Governing Documents:
  - "docs/BINDING_DECISIONS.md"
  - "docs/WAVE2_ARCHITECTURE.md"
  - "docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md"
  - "docs/WAVE2_ROADMAP.md"
  - "docs/WAVE2_MASTER_DESIGN.md"
  - "docs/HANDOFF_PHASE7_COMPLETE.md"

# [Binding Decisions]
Applicable BDs:
  - "BD-001: Supabase as primary persistence"
  - "BD-015: Event Sourcing for Domain events"
  - "BD-022: No direct DB access from Domain"
  - "BD-030: AI/LLM 使用禁止（本PRでは適用→Ruleベース実装）"
Non-applicable BDs:
  - "BD-045: Repository Interface before Adapter（PR-041で完成済み）"

# [Scope Flags]
Repository Required:
  Value: NO
  Detail: "NetworkSignalPersistenceServiceV2 を再利用"

Event Required:
  Value: YES
  Detail: "MenstrualPhaseDetectedEvent を追加"

API Required:
  Value: YES
  Detail: "POST /api/menstrual-phase/resolve を追加"

DI Required:
  Value: YES
  Detail: "MENSTRUAL_PHASE_RESOLVER_TOKEN を登録"

Migration Required:
  Value: NO
  Detail: "PR-042で完成したスキーマを使用"

UI Required:
  Value: NO
  Detail: "UI統合はPR-046以降"

# [Implementation Target]
Purpose: "月経周期データからMenstrualPhaseを自動解決し、EmotionSignalと統合する"

Implementation Target: |
  - MenstrualPhaseResolver クラスを作成する
  - MenstrualPhaseRule を定義する
  - EmotionSignalGenerator に MenstrualPhase 解決を統合する
  - EventBus 経由で MenstrualPhaseDetectedEvent を発火する
  - NetworkSignalPersistenceServiceV2 を使用して永続化する
  - POST /api/menstrual-phase/resolve エンドポイントを追加する
  - DI Token を登録する

Non-goals: |
  - UI変更（PR-046担当）
  - Disease Signal 実装（PR-045担当）
  - Similarity Signal 実装（後続PR担当）
  - 新規Repository作成（PR-041で完成済み）
  - Supabase Migration追加（PR-042で完成済み）
  - AI/LLM の使用（Ruleベースで実装）

# [Forbidden Changes]
Forbidden Changes:
  - "INetworkSignalRepository など Repository Interface の新設・変更"
  - "Supabase Migration ファイルの追加（supabase/migrations/配下）"
  - "AI/LLM の使用（OpenAI, Anthropic API 等）"
  - "app-legacy.js の変更"
  - "Disease Signal / Similarity Signal に関するコード"
  - "既存のEmotionSignalRuleEngine の内部実装変更"

# [Test Requirements]
Test Minimum Count: 15

Required Tests:
  - "Unit: MenstrualPhaseResolver - 正常系（フォリキュール期・排卵期・黄体期・月経期）"
  - "Unit: MenstrualPhaseResolver - 異常系（データなし・不完全なデータ）"
  - "Unit: MenstrualPhaseRule - 全条件分岐"
  - "Unit: MenstrualPhaseResolver - 境界値（周期の端）"
  - "Integration: EmotionSignalGenerator + MenstrualPhaseResolver"
  - "Integration: EventBus 経由での MenstrualPhaseDetectedEvent 発火"
  - "Integration: NetworkSignalPersistenceServiceV2 での永続化"
  - "API: POST /api/menstrual-phase/resolve 正常系"
  - "API: POST /api/menstrual-phase/resolve 認証エラー"
  - "API: POST /api/menstrual-phase/resolve バリデーションエラー"
  - "Architecture Guard: MenstrualPhaseResolver が Repository を直接使用しない"
  - "Regression: 既存の EmotionSignal が壊れていない"
  - "Regression: PR-041〜043 の既存テストが全PASS"
```

---

## Step 2: Validation 4種の実行結果

### 11_PR_RESPONSIBILITY_REGISTRY.md 確認結果

```
PR-044 責務確認:
- Registry にエントリあり: ✅
- 責務: MenstrualPhase Auto-Resolution
- Repository担当: NO ✅（PR-041完了済みのため新設禁止）
- Migration担当: NO ✅（PR-042完了済みのため追加禁止）
- Event担当: YES ✅（MenstrualPhaseDetectedEvent）
- API担当: YES ✅
- DI担当: YES ✅
- UI担当: NO ✅

→ Responsibility: PASS ✅
```

### 12_RESPONSIBILITY_COLLISION_CHECKLIST.md 実行結果

```
A. Repository衝突: PASS ✅
   INetworkSignalRepository は PR-041 で完成。新設なし。

B. Migration衝突: PASS/N/A ✅
   Migration Required = NO。対象外。

C. Domain衝突: PASS ✅
   MenstrualPhase は PR-043 未実装。後続PR担当でもない。

D. Event衝突: PASS ✅
   MenstrualPhaseDetectedEvent は新規定義。既存Eventと重複なし。

E. API衝突: PASS ✅
   /api/menstrual-phase/resolve は未存在。

H. File衝突: PASS ✅
   app-legacy.js は Forbidden → 触らない。

I. PR Chain衝突: PASS ✅
   PR-045（Disease Signal）の責務を先取りしていない。

→ Collision Result: PASS ✅
```

### 13_ROADMAP_VALIDATOR.md 実行結果

```
1. PR番号位置: PASS ✅（PR-041〜043完了、PR-044が正しい次のPR）
2. 責務一致: PASS ✅（WAVE2_ROADMAP.md でPR-044 = MenstrualPhase Auto-Resolution）
3. 次PR侵入なし: PASS ✅（Disease Signal は実装しない）
4. 前PR戻りなし: PASS ✅（Repository/Migration の再実装なし）
5. Governing Docs整合: PASS ✅
6. BD違反なし: PASS ✅（AI/LLM不使用、Ruleベース実装）
7. Wave/Phase整合: PASS ✅（Wave 2 / Phase 8）

→ Roadmap Validation: PASS ✅
```

### 14_PR_SCOPE_VALIDATOR.md 実行結果

```
A. 追加予定機能: PASS ✅（全機能がInput Sheet記載）
B. 変更予定ファイル: PASS ✅（Forbidden Changesに含まれるファイルなし）
C. 新規Repository: PASS/N/A ✅（NO → 既存を使用）
D. 新規Migration: PASS/N/A ✅（NO → 既存スキーマを使用）
E. 新規Event: PASS ✅（YES → MenstrualPhaseDetectedEvent）
F. 新規API: PASS ✅（YES → POST /api/menstrual-phase/resolve）
G. 新規DI: PASS ✅（YES → MENSTRUAL_PHASE_RESOLVER_TOKEN）
H. UI変更: PASS/N/A ✅（NO → UI変更なし）
I. Scope Creep: なし ✅（Disease Signal衝動を抑制）

→ Scope Result: PASS ✅
```

---

## Step 3: 生成されるPRプロンプト（概要）

*（実際のプロンプトは `01_PR_PROMPT_TEMPLATE.md` に入力シートを流し込んで生成）*

```
Role: IPPOのEmotion Signal Domain専門エンジニア

Governing Documents:
1. docs/BINDING_DECISIONS.md
2. docs/WAVE2_ARCHITECTURE.md
3. docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md
4. docs/WAVE2_ROADMAP.md
5. docs/WAVE2_MASTER_DESIGN.md
6. docs/HANDOFF_PHASE7_COMPLETE.md

Current State:
- PR-041: Repository Interface/Adapter/Factory 完了
- PR-042: Supabase Persistence Foundation 完了
- PR-043: Emotion Signal Generation Foundation 完了
- PR-044: MenstrualPhase Auto-Resolution（本PR）

PR Scope: MenstrualPhaseResolver + EmotionSignal統合 + Event + API + DI

Forbidden:
❌ Repository Interface 新設
❌ Supabase Migration 追加
❌ AI/LLM 使用
❌ app-legacy.js 変更
❌ Disease Signal 実装
❌ Similarity Signal 実装

Required Tests: 15件以上

Definition of Done: [08_DEFINITION_OF_DONE.md 参照]
```

---

## Step 4: Completion Report（期待される出力）

```
## PR-044 Completion Report

Summary:
MenstrualPhaseResolverを実装し、EmotionSignalGeneratorに統合した。
月経周期データから自動的にMenstrualPhaseを解決し、EventBus経由で
MenstrualPhaseDetectedEventを発火する。
NetworkSignalPersistenceServiceV2経由で永続化される。

Created Files:
- src/domain/emotion-signal/menstrual-phase-resolver.ts
- src/domain/emotion-signal/menstrual-phase-rule.ts
- src/api/menstrual-phase/menstrual-phase.controller.ts
- src/events/menstrual-phase-detected.event.ts
- src/domain/emotion-signal/__tests__/menstrual-phase-resolver.test.ts
（他テストファイル）

Updated Files:
- src/domain/emotion-signal/emotion-signal-generator.ts（MenstrualPhase統合）
- src/di/tokens.ts（MENSTRUAL_PHASE_RESOLVER_TOKENを追加）
- src/di/container.ts（DI登録）

Tests Added: 17件
Total Passing Tests: 既存234件 + 新規17件 = 251件
Regression: なし ✅
BD Compliance: BD-001, BD-015, BD-022 準拠 ✅

Next PR Inputs:
- PR-045: Disease Signal Integration
- MenstrualPhaseResolver は DI Token 経由で取得可能
- EventBus の MenstrualPhaseDetectedEvent を Disease Signal が購読する
```
