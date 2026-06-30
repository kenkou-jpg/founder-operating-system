# STANDARD_MODE

> 通常より重要度が高い PR を、過剰にならず安全に進めるモード。
> 新 Domain / Service / Event / DI 構成追加、複数ファイル横断変更などで使用する。

---

## Mode Selection（必須）

```
STANDARD は MODE_SELECTION_MATRIX.md で選択された場合のみ利用する。
Claude Code の推測によるモード選択は禁止。
MODE_SELECTION_MATRIX.md の判定フローで STANDARD と決定した PR のみ、このファイルを読む。
```

---

## Optimization Pack（必須参照）

```
This mode must follow:
- SMART_DOCUMENT_LOADING.md  （必要文書のみ読む）
- TOKEN_OPTIMIZATION.md      （トークン消費の行動規範）
- REPORT_OPTIMIZATION.md     （最大 50 行の STANDARD Summary）
```

---

## 用途

```
✅ 新 Domain 追加
✅ 新 Service 追加
✅ 新 Repository 追加
✅ 新 Event 追加
✅ ApiGateway 追加
✅ DI 構成追加
✅ Architecture Guard 追加
✅ Feature Registry / Route Registry 追加
✅ 既存 Domain の構造拡張
✅ 複数ファイル横断変更（3ファイル超）
✅ Phase 中盤の重要 PR
```

---

## 必須チェック（省略不可）

```
□ PR Input Sheet 簡易記入（主要フィールドのみ）
□ Responsibility Validation（11_PR_RESPONSIBILITY_REGISTRY.md）
□ Roadmap Validation（13_ROADMAP_VALIDATOR.md）
□ Scope Validation（14_PR_SCOPE_VALIDATOR.md）
□ BD Compliance（06_BD_COMPLIANCE_CHECKLIST.md）
□ 関連する Architecture チェック（05_ARCHITECTURE_CHECKLIST.md の該当項目）
□ 関連テスト（Unit / Integration / Architecture Guard）
□ Regression 確認（影響範囲のテスト）
□ Build 成功確認
□ Completion Report（STANDARD_MODE 形式）
□ Progress Registry Live Progress 更新
□ Decision Log 更新要否判定（条件に該当しなければ「更新不要」と明示）
```

---

## 省略可能な手順

```
△ 全文書の長文要約（必要箇所のみ参照）
△ 全 BD の詳細な非適用一覧出力
△ 過剰な中間レポート
△ Milestone History 更新（Phase / Wave 完了時以外）
△ Full Regression（影響範囲を絞って実行）
```

---

## 出力形式

STANDARD_MODE では以下のサマリーを出力する。

```
## STANDARD_MODE Summary

PR: PR-XXX — [タイトル]
Mode Reason: [STANDARD_MODE を選択した理由]
Validation Results:
  - Responsibility: PASS / STOP
  - Collision: PASS / STOP
  - Roadmap: PASS / STOP
  - Scope: PASS / STOP
  - BD Compliance: PASS / STOP
Files:
  - Created: [ファイル名]
  - Updated: [ファイル名]
Tests: X件追加 / 合計Y件 PASS / Build PASS
Architecture: [変更の有無と内容]
BD: [適用した BD 番号]
Progress Registry: Current PR → PR-XXX へ更新
Decision Log: 更新不要 / 更新あり（DLOG-XXX）
Next PR: PR-XXX — [次PRタイトル]
```

---

## Execution Metadata（STANDARD_MODE 完了時に生成）

```
## Execution Metadata

Mode:               STANDARD
Reason:             [選択理由を1文]
Dispatcher Version: v0.4
Escalation:         NO / YES
  Previous Mode:    FAST（Escalation YES の場合のみ）
  Current Mode:     STANDARD（Escalation YES の場合のみ）
  Escalation Reason:[理由]（Escalation YES の場合のみ）
Generated At:       YYYY-MM-DD
```

**この Metadata を Completion Report と Progress Registry に引き継ぐこと。**

---

## Escalation トリガー

以下が判明したら FULL_MODE へ切り替える。

```
→ FULL_MODE:
  □ 想定外の Architecture 変更が必要になった
  □ DB Migration が必要になった
  □ BD 違反リスクが出た
  □ Security / Privacy / Consent に触れることが判明した
  □ Scope 外実装が必要になった
  □ Pre-existing failure ではない新規失敗が発生した
  □ Founder 判断が必要になった
```

---

## IPPO 適用例

```
PR-046: Disease Cluster Statistics
  新 Repository 追加 / 新 Service 追加
  → STANDARD_MODE

PR-047: FeatureVector V2（12次元）
  既存 FeatureVector の構造拡張 / DI 更新
  → STANDARD_MODE

PR-048: Longitudinal Edge Enricher
  新 Service / 複数ファイル横断変更
  → STANDARD_MODE
```
