# 06 — Binding Decision Compliance Checklist

> Binding Decision（BD）の確認用テンプレート。
> PRプロンプト生成前に記入し、AIに渡す。
> IPPOのようにBD-001〜BD-060が存在するプロジェクトでも使用できる構造。

---

## BDとは

Binding Decision（BD）は、プロジェクトの根本的な技術・事業判断を記録したもの。
すべてのPRはBDに準拠しなければならない。
BDはFounder以外が変更できない。

**BDは `governance/BINDING_DECISIONS.md`（プロジェクト固有）または
`[project]/docs/BINDING_DECISIONS.md` に記録されている。**

---

## Step 1 — Applicable BD（適用されるBD）

このPRに関係するBDをすべてリストアップしてください。

| BD番号 | タイトル | 本PRへの影響 | 準拠確認 |
|-------|---------|------------|---------|
| BD-XXX | | | ⬜ |
| BD-XXX | | | ⬜ |
| BD-XXX | | | ⬜ |

---

## Step 2 — Non-applicable BD（適用されないBD）

このPRに関係しないBDを明示してください（「不要なのに守ろうとする」事故を防ぐ）。

| BD番号 | タイトル | 適用除外の理由 |
|-------|---------|--------------|
| BD-XXX | | |
| BD-XXX | | |

---

## Step 3 — Conflicts（衝突）

BDとPR Scopeが衝突する箇所があれば記録してください。

| 衝突するBD | 衝突内容 | 解決策 |
|-----------|---------|-------|
| BD-XXX | | |

**衝突がある場合は実装を開始してはいけません。Founderの承認が必要です。**

---

## Step 4 — Resolution

Step 3の衝突をどう解決するか記録してください。

```
衝突内容:
解決策:
Founder承認: YES / NO / 不要
承認日時:
```

---

## Step 5 — Approval Required?

| 確認項目 | 結果 |
|---------|------|
| Founder Approval Required? | YES / NO |
| Council Required? | YES / NO |
| BDの改訂が必要か? | YES / NO |

---

## BD Compliance Result

```
BD Compliance Check
-------------------
Applicable BDs: [BD番号リスト]
All Compliant: YES / NO
Conflicts: [あれば内容] / none
Founder Approval: [必要/不要/取得済み]

→ PASS / STOP
```

**STOP の場合はFounderへ報告し、解決するまで実装を進めない。**

---

## IPPOでの参考例

IPPOプロジェクトでのBD適用例（PR-044 MenstrualPhase Auto-Resolutionの場合）:

| BD番号 | タイトル | 適用 | 準拠 |
|-------|---------|------|------|
| BD-001 | Supabase as primary persistence | ✅ 適用 | ✅ 既存ServiceV2を使用 |
| BD-015 | Event Sourcing for Domain events | ✅ 適用 | ✅ EventBus経由 |
| BD-022 | No direct DB access from Domain | ✅ 適用 | ✅ Repository経由 |
| BD-030 | AI/LLM使用禁止（本PR） | ✅ 適用 | ✅ ルールベースで実装 |
| BD-045 | Repository Interface before Adapter | ❌ 非適用 | — PR-041で完成済み |

---

## 全BDが確認済みであることの宣言

```
[ ] すべての関連BDを確認した
[ ] 衝突するBDに対してFounder承認を得た（または衝突なし）
[ ] AI/LLM使用BDの扱いを確認した
[ ] セキュリティ・プライバシー関連BDを確認した
[ ] Migration・DB変更関連BDを確認した（該当する場合）

BD Compliance: PASS / STOP
```
