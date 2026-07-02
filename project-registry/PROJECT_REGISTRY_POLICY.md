# PROJECT_REGISTRY_POLICY

> Founder Operating System（Common OS）と Project Registry の分離ルールを定義する。
> このポリシーに違反する変更は禁止する。

---

## Rule 1 — Common OS にプロジェクト固有 PR を書いてはいけない

```
Founder Operating System 本体（CLAUDE.md / BOOTSTRAP.md / FOUNDER_OS_REFERENCE.md /
development-os / founder-workflow-os / analytics-os など）に、
特定プロジェクトの PR 番号・PR 履歴・実装詳細を記録してはいけない。

プロジェクト固有 PR の記録先:
  → project-registry/[app-name]/PROJECT_PROGRESS.md
```

---

## Rule 2 — Progress Registry は共通の現在地のみ保持する

```
founder-workflow-os/08_PROGRESS_REGISTRY.md が管理するのは以下のみ:

  Current Project:  [プロジェクト名]
  Current Phase:    [Phase]
  Current PR:       [PR 番号]

PR の完了履歴・Milestone 詳細・Scope 変更履歴は Common OS に書かない。

詳細の記録先:
  → project-registry/[app-name]/PROJECT_PROGRESS.md
```

---

## Rule 3 — Responsibility Registry は共通責務のみ管理する

```
development-os/pr-generator-os/11_PR_RESPONSIBILITY_REGISTRY.md が管理するのは:

  共通の責務ルール・責務分離の原則

PR 単位の責務履歴・Scope 変更・衝突記録は Common OS に書かない。

履歴の記録先:
  → project-registry/[app-name]/RESPONSIBILITY_HISTORY.md
```

---

## Rule 4 — Analytics OS はプロジェクト固有 KPI を管理しない

```
analytics-os/ が管理するのは以下のみ:

  OS 利用率（Balance Score / Usage Matrix）
  Founder Efficiency（Asset Accumulation Score）
  OS 成熟度（Scorecard）

プロジェクト固有 KPI（IPPO の MAU・MRR・Retention など）は Analytics OS に書かない。

プロジェクト KPI の記録先:
  → project-registry/[app-name]/WEEKLY_METRICS.md
```

---

## Rule 5 — Project Registry が管理する情報

```
各 project-registry/[app-name]/ が管理する情報:

  PROJECT_PROGRESS.md:
    - Current Phase / Current PR / Completed PR
    - Next PR / Milestone 履歴

  RESPONSIBILITY_HISTORY.md:
    - PR ごとの責務・Scope 履歴
    - 変更履歴・衝突記録

  WEEKLY_METRICS.md:
    - PR 数 / テスト数 / Build 状態
    - Bug 件数 / Velocity
    - プロジェクト固有 KPI（MAU / MRR など）
```

---

## 違反チェックリスト

Claude Code は以下を毎 PR で確認する。

```
□ Common OS ファイルにプロジェクト固有 PR 番号を追記していないか
□ 08_PROGRESS_REGISTRY.md に PR 履歴を追記していないか
□ 11_PR_RESPONSIBILITY_REGISTRY.md に PR 単位履歴を追記していないか
□ analytics-os/ にプロジェクト固有 KPI を追記していないか
□ プロジェクト固有情報を project-registry/[app-name]/ に記録したか
```
