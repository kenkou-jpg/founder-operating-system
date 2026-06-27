# 11 — PR Responsibility Registry

> 各PRの責務を永久管理する文書。
> **PR Scopeの唯一のSSoT（Single Source of Truth）。**
> PRが完了したら必ずここに登録する。削除しない（Append-Only）。

---

## この文書の使い方

1. **PR開始前:** 本PRの責務が既存エントリと衝突していないか確認する
2. **PR完了後:** 完了したPRのエントリを追加する（ステータスを「完了」に更新）
3. **Collision検知:** `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` と併用する

---

## Registry テンプレート

新しいPRを登録するときは以下のテンプレートを使う:

```markdown
### PR-[番号] — [タイトル]

| 項目 | 内容 |
|------|------|
| **ステータス** | 計画中 / 実装中 / 完了 |
| **タイプ** | Domain / Repository / Infrastructure / Event / API / UI / Analytics / AI / Research / Governance / Migration |
| **責務** | （一言で：このPRが「何を」担当するか） |
| **Wave / Phase** | |
| **入力（前提とするもの）** | |
| **出力（後続PRが使うもの）** | |
| **依存PR** | PR-XXX（完了済みであること）|
| **次PR** | PR-XXX |

**追加してよいもの:**
- （このPRで追加・作成できるもの）

**追加禁止:**
- （このPRで追加してはいけないもの）

**変更禁止:**
- （このPRで変更してはいけないファイル・クラス）

**削除禁止:**
- （このPRで削除してはいけないもの）

| フラグ | 値 |
|-------|-----|
| Repository担当 | YES / NO |
| Migration担当 | YES / NO |
| Event担当 | YES / NO |
| API担当 | YES / NO |
| UI担当 | YES / NO |
| AI担当 | YES / NO |
| DB担当 | YES / NO |
| DI担当 | YES / NO |
```

---

## Registry — IPPO（実例）

### PR-041 — NetworkSignal Repository V2: Interface / Adapter / Factory

| 項目 | 内容 |
|------|------|
| **ステータス** | 完了 |
| **タイプ** | Repository |
| **責務** | Repository Interface・Adapter・Factory・Persistence・Migrationの定義 |
| **Wave / Phase** | Wave 2 / Phase 6 |
| **入力** | 既存NetworkSignal Domain |
| **出力** | `INetworkSignalRepository` Interface / `NetworkSignalSupabaseAdapter` / `NetworkSignalRepositoryFactory` |
| **依存PR** | PR-040（完了済み）|
| **次PR** | PR-042 |

**追加してよいもの:**
- Repository Interface（`INetworkSignalRepository`）
- Repository Adapter（Supabase実装）
- Repository Factory
- Persistence Service
- Migration（PR-041スコープ内のもの）

**追加禁止:**
- Supabase Repository の本番投入（PR-042担当）
- Domain変更
- UI変更

**変更禁止:**
- 既存のDomain Entity
- 既存のScreen

**削除禁止:**
- 既存のNetworkSignal実装

| フラグ | 値 |
|-------|-----|
| Repository担当 | YES |
| Migration担当 | YES |
| Event担当 | NO |
| API担当 | NO |
| UI担当 | NO |
| AI担当 | NO |
| DB担当 | YES（スキーマ定義のみ）|
| DI担当 | YES（Factory登録）|

---

### PR-042 — Supabase Persistence Foundation

| 項目 | 内容 |
|------|------|
| **ステータス** | 完了 |
| **タイプ** | Infrastructure / Repository |
| **責務** | SupabaseRepository本番投入・Factory切替・EventStore |
| **Wave / Phase** | Wave 2 / Phase 7 |
| **入力** | PR-041の Interface / Adapter / Factory |
| **出力** | 本番動作するSupabase永続化 / `NetworkSignalPersistenceServiceV2` |
| **依存PR** | PR-041（完了済み）|
| **次PR** | PR-043 |

**追加してよいもの:**
- Supabase Repository（本番版）
- Factory切替（Mock → Supabase）
- EventStore実装

**追加禁止:**
- Repository Interface（PR-041担当、完了済み）
- Domain追加
- UI変更

**変更禁止:**
- `INetworkSignalRepository` Interface
- 既存Domain Entity

**削除禁止:**
- Mock Repository（切替可能な状態で保持）

| フラグ | 値 |
|-------|-----|
| Repository担当 | YES（本番投入）|
| Migration担当 | NO |
| Event担当 | YES（EventStore）|
| API担当 | NO |
| UI担当 | NO |
| AI担当 | NO |
| DB担当 | YES（実装）|
| DI担当 | YES（Factory切替）|

---

### PR-043 — Emotion Signal Generation Foundation

| 項目 | 内容 |
|------|------|
| **ステータス** | 完了 |
| **タイプ** | Domain / AI（Rule Engine）|
| **責務** | EmotionSignal RuleエンジンとGenerator基盤 |
| **Wave / Phase** | Wave 2 / Phase 7 |
| **入力** | PR-042の永続化基盤 |
| **出力** | `EmotionSignalRuleEngine` / `EmotionSignalGenerator` / `initializeSession` |
| **依存PR** | PR-042（完了済み）|
| **次PR** | PR-044 |

**追加してよいもの:**
- EmotionSignal RuleEngine
- EmotionSignalGenerator
- initializeSession
- 基本Emotionルール定義

**追加禁止:**
- MenstrualPhase関連（PR-044担当）
- Disease / Similarity Signal（後続PR担当）
- Repository変更

**変更禁止:**
- PR-041/042で確立したRepository層

**削除禁止:**
- 既存のEmotionSignal定義（あれば）

| フラグ | 値 |
|-------|-----|
| Repository担当 | NO |
| Migration担当 | NO |
| Event担当 | NO |
| API担当 | NO |
| UI担当 | NO |
| AI担当 | YES（Ruleエンジン）|
| DB担当 | NO |
| DI担当 | NO |

---

### PR-044 — MenstrualPhase Auto-Resolution（計画中）

| 項目 | 内容 |
|------|------|
| **ステータス** | 計画中 |
| **タイプ** | Domain / Event / API |
| **責務** | MenstrualPhaseの自動解決・EmotionSignal統合・API公開 |
| **Wave / Phase** | Wave 2 / Phase 8 |
| **入力** | PR-043の EmotionSignalGenerator / PR-042の PersistenceServiceV2 |
| **出力** | `MenstrualPhaseResolver` / 統合済み EmotionSignalGenerator / APIエンドポイント |
| **依存PR** | PR-043（完了済み）|
| **次PR** | PR-045 |

**追加してよいもの:**
- `MenstrualPhaseResolver`
- EmotionSignalGeneratorへのMenstrualPhase統合
- EventBus経由の発火
- APIエンドポイント
- DI Token登録

**追加禁止:**
- Repository Interface新設（PR-041完了済み）
- Supabase Migration追加（PR-042完了済み）
- AI/LLM使用
- Disease Signal（後続PR担当）
- Similarity Signal（後続PR担当）

**変更禁止:**
- `app-legacy.js`
- PR-041の Repository Interface
- PR-042の Migration

**削除禁止:**
- 既存のEmotionSignalルール

| フラグ | 値 |
|-------|-----|
| Repository担当 | NO |
| Migration担当 | NO |
| Event担当 | YES |
| API担当 | YES |
| UI担当 | NO |
| AI担当 | NO（ルールベース）|
| DB担当 | NO |
| DI担当 | YES |

---

## Registry — 新規プロジェクト用テンプレート

新しいプロジェクトを始めるとき、このセクションを複製して使用してください。

### [Project Name] — PR Registry

（最初のPRから順に追記していく）

---

## 運用ルール

1. **PR開始前に必ず確認する** — 既存エントリの `追加禁止` / `変更禁止` と照合する
2. **PR完了後に必ず追記する** — ステータスを「完了」に更新する
3. **削除しない（Append-Only）** — 廃止されたPRはステータスを「廃止」にする
4. **このファイル自体がSSoT** — 他の場所と矛盾する場合はここが正

---

## 責務衝突の発見

このRegistryを読んで以下を確認する:

- **同じInterfaceを2つのPRが作ろうとしていないか**
- **同じMigrationを2つのPRが持っていないか**
- **前PRで「追加禁止」のものを本PRが追加しようとしていないか**
- **後PRの責務を本PRが先取りしていないか**

衝突を発見したら `12_RESPONSIBILITY_COLLISION_CHECKLIST.md` で詳細確認する。
