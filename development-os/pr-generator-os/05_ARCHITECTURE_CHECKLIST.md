# 05 — Architecture Checklist

> Architecture違反を防ぐチェックリスト。
> PR実装中・レビュー時の両方で使用する。

---

## レイヤー境界チェック

### 依存方向の違反

- [ ] **UI → Repository 禁止**
  - Screen / Component から Repository を直接 import していないか
  - 違反例: `import { UserRepository } from '../../repositories/UserRepository'` を Screen内で使用
  - 正しい依存: Screen → Hook / ViewModel → UseCase → Repository

- [ ] **Feature → Repository 禁止**
  - Feature層から Repository を直接呼んでいないか
  - 正しい依存: Feature → UseCase → Repository

- [ ] **Domain → Screen 禁止**
  - Domain Entity / ValueObject が UI コンポーネントを import していないか
  - Domain は UI に一切依存しない

- [ ] **Domain → External Service 直接依存禁止**
  - Domain が外部API・DBを直接呼んでいないか
  - 外部サービスは必ず Repository / Service 経由

- [ ] **Repository → UI 依存禁止**
  - Repository が Screen / Component を import していないか

---

## 設計パターン違反

- [ ] **循環依存（Circular Dependency）禁止**
  - A → B → A のような循環参照がないか
  - ツール: `madge` 等で検出（`development-os/` のCI標準参照）

- [ ] **God Object 禁止**
  - 1つのクラス・モジュールが過多な責務を持っていないか
  - 目安: 300行超のクラスは要レビュー

- [ ] **重複ロジック（Duplicate Logic）禁止**
  - 同じビジネスロジックが2箇所以上に書かれていないか
  - 発見した場合は共通化してから実装

- [ ] **隠れた状態（Hidden State）禁止**
  - グローバル変数・クロージャ内の隠れた状態がないか
  - 状態は必ず明示的に管理（Store / Context / Props）

---

## データアクセス違反

- [ ] **DB直接アクセス禁止**
  - Repository層を経由せずに DB（Supabase等）を直接呼んでいないか
  - 違反例: `supabase.from('users').select(...)` を Domain / Screen 内で直接呼ぶ

- [ ] **localStorage / AsyncStorage 直接アクセス禁止**
  - ストレージへの直接アクセスが Repository 外にないか
  - キャッシュ戦略は Repository 内に閉じる

---

## Single Source of Truth 違反

- [ ] **SSOT違反禁止**
  - 同じデータが複数のStateに重複して保持されていないか
  - 正しい設計: 一つのSourceから派生・参照

- [ ] **型定義の重複禁止**
  - 同じデータ構造の型が複数箇所で定義されていないか
  - 型は単一の場所で定義し、import して使う

---

## レガシーコード保護

- [ ] **Legacy変更禁止（該当する場合）**
  - `app-legacy.js` 等の指定されたレガシーファイルを変更していないか
  - Forbidden Changes リストを `02_PR_INPUT_SHEET.md` で確認

- [ ] **後方互換性の維持**
  - 既存のPublic APIを破壊的に変更していないか
  - 変更が必要な場合は Migration PR として別PRを立てる

---

## Architecture Guard

- [ ] **Architecture Guard の更新**
  - 新しいレイヤー・モジュールを追加した場合、Architecture Guardテストを更新したか
  - Guard がない場合は追加を検討する

- [ ] **Guard テストのPASS確認**
  - 既存の Architecture Guard テストがすべてPASSしているか

---

## 実装完了後の最終確認

```
□ レイヤー境界: すべての依存方向が正しい
□ 循環依存: なし（ツールで確認済み）
□ God Object: 1クラス1責務を守っている
□ 重複ロジック: なし
□ DB直接アクセス: Repository 外にない
□ SSOT: 重複したStateがない
□ Legacy保護: Forbidden Changesファイルを変更していない
□ Guard: 更新・PASSを確認済み
```

---

## 違反発見時の対応

Architecture 違反を発見した場合:

1. 実装を**一時停止する**
2. 違反内容と影響範囲を文書化する
3. Founderに報告する（`governance/DECISION_LOG.md` に記録）
4. 承認を得てから対応方法を決める

**自己判断でArchitecture違反を「このくらいなら大丈夫」と通さない。**
