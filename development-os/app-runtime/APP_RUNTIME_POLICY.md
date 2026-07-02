# APP_RUNTIME_POLICY

> Founder Operating System — App Runtime Export の正式ポリシー。
> Version: v1.0 | 2026-07-02

---

## Purpose

各アプリが Founder OS に毎 PR 依存することなく、独立した AI 実行環境を持つための標準化ポリシー。
Founder OS は Canonical Source として維持しつつ、各アプリには Lightweight Runtime を配置する。

---

## Rule 1 — 新規アプリ作成時は必ず Runtime を生成する

```
新しいアプリ（リポジトリ）を作成するとき、必ず以下を生成してそのリポジトリ直下に配置する。

  CLAUDE.md        ← Claude Code のエントリポイント
  AI_EXECUTION.md  ← PR 実行ルールの軽量版

テンプレート: development-os/app-runtime/CLAUDE_TEMPLATE.md
             development-os/app-runtime/AI_EXECUTION_TEMPLATE.md

チェックリスト: development-os/app-runtime/APP_RUNTIME_CHECKLIST.md
```

---

## Rule 2 — Founder OS は Canonical Source である

```
Founder Operating System は唯一の正本（Canonical Source）として維持する。

- App Runtime は Founder OS の「コピー」ではなく「Export」である
- App Runtime が Founder OS の代替・代用になることはない
- Founder OS の更新は引き続き Founder OS リポジトリで行う
- App Runtime の内容が古くなった場合は、Founder OS を参照して再 Export する

Founder OS を廃止・削除してはいけない。
```

---

## Rule 3 — 各アプリは Lightweight Runtime を利用する

```
各アプリは、PR 実行時に以下の順序で AI を起動する。

  CLAUDE.md（エントリポイント）
    ↓
  AI_EXECUTION.md（実行ルール）
    ↓
  HANDOFF（アプリ固有の引き継ぎ情報）
    ↓
  PR Scope・依存ファイル・テスト
    ↓
  Implementation → Completion Report

外部 Founder OS を毎 PR で読み込む設計にしてはいけない。
```

---

## Rule 4 — 通常 PR では外部 Founder OS を毎回読みに行かない

```
通常の PR 実行（FAST / STANDARD / FULL）では、
アプリのリポジトリ内にある CLAUDE.md と AI_EXECUTION.md のみを使用する。

外部 Founder OS を読みに行くのは以下の場合のみ:
  - AI_EXECUTION.md の更新が必要と判断した場合（Founder 承認後）
  - Founder OS 自体の更新作業を行う場合
  - Founder OS と App Runtime の整合性確認が必要な場合（Phase完了 / Wave完了 時）

通常 PR でのルール: AI_EXECUTION.md に記載されていない判断 → Founder に確認。Founder OS を自己判断で読みに行かない。
```

---

## Rule 5 — Founder OS が更新された場合のみ Runtime Export を更新する

```
App Runtime は自動的に更新されない。以下のタイミングで更新を検討する。

  更新を検討するタイミング:
    □ Founder OS のメジャー / マイナーバージョンアップ（CHANGELOG 参照）
    □ Execution Mode の定義変更
    □ Validation ルールの変更
    □ Report Optimization の形式変更
    □ Background Agent 禁止ポリシーの変更

  更新しなくてよいタイミング:
    □ Founder OS の PATCH 更新（誤字修正・補足追記）
    □ Founder OS 固有のファイル追加（アプリ Runtime に影響しない変更）

更新判断は Founder が行う。App Runtime の自己書き換えは禁止。
```

---

## Rule 6 — App Runtime は Founder OS の要約ではなく Execution Runtime である

```
App Runtime は Founder OS の「要約」「抜粋」「ダイジェスト」ではない。

App Runtime は:
  - PR を実行するための最小限の実行ルールを持つ
  - Execution Mode（FAST / STANDARD / FULL）を定義する
  - Validation・Test・Report の形式を定義する
  - Repository Exploration Policy を内包する
  - アプリ固有の HANDOFF パス・Roadmap 参照先を明記する

App Runtime は Founder OS の品質ルールを下げてはいけない。
Execution の品質は Founder OS と同等水準を維持する。
```

---

## Enforcement

このポリシーに違反した場合:

```
1. 外部 Founder OS を毎 PR で読み込んでいる → CLAUDE.md の Startup Rule を確認し修正する
2. App Runtime なしでアプリを立ち上げた → APP_RUNTIME_CHECKLIST.md に従い Runtime を生成する
3. Founder OS を削除・廃止しようとした → 禁止。Founder に確認する
4. App Runtime の品質を Founder OS より低く設定した → AI_EXECUTION_TEMPLATE.md に従い再生成する
```

---

## 関連ドキュメント

- `README.md` — App Runtime Export の概要
- `CLAUDE_TEMPLATE.md` — CLAUDE.md テンプレート
- `AI_EXECUTION_TEMPLATE.md` — AI_EXECUTION.md テンプレート
- `APP_RUNTIME_CHECKLIST.md` — 新規アプリ作成チェックリスト
- `FOUNDER_OS_REFERENCE.md` — Founder OS の Canonical Source 定義
