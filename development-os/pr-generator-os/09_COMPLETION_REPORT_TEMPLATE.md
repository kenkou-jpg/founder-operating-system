# 09 — Completion Report Template

> PR完了レポートのテンプレート。
> AIが実装を完了したら、このテンプレートに沿ってレポートを提出する。
> レポートはそのまま `governance/DECISION_LOG.md` やHandoff文書に転記できる品質で書く。

---

```markdown
## PR-[番号] Completion Report
**Project:** [プロジェクト名]
**Title:** [PRタイトル]
**Completed:** [YYYY-MM-DD]
**Wave / Phase:** [Wave X / Phase N]
**Execution Mode:** FAST_MODE / STANDARD_MODE / FULL_MODE
**Mode Reason:** [選択理由を1文]
**Skipped Checks:** [省略したチェック一覧、なければ "None"]
**Escalation:** なし / あり（[元モード] → [新モード]、理由: [内容]）

---

### Execution Metadata

> `00_EXECUTION_DISPATCHER.md` で生成した Execution Metadata をそのまま転記する。

```
## Execution Metadata

Mode:               FAST / STANDARD / FULL
Reason:             [モード選択の根拠]
Dispatcher Version: v0.4
Escalation:         NO / YES
  Previous Mode:    （YES の場合のみ）
  Current Mode:     （YES の場合のみ）
  Escalation Reason:（YES の場合のみ）
Generated At:       YYYY-MM-DD
```

---

### Summary

（1〜3文でPRの成果を要約する。技術的な説明より「何が実現できるようになったか」を書く。）

---

### Scope Verification

- Scope完了: ✅ / ❌
- Non-goals未混入: ✅ / ❌
- Forbidden Changes未変更: ✅ / ❌

---

### Created Files

| ファイルパス | 役割 |
|-----------|------|
| `path/to/file.ts` | 説明 |
| `path/to/file.ts` | 説明 |

（追加ファイルがない場合は「None」）

---

### Updated Files

| ファイルパス | 変更内容 |
|-----------|---------|
| `path/to/file.ts` | 変更の要約 |
| `path/to/file.ts` | 変更の要約 |

（更新ファイルがない場合は「None」）

---

### Deleted Files

| ファイルパス | 削除理由 |
|-----------|---------|
| `path/to/file.ts` | 削除の理由 |

（削除ファイルがない場合は「None」）

---

### Domain Changes

（Domain層への変更サマリー。追加されたEntity / ValueObject / Rule / Service を記録。）

**追加:**
- `ClassName` — 役割の説明

**変更:**
- `ClassName` — 変更内容の説明

**変更なし:** ✅（Domain変更がない場合）

---

### Repository Changes

（Repository層への変更サマリー。Interface / Adapter / Factory の変更を記録。）

**追加:**
- `RepositoryName` — 役割の説明

**変更:**
- `RepositoryName` — 変更内容の説明

**変更なし:** ✅（Repository変更がない場合）

---

### Event Changes

（Event Sourcingへの変更サマリー。追加・変更されたEventを記録。）

**追加:**
- `EventName` — 発火条件と用途

**変更:**
- `EventName` — 変更内容（理由も記録）

**変更なし:** ✅（Event変更がない場合）

---

### API Changes

（APIへの変更サマリー。追加・変更されたエンドポイントを記録。）

**追加:**
- `METHOD /path` — 説明

**変更:**
- `METHOD /path` — 変更内容

**変更なし:** ✅（API変更がない場合）

---

### DI Changes

（DI（依存性注入）設定への変更サマリー。追加・変更されたTokenを記録。）

**追加:**
- `TOKEN_NAME` — 注入されるクラスと用途

**変更:**
- `TOKEN_NAME` — 変更内容

**変更なし:** ✅（DI変更がない場合）

---

### Architecture Guard Changes

（Architecture Guardテストへの変更サマリー。）

**追加:**
- `GuardName` — 検知するルール

**更新:**
- `GuardName` — 更新内容

**変更なし:** ✅（Guard変更がない場合）

---

### Tests Added

| テスト名 | 種別 | 説明 |
|---------|------|------|
| `describe > it` | Unit | テストの説明 |
| `describe > it` | Integration | テストの説明 |

**追加テスト数: X件**

---

### Test Results

```
追加テスト: X件
総テスト数（既存 + 新規）: X件
PASS: X件
FAIL: 0件
Regression: なし ✅

Build: PASS ✅
型チェック: PASS ✅
Lint: PASS ✅
```

---

### Pre-existing Failures

（PR実装前から存在していた失敗テスト。本PRの責任範囲外のもの。）

| テスト名 | 失敗理由 | 担当PR |
|---------|---------|--------|
| | | |

（なければ「None — すべてのテストが本PR前からPASSしていた」）

---

### BD Compliance

| BD番号 | タイトル | 準拠 |
|-------|---------|------|
| BD-XXX | | ✅ |

**BD違反: なし ✅**

---

### Known Limitations

（このPRで解決できなかった既知の問題・制限事項。次PRへの引き継ぎ事項。）

1. 制限内容 — 理由・対応方針

（なければ「None」）

---

### Next PR Inputs

**次PR番号:** PR-[XXX]
**次PRタイトル:** [タイトル]

**引き継ぎ情報:**
- 本PRで追加した `ClassName` を次PRでは `XXX` として使用する
- 本PRで定義した `EventName` を次PRの `SubscriberXXX` が受け取る
- （以下、次PRのAIが把握すべき情報を記載）

**次PRの前提条件:**
- [ ] 本PRのmergeが完了していること
- [ ] [その他の前提条件]

---

### Responsibility Registry Update

以下を `11_PR_RESPONSIBILITY_REGISTRY.md` に追記してください:

```
| PR-[番号] | [タイトル] | [責務の一言要約] | 完了 |
```
```

---

## 使い方

1. AIが実装完了後、このテンプレートの `[]` と `{{}}` を埋めてレポートを提出する
2. Founderはレポートを確認し、`08_DEFINITION_OF_DONE.md` と照合する
3. DoD完全クリアを確認してからPRをmergeする
4. `11_PR_RESPONSIBILITY_REGISTRY.md` を更新する
5. 必要に応じてHandoff文書を更新する
