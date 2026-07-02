# BOOTSTRAP

> Founder Operating System の唯一の実行起点。
> Claude Code が「Founder Operating System に従ってください。」という指示を受けたら、必ずここから開始する。
> このファイルを無視して直接 OS ファイルを読むことは禁止。

---

## 実行順序（厳守）

```
BOOTSTRAP（このファイル）
  ↓
FOUNDER_OS_REFERENCE.md（External Repository Mapping — 参照先を確定）
  ↓
Execution Dispatcher（00_EXECUTION_DISPATCHER.md — PR 実行の起点）
  ↓
MODE_SELECTION_MATRIX.md（ルールベースで FAST / STANDARD / FULL を決定）
  ↓
REPOSITORY_EXPLORATION_POLICY.md（探索範囲を確定 — Background Agent / 全探索禁止）
  ↓
Optimization Pack（SMART_DOCUMENT_LOADING → TOKEN_OPTIMIZATION → REPORT_OPTIMIZATION）
  ↓
PR Generator OS（選択した MODE.md に従い実装）
  ↓
Implementation → Completion Report → Progress Registry → Decision Log 判定
```

---

## Startup Origin Rule

```
BOOTSTRAP は Claude Code Startup Rule（CLAUDE.md）からのみ開始される。
直接 Execution Dispatcher を開始してはならない。
CLAUDE.md → BOOTSTRAP.md の順序は変更禁止。
```

---

## Bootstrap Completion Rule

```
BOOTSTRAP は Execution Dispatcher を起動するまで終了してはいけない。

Execution Dispatcher 起動後も Execution Rule（CLAUDE.md）に従い、
Completion Report が完成するまで継続してください。

途中で止まることは禁止する。
```

---

## 禁止事項

```
禁止: BOOTSTRAP.md を読まずに Execution Dispatcher を直接読む
禁止: Founder OS のファイルを検索・探索する
禁止: FOUNDER_OS_REFERENCE.md を読まずに OS ファイルのパスを推測する
禁止: この順序を変更する
禁止: PR開始時に Background Research Agent（Explore / general-purpose 等）を起動する
禁止: 対象プロジェクトの Repository 全体・Scope外ファイルを探索する
禁止: Startup Sequence で既読のファイルを再読する（9ファイル: CLAUDE/BOOTSTRAP/FOUNDER_OS_REFERENCE/
      DISPATCHER/MATRIX/REPO_POLICY/SMART_LOADING/TOKEN_OPT/REPORT_OPT）
禁止: Agent tool を PR 処理中に任意の目的で起動する（詳細: CLAUDE.md Background Agent 禁止ルール）
```

---

## Founder OS Invocation

「Founder Operating System に従ってください。」という指示は以下と同義。

```
最新版 Founder Operating System のルールを適用し、
BOOTSTRAP.md を起点として Execution Dispatcher を開始する。
```

---

## 参照先

- `FOUNDER_OS_REFERENCE.md` — Repository Mapping・Loading Rules
- `development-os/pr-generator-os/00_EXECUTION_DISPATCHER.md` — Execution Dispatcher
- `development-os/pr-generator-os/REPOSITORY_EXPLORATION_POLICY.md` — Repository 探索制限ルール
