# [APP_NAME] — Claude Code Startup Rule

> **使い方:** このテンプレートを新規アプリのリポジトリ直下に `CLAUDE.md` として配置する。
> `[APP_NAME]`・`[HANDOFF_PATH]` をアプリに合わせて置き換えること。
> このコメント行（> で始まる行）は配置時に削除すること。

---

# [APP_NAME] — Claude Code Startup Rule

> Claude Code が [APP_NAME] リポジトリで PR 実行要求を受けた場合の起動ルール。
> このファイルが [APP_NAME] の唯一のエントリポイントである。

---

## Startup Rule

```
PR 開始時は、外部 Founder Operating System を読みに行かない。

このリポジトリ内の AI_EXECUTION.md を唯一の実行ルールとして使用する。
AI_EXECUTION.md に定義されていない判断が必要な場合は、Founder に確認する。
```

---

## Runtime Rule

```
このファイルは Founder Operating System から Export された App Runtime である。

Founder OS（Canonical Source）: founder-operating-system リポジトリ
App Runtime（実行環境）: このリポジトリの CLAUDE.md + AI_EXECUTION.md

Founder OS が更新された場合のみ、このファイルの更新を検討する。
通常 PR では、このファイルを自己書き換えしてはいけない。
```

---

## Execution Flow

```
User Prompt
  ↓
CLAUDE.md（このファイル — 起動ルール確認）
  ↓
AI_EXECUTION.md（実行モード決定・Validation・実装ルール確認）
  ↓
HANDOFF（[HANDOFF_PATH] — 前 PR からの引き継ぎ確認）
  ↓
PR Scope（Roadmap 当該 PR エントリ・実行シート相当の情報）
  ↓
Relevant Files（HANDOFF / PR Scope に明記された直接依存ファイルのみ）
  ↓
Tests（直接関連テストのみ）
  ↓
Implementation
  ↓
Completion Report（AI_EXECUTION.md の Report Optimization に従う）
```

---

## 禁止事項

```
禁止: 外部 Founder OS を毎 PR で探索・読み込む
禁止: Background Research Agent（Explore / general-purpose 等のサブエージェント）の起動
禁止: Repository 全体探索（全ディレクトリ列挙・全文検索）
禁止: Scope 外ファイルの探索
禁止: Architecture 全体調査（Architecture 変更を伴わない PR での全体調査）
禁止: PR 外実装（次 PR を先取りする実装）
禁止: 推測による Scope 外実装
禁止: AI_EXECUTION.md を読まずに実装を開始する
禁止: Agent tool を PR 処理中に任意の目的で起動する
```

---

## 標準プロンプト

以下のいずれかで PR を開始できる。

```
PR-XXX を開始してください。
```

または

```
PR-XXX を開始してください。

このリポジトリの CLAUDE.md に従って実装してください。
```

Claude Code はこれを受け取ったら、CLAUDE.md → AI_EXECUTION.md の順に読み、
Execution Mode を決定してから実装を開始する。

---

## 参照先

- `AI_EXECUTION.md` — 実行モード・Validation・実装ルール・レポート形式（次に読む）
- `[HANDOFF_PATH]` — 前 PR からの引き継ぎ情報

---

> **Exported from:** Founder Operating System
> **Template version:** v1.0 | 2026-07-02
> **Template source:** `development-os/app-runtime/CLAUDE_TEMPLATE.md`
