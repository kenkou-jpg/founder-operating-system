# SMART_DOCUMENT_LOADING

> 毎 PR で全 Governing Documents を読まない。必要な文書だけ読む。
> コンテキスト消費を削減しながら、重要文書の読み落としを防ぐ。

---

## Purpose

1. **必要十分な文書読込** — PR の種類・Mode に応じた最小限の読込
2. **コンテキスト消費削減** — 不要な全文書読込を排除
3. **重要文書の読み落とし防止** — Mode 別の必須リストで抜け漏れを防ぐ
4. **Mode 別の文書読込ルール** — FAST / STANDARD / FULL で読む文書を分ける

---

## FAST_MODE — 読込ルール

### 必須（毎回読む）

```
- Roadmap の当該 PR エントリ（PR 番号の行のみ）
- Responsibility Registry の当該 PR エントリ
- Progress Registry の Live Progress スナップショット
- FAST_MODE.md（このセッションのモードファイル）
- 実装対象のソースファイル・テストファイル
```

### 必要時のみ（該当する場合だけ読む）

```
- Architecture（Architecture Guard に触れる変更がある場合）
- BD Compliance（適用可能な BD が不明な場合）
- Implementation Governance（PRの前提仕様が不明な場合）
```

### 読まない文書

```
✗ 全 Council 文書
✗ 全 Business / Growth / GTM 文書
✗ 全 BD 一覧（適用外を含む）
✗ Founder Strategic Review 全文
✗ 過去 PR 完了レポート全文
✗ Wave 全体の実装方針文書（当該 PR に関係しない部分）
```

---

## STANDARD_MODE — 読込ルール

### 必須（毎回読む）

```
- Roadmap の当該 PR エントリ（Phase 単位）
- Responsibility Registry（当該 PR + 直前 2〜3 件）
- Architecture の関連セクション（新 Domain / Service / Event の部分）
- BD の関連セクション（適用可能な BD のみ）
- Progress Registry の Live Progress スナップショット
- 関連 Domain ファイル
- 関連テストファイル
```

### 必要時のみ

```
- Implementation Governance（実装仕様の確認が必要な場合）
- Council 文書（新 Domain が Council の決定に依存する場合）
- Data Asset Council / Network Evolution Council（該当する場合）
```

### 読まない文書

```
✗ 全 Council 文書（関係しない Council は読まない）
✗ 全 BD 一覧（適用外を含む）
✗ 全 Business / Legal 文書（変更がない場合）
✗ 過去 PR 完了レポート全文
```

---

## FULL_MODE — 読込ルール

### 必須（毎回読む）

```
- Governing Document Hierarchy（04_GOVERNING_DOCUMENT_CHECKLIST.md）
- Roadmap（全体構成の確認）
- Architecture（全セクション）
- Implementation Governance
- 関連 Council 文書（変更対象に関係する Council）
- Business / Legal / Regulatory 文書（変更がある場合）
- BD 関連セクション（全適用可能 BD）
- Progress Registry（Live Progress + 直近 Milestone）
- Decision Log 更新条件（09_DECISION_LOG.md の Update Rule）
```

### 必要時のみ

```
- 過去 Phase の完了レポート（依存関係の確認が必要な場合）
- 全 Council 文書（Architecture 変更が複数 Council に影響する場合）
```

---

## Escalation Loading

FAST_MODE で進めている途中に以下が発覚した場合、追加で以下の文書を読み込む。

| 発覚内容 | 追加読込 |
|---------|---------|
| Architecture 変更が必要 | Architecture 全体 + Architecture Guard |
| DB / Migration が必要 | Migration ガイド + BD (DB 関連) |
| BD 違反リスク | BD Compliance Checklist + 関連 BD |
| Security / Privacy / Consent | Legal OS + Privacy Policy 方針 |
| AI / Research / Release | 関連 Council + Release Checklist |
| Scope 外実装の必要性 | Roadmap + Responsibility Registry（全体）|

---

## Output Rule

文書を読んだ後、**長文要約は禁止**。出力は以下のみ。

```
Documents Loaded:
- [ファイル名]
- [ファイル名]

Reason:
- [なぜこの文書が必要か、1文]
```

---

## 関連ドキュメント

- `00_EXECUTION_DISPATCHER.md` — Mode 選択（このファイルより先に読む）
- `TOKEN_OPTIMIZATION.md` — トークン消費の行動規範
- `FAST_MODE.md` / `STANDARD_MODE.md` / `FULL_MODE.md` — Mode 別必須チェック
