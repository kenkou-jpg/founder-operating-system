# FULL_MODE

> 設計・安全性・Phase / Wave に関わる重要 PR を完全監査するモード。
> Architecture 変更・DB Migration・Release・Phase 終了など、影響範囲が大きい PR で使用する。

---

## 用途

```
✅ Architecture 変更（レイヤー構造・依存関係の再定義）
✅ DB Migration 追加
✅ Supabase Schema 変更
✅ Security / Privacy / Consent 変更
✅ AI / LLM / Medical Safety 変更
✅ Research Dataset 公開・Export・License に関わる変更
✅ Release Candidate
✅ Beta Release
✅ Official Release
✅ Phase 終了 PR
✅ Wave 終了 PR
✅ Legacy 削除
✅ 重大なリファクタリング（複数ドメイン横断）
✅ Roadmap 変更
✅ Governing Document 変更
✅ Binding Decision 追加 / 変更
✅ Founder 判断が必要な変更
```

---

## 必須チェック（省略不可）

```
□ Full PR Input Sheet（全フィールド記入）
□ Full Responsibility Validation（11_PR_RESPONSIBILITY_REGISTRY.md）
□ Full Collision Detection（12_RESPONSIBILITY_COLLISION_CHECKLIST.md）
□ Full Roadmap Validation（13_ROADMAP_VALIDATOR.md）
□ Full Scope Validation（14_PR_SCOPE_VALIDATOR.md）
□ Full BD Compliance（06_BD_COMPLIANCE_CHECKLIST.md — 全 BD 確認）
□ Governing Document 確認（04_GOVERNING_DOCUMENT_CHECKLIST.md）
□ Architecture Compliance（05_ARCHITECTURE_CHECKLIST.md — 全項目）
□ Security / Privacy 確認（該当する場合）
□ Full relevant tests（Unit / Integration / Architecture Guard / Regression）
□ Full Regression
□ Build 成功・型チェック・Lint 確認
□ Full Completion Report（09_COMPLETION_REPORT_TEMPLATE.md）
□ Progress Registry Live Progress 更新
□ Milestone History 更新（Phase / Wave 完了時）
□ Decision Log 更新条件判定（条件に該当する場合は更新）
□ Founder 承認待ち確認（Founder 判断が必要な場合）
```

---

## 出力形式

FULL_MODE では以下の完全なサマリーを出力する。

```
## FULL_MODE Summary

PR: PR-XXX — [タイトル]
Mode Reason: [FULL_MODE を選択した理由]

Governing Documents:
  - 確認済み: [文書リスト]
  - 違反: なし / [内容]

Input Sheet:
  - Scope Flags: [Repository/Event/API/DI/Migration/UI/Guard の YES/NO]

Responsibility: PASS / STOP
Roadmap: PASS / STOP
Scope: PASS / STOP
BD Compliance: PASS / STOP（適用 BD: [番号リスト]）

Architecture:
  - Compliance: PASS / STOP
  - 変更内容: [変更の有無と内容]

Security / Privacy:
  - 該当: yes / no
  - 確認結果: PASS / STOP

Tests: X件追加 / 合計Y件 PASS
Regression: PASS / STOP（X件）
Build: PASS / STOP

Progress Registry:
  - Live Progress: Current PR → PR-XXX へ更新
Milestone History:
  - 更新あり: [Phase/Wave 完了の場合]
  - 更新なし

Decision Log:
  - 更新あり: DLOG-XXX / 更新不要

Founder Approval:
  - 必要: yes / no
  - 状態: 承認待ち / 承認済み / 不要

Next PR: PR-XXX — [次PRタイトル]
```

---

## IPPO 適用例

```
PR-041: NetworkSignal Repository V2
  新 Repository Interface / Migration 追加 / Architecture 変更
  → FULL_MODE

Phase A Complete（PR-041〜045 完了時）
  → FULL_MODE + Milestone History 追記

Wave2 Complete（PR-075 完了時）
  → FULL_MODE + Milestone History 追記 + Decision Log 判定
```

---

## Founder 承認フロー

FULL_MODE で Founder 判断が必要な場合:

```
1. 実装前に Founder に判断内容を提示する
2. Founder の承認を得てから実装を開始する
3. 承認内容を Completion Report に記録する
4. 必要に応じて 09_DECISION_LOG.md に記録する
```
