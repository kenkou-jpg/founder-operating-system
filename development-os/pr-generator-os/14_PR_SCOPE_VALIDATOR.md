# 14 — PR Scope Validator

> PR Scope を固定し、Scope Creep を防ぐ。
> 追加・変更しようとするもの一つひとつに対して「Scope内か？」を判定する。
> 1項目でも STOP が出たら実装を止める。

---

## 実行手順

1. `02_PR_INPUT_SHEET.md` の全セクションを確認する
2. 実装しようとしているものをリストアップする
3. 各項目について以下のValidationを実行する
4. Scope Result を出力する

---

## Validation A — 追加予定機能

実装しようとしている機能を列挙し、一つずつ判定する。

| 追加予定の機能 | Scope内か | 根拠 |
|-------------|---------|------|
| [機能名] | YES / NO | `02_PR_INPUT_SHEET.md` の `Implementation Target` に記載あり / なし |
| [機能名] | YES / NO | |

**NO が1つでもあれば STOP。**

---

## Validation B — 変更予定ファイル

変更しようとしているファイルを列挙し、一つずつ判定する。

| 変更予定ファイル | Scope内か | 根拠 |
|--------------|---------|------|
| `path/to/file.ts` | YES / NO | |
| `path/to/file.ts` | YES / NO | |

**Forbidden Changesリストとの照合:**
| ファイル | Forbidden Changesに含まれるか | 判定 |
|---------|--------------------------|------|
| `path/to/file.ts` | YES / NO | STOP / PASS |

---

## Validation C — 新規Repository

```
新規Repositoryの追加が必要か？

Input Sheetの値: Repository Required = [YES / NO]

実装で追加しようとしているRepository:
- [Repositoryクラス名またはNone]

判定:
- Input Sheet が NO なのに Repository を追加しようとしている → STOP
- Input Sheet が YES かつ 追加するRepositoryがScopeに記載されている → PASS
- Input Sheet が YES かつ Input Sheetにない追加Repository → STOP

→ Repository: PASS / STOP
```

---

## Validation D — 新規Migration

```
新規Migrationの追加が必要か？

Input Sheetの値: Migration Required = [YES / NO]

実装で追加しようとしているMigration:
- [Migrationファイル名またはNone]

判定:
- Input Sheet が NO なのに Migration を追加しようとしている → STOP
- Input Sheet が YES かつ Scope内のMigration → PASS

→ Migration: PASS / STOP
```

---

## Validation E — 新規Event

```
新規Eventの追加が必要か？

Input Sheetの値: Event Required = [YES / NO]

実装で追加しようとしているEvent:
- [Event名またはNone]

判定:
- Input Sheet が NO なのに Event を追加しようとしている → STOP
- Input Sheet が YES かつ Scope内のEvent → PASS

→ Event: PASS / STOP
```

---

## Validation F — 新規API

```
新規APIの追加が必要か？

Input Sheetの値: API Required = [YES / NO]

実装で追加しようとしているAPIエンドポイント:
- [METHOD /path またはNone]

判定:
- Input Sheet が NO なのに API を追加しようとしている → STOP
- Input Sheet が YES かつ Scope内のAPI → PASS

→ API: PASS / STOP
```

---

## Validation G — 新規DI

```
新規DI Tokenの追加が必要か？

Input Sheetの値: DI Required = [YES / NO]

実装で追加しようとしているDI Token:
- [TOKEN_NAME またはNone]

判定:
- Input Sheet が NO なのに DI Token を追加しようとしている → STOP
- Input Sheet が YES かつ Scope内のDI Token → PASS

→ DI: PASS / STOP
```

---

## Validation H — UI変更

```
UIの変更が必要か？

Input Sheetの値: UI Required = [YES / NO]

実装で変更しようとしているScreen/Component:
- [ファイルパスまたはNone]

判定:
- Input Sheet が NO なのに UI を変更しようとしている → STOP
- Input Sheet が YES かつ Scope内のUI変更 → PASS

→ UI: PASS / STOP
```

---

## Validation I — Scope Creep 総合判定

以下の兆候がある場合は Scope Creep の可能性が高い:

- [ ] 実装中に「これもついでに直そう」と思った
- [ ] Scope外のバグを発見して修正しようとしている
- [ ] Input Sheetに書いていないファイルを変更しようとしている
- [ ] 「次のPRのためにここを準備しておこう」と思った
- [ ] テストを書いていたら Scope外のコードが気になった

**上記に該当する場合:** 修正したい内容を別のIssue / PRとして記録し、本PRでは実施しない。

---

## Scope Result

```
==================================
PR Scope Validation Result
==================================

PR-[番号]: [タイトル]
実行日時: [YYYY-MM-DD HH:MM]

Validation結果:
A. 追加予定機能: PASS / STOP
B. 変更予定ファイル: PASS / STOP
C. 新規Repository: PASS / STOP / N/A
D. 新規Migration: PASS / STOP / N/A
E. 新規Event: PASS / STOP / N/A
F. 新規API: PASS / STOP / N/A
G. 新規DI: PASS / STOP / N/A
H. UI変更: PASS / STOP / N/A
I. Scope Creep兆候: なし / あり

==================================
→ Scope Result: PASS / STOP
==================================

[STOP の場合]
Scope違反の内容:
- [具体的な違反内容]

対処方法:
- [Scopeから除外する / 別PRを立てる / Founder承認を取る]
==================================
```

---

## PASS条件

- すべての Validation が PASS または N/A
- または STOP 項目について Scope から除外済み / Founder 承認済み

---

## IPPOでのScope Validation例（PR-044）

```
A. 追加予定機能:
   - MenstrualPhaseResolver: YES（Input Sheet記載）
   - EmotionSignalGenerator統合: YES（Input Sheet記載）
   → PASS

B. 変更予定ファイル:
   - emotion-signal-generator.ts: YES（統合対象）
   - app-legacy.js: NO → Forbidden Changesに記載 → STOP候補
   ※ app-legacy.js は変更しないため問題なし
   → PASS

C. 新規Repository: Input Sheet = NO → PASS/N/A

D. 新規Migration: Input Sheet = NO → PASS/N/A

E. 新規Event: Input Sheet = YES
   - MenstrualPhaseDetectedEvent: Scope記載あり → PASS

F. 新規API: Input Sheet = YES
   - POST /api/menstrual-phase: Scope記載あり → PASS

G. 新規DI: Input Sheet = YES
   - MENSTRUAL_PHASE_RESOLVER_TOKEN: Scope記載あり → PASS

H. UI変更: Input Sheet = NO → PASS/N/A

I. Scope Creep: Disease Signalをついでに実装したい衝動を抑制 → なし

→ Scope Result: PASS ✅
```
