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
Optimization Pack（SMART_DOCUMENT_LOADING → TOKEN_OPTIMIZATION → REPORT_OPTIMIZATION）
  ↓
PR Generator OS（選択した MODE.md に従い実装）
  ↓
Implementation → Completion Report → Progress Registry → Decision Log 判定
```

---

## 禁止事項

```
禁止: BOOTSTRAP.md を読まずに Execution Dispatcher を直接読む
禁止: Founder OS のファイルを検索・探索する
禁止: FOUNDER_OS_REFERENCE.md を読まずに OS ファイルのパスを推測する
禁止: この順序を変更する
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
