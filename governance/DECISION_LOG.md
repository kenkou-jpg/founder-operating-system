# Decision Log

> 重要な意思決定の記録。「なぜそう決めたか」を未来の自分のために残す。

## Format

```
## [YYYY-MM-DD] [Decision Title]

**Context:** なぜこの決定が必要だったか
**Options Considered:** 検討した選択肢
**Decision:** 何を決めたか
**Rationale:** なぜそれを選んだか
**Consequences:** この決定が引き起こすこと（良い面・悪い面）
**Review Date:** いつ見直すか（オプション）
```

---

## 2026-06-27 — Founder Operating System の創設

**Context:**
複数のプロダクト（ippo, AgriPath, Fasting App）を同一の創業者が運営するにあたり、
判断基準・技術標準・ブランド基準がそれぞれのリポジトリに散在していた。

**Options Considered:**
1. 各リポジトリに個別のドキュメントを持つ
2. Notionで一元管理する
3. 専用GitHubリポジトリ（founder-operating-system）で管理する

**Decision:**
Option 3 — 専用GitHubリポジトリ `founder-operating-system` を作成する

**Rationale:**
- バージョン管理・変更履歴が自動的に残る
- Markdownで書けるため、エンジニアとして自然なワークフロー
- 各プロダクトリポジトリからの参照が明確
- Notionに依存しない（ツール変更リスクの排除）

**Consequences:**
- 良い面: 全プロダクトの判断に一貫性が生まれる
- 悪い面: OS自体のメンテナンスコストが発生する
- 良い面: 将来のチームメンバーへのオンボーディングが容易になる

**Review Date:** 2027-01-01（年次レビュー）
