# TOKEN_OPTIMIZATION

> Claude Code のトークン消費を抑える行動規範。
> 5時間制限・コンテキスト上限に対応するため、必要十分な消費量で PR を完遂する。
> 品質低下ではなく、不要な処理の排除が目的。

---

## Must（必ず行う）

```
□ PR 開始時に 00_EXECUTION_DISPATCHER.md を読み、Mode を最初に決める
□ SMART_DOCUMENT_LOADING.md に従い、必要な文書だけ読む
□ 読んだ文書を長文要約しない（Documents Loaded の短い出力のみ）
□ 変更ファイルを PR Scope に絞る
□ 関連テストを先に実行する（全テストより先に影響範囲のテストを動かす）
□ フルテストスイートは FULL_MODE / Phase完了 / Wave完了 時のみ実行
□ エラー時のみ詳細分析を行う（エラーがなければ分析不要）
□ Pre-existing failure は 1行で記録し、深掘りしない
□ Completion Report は REPORT_OPTIMIZATION.md に従って Mode 別に短縮する
□ Progress Registry は Live Progress の更新のみ行う
□ Decision Log は更新条件に該当する場合のみ更新する
```

---

## Must Not（してはいけない）

```
✗ 全 Governing Documents を毎回読む
✗ 全 BD を毎回列挙する
✗ 全過去 PR の完了レポートを再確認する
✗ Completion Report を毎回長文化する
✗ 同じ説明を Completion Report / Progress Registry / Decision Log に重複して書く
✗ Pre-existing failure を毎回深掘り・原因調査する
✗ Scope 外の調査・実装に広げる
✗ PR 中に Founder OS の改善案を実装する（記録のみ可）
✗ Wave2 期間中に新 OS を作る（Founder OS Freeze Rule）
✗ 判断に迷って Scope 外の文書を大量に読む（迷ったら STANDARD_MODE へ）
```

---

## Test Optimization

Mode ごとにテスト実行範囲を絞る。

```
FAST_MODE:
  - 変更した Domain / Service / UseCase の Unit Test
  - 関連する Architecture Guard Test
  - Build（型チェック・Lint）
  - フルスイートは基本不要（Scope が明確な場合）

STANDARD_MODE:
  - 関連テスト（新 Domain / Event / DI の Unit / Integration）
  - Regression subset（変更した Domain に関係するテスト）
  - 必要時 full suite（Phase 中盤の重要 PR）

FULL_MODE:
  - relevant tests + full regression + build
  - Phase / Wave / Release 時は full suite 必須
```

---

## Output Optimization

デフォルト出力は以下の 4 要素にまとめる。

```
Decision: [何を判断したか]
Action:   [何をしたか]
Result:   [結果]
Next:     [次のアクション]
```

詳細が必要な場合のみ Mode 別レポート形式（REPORT_OPTIMIZATION.md）を使う。

---

## 5時間制限への対応方針

| リスク | 対処 |
|-------|------|
| 文書読込でコンテキストが膨らむ | SMART_DOCUMENT_LOADING.md で必要文書のみ読む |
| Completion Report が長くなる | REPORT_OPTIMIZATION.md で Mode 別上限を守る |
| テスト実行に時間がかかる | Test Optimization で関連テストのみ先行実行 |
| 重複説明でトークンを消費する | No Duplicate Reporting（Report / Registry / Log の役割分離） |
| Pre-existing failure の調査に時間をかける | 1行記録のみ、深掘りしない |
| Scope 外の調査に広がる | Dispatcher の Escalation Rule に従い、必要なら Mode 変更のみ |

---

## 関連ドキュメント

- `00_EXECUTION_DISPATCHER.md` — Mode 選択（最初に読む）
- `SMART_DOCUMENT_LOADING.md` — 文書読込ルール
- `REPORT_OPTIMIZATION.md` — レポート最適化
- `FAST_MODE.md` / `STANDARD_MODE.md` / `FULL_MODE.md` — Mode 別必須チェック
