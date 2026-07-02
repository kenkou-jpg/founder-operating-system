# IPPO — RESPONSIBILITY_HISTORY

> IPPO の PR ごとの責務・Scope 履歴を管理する。
> 11_PR_RESPONSIBILITY_REGISTRY.md（Common OS）には共通責務ルールのみ記録する。
> PR 単位の履歴はここに記録する。

---

## 責務履歴テンプレート

```
PR-XXX — [タイトル]
  責務: [この PR が持つ唯一の責務]
  Scope: [実装対象]
  Non-goals: [意図的に含まないもの]
  依存 PR: [前提となる PR]
  後続 PR: [この PR が前提となる PR]
  Scope Creep: なし / あり（内容）
  完了日: YYYY-MM-DD
```

---

## PR 責務履歴

### PR-041

```
PR-041 — Wave2 Phase A 開始 PR
  責務: Wave2 Phase A の起点となる実装
  Scope: （詳細は IPPO リポジトリ参照）
  Non-goals: Wave2 Phase B 以降の実装
  依存 PR: Wave1 Complete
  後続 PR: PR-042
  Scope Creep: なし
  完了日: 2026-06
```

### PR-042

```
PR-042 — Wave2 Phase A 継続
  責務: Wave2 Phase A 継続実装
  Scope: （詳細は IPPO リポジトリ参照）
  Non-goals: Phase A 範囲外
  依存 PR: PR-041
  後続 PR: PR-043
  Scope Creep: なし
  完了日: 2026-06
```

### PR-043

```
PR-043 — Wave2 Phase A 継続
  責務: Wave2 Phase A 継続実装
  Scope: （詳細は IPPO リポジトリ参照）
  Non-goals: Phase A 範囲外
  依存 PR: PR-042
  後続 PR: PR-044
  Scope Creep: なし
  完了日: 2026-06
```

---

## 責務衝突記録

```
衝突なし（Wave2 Phase A 現時点）
```

---

## 更新ルール

```
PR 完了時:
  1. このファイルに PR 責務履歴を追記する
  2. 11_PR_RESPONSIBILITY_REGISTRY.md（Common OS）には追記しない
  3. Scope Creep があった場合は記録し、次 PR の Non-goals に反映する
```
