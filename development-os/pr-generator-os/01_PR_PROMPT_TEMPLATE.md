# 01 — PR Prompt Template

> AIに渡すPR実装プロンプトの汎用テンプレート。
> `02_PR_INPUT_SHEET.md` を埋めてから、このテンプレートの `{{}}` を置換して使う。

---

```
## Role

あなたは {{PROJECT_NAME}} の {{DOMAIN}} 専門のソフトウェアエンジニアです。
以下の実装指示に従い、PR-{{PR_NUMBER}} を完成させてください。

あなたは Governing Documents をすべて読み込み、
Architecture・Binding Decisions・Roadmap に完全準拠した実装のみを行います。

---

## Governing Documents

実装前に以下を必ず読み込んでください。読み込みが完了したら「読み込み完了」と返答してください。

{{#each GOVERNING_DOCUMENTS}}
- {{this}}
{{/each}}

上位文書の優先順位:
1. Binding Decisions（最上位・変更不可）
2. Architecture Document
3. Implementation Governance / Roadmap
4. 直前Handoff
5. PR Scope（このドキュメント）

---

## Current State

現在のリポジトリ状態:

- 完了済みPR: {{COMPLETED_PRS}}
- 直前PR: {{PREVIOUS_PR}} — {{PREVIOUS_PR_TITLE}}
- 本PR: PR-{{PR_NUMBER}} — {{PR_TITLE}}
- 次PR: {{NEXT_PR}} — {{NEXT_PR_TITLE}}

{{CURRENT_STATE_DESCRIPTION}}

---

## PR Scope

**PR番号:** PR-{{PR_NUMBER}}
**タイトル:** {{PR_TITLE}}
**Wave / Phase:** {{WAVE_PHASE}}
**ドメイン:** {{DOMAIN}}

### このPRで実装すること

{{IMPLEMENTATION_TARGET}}

### このPRで実装しないこと（Non-goals）

{{NON_GOALS}}

---

## Purpose

{{PURPOSE}}

---

## Implementation Target

{{IMPLEMENTATION_DETAIL}}

---

## Forbidden Changes

以下は**絶対に変更・追加・削除してはいけません。**

{{#each FORBIDDEN_CHANGES}}
- ❌ {{this}}
{{/each}}

これらへの変更が必要に見えた場合は、実装を止めて報告してください。
絶対に自己判断で変更しないでください。

---

## Architecture Rules

{{#if ARCHITECTURE_RULES}}
{{ARCHITECTURE_RULES}}
{{else}}
以下のアーキテクチャ原則に従ってください:

1. レイヤー境界を越えた依存を作らない
   - UI → Repository の直接依存禁止
   - Feature → Repository の直接依存禁止
   - Domain → Screen の依存禁止

2. 循環依存禁止

3. God Object 禁止（1クラス1責務）

4. 重複ロジック禁止（Single Source of Truth）

5. 隠れた状態禁止（State は明示的に管理）

6. DB直接アクセス禁止（必ずRepository層を経由）

7. Append-Only原則（削除より追記）
{{/if}}

---

## Repository Rules

{{#if REPOSITORY_REQUIRED}}
Repository が必要な場合:
{{REPOSITORY_RULES}}
{{else}}
このPRでは**新規Repositoryの作成は禁止**です。
既存のRepositoryを使用してください。
{{/if}}

---

## Event Rules

{{#if EVENT_REQUIRED}}
Event Sourcing が必要な場合:
{{EVENT_RULES}}
{{else}}
このPRでは**新規Eventの追加は禁止**です。
{{/if}}

---

## API Rules

{{#if API_REQUIRED}}
API Gateway が必要な場合:
{{API_RULES}}
{{else}}
このPRでは**新規APIエンドポイントの追加は禁止**です。
{{/if}}

---

## DI Rules

{{#if DI_REQUIRED}}
DI（依存性注入）が必要な場合:
{{DI_RULES}}
{{else}}
このPRでは**新規DI Tokenの追加は禁止**です。
既存のDI設定を使用してください。
{{/if}}

---

## Migration Rules

{{#if MIGRATION_REQUIRED}}
Migration が必要な場合:
{{MIGRATION_RULES}}
{{else}}
このPRでは**DBスキーマの変更・Migration追加は禁止**です。
既存のスキーマを使用してください。
{{/if}}

---

## Test Requirements

最低 {{TEST_MINIMUM_COUNT}} 件のテストを追加してください。

必須テスト:
{{#each REQUIRED_TESTS}}
- [ ] {{this}}
{{/each}}

テストの原則:
- 実装と同時にテストを書く（後回し禁止）
- テストなしのPRはDefinition of Doneを満たさない
- 既存テストを壊してはいけない（Regression禁止）
- テストは独立して実行できること（他テストへの依存禁止）

---

## Definition of Done

以下をすべて満たすまでPRは完了ではありません:

- [ ] Scope内の実装がすべて完了している
- [ ] Non-goalsの内容が混入していない
- [ ] Forbidden Changesが変更されていない
- [ ] Architecture Rulesに違反していない
- [ ] Binding Decisionsに違反していない
- [ ] テストが {{TEST_MINIMUM_COUNT}} 件以上追加されている
- [ ] すべてのテストがPASSしている
- [ ] 既存テストがRegressionしていない
- [ ] Completion Reportが提出されている
- [ ] 次PRへの入力情報が明確になっている

---

## Completion Report Format

完了時に以下の形式でレポートを提出してください:

```
## PR-{{PR_NUMBER}} Completion Report

### Summary
（1〜3文でPRの成果を要約）

### Created Files
- path/to/file.ts
- ...

### Updated Files
- path/to/file.ts（変更内容の要約）
- ...

### Deleted Files
- （削除したファイルがあれば）

### Domain Changes
（Domain層への変更サマリー）

### Repository Changes
（Repository層への変更サマリー、またはNone）

### Event Changes
（Event Sourcingへの変更サマリー、またはNone）

### API Changes
（APIへの変更サマリー、またはNone）

### DI Changes
（DI設定への変更サマリー、またはNone）

### Architecture Guard Changes
（Architecture Guardへの変更サマリー、またはNone）

### Tests Added
- テスト名: 説明
- ...

### Total Passing Tests
（既存 + 新規）: X件

### Pre-existing Failures
（実装前から存在していた失敗テスト、なければNone）

### BD Compliance
- 適用されたBD: BD-XXX, BD-YYY
- 違反なし: ✅

### Known Limitations
（既知の制限・次PRへ持ち越す事項）

### Next PR Inputs
- 次PR番号: PR-{{NEXT_PR}}
- 引き継ぎ情報: ...
```
```

---

## 使い方

1. `02_PR_INPUT_SHEET.md` に必要情報を記入する
2. このテンプレートの `{{}}` を入力シートの値で置換する
3. Validation 4種（11〜14）を実行し、すべて PASS であることを確認する
4. 完成したプロンプトをAIに渡す
5. 実装完了後、`09_COMPLETION_REPORT_TEMPLATE.md` で完了レポートを提出する
