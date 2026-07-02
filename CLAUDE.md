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
REPOSITORY_EXPLORATION_POLICY.md（探索範囲を確定 — Background Agent / 全探索禁止）
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
Repository Exploration Policy を確認する（探索範囲を確定する）
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
禁止: PR開始時に Background Research Agent を起動する（REPOSITORY_EXPLORATION_POLICY.md）
禁止: 対象プロジェクトの Repository 全体を探索する
禁止: PR Scope外のファイルを探索する
禁止: Startup Sequence で既読のファイルを再読する（再読禁止 — SMART_DOCUMENT_LOADING.md v0.4.11）
禁止: Agent tool（Explore / general-purpose 等のサブエージェント）を PR 処理中に起動する
```

### Background Agent 禁止ルール（v0.4.11 強化）

```
Background Research Agent（Explore / general-purpose / その他サブエージェント全般）を
PR 処理の任意の段階で起動することを禁止する。

「理解を深めるため」「念のため」「依存関係を確認するため」という理由を問わず禁止。
Agent tool の呼び出しを検討した時点で即座に停止し、REPOSITORY_EXPLORATION_POLICY.md を再確認すること。

代替手段: HANDOFF / Roadmap 当該PRエントリ / PR_INPUT_SHEET に依存情報が記載されている。
不明な場合は Founder に報告する（3ファイル・3ディレクトリを超える探索が必要な場合と同様）。
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
- `development-os/pr-generator-os/REPOSITORY_EXPLORATION_POLICY.md` — Repository 探索制限ルール（Background Agent禁止・全探索禁止）
