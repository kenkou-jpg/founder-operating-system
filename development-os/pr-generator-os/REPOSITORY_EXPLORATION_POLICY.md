# REPOSITORY_EXPLORATION_POLICY

> PR開始時の不要なリポジトリ探索・Background Research Agent起動・Scope外調査を禁止し、
> Claude Codeのトークン消費を削減するための強制ルール。
> `MODE_SELECTION_MATRIX.md` で Mode を決定した直後、`SMART_DOCUMENT_LOADING.md` を読む前に必ず適用する。
> Version: v1.1 | 2026-07-02 | v0.4.11: Agent禁止強化・再読禁止明記

---

## Purpose

```
1. PR開始時の探索コストを削減する（Background Agent起動はトークン消費が最大級）
2. HANDOFF / Roadmap / Responsibility Registry に既にある情報の再探索を防ぐ
3. Scope Creepの温床となる「理解のための広範囲調査」を防ぐ（14_PR_SCOPE_VALIDATOR.md と連動）
4. 探索範囲を PR Scope 内に構造的に閉じ込める
```

**トークン削減は目的であって、品質低下の言い訳にしてはならない。読むべき文書（Validation 4種・直接依存ファイル）は引き続き必須。**

---

## Position in Execution Flow

`00_EXECUTION_DISPATCHER.md` の Execution Flow に以下の位置で組み込む。

```
PR 開始
  ↓
BOOTSTRAP
  ↓
FOUNDER_OS_REFERENCE
  ↓
MODE_SELECTION_MATRIX（Mode 決定）
  ↓
REPOSITORY_EXPLORATION_POLICY（このファイル — 探索範囲を確定）
  ↓
SMART_DOCUMENT_LOADING（必要最小限の文書のみ）
  ↓
Validation
  ↓
Implementation
```

**このファイルを経由せずに SMART_DOCUMENT_LOADING.md 以降に進んではならない。**

---

## 禁止事項（12項目・省略不可）

```
1. PR開始時の Background Research Agent 起動禁止（Explore / general-purpose 等のサブエージェント全般）
2. Repository 全体探索禁止
3. Scope外ファイル探索禁止
4. 「理解のため」の広範囲調査禁止
5. まず HANDOFF / Roadmap / PR Scope を読む（第一手順として必須）
6. 依存ファイルは HANDOFF と PR Scope から特定する（推測探索禁止）
7. 読むファイルは必要最小限に限定する
8. 不明点がある場合のみ、対象ディレクトリ内に限定して検索してよい
9. Architecture 変更がない PR では Architecture 全体探索禁止
10. Validation（Responsibility / Roadmap / Scope / BD Compliance）前に大量探索してはいけない
11. Agent tool を「念のため」「理解を深めるため」という理由で起動することは禁止（理由の種類を問わず禁止）
12. Startup Sequence 既読ファイル（9点）の再読禁止（詳細: SMART_DOCUMENT_LOADING.md 再読禁止ルール）
```

---

## 許可される読込（Allowed Reads）

```
✅ HANDOFF文書（当該プロジェクトの最新ハンドオフ）
✅ Roadmap の当該PRエントリのみ
✅ PR Scope（02_PR_INPUT_SHEET.md の Implementation Target に列挙されたファイル）
✅ 直接依存ファイル（HANDOFF / 11_PR_RESPONSIBILITY_REGISTRY.md の「入力」「依存PR」に明記されたファイルのみ）
✅ 直接関連テストファイル
✅ 必須 Validation 文書（Responsibility / Roadmap / Scope / BD Compliance）
```

上記以外のファイルを読む場合は、下記「Escalation — 限定探索が必要な場合」の手順に従うこと。

---

## 禁止される調査行動（Forbidden Investigation Actions）

```
✗ Background Research Agent（Explore / general-purpose 等のサブエージェント全般）を
  PR開始時・Validation前に起動すること
✗ Repository全体に対する広範囲 grep / Glob（全ファイル名検索・全ディレクトリ列挙）
✗ Scope外ドメインの実装ファイルを「念のため」「参考までに」読むこと
✗ Architecture変更を伴わないPRで Architecture 全体を読み直すこと
✗ 「理解を深めるため」という理由での関連PRの完了レポート全文読み込み
✗ 依存関係が不明なまま、複数ドメインを横断して探索を広げること
```

---

## STANDARD_MODE / FAST_MODE における追加禁止事項

```
禁止: Background agent の起動（Explore / general-purpose 等サブエージェント全般）
禁止: broad repository scan（ディレクトリ全列挙・全文検索）
禁止: exploratory grep（キーワードのみを頼りにした探索的検索）
禁止: unrelated domain inspection（Scope外ドメインの実装確認）
禁止: full architecture investigation（Architecture変更がないPRでの全体調査）
```

**FULL_MODE の扱い:** Architecture 変更・Migration・Release・Phase/Wave完了 PR では、性質上 Council 文書・Architecture 全体の確認が引き続き必須である。本ポリシーは FULL_MODE の必須 Validation・必須読込を制限しない。FULL_MODE でも「不要な探索」（無関係ドメインの調査・過去レポート全文読み込み等）は引き続き禁止する。

---

## Escalation — 限定探索が必要な場合

HANDOFF / Roadmap / Responsibility Registry からファイルパスを特定できない不明点がある場合のみ、以下の手順で最小限の探索を許可する。

```
1. 対象ディレクトリを1つに絞る（例: src/domains/research-query/ のみ）
2. Glob / Grep を対象ディレクトリ内に限定して実行する（同期的に直接ツールで確認する）
3. Background Agent は使用しない
4. 探索した理由と読んだファイルを「Documents Loaded」形式で1行報告する
```

Repository全体を対象にした探索、または **3ファイル・3ディレクトリを超える横断探索** が必要になった場合は、実装を停止し Founder に報告する（Scope外実装の可能性が高い — `14_PR_SCOPE_VALIDATOR.md` の Validation I を参照）。

---

## Rationale（なぜこのポリシーが必要か）

```
- Background Research Agent の起動は数万トークン規模のコンテキストを消費する
- HANDOFF / Roadmap / Responsibility Registry には依存ファイルパスが明記済みであることが多く、
  探索はしばしば重複作業になる
- 探索範囲が広がるほど Scope Creep のリスクが高まる（14_PR_SCOPE_VALIDATOR.md）
- 5時間制限下では PR 完遂を最優先すべきであり、不要な探索は TOKEN_OPTIMIZATION.md の
  「Must Not」に該当する行動である
```

---

## 違反時の対応

Repository Exploration Policy 違反を発見した場合:

```
1. 実装を一時停止する
2. 探索した理由・読んだファイルを記録する
3. HANDOFF / Roadmap 側の情報が不足していた場合は、追記の要否を Founder に確認する
```

**自己判断で「今回だけは探索が必要」と広範囲調査を正当化しない。**

---

## 関連ドキュメント

- `00_EXECUTION_DISPATCHER.md` — このポリシーの実行順序上の位置
- `SMART_DOCUMENT_LOADING.md` — 探索確定後に読む文書を絞り込むルール
- `TOKEN_OPTIMIZATION.md` — トークン消費の行動規範
- `STANDARD_MODE.md` / `FAST_MODE.md` — Mode別の探索制限
- `14_PR_SCOPE_VALIDATOR.md` — Scope Creep防止（探索範囲の逸脱と連動）
- `11_PR_RESPONSIBILITY_REGISTRY.md` — 依存ファイル・依存PRの特定元
