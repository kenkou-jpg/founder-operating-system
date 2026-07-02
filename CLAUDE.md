# Founder Operating System — Claude Code Startup Rule

> Claude Code が Founder Operating System に関する実行要求を受けた場合の起動ルール。
> このファイルが Founder Operating System の最上位エントリポイントである。

---

## Claude Code Startup Rule

```
Claude Code は Founder Operating System に関する実行要求を受けた場合、
最初に BOOTSTRAP.md を読むこと。

BOOTSTRAP.md を経由せずに Execution Dispatcher を開始してはならない。

Repository 探索は禁止する。
推測による Execution は禁止する。
```

---

## Startup Sequence

```
User Prompt
  ↓
CLAUDE.md（このファイル — 起動ルール確認）
  ↓
BOOTSTRAP.md（実行起点 — 順序確定）
  ↓
FOUNDER_OS_REFERENCE.md（External Repository Mapping — 参照先確定）
  ↓
Execution Dispatcher（00_EXECUTION_DISPATCHER.md — PR 実行起点）
  ↓
MODE_SELECTION_MATRIX.md（ルールベース Mode 決定）
  ↓
Optimization Pack（SMART_DOCUMENT_LOADING → TOKEN_OPTIMIZATION → REPORT_OPTIMIZATION）
  ↓
PR Generator OS（FAST_MODE / STANDARD_MODE / FULL_MODE）
  ↓
Implementation
  ↓
Completion Report
  ↓
Progress Registry（Live Progress 更新）
  ↓
Decision Log 判定（条件該当時のみ更新）
```

---

## Execution Rule

Founder Operating System に関する実行要求を受けた場合、Claude Code は以下を必ず順番通り実施する。

```
BOOTSTRAP.md を読む
  ↓
FOUNDER_OS_REFERENCE.md を読む
  ↓
Execution Dispatcher を起動する
  ↓
Execution Mode を決定する（MODE_SELECTION_MATRIX）
  ↓
Optimization Pack を適用する
  ↓
PR Generator OS を実行する（PR_INPUT_SHEET 記入）
  ↓
Validation を実施する（Mode 別）
  ↓
Implementation を完了する
  ↓
Completion Report を作成する
  ↓
Progress Registry を更新する
  ↓
Decision Log 判定を実施する
```

```
途中終了は禁止する。
途中で推測してはいけない。
Repository 探索は禁止する。
Execution Dispatcher の途中から開始してはいけない。
Completion Report が完成するまで Execution を終了してはいけない。
```

---

## 禁止事項

```
禁止: CLAUDE.md を読まずに BOOTSTRAP.md を直接読む
禁止: BOOTSTRAP.md を経由せずに Execution Dispatcher を開始する
禁止: Founder OS のファイルを検索・探索する
禁止: ファイルパスを推測して直接読む
禁止: この Startup Sequence を変更・省略する
```

---

## 対象となる実行要求

以下のいずれかを含むプロンプトを受けた場合、この Startup Rule を適用する。

```
- 「Founder Operating System に従ってください。」
- 「PR Generator OS を使ってください。」
- 「Execution Dispatcher を開始してください。」
- 「週次レビューを実施してください。Analytics OS に従ってください。」
- その他 Founder OS に関する実行要求全般
```

---

## 参照先

- `BOOTSTRAP.md` — 実行起点（次に読む）
- `FOUNDER_OS_REFERENCE.md` — External Repository Mapping
- `development-os/pr-generator-os/00_EXECUTION_DISPATCHER.md` — Execution Dispatcher
