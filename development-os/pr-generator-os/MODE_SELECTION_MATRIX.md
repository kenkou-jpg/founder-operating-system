# MODE_SELECTION_MATRIX

> Execution Dispatcher が Execution Mode を決定するための唯一のルール表。
> Claude Code の推測は禁止。このマトリクスに従い、一意に Mode を決定する。
> Version: v1.0 | 2026-06-30

---

## 基本原則

```
最も高いリスクの条件を優先する。

例: Pure Function + Migration → Migration が優先 → FULL
例: Entity追加 + Architecture変更 → Architecture変更が優先 → FULL
例: Bug Fix + Repository追加 → Repository追加が優先 → STANDARD
```

**推測禁止 — 必ずこのマトリクスで決定する。**

---

## 判定フロー

```
PR 開始
  ↓
[1] Architecture 変更？ → YES → FULL
  ↓ NO
[2] Migration あり？ → YES → FULL
  ↓ NO
[3] Security / Privacy / Regulatory / Consent 変更？ → YES → FULL
  ↓ NO
[4] Authentication / Authorization 変更？ → YES → FULL
  ↓ NO
[5] Release / Phase完了 / Wave完了？ → YES → FULL
  ↓ NO
[6] Database 変更 / Repository構造変更？ → YES → FULL
  ↓ NO
[7] Business Strategy / Founder OS 変更？ → YES → FULL
  ↓ NO
[8] Legacy Removal / Performance大幅改善？ → YES → FULL
  ↓ NO
[9] Entity / Domain Service / Application Service 追加？ → YES → STANDARD
  ↓ NO
[10] API追加 / Domain Event追加？ → YES → STANDARD
  ↓ NO
[11] DI追加 / Composition Root変更？ → YES → STANDARD
  ↓ NO
[12] Feature Registry / Route Registry 変更？ → YES → STANDARD
  ↓ NO
[13] Repository実装追加？ → YES → STANDARD
  ↓ NO
[14] Medium Refactoring / Analytics機能追加？ → YES → STANDARD
  ↓ NO
→ FAST
```

---

## Mode Selection Matrix

### FAST — 対象 PR タイプ

| PR タイプ | 条件 |
|---------|------|
| Pure Function | 副作用なし・Architecture変更なし |
| Utility | 共通ユーティリティ追加・変更なし |
| Validation | バリデーション追加・ロジック変更なし |
| Formatter | フォーマッター追加・変更なし |
| Small Refactoring | 既存構造内・Migration不要 |
| Documentation | ドキュメント追加・変更のみ |
| Prompt | AI プロンプト追加・改善 |
| Template | テンプレート追加・更新 |
| Analytics更新 | CURRENT_STATE / Usage Matrix 等の記録更新 |
| Progress更新 | Progress Registry の Live Progress 更新 |
| Decision判定 | Decision Log の更新条件確認・記録 |
| Event追加（既存構造内） | 既存 Event 構造を変更しない追加 |
| Test追加 | 新機能なし・テストのみ追加 |
| Bug Fix（局所） | 単一ファイル・Architecture変更なし |

**FAST の特徴:**
- Architecture 変更なし
- Migration なし
- Repository 変更なし
- Business 変更なし
- 影響範囲が単一ファイル〜数ファイル

---

### STANDARD — 対象 PR タイプ

| PR タイプ | 条件 |
|---------|------|
| Entity追加 | 新 Entity 定義・既存 Architecture に準拠 |
| Domain Service追加 | 新 Domain Service・既存 Architecture に準拠 |
| Application Service追加 | 新 Application Service・DI 追加を伴う |
| API追加 | 新エンドポイント・Route Registry 変更を伴う |
| Domain Event追加 | 新 Event 定義・Event Handler 追加 |
| DI追加 | 依存注入の追加・Composition Root 変更 |
| Composition Root変更 | DI 設定変更・Module 追加 |
| Feature Registry変更 | Feature Flag の追加・変更 |
| Route Registry変更 | ルーティング追加・変更 |
| Repository実装追加 | 新 Repository 実装・既存 Interface 準拠 |
| Analytics機能追加 | Analytics OS に新機能・ファイル追加 |
| Medium Refactoring | 複数ファイル・Domain 境界内・Migration不要 |

**STANDARD の特徴:**
- Architecture 維持（変更しない）
- Migration 不要
- Scope 限定（単一 Domain 内）
- Validation 4種すべて必須

---

### FULL — 対象 PR タイプ

| PR タイプ | 条件 |
|---------|------|
| Architecture変更 | Domain 境界変更・層構造変更・依存方向変更 |
| Migration追加 | DB スキーマ変更・データ移行スクリプト追加 |
| Database変更 | テーブル追加・カラム変更・Index 変更 |
| Consent変更 | 同意フロー・同意スキーマの変更 |
| Security変更 | セキュリティポリシー・暗号化・署名の変更 |
| Privacy変更 | データ収集範囲・個人情報処理の変更 |
| Regulatory変更 | 法規制対応・コンプライアンス変更 |
| Authentication変更 | 認証方式・Token 管理の変更 |
| Authorization変更 | 権限モデル・Guard ロジックの変更 |
| Release | 本番リリース・バージョンタグ |
| Phase完了 | Wave 内 Phase の完了 PR |
| Wave完了 | Wave 全体の完了 PR |
| Legacy Removal | 旧コード・旧 API の削除 |
| Performance大幅改善 | Architecture レベルの最適化 |
| Repository構造変更 | ディレクトリ構造・Module 境界の変更 |
| Business Strategy変更 | 事業戦略・収益モデルの変更 |
| Founder OS変更 | Governing Document・Binding Decision の変更 |

**FULL の特徴:**
- すべての Validation 必須
- Milestone History 更新対象
- Founder 承認フロー必須
- Architecture Checklist すべて実施

---

## 複合 PR の判定ルール

```
複数のタイプが混在する PR は、最も高いリスクの条件を採用する。

優先順位（高→低）:
  FULL > STANDARD > FAST

例:
  Pure Function + Migration        → FULL（Migration が優先）
  Entity追加 + Architecture変更    → FULL（Architecture変更が優先）
  Bug Fix + DI追加                 → STANDARD（DI追加が優先）
  Template更新 + Test追加           → FAST（両方 FAST のため）
```

**不明な場合は上位 Mode を選択する（STANDARD → FULL, FAST → STANDARD）。**

---

## Escalation ルール

実行中に以下を発見した場合、現在の Mode から上位 Mode へ Escalate する。

| 発見内容 | Escalation先 |
|---------|-------------|
| Architecture 変更が必要と判明 | → FULL |
| Migration が必要と判明 | → FULL |
| Security / Privacy リスク発見 | → FULL |
| BD（Binding Decision）違反発見 | → FULL |
| Repository 追加が必要と判明 | → STANDARD |
| DI 変更が必要と判明 | → STANDARD |

Escalation 発生時: `Escalation: YES` を Execution Metadata に記録し、FULL MODE の追加 Validation を実施する。

---

## 参照元

- `00_EXECUTION_DISPATCHER.md` — このマトリクスを呼び出す Dispatcher
- `FAST_MODE.md` — FAST Mode の詳細ルール
- `STANDARD_MODE.md` — STANDARD Mode の詳細ルール
- `FULL_MODE.md` — FULL Mode の詳細ルール
- `SMART_DOCUMENT_LOADING.md` — Mode 決定後の文書読込ルール
