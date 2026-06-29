# 09 — Decision Log

> Founder の重要判断を Append-Only で記録する。
> この文書は Binding Decision ではありません。
> 将来的に Council や Binding Decision に昇格する判断の候補を保存する場所です。

---

## Purpose

Decision Log は以下の目的のために存在します。

1. **Founder判断を残す** — 「なぜそう決めたか」を記録し、記憶に頼らないようにする
2. **判断の理由を残す** — 状況・制約・代替案を記録して判断の文脈を保存する
3. **後から判断を再評価できるようにする** — 時間が経ってから見直し、改善できる
4. **次のアプリへ知見を移す** — 同じ判断ミスを繰り返さないための知識資産にする
5. **Council化すべき判断を見つける** — 繰り返し登場する判断パターンを発見する

---

## Non-goals

Decision Log は以下を行いません。

- ❌ Binding Decision を直接変更しない（`governance/BINDING_DECISIONS.md` が正）
- ❌ Governing Document を上書きしない
- ❌ Product Roadmap を変更しない（ippo リポジトリ内の ROADMAP.md が正）
- ❌ Architecture を変更しない（ippo リポジトリ内の ARCHITECTURE.md が正）
- ❌ Legal 判断を代替しない（`legal-os/` が定義）
- ❌ 医療判断を代替しない
- ❌ IPPO の Governing Documents の権限を持たない

**この文書への記録は、設計・実装・ロードマップを変えません。**
**変更が必要な場合は、各 Governing Document を直接更新してください。**

---

## Decision Log Template

```
### DLOG-XXX — [タイトル]

Decision ID: DLOG-XXX
Date: YYYY-MM-DD
Project: Founder OS / IPPO / AgriPath / All
Category: OS Design / Development / Business / Legal / Portfolio / Workflow
Decision: （1〜3文で判断内容を記述）
Context: （判断が必要になった背景・状況）
Reason: （なぜその判断をしたか）
Alternatives Considered: （検討したが採用しなかった選択肢）
Impact: （この判断がもたらす影響）
Related Documents: （関連するファイルパス）
Related PRs: （関連する PR 番号、なければ "—"）
Requires Council? yes / no
Requires Founder Approval? yes / no
Review Date: YYYY-MM（見直し推奨時期）
Status: Active / Superseded / Archived
```

---

## Initial Decisions

### DLOG-001 — Founder OS を独立リポジトリとして管理する

```
Decision ID: DLOG-001
Date: 2026-06-27
Project: Founder OS
Category: OS Design
Decision: Founder Operating System は IPPO リポジトリではなく、
          独立リポジトリ（founder-operating-system）として管理する。
Context: IPPO の開発を進める中で、PR開発プロセス・ライフサイクル・
         運営基準を体系化する必要が生じた。
Reason: Founder OS は IPPO 固有の資産ではなく、AgriPath・Fasting App・
        Imaging Agriculture など全アプリ共通の運営・開発 OS だから。
        IPPO リポジトリに混在させると、将来のアプリへの転用が困難になる。
Alternatives Considered:
  - IPPO リポジトリ内の docs/ に統合（→ IPPO 固有資産になるため却下）
  - Notion / esa などの外部ツール（→ Git 管理・バージョン管理ができないため却下）
Impact: Founder OS の知見が全アプリで再利用可能になる。
        IPPO の Governing Documents との分離が明確になる。
Related Documents: README.md, CANONICAL_SOURCE.md
Related PRs: —
Requires Council? no
Requires Founder Approval? yes（完了）
Review Date: 2027-06
Status: Active
```

---

### DLOG-002 — PR Generator OS を全アプリ共通の Development OS として管理する

```
Decision ID: DLOG-002
Date: 2026-06-27
Project: Founder OS
Category: OS Design
Decision: PR Generator OS は IPPO 専用ではなく、全アプリ共通の
          Development OS として development-os/pr-generator-os/ に管理する。
Context: IPPO の PR 開発を標準化するために PR Generator OS を作成したが、
         AgriPath・Fasting App でも同じ課題（PRスコープ衝突・責務曖昧）が
         起きることが予測された。
Reason: PR単位開発の品質管理は全プロジェクトで共通の課題であり、
        テンプレート化することで次のアプリの立ち上げコストを削減できるため。
Alternatives Considered:
  - IPPO リポジトリ内に置く（→ 再利用不可になるため却下）
  - プロジェクトごとに別々のファイルを作る（→ メンテナンスコストが増大するため却下）
Impact: AgriPath / Fasting App のPR開発時に即座に再利用可能になる。
        PR Generator OS の改善が全プロジェクトに波及する。
Related Documents: development-os/pr-generator-os/README.md
Related PRs: —
Requires Council? no
Requires Founder Approval? yes（完了）
Review Date: 2027-06
Status: Active
```

---

### DLOG-003 — Council Generator OS / Architecture Generator OS / Workflow Automation は後回しにする

```
Decision ID: DLOG-003
Date: 2026-06-28
Project: Founder OS
Category: OS Design / Portfolio
Decision: Founder Workflow OS は v0.1 で完成とし、
          Council Generator OS / Architecture Generator OS / Workflow Automation は
          IPPO PR-044〜075 完了後に着手する。
Context: Founder OS の設計が一通り固まった時点で、追加機能の候補として
         Council Generator OS / Architecture Generator OS / Workflow Automation が
         挙がった。
Reason: Workflow は 01〜07 で十分機能する状態になっている。
        Council / Architecture / Automation は実運用（IPPO PR-044〜）で
        追加知見を得てから作る方が、実態に即した設計になる。
        今作っても机上の空論になるリスクがある。
Alternatives Considered:
  - 今すぐ全部作る（→ IPPO 開発が停滞するため却下）
  - Workflow Automation だけ先に作る（→ 実運用データなしに自動化対象を定めるのは時期尚早）
Impact: IPPO PR-044〜075 に集中できる。
        Founder OS の作り込みが本来の開発を妨げない。
Related Documents: founder-workflow-os/README.md, ROADMAP.md
Related PRs: —
Requires Council? no
Requires Founder Approval? yes（完了）
Review Date: 2026-12（IPPO Wave2 完了後）
Status: Active
```

---

### DLOG-004 — Progress Registry と Decision Log を作成したら IPPO 開発へ戻る

```
Decision ID: DLOG-004
Date: 2026-06-28
Project: Founder OS / IPPO
Category: Portfolio / Workflow
Decision: Progress Registry（08）と Decision Log（09）を作成したら、
          Founder OS の作業を一時停止し、IPPO PR-044 の実装に戻る。
Context: Founder OS を整備することで IPPO 開発の安全性と再現性が高まる一方、
         OS 整備に時間をかけすぎると IPPO 本来の開発が停滞する。
Reason: Founder OS の作り込みが IPPO 本来の開発を妨げないようにするため。
        次の最優先は IPPO PR-044〜075。
        OS は IPPO 開発の合間に継続的に改善する。
Alternatives Considered:
  - Council Generator OS も今回作る（→ DLOG-003 で却下済み）
  - Progress Registry だけ作って Decision Log は省略する
    （→ 判断履歴の紛失リスクがあるため却下）
Impact: IPPO Wave2 の開発が再開できる。
        Progress Registry により、IPPO 現在地の確認コストがゼロになる。
Related Documents: 08_PROGRESS_REGISTRY.md
Related PRs: PR-044
Requires Council? no
Requires Founder Approval? yes（完了）
Review Date: 2026-09
Status: Active
```

---

### DLOG-005 — Progress Registry と Decision Log は IPPO Governing Documents ではない

```
Decision ID: DLOG-005
Date: 2026-06-28
Project: Founder OS / IPPO
Category: OS Design / Governance
Decision: Progress Registry（08）と Decision Log（09）は、
          IPPO の設計・ロードマップ・Architecture を変更しない。
          これらは Founder OS 側の状態管理・記録文書であり、
          IPPO の Governing Documents には属さない。
Context: Founder OS に追加された文書が IPPO の設計に影響を与えないことを
         明確に定義する必要があった。
Reason: 状態管理と意思決定記録は Founder OS 側のドキュメントであり、
        IPPO の Governing Documents（ARCHITECTURE.md / BINDING_DECISIONS.md /
        ROADMAP.md 等）とは別の権限体系に属するため。
Alternatives Considered:
  - IPPO リポジトリ内に Progress Registry を置く
    （→ IPPO 固有資産になり他アプリへ転用できないため却下）
Impact: IPPO の設計・ロードマップ・Architecture は変更されない。
        Progress Registry / Decision Log はあくまで記録・参照文書として機能する。
Related Documents: CANONICAL_SOURCE.md, governance/BINDING_DECISIONS.md
Related PRs: —
Requires Council? no
Requires Founder Approval? yes（完了）
Review Date: 2027-06
Status: Active
```

---

## Update Rule（更新条件）

Decision Log は以下のいずれかに該当した場合のみ更新する。

```
□ Roadmap 変更
□ Architecture 変更
□ Governing Document 変更
□ Business Strategy 変更
□ Founder Strategy 変更
□ 新しい OS 追加
□ 新しいテンプレート追加
□ Binding Decision 候補
```

**上記以外は Decision Log 更新禁止。**

日常的な PR 開発・実装作業・バグ修正・リファクタリングは
Decision Log を更新しない。

---

### DLOG-006 — Founder Capability OS 構想を Wave2 完了後の設計候補として記録する

```
Decision ID: DLOG-006
Date: 2026-06-29
Project: Founder Operating System
Category: Future OS / Founder Capability
Decision: Founder Growth OS ではなく Founder Capability OS として、
          Wave2 完了後に設計候補として扱う。
          Wave2 期間中は Founder OS Freeze Rule により実装禁止。
          本エントリはその記録のみ行う。

Context: Founder が在宅収入・副業・仕事選びを検討する中で、
         「仕事で得た能力を IPPO や将来アプリへ還元する仕組み」が必要になった。
         これは一般的なキャリア管理ではなく、Founder が自社プロダクトに必要な能力を
         意図的に獲得し、事業へ移転し、Founder OS へ標準化する仕組みである。

Reason: このOSが管理する対象は「成長」そのものではなく、
        SEO / UX / SaaS運営 / KPI分析 / コンテンツ / オンボーディング /
        価格設計 / 継続率改善などの具体的な Capability であるため。
        そのため Founder Growth OS ではなく Founder Capability OS という名称が適切。

Core Concept:
  仕事
  ↓ 学んだこと
  ↓ IPPO へ適用
  ↓ 効果測定
  ↓ Founder OS へ標準化
  ↓ 次のアプリへ再利用

Planned Structure (post-Wave2 設計候補):
  Founder Capability OS
  ├── Capability Map
  ├── Learning Strategy
  ├── Work Selection Framework
  ├── Skill Transfer Framework
  ├── Knowledge Management
  ├── Reflection System
  └── Capability KPI

Important Principle:
  「この仕事は、自社プロダクトのどの能力を伸ばすのか？」という基準で仕事を選ぶ。

Initial Capability Map:
  - SEO: 集客・記事・検索流入
  - UX: 継続率・オンボーディング
  - KPI: ダッシュボード・改善判断
  - Content: note・LP・教育コンテンツ
  - Onboarding: 初回体験・ヘルプ・離脱防止
  - Pricing: Premium設計・収益化
  - Customer Success: 問い合わせ・ユーザー理解
  - Research: 市場調査・競合分析
  - Analytics: 行動分析・改善サイクル
  - SaaS Operations: 運営・改善・リリース管理

Alternatives Considered:
  - Founder Growth OS → 「成長」という結果を指すため範囲が広すぎる → 却下
  - Career OS → 一般的なキャリア管理に見え Founder OS の思想とズレる → 却下
  - Learning OS → 学習に寄りすぎ、IPPO や事業への Skill Transfer が弱くなる → 却下

Impact: Wave2 完了後、Founder OS v1.0 以降で設計候補になる。
        IPPO・断食アプリ・Imaging Agriculture・AgriPath など全アプリへ適用可能。
        Founder の仕事選び・学習・事業改善が分断されず、能力獲得が資産化される。

Related Documents:
  - founder-workflow-os/09_DECISION_LOG.md（このファイル）
  - founder-workflow-os/08_PROGRESS_REGISTRY.md
  - Founder OS Freeze Rule（Wave2 期間中は新 OS 実装禁止）
  - template-business-os/README.md
  - brand-os/README.md
  - analytics-os/README.md
  - customer-success-os/README.md

Related PRs: None（Wave2 期間中は実装しない）

Requires Council? yes（Wave2 完了後に実施）
Requires Founder Approval? yes（実装前に承認必須）

Review Date: IPPO Wave2 PR-075 完了後
Status: Deferred / Recorded for post-Wave2 design
```

---

## Review Rule

Decision Log は以下のタイミングで見直してください。

| タイミング | 内容 |
|---------|------|
| **月次** | Status が Active のエントリを確認。Superseded になったものを更新 |
| **PR区切り**（Wave完了時） | 関連する Decision の Impact を実績と照合 |
| **Council前** | Council の議題に関連する Decision を洗い出す |
| **新アプリ開始前** | 過去の Decision から転用可能な知見を抽出する |
| **Founder OS v1.0化前** | すべての Active Decision を棚卸しし、BD化またはアーカイブを決定 |

---

## 関連ドキュメント

- `governance/BINDING_DECISIONS.md` — 拘束力のある決定（BD）の管理場所
- `governance/DECISION_LOG.md` — OS レベルの意思決定記録（こちらはアプリ横断の Founder 判断）
- `08_PROGRESS_REGISTRY.md` — 現在地の記録
- `03_DECISION_CHECKPOINTS.md` — Founder 判断ポイントの定義
