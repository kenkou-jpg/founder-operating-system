# APP_RUNTIME_CHECKLIST

> 新規アプリ作成時の App Runtime Export チェックリスト。
> すべての項目を確認してから PR を開始する。

---

## Phase 1 — Runtime ファイル生成

```
□ CLAUDE.md 作成
    テンプレート: development-os/app-runtime/CLAUDE_TEMPLATE.md
    配置先: [APP_REPO]/CLAUDE.md
    確認: [APP_NAME] に置き換えた か
    確認: [HANDOFF_PATH] をアプリの実際のパスに置き換えたか
    確認: テンプレートのコメント行（> で始まる行）を削除したか

□ AI_EXECUTION.md 作成
    テンプレート: development-os/app-runtime/AI_EXECUTION_TEMPLATE.md
    配置先: [APP_REPO]/AI_EXECUTION.md
    確認: [APP_NAME] に置き換えたか
    確認: [HANDOFF_PATH] をアプリの実際のパスに置き換えたか
    確認: [APP_SPECIFIC_LEGACY_RULE] をアプリ固有ルールに置き換えたか
    確認: テンプレートのコメント行（> で始まる行）を削除したか
```

---

## Phase 2 — HANDOFF 確認

```
□ HANDOFF 作成
    アプリの引き継ぎ情報ファイルが存在することを確認する
    存在しない場合は Founder に確認してから Runtime を配置する
    HANDOFF パスを CLAUDE.md / AI_EXECUTION.md に正しく記載したか確認する

□ HANDOFF に以下が含まれているか確認
    □ 直近完了 PR の情報
    □ 次 PR の情報
    □ 直接依存ファイルのパス
    □ 現在の Phase / Wave 情報
```

---

## Phase 3 — Runtime 動作確認

```
□ Startup 確認
    「PR-001 を開始してください。」と入力したとき
    → CLAUDE.md を最初に読むか
    → AI_EXECUTION.md を次に読むか
    → HANDOFF を読むか
    → 外部 Founder OS を読みに行っていないか

□ Repository Exploration 確認
    PR 開始時に Background Research Agent が起動していないか
    Repository 全体探索が発生していないか
    Broad grep が走っていないか
    Scope 外ファイルを読んでいないか

□ Background Agent 禁止確認
    Agent tool が呼ばれていないか
    「理解のため」「念のため」の探索が発生していないか

□ Token Optimization 確認
    Startup Sequence で既読ファイルが再読されていないか
    Documents Loaded が HANDOFF + PR Scope + 直接依存ファイルに限定されているか
    Validation 出力が PASS / FAIL + 理由 1 行になっているか
```

---

## Phase 4 — PR Generator 確認

```
□ PR Generator 確認
    Execution Mode（FAST / STANDARD / FULL）が正しく選択されているか
    Validation 4 種（Responsibility / Roadmap / Scope / BD Compliance）が実施されているか
    Completion Report が AI_EXECUTION.md の Report Optimization 形式に従っているか
    Progress Update（HANDOFF 更新）が PR 完了時に実施されているか

□ Runtime Export 完了
    CLAUDE.md がリポジトリ直下に配置されているか
    AI_EXECUTION.md がリポジトリ直下に配置されているか
    APP_RUNTIME_POLICY.md の Rule 1〜6 に準拠しているか
    Founder OS は変更していないか（変更禁止）
```

---

## 完了確認

```
□ 上記すべてにチェックが入ったことを確認した

Runtime Export 完了。
このアプリは外部 Founder OS を毎 PR で読みに行かずに PR を実行できる。
```

---

## 関連ドキュメント

- `README.md` — App Runtime Export の概要
- `APP_RUNTIME_POLICY.md` — Founder OS 正式ポリシー（Rule 1〜6）
- `CLAUDE_TEMPLATE.md` — CLAUDE.md テンプレート
- `AI_EXECUTION_TEMPLATE.md` — AI_EXECUTION.md テンプレート
