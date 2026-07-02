# App Runtime Export

> Founder Operating System から各アプリ向けの Lightweight Execution Runtime を生成する仕組み。

---

## Runtime とは何か

App Runtime は、各アプリのリポジトリに配置する **軽量 AI 実行環境** です。

```
CLAUDE.md       ← Claude Code のエントリポイント
AI_EXECUTION.md ← PR 実行ルールの軽量版
```

この 2 ファイルを読めば、Claude Code は外部 Founder OS を参照せずに PR を完遂できます。

---

## Founder OS との役割分担

| | Founder Operating System | App Runtime |
|---|---|---|
| **役割** | Canonical Source / 原本 / テンプレート | Execution Runtime / 実行環境 |
| **配置場所** | `founder-operating-system/` リポジトリ | 各アプリのリポジトリ直下 |
| **更新タイミング** | OS 改善・ポリシー追加時 | Founder OS が更新された場合のみ |
| **読み込みタイミング** | Runtime Export 生成時 / OS 更新時 | 毎 PR（CLAUDE.md → AI_EXECUTION.md）|
| **内容** | 完全版ルール・テンプレート・マトリクス | PR 実行に必要なルールのみ |

**Founder OS は削除・廃止しない。Canonical Source として維持する。**

---

## Export の考え方

Founder OS は「何をすべきか」の原本。App Runtime は「どう実行するか」の軽量版。

```
Founder Operating System（原本）
  ↓ Export
App Runtime（CLAUDE.md + AI_EXECUTION.md）
  ↓ 配置
Application Repository
  ↓ 毎 PR
Claude Code が読み込み → PR 実行
```

Export の基準:
- Founder OS の **全ファイルを読ませない**
- PR 実行に直接必要なルールのみを移植する
- アプリ固有の情報（HANDOFF パス等）はアプリに合わせて調整する
- 品質ルール（Validation 4種・Test Rule・Report形式）は省略しない

---

## 適用対象

| アプリ | 状態 |
|-------|------|
| IPPO | Runtime 適用済み（v1.0） |
| AgriPath | 立ち上げ時に生成 |
| Fasting App | 立ち上げ時に生成 |
| Imaging Agriculture | 研究 PR 管理に適用予定 |
| 新規 SaaS | テンプレートから即時生成 |

---

## 利点

1. **トークン削減** — 毎 PR で Founder OS 全体を読む必要がなくなる（推定 -6,000〜38,000 tokens / PR）
2. **起動高速化** — CLAUDE.md → AI_EXECUTION.md の 2 ファイルで PR 開始可能
3. **標準化** — すべてのアプリが同じ品質基準で PR を実行できる
4. **独立性** — アプリ側のリポジトリが Founder OS リポジトリに依存しない
5. **拡張性** — 新規アプリを追加するたびにテンプレートから即時生成

---

## ファイル構成

```
development-os/app-runtime/
├── README.md                  ← このファイル
├── APP_RUNTIME_POLICY.md      ← Founder OS 正式ポリシー
├── CLAUDE_TEMPLATE.md         ← CLAUDE.md のテンプレート
├── AI_EXECUTION_TEMPLATE.md   ← AI_EXECUTION.md のテンプレート
└── APP_RUNTIME_CHECKLIST.md   ← 新規アプリ作成時のチェックリスト
```

---

## 関連ドキュメント

- `APP_RUNTIME_POLICY.md` — App Runtime Export の正式ポリシー（Rule 1〜6）
- `CLAUDE_TEMPLATE.md` — 新規アプリの CLAUDE.md テンプレート
- `AI_EXECUTION_TEMPLATE.md` — 新規アプリの AI_EXECUTION.md テンプレート
- `APP_RUNTIME_CHECKLIST.md` — 新規アプリ作成チェックリスト
- `FOUNDER_OS_REFERENCE.md` — Founder OS の External Repository Mapping
