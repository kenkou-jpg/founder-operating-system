# Example: Generic Domain PR — CropHealth Assessment

> PR Generator OS の汎用利用例。
> 架空のアプリ「AgriScan」での Domain PR を例に、
> IPPO以外でもPR Generator OSが機能することを示す。

---

## 前提

**プロジェクト:** AgriScan（農業向け作物健康診断アプリ）
**PR番号:** PR-007
**タイトル:** CropHealth Assessment Domain — 作物健康スコア計算
**PRタイプ:** Domain PR（`03_PR_TYPE_MATRIX.md` の #1 に相当）

---

## Step 1: 02_PR_INPUT_SHEET.md を埋めた状態

```yaml
Project Name: "AgriScan"
PR Number: "007"
PR Title: "CropHealth Assessment Domain"
Wave / Phase: "Phase 2 / Sprint 3"
Domain: "crop-health"

PR Chain:
  Completed PRs: "PR-001〜PR-006"
  Previous PR:
    Number: "006"
    Title: "Field Repository Interface & Supabase Adapter"
  This PR:
    Number: "007"
    Title: "CropHealth Assessment Domain"
  Next PR:
    Number: "008"
    Title: "CropHealth API Endpoint"

Governing Documents:
  - "docs/ARCHITECTURE.md"
  - "docs/BINDING_DECISIONS.md"
  - "docs/IMPLEMENTATION_GOVERNANCE.md"
  - "docs/SPRINT3_ROADMAP.md"
  - "docs/HANDOFF_SPRINT2_COMPLETE.md"

Applicable BDs:
  - "BD-003: PostgreSQL via Supabase as primary DB"
  - "BD-007: Domain must not depend on external services"
  - "BD-012: All Domain events via EventBus"

Repository Required:
  Value: NO
  Detail: "Field Repository はPR-006で完成済み"

Event Required:
  Value: YES
  Detail: "CropHealthAssessedEvent を追加"

API Required:
  Value: NO
  Detail: "APIはPR-008担当"

DI Required:
  Value: YES
  Detail: "CROP_HEALTH_ASSESSOR_TOKEN を登録"

Migration Required:
  Value: NO
  Detail: "既存 field_assessments テーブルを使用"

UI Required:
  Value: NO
  Detail: "UIはPR-009担当"

Implementation Target: |
  - CropHealthScore ValueObject を作成する
  - CropHealthRule（病害・栄養不足・成長段階別）を定義する
  - CropHealthAssessor Service を実装する
  - EventBus 経由で CropHealthAssessedEvent を発火する
  - DI Token を登録する

Non-goals: |
  - APIエンドポイント（PR-008担当）
  - UI表示（PR-009担当）
  - 画像解析連携（PR-012担当）
  - 新規Repository作成
  - DBスキーマ変更

Forbidden Changes:
  - "IFieldRepository など既存のRepository Interface"
  - "Field Domain Entity"
  - "Supabase Migration ファイル"
  - "既存のUIコンポーネント"

Test Minimum Count: 12
```

---

## Step 2: Validation 4種の実行結果

### 11_PR_RESPONSIBILITY_REGISTRY.md 確認

```
PR-007 責務確認:
- CropHealth Assessment Domain を担当
- Repository担当: NO（PR-006完了済み）
- Migration担当: NO（既存スキーマを使用）
- Event担当: YES（CropHealthAssessedEvent）
- API担当: NO（PR-008担当）
- UI担当: NO（PR-009担当）

既存エントリとの衝突:
- PR-006: Field Repository Interface → 完了済み。IFieldRepositoryの新設は禁止。
- PR-008: CropHealth API → 計画中。APIエンドポイントはPR-008担当。

→ Responsibility: PASS ✅
```

### 12_RESPONSIBILITY_COLLISION_CHECKLIST.md

```
A. Repository衝突: PASS ✅（IFieldRepository はPR-006完了済み）
B. Migration衝突: N/A ✅（Migration Requiredなし）
C. Domain衝突: PASS ✅（CropHealth Domainは新規・未実装）
D. Event衝突: PASS ✅（CropHealthAssessedEvent は新規）
E. API衝突: N/A ✅（API RequiredなしのためPR-008への先取り確認のみ）
H. File衝突: PASS ✅（Forbidden Changesファイルを変更しない）
I. PR Chain衝突: PASS ✅（PR-008のAPIを先取りしていない）

→ Collision Result: PASS ✅
```

### 13_ROADMAP_VALIDATOR.md

```
1. PR番号位置: PASS ✅（PR-001〜006完了、PR-007が次）
2. 責務一致: PASS ✅（SPRINT3_ROADMAPでPR-007 = CropHealth Domain）
3. 次PR侵入なし: PASS ✅（APIはPR-008、UIはPR-009）
4. 前PR戻りなし: PASS ✅
5. Governing Docs整合: PASS ✅
6. BD違反なし: PASS ✅（BD-007: Domain外部依存なし → Ruleベース実装）
7. Sprint整合: PASS ✅（Phase 2 / Sprint 3）

→ Roadmap Validation: PASS ✅
```

### 14_PR_SCOPE_VALIDATOR.md

```
A. 機能: PASS ✅（全機能がInput Sheet記載）
B. ファイル: PASS ✅（Forbidden不含）
C. Repository: N/A ✅
D. Migration: N/A ✅
E. Event: PASS ✅（CropHealthAssessedEvent）
F. API: N/A ✅（API Required = NO）
G. DI: PASS ✅（CROP_HEALTH_ASSESSOR_TOKEN）
H. UI: N/A ✅（UI Required = NO）
I. Scope Creep: なし ✅

→ Scope Result: PASS ✅
```

---

## Step 3: 生成されるPRプロンプト（概要）

```
Role: AgriScan の CropHealth Domain 専門エンジニア

Governing Documents:
1. docs/ARCHITECTURE.md
2. docs/BINDING_DECISIONS.md
3. docs/IMPLEMENTATION_GOVERNANCE.md
4. docs/SPRINT3_ROADMAP.md
5. docs/HANDOFF_SPRINT2_COMPLETE.md

Current State:
- PR-001〜006: 完了済み
- PR-006: Field Repository Interface & Supabase Adapter 完了
- PR-007: CropHealth Assessment Domain（本PR）

PR Scope:
- CropHealthScore ValueObject
- CropHealthRule（病害・栄養・成長段階）
- CropHealthAssessor Service
- CropHealthAssessedEvent

Forbidden:
❌ IFieldRepository Interface の変更
❌ Supabase Migration の追加
❌ API エンドポイント（PR-008担当）
❌ UI コンポーネント（PR-009担当）
❌ 画像解析ロジック（PR-012担当）

Architecture Rules:
- CropHealthAssessor は外部サービスに直接依存しない（BD-007）
- Event は必ず EventBus 経由（BD-012）
- DB アクセスは Repository 経由のみ

Tests Required: 12件以上
- Unit: CropHealthScore の正常・異常・境界値
- Unit: CropHealthRule の全条件分岐（病害/栄養/成長段階）
- Unit: CropHealthAssessor の統合
- Integration: EventBus 経由のEvent発火
- Architecture Guard: Domain外部依存なし
- Regression: PR-001〜006の既存テスト全PASS
```

---

## Step 4: Completion Report（期待される出力）

```
## PR-007 Completion Report
Project: AgriScan

Summary:
CropHealthAssessor Domainを実装した。
作物の病害・栄養状態・成長段階をRuleベースで評価し、
CropHealthScoreとして数値化する。
評価完了時にCropHealthAssessedEventをEventBus経由で発火する。

Created Files:
- src/domain/crop-health/crop-health-score.value-object.ts
- src/domain/crop-health/crop-health-rule.ts
- src/domain/crop-health/crop-health-assessor.service.ts
- src/events/crop-health-assessed.event.ts
- src/domain/crop-health/__tests__/crop-health-score.test.ts
- src/domain/crop-health/__tests__/crop-health-rule.test.ts
- src/domain/crop-health/__tests__/crop-health-assessor.test.ts

Tests Added: 14件
Total Passing Tests: 既存89件 + 新規14件 = 103件
Regression: なし ✅
BD Compliance: BD-003, BD-007, BD-012 準拠 ✅

Next PR Inputs:
- PR-008: CropHealth API Endpoint
- CROP_HEALTH_ASSESSOR_TOKEN で DI から CropHealthAssessor を取得可能
- POST /api/crop-health/assess → CropHealthAssessor.assess(fieldId, imageData) を呼ぶ
- CropHealthAssessedEvent の Payload: { fieldId, score, riskFactors, timestamp }
```

---

## このサンプルが示すこと

| 観点 | 示していること |
|-----|-------------|
| 汎用性 | IPPOとは全く異なるドメイン（農業×画像）でも同じOSが機能する |
| PRタイプ | Domain PRの典型パターン（Repository不要・API不要・Domain専念）|
| Validation | 4種のValidationがAgriScanでも同じように機能する |
| Forbidden | プロジェクト固有のForbiddenが自然に定義できる |
| 再利用性 | `01_PR_PROMPT_TEMPLATE.md` の変数を変えるだけで別プロジェクトに適用可能 |
