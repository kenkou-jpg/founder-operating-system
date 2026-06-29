# 08 — Definition of Done

> 全PR共通の完了条件。
> これをすべて満たすまで、PRは「完了」ではない。
> AIへのプロンプトにも、このDefinition of Doneを含める。

---

## Execution Mode 確認

- [ ] **Execution Mode が選択されている**（`00_EXECUTION_DISPATCHER.md` のルールに基づく）
- [ ] **Mode 固有の必須チェックがすべて満たされている**（FAST / STANDARD / FULL それぞれの必須リスト参照）
- [ ] **Escalation 確認済み**（実装中にモード変更が必要な事態が起きていないか）

---

## 必須条件（すべてクリアすること）

### 1. Scope完了

- [ ] PR Scopeに定義されたすべての実装が完了している
- [ ] `02_PR_INPUT_SHEET.md` の `Implementation Target` がすべて実装されている
- [ ] 部分実装（「とりあえず動く」状態）でPRを閉じない

### 2. Non-goals未混入

- [ ] Scopeに含まれないものが実装に混入していない
- [ ] `02_PR_INPUT_SHEET.md` の `Non-goals` が実装されていないことを確認
- [ ] 「ついでに」「一緒に」の実装がない

### 3. Architecture違反なし

- [ ] `05_ARCHITECTURE_CHECKLIST.md` がすべてクリアされている
- [ ] レイヤー境界を違反した依存がない
- [ ] 循環依存がない
- [ ] God Object がない
- [ ] SSOT違反がない

### 4. Forbidden Changes未変更

- [ ] `02_PR_INPUT_SHEET.md` の `Forbidden Changes` に記載されたファイル・機能を変更していない
- [ ] `app-legacy.js` 等の保護ファイルを変更していない（該当する場合）

### 5. Tests PASS

- [ ] 新しく追加したテストがすべてPASSしている
- [ ] 最低 `TEST_MINIMUM_COUNT` 件のテストを追加している
- [ ] `07_TEST_CHECKLIST.md` に記載した必須テストをすべて追加している

### 6. Regression なし

- [ ] 既存テストがPR実装後もすべてPASSしている
- [ ] 既存機能への意図しない副作用がない
- [ ] Build が成功している（型エラー・Lintエラーなし）

### 7. Governing Documents違反なし

- [ ] `04_GOVERNING_DOCUMENT_CHECKLIST.md` で確認したすべての上位文書に準拠している
- [ ] `06_BD_COMPLIANCE_CHECKLIST.md` がPASSしている
- [ ] Binding Decision違反がない

### 8. Validation PASS

- [ ] `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` → PASS
- [ ] `13_ROADMAP_VALIDATOR.md` → PASS
- [ ] `14_PR_SCOPE_VALIDATOR.md` → PASS

### 9. Completion Report提出

- [ ] `09_COMPLETION_REPORT_TEMPLATE.md` を使って完了レポートを提出している
- [ ] 作成・更新・削除ファイルが明確に記録されている
- [ ] テスト追加数と総テスト数が記録されている

### 10. Next PRへの入力明確化

- [ ] 次PRが何を前提とするかが明確になっている
- [ ] `11_PR_RESPONSIBILITY_REGISTRY.md` に本PRの責務が登録されている
- [ ] 次PRのFounderが本PRの成果物を理解できる状態になっている

---

## プロジェクトへの追加条件

プロジェクト固有の完了条件があれば以下に追記してください:

### IPPO追加条件

- [ ] Wave 2 Architecture ルールに準拠している
- [ ] `HANDOFF_PHASE[N]_COMPLETE.md` が更新されている（Phaseの最終PRの場合）

### 新規プロジェクト追加条件

- [ ] （プロジェクト立ち上げ時に記入）

---

## Definition of Done チェック結果

```
Definition of Done
------------------
1. Scope完了:             ✅ / ❌
2. Non-goals未混入:        ✅ / ❌
3. Architecture違反なし:   ✅ / ❌
4. Forbidden未変更:        ✅ / ❌
5. Tests PASS:             ✅ / ❌ (X件追加 / 合計Y件)
6. Regression なし:        ✅ / ❌
7. Governing Docs準拠:     ✅ / ❌
8. Validation PASS:        ✅ / ❌
9. Completion Report:      ✅ / ❌
10. Next PR明確化:          ✅ / ❌

→ PR-[XXX]: COMPLETE / INCOMPLETE
```

**1つでも ❌ がある場合は INCOMPLETE。解消するまでPRをmergeしない。**
