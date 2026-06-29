# PR Generator OS

> 一人Founderが複数アプリを長期運営するための、PR単位開発標準化システム。

---

## Execution Mode Dispatcher

**Claude Code は PR 開始時に `00_EXECUTION_DISPATCHER.md` を最初に読み、実行モードを決定する。**

| Mode | 用途 | コンテキスト消費 |
|------|------|--------------|
| `FAST_MODE` | 通常 PR（Roadmap 通り・Architecture 変更なし）| 低 |
| `STANDARD_MODE` | 重要度中（新 Domain / Event / DI など）| 中 |
| `FULL_MODE` | Architecture 変更・Migration・Release・Phase 終了 | 最大 |

**モード選択は AI の独自判断ではなく、`00_EXECUTION_DISPATCHER.md` の OS ルールに基づく。**
**判断に迷う場合は `STANDARD_MODE`。Security / Privacy / AI / Research / Release は必ず `FULL_MODE`。**

### Execution Flow

```
Dispatcher（00_EXECUTION_DISPATCHER.md）
  ↓
Execution Metadata 生成（Mode / Reason / Version / Escalation / Generated At）
  ↓
Implementation（FAST_MODE / STANDARD_MODE / FULL_MODE）
  ↓
Completion Report（Execution Metadata を転記）
  ↓
Progress Registry Live Progress（Execution Metadata を転記）
```

---

## PR Generator OSとは何か

PR Generator OS は、AIに渡すPR実装プロンプトの品質を標準化・安定化するための
テンプレートとチェックリストの集合体です。

**解決する問題:**
- チャットをまたぐと同じ品質のPR指示を再現できない
- PRごとに責務が曖昧になり、Scope Creepが起きる
- アーキテクチャ違反・Binding Decision違反が気づかれずに混入する
- 前PRの責務と後PRの責務が衝突する

**このOSがもたらすもの:**
- PRプロンプトの再現性（誰が・いつ書いても同じ品質）
- 責務衝突の事前検知
- Roadmapからの逸脱防止
- Scope Creepの防止

---

## どのアプリで使うか

**すべてのアプリ・プロジェクトで使います。**

| プロジェクト | 状態 |
|-----------|------|
| IPPO | 実証プロジェクト（PR-041〜活用中） |
| AgriPath | 立ち上げ時に適用予定 |
| Fasting App | 立ち上げ時に適用予定 |
| Imaging Agriculture | 研究PR管理に適用予定 |
| 新規SaaS | テンプレートから即時適用 |

---

## IPPOでの使い方

1. **`00_EXECUTION_DISPATCHER.md` を読み、実行モードを決定する**
2. PR開始前に `04_GOVERNING_DOCUMENT_CHECKLIST.md` で上位文書を確認
3. `02_PR_INPUT_SHEET.md` に今回PRの情報を埋める
3. `11_PR_RESPONSIBILITY_REGISTRY.md` で責務重複を確認
4. **Validation 4種を実行（必須）:**
   - `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` → PASS確認
   - `13_ROADMAP_VALIDATOR.md` → PASS確認
   - `14_PR_SCOPE_VALIDATOR.md` → PASS確認
   - `06_BD_COMPLIANCE_CHECKLIST.md` → PASS確認
5. `01_PR_PROMPT_TEMPLATE.md` に入力シートの内容を流し込んでプロンプト生成
6. AIにプロンプトを渡して実装
7. `10_REVIEW_CHECKLIST.md` でレビュー
8. `09_COMPLETION_REPORT_TEMPLATE.md` で完了レポート提出
9. `11_PR_RESPONSIBILITY_REGISTRY.md` に完了PRの責務を登録

---

## 新規アプリでの使い方

1. `02_PR_INPUT_SHEET.md` の `Project Name` に新アプリ名を記入
2. `04_GOVERNING_DOCUMENT_CHECKLIST.md` を新アプリの文書構成に合わせてカスタマイズ
3. `11_PR_RESPONSIBILITY_REGISTRY.md` を新アプリ用に初期化
4. あとはIPPOと同じフロー

**IPPOで蓄積したパターンは `examples/` を参照してください。**

---

## 生成されるもの

PR Generator OSを使うと以下が生成されます：

- **PRプロンプト** — AIに渡す実装指示（`01_PR_PROMPT_TEMPLATE.md`から）
- **責務登録エントリ** — `11_PR_RESPONSIBILITY_REGISTRY.md`への行
- **完了レポート** — `09_COMPLETION_REPORT_TEMPLATE.md`から

生成されるのはMarkdownドキュメントのみです。**実装コードは生成しません。**

---

## Validation（必須: PR Prompt生成前に全件実行）

PR Promptを生成・AIに渡す前に、以下4つのValidationを必ず実行してください。
1件でも `STOP` が出た場合は、解消するまでPRを進めてはいけません。

| Validation | ファイル | 目的 |
|-----------|---------|------|
| Responsibility Validation | `11_PR_RESPONSIBILITY_REGISTRY.md` | 責務がRoadmapと一致しているか |
| Collision Detection | `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` | 他PRとの責務衝突がないか |
| Roadmap Validation | `13_ROADMAP_VALIDATOR.md` | Roadmapから逸脱していないか |
| Scope Validation | `14_PR_SCOPE_VALIDATOR.md` | Scope Creepがないか |

---

## 禁止事項

- 実装コードをこのOSに追加すること
- アプリのpackage.jsonを変更すること
- CI/CD設定をこのOSから変更すること
- IPPOリポジトリを直接変更すること
- テンプレートをIPPO専用に書き換えること（汎用性を守る）
- Validation未実施でPRを進めること

---

## ファイル構成

```
pr-generator-os/
├── README.md                           ← このファイル
│
├── [Execution Mode — 最初に読む]
├── 00_EXECUTION_DISPATCHER.md         ← Mode選択ルール（FAST/STANDARD/FULL）
├── FAST_MODE.md                       ← Fast Mode 必須チェック・出力形式
├── STANDARD_MODE.md                   ← Standard Mode 必須チェック・出力形式
├── FULL_MODE.md                       ← Full Mode 必須チェック・出力形式
│
├── [Input]
├── 02_PR_INPUT_SHEET.md               ← PR情報の入力シート
│
├── [Prompt Generation]
├── 01_PR_PROMPT_TEMPLATE.md           ← AIへのPR実装プロンプトテンプレート
├── 03_PR_TYPE_MATRIX.md               ← PRタイプ別の必須事項マトリクス
│
├── [Pre-PR Validation]
├── 04_GOVERNING_DOCUMENT_CHECKLIST.md ← 上位文書確認チェックリスト
├── 11_PR_RESPONSIBILITY_REGISTRY.md   ← PR責務SSOT（永久管理）
├── 12_RESPONSIBILITY_COLLISION_CHECKLIST.md ← 責務衝突検知
├── 13_ROADMAP_VALIDATOR.md            ← Roadmap逸脱検知
├── 14_PR_SCOPE_VALIDATOR.md           ← Scope Creep防止
│
├── [Implementation Guard]
├── 05_ARCHITECTURE_CHECKLIST.md       ← Architecture違反防止
├── 06_BD_COMPLIANCE_CHECKLIST.md      ← Binding Decision確認
├── 07_TEST_CHECKLIST.md               ← テスト確認
│
├── [Completion]
├── 08_DEFINITION_OF_DONE.md           ← 全PR共通完了条件
├── 09_COMPLETION_REPORT_TEMPLATE.md   ← 完了レポートテンプレート
├── 10_REVIEW_CHECKLIST.md             ← PRレビューチェックリスト
│
└── examples/
    ├── IPPO_PR044_EXAMPLE.md          ← IPPO PR-044の生成例
    └── GENERIC_DOMAIN_PR_EXAMPLE.md   ← 汎用Domain PRの例
```

---

## Version方針

| バージョン | 内容 |
|----------|------|
| v0.1 | 基本テンプレート（ファイル01〜10 + examples） |
| v0.2 | Validation強化（ファイル11〜14追加） |
| v0.4 | Execution Mode Dispatcher 追加（FAST/STANDARD/FULL） |
| v0.5 | プロジェクト別カスタマイズレイヤー追加 |
| v1.0 | 実運用で検証済み、AgriPath等でも使用 |

**現在: v0.4**

変更は `governance/CHANGELOG.md` に記録します。
