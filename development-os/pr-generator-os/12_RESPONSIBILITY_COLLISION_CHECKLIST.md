# 12 — Responsibility Collision Checklist

> AIが実装前に責務衝突を検知するチェックリスト。
> `11_PR_RESPONSIBILITY_REGISTRY.md` と照合しながら実行する。
> 1項目でも ❌ が出たら STOP。実装を開始しない。

---

## 実行手順

1. `11_PR_RESPONSIBILITY_REGISTRY.md` を読み込む
2. `02_PR_INPUT_SHEET.md` の本PRの情報を確認する
3. 以下の各チェック項目を順番に確認する
4. 最後に Collision Result を出力する

---

## Collision Check Items

### A. Repository 衝突チェック

- [ ] **このRepositoryは既存PRで完成していないか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の完了済みPRに、同名のRepository担当がないか
  - 例: `INetworkSignalRepository` は PR-041 で完成済み → 新設禁止

- [ ] **このInterfaceは既に存在しないか**
  - 同名のInterface定義を追加しようとしていないか
  - Interface の再定義・上書きは禁止

- [ ] **このAdapterは別PR担当ではないか**
  - Adapter追加が他PRの `追加してよいもの` になっていないか

### B. Migration 衝突チェック

- [ ] **このMigrationは別PR担当ではないか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` で `Migration担当: YES` になっている完了済みPRが存在するか
  - 存在する場合、そのMigrationは完了済み → 新規Migration不要

- [ ] **このMigrationは本PRのスコープか**
  - `02_PR_INPUT_SHEET.md` で `Migration Required: NO` になっていないか

### C. Domain 衝突チェック

- [ ] **このDomainはRoadmap対象外ではないか**
  - `13_ROADMAP_VALIDATOR.md` で確認（連携）
  - 今のPhaseで実装すべきDomainか

- [ ] **このDomainは前PRで実装済みではないか**
  - 同じEntity / ValueObject / Service を再実装しようとしていないか

- [ ] **このDomainは次PR担当ではないか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の計画中PRの `追加してよいもの` に含まれていないか

### D. Event 衝突チェック

- [ ] **このEventは既存実装と重複しないか**
  - 同名のEventが既に定義されていないか
  - 同じ発火タイミングのEventが重複していないか

- [ ] **このEventは別PR担当ではないか**
  - 他のPRの `Event担当: YES` と衝突していないか

### E. API 衝突チェック

- [ ] **このAPIは既存Gatewayと重複しないか**
  - 同じエンドポイント（method + path）が既に存在しないか

- [ ] **このAPIは別PR担当ではないか**
  - 他のPRの `API担当: YES` と衝突していないか

### F. Route / Feature 衝突チェック

- [ ] **このFeatureはRouteRegistryに登録済みではないか**
  - 同名のRoute / Feature が既に登録されていないか
  - 登録済みの場合は変更PRとして扱う

### G. DI 衝突チェック

- [ ] **このDI登録は既存Tokenと衝突しないか**
  - 同名のDI Tokenが既に登録されていないか
  - Token名の衝突は実行時エラーを引き起こす

### H. File 衝突チェック

- [ ] **このPRで変更してはいけないファイルを触っていないか**
  - `02_PR_INPUT_SHEET.md` の `Forbidden Changes` を確認
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の前PRの `変更禁止` を確認

### I. PR Chain 衝突チェック

- [ ] **次PR担当の責務を実装していないか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の次PRの `追加してよいもの` を先取りしていないか

- [ ] **前PRの責務を再実装していないか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の完了済みPRと同じものを実装しようとしていないか

### J. Architecture Layer 衝突チェック

- [ ] **Architecture Layerを飛び越えていないか**
  - `05_ARCHITECTURE_CHECKLIST.md` の依存方向ルールを違反していないか
  - Layer Jumpは責務衝突の一種

---

## Collision Result

すべての項目を確認したら、以下の形式で結果を出力してください:

```
==================================
Collision Detection Result
==================================

PR-[番号]: [タイトル]
実行日時: [YYYY-MM-DD HH:MM]

チェック結果:
A. Repository衝突: PASS / FAIL
B. Migration衝突: PASS / FAIL / N/A
C. Domain衝突: PASS / FAIL
D. Event衝突: PASS / FAIL / N/A
E. API衝突: PASS / FAIL / N/A
F. Route衝突: PASS / FAIL / N/A
G. DI衝突: PASS / FAIL / N/A
H. File衝突: PASS / FAIL
I. PR Chain衝突: PASS / FAIL
J. Architecture Layer衝突: PASS / FAIL

==================================
→ Collision Result: PASS / STOP
==================================

[STOP の場合]
衝突理由:
- [具体的な衝突内容]

衝突対象PR:
- PR-[番号]: [衝突している責務]

修正案:
- [衝突を解消するための提案]

Founder承認が必要: YES / NO
==================================
```

**STOP が出た場合は、修正案を確認してFounderと合意するまで実装を開始しない。**

---

## IPPOでのCollision例（PR-044）

PR-044でこのチェックリストを実行した場合の期待される結果:

```
A. Repository衝突: PASS
   → INetworkSignalRepositoryはPR-041で完成。新設なし。✅

B. Migration衝突: PASS / N/A
   → Migration Requiredがfalseのため対象外。✅

C. Domain衝突: PASS
   → MenstrualPhaseはPR-043未実装、PR-045以降の担当でもない。✅

D. Event衝突: PASS
   → MenstrualPhaseEventは新規定義。重複なし。✅

E. API衝突: PASS
   → /api/menstrual-phase は未存在。✅

H. File衝突: PASS
   → app-legacy.jsはForbiddenとしてInputSheetに記載済み。触らない。✅

I. PR Chain衝突: PASS
   → PR-045（Disease Signal）の責務を先取りしていない。✅

→ Collision Result: PASS ✅
```
