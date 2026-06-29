# FAST_MODE

> 通常 PR を低コンテキスト消費で進めるモード。
> Architecture / Migration / Governing Document に変更がない、Roadmap 通りの実装 PR で使用する。

---

## 用途

```
✅ Wave 開発中の通常 PR
✅ 既存設計内の実装（Domain / Service / UseCase の追加）
✅ Architecture 変更なし
✅ DB Migration なし
✅ Governing Document 変更なし
✅ Founder 判断が不要な変更
✅ Decision Log 更新条件に該当しない
```

---

## 必須チェック（省略不可）

```
□ PR 番号・タイトルの確認
□ Roadmap 上の位置確認（このPRが Roadmap 通りか）
□ Scope 確認（Implementation Target / Non-goals の確認）
□ Forbidden Changes 確認
□ BD 重大違反確認（全 BD ではなく、適用可能な BD のみ）
□ 対象 PR のみ実装（Scope Creep 確認）
□ 必要最小限のテスト（Unit / Integration の正常・異常・境界値）
□ Build 成功・関連テスト PASS 確認
□ 簡潔な Completion Report（FAST_MODE 形式）
□ Progress Registry Live Progress 更新
□ Decision Log 更新要否判定（条件に該当しなければ「更新不要」と明示）
```

---

## 省略可能な手順

```
△ 長文 Input Sheet の全項目出力（Scope 確認で代替）
△ 詳細 Validation ログ出力（チェック結果のみ記録）
△ 全 Governing Documents の長文要約
△ 全 BD 一覧の詳細出力（適用可能 BD のみ確認）
△ 詳細な Progress 説明
△ Decision Log の長文評価
△ Milestone History 更新（Phase / Wave 完了時以外）
△ Full Regression（影響範囲が明確な場合はスコープを絞る）
```

---

## 出力形式

FAST_MODE では以下の簡潔なサマリーを出力する。

```
## FAST_MODE Summary

PR: PR-XXX — [タイトル]
Scope: [実装内容を1〜2文]
Validation:
  - Roadmap: PASS
  - Scope: PASS
  - BD (applicable): PASS
  - Forbidden: PASS
Tests: X件追加 / 合計Y件 PASS / Build PASS
Progress: Current PR → PR-XXX へ更新
Decision Log: 更新不要（更新条件に該当せず）
Next: PR-XXX — [次PRタイトル]
```

---

## Execution Metadata（FAST_MODE 完了時に生成）

```
## Execution Metadata

Mode:               FAST
Reason:             [選択理由を1文]
Dispatcher Version: v0.4
Escalation:         NO
Generated At:       YYYY-MM-DD
```

**この Metadata を Completion Report と Progress Registry に引き継ぐこと。**

---

## Escalation トリガー

以下が判明したら STANDARD_MODE または FULL_MODE へ切り替える。

```
→ STANDARD_MODE:
  □ 想定外の新 Repository / Service が必要になった
  □ 複数ファイル横断変更が必要になった

→ FULL_MODE:
  □ Architecture 変更が必要になった
  □ Migration が必要になった
  □ BD 違反リスクが出た
  □ Security / Privacy / Consent に触れることが判明した
  □ Founder 判断が必要になった
```

---

## IPPO 適用例

```
PR-044: MenstrualPhase Auto-Resolution
  Architecture変更なし / Migration なし / BD 追加なし
  → FAST_MODE

PR-045: Emotion Signal Persistence Integration
  既存 Repository を使用 / Architecture 変更なし
  → FAST_MODE
```
