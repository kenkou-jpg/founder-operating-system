# FOUNDER_OS_REFERENCE

> External Repository Mapping v1.0
> Execution Dispatcher が Founder Operating System を決定論的に参照するための唯一の起点。
> Claude Code は Founder OS を探してはいけない。必ずこのファイルを起点として参照する。

---

## Purpose

Founder Operating System は IPPO リポジトリには存在しない。
独立した Repository として管理されており、IPPO とは別のリポジトリ構造を持つ。

Execution Dispatcher はこの文書を唯一の参照元とする。
Claude Code が Founder OS のファイルを探索・検索することは禁止する。

---

## Repository Mapping

| OS / Component | Repository | Branch | Purpose |
|---------------|-----------|--------|---------|
| **Founder Operating System（全体）** | 独立 Repository（IPPO とは別管理）| `master` | Founder の全 OS を統合管理 |
| **Development OS** | 同上 | `master` | 開発標準・アーキテクチャ方針 |
| **PR Generator OS** | 同上 | `master` | PR 単位開発の標準化・テンプレート |
| **Execution Dispatcher** | 同上 `development-os/pr-generator-os/00_EXECUTION_DISPATCHER.md` | `master` | PR 開始時の Mode 決定エントリポイント |
| **MODE_SELECTION_MATRIX** | 同上 `development-os/pr-generator-os/MODE_SELECTION_MATRIX.md` | `master` | ルールベース Mode 決定マトリクス |
| **Optimization Pack** | 同上 `development-os/pr-generator-os/` | `master` | SMART_DOCUMENT_LOADING / TOKEN_OPTIMIZATION / REPORT_OPTIMIZATION |
| **Founder Workflow OS** | 同上 `founder-workflow-os/` | `master` | Founder の業務フロー・Stage 管理 |
| **Progress Registry** | 同上 `founder-workflow-os/08_PROGRESS_REGISTRY.md` | `master` | 現在地管理（Live Progress + Milestone History）|
| **Decision Log** | 同上 `founder-workflow-os/09_DECISION_LOG.md` | `master` | Founder 判断履歴（Append-Only）|
| **Analytics OS** | 同上 `analytics-os/` | `master` | Founder OS 成熟度・使用率の定量管理 |
| **Analytics Current State** | 同上 `analytics-os/os-metrics/CURRENT_STATE.md` | `master` | Analytics Snapshot First の起点 |
| **Governance** | 同上 `governance/` | `master` | CHANGELOG / BINDING_DECISIONS / ADR |
| **CANONICAL_SOURCE** | 同上 `CANONICAL_SOURCE.md` | `master` | 文書ヒエラルキーの定義 |

---

## Reference Rules

### Claude Code への禁止事項

```
禁止: Founder OS を検索・探索する
禁止: リポジトリ構造を推測する
禁止: IPPO リポジトリ内で Founder OS を探す
禁止: このファイルを無視して直接 OS ファイルを読む
```

### Claude Code への必須事項

```
必須: PR 開始時に必ずこのファイルを確認する
必須: 必要なファイルのパスをこのファイルから特定する
必須: Execution Dispatcher → MODE_SELECTION_MATRIX の順番で読む
必須: 不要なファイルは読まない（TOKEN_OPTIMIZATION.md に従う）
```

---

## Loading Rules（PR タイプ別）

### 通常 PR（FAST / STANDARD）

```
FOUNDER_OS_REFERENCE.md（このファイル）
  ↓
Execution Dispatcher（00_EXECUTION_DISPATCHER.md）
  ↓
MODE_SELECTION_MATRIX.md（FAST / STANDARD / FULL を決定）
  ↓
Optimization Pack（SMART_DOCUMENT_LOADING → TOKEN_OPTIMIZATION → REPORT_OPTIMIZATION）
  ↓
必要最小限の文書のみ読む
  ↓
Implementation → Completion Report → Progress Registry → Decision Log 判定
  ↓
終了
```

### FULL PR（Architecture / Migration / Release / Phase完了 / Wave完了）

```
FOUNDER_OS_REFERENCE.md（このファイル）
  ↓
Execution Dispatcher（00_EXECUTION_DISPATCHER.md）
  ↓
MODE_SELECTION_MATRIX.md（FULL 決定）
  ↓
FULL_MODE.md（必須 Validation すべて実施）
  ↓
SMART_DOCUMENT_LOADING.md の FULL ロードルールに従い必要文書を読む
  ↓
Progress Registry Milestone History 更新
  ↓
Decision Log 更新条件確認
  ↓
Founder 承認フロー
  ↓
終了
```

### 週次レビュー

```
FOUNDER_OS_REFERENCE.md（このファイル）
  ↓
analytics-os/os-metrics/CURRENT_STATE.md（Snapshot First）
  ↓
analytics-os/os-metrics/CONTEXT_LOADER.md（必要ファイルを決定）
  ↓
週次レビュー実施
  ↓
CURRENT_STATE.md 更新
  ↓
終了
```

---

## External Repository と IPPO の関係

| リポジトリ | 役割 | 変更可否 |
|-----------|------|---------|
| **Founder Operating System** | Founder の OS・標準・テンプレートを管理 | Claude Code が更新可（OS 更新時）|
| **IPPO** | プロダクト実装・Governing Documents を管理 | IPPO 開発 PR 時のみ更新可 |

**IPPO リポジトリへの変更は IPPO の PR 作業時のみ。Founder OS 作業で IPPO を変更してはいけない。**

---

## Dispatcher Version

```
Execution Dispatcher Version: v0.4.3（MODE_SELECTION_MATRIX 対応）
External Repository Mapping Version: v1.0
Last Updated: 2026-06-30
```
