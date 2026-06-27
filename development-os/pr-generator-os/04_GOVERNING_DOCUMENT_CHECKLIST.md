# 04 — Governing Document Checklist

> PR開始前に読むべき上位文書の確認チェックリスト。
> AIにこのチェックリストを渡し、すべての文書を読み込ませてから実装を始める。

---

## 汎用チェックリスト（全プロジェクト共通）

PR開始前に以下の文書カテゴリを確認してください。
各行に対応する実際のファイルパスを記入して使用してください。

### Level 0 — 根本思想（変更不可・最上位）

- [ ] **Founder Philosophy**
  - ファイル: `founder-operating-system/FOUNDER_PHILOSOPHY.md`
  - 確認内容: 今回のPRがFounder Philosophyに反していないか

- [ ] **Operating Principles**
  - ファイル: `founder-operating-system/OPERATING_PRINCIPLES.md`
  - 確認内容: 18原則に違反していないか（特に #2 Single Source of Truth, #14 Security）

### Level 1 — Product Thesis & Vision

- [ ] **Product Thesis / Vision**
  - ファイル: `[プロジェクト]/docs/PRODUCT_THESIS.md` または同等文書
  - 確認内容: このPRがProduct Visionと整合しているか

- [ ] **Business Strategy**
  - ファイル: `[プロジェクト]/docs/BUSINESS_STRATEGY.md`
  - 確認内容: ビジネス判断に影響する変更がないか

### Level 2 — Architecture & Governance（必須）

- [ ] **Architecture Document**
  - ファイル: `[プロジェクト]/docs/ARCHITECTURE.md` または同等文書
  - 確認内容: レイヤー構造・依存関係・設計パターンの確認

- [ ] **Implementation Governance**
  - ファイル: `[プロジェクト]/docs/IMPLEMENTATION_GOVERNANCE.md` または同等文書
  - 確認内容: PR単位の実装ルール・禁止事項の確認

- [ ] **Roadmap**
  - ファイル: `[プロジェクト]/docs/ROADMAP.md` または同等文書
  - 確認内容: 本PRがRoadmap上の正しい位置にあるか

- [ ] **Binding Decisions**
  - ファイル: `[プロジェクト]/docs/BINDING_DECISIONS.md` または同等文書
  - 確認内容: 適用されるBDと違反するBDの洗い出し

### Level 3 — Legal & Regulatory

- [ ] **Legal / Regulatory Constraints**
  - ファイル: `founder-operating-system/legal-os/README.md`
  - 確認内容: データ保護・プライバシー・規制への適合

### Level 4 — Current State（必須）

- [ ] **Current Handoff / State Document**
  - ファイル: `[プロジェクト]/docs/HANDOFF_[PHASE]_COMPLETE.md` または同等文書
  - 確認内容: 直前PRの完了状態・未解決事項・次PRへの引き継ぎ

- [ ] **PR Responsibility Registry**
  - ファイル: `founder-operating-system/development-os/pr-generator-os/11_PR_RESPONSIBILITY_REGISTRY.md`
  - 確認内容: 本PRの責務が他PRと重複していないか

---

## 優先順位ルール

上位文書と下位文書が衝突する場合:

```
Binding Decisions（最上位・絶対）
    ↓ 以下は逆らえない
Architecture Document
    ↓
Implementation Governance / Roadmap
    ↓
Handoff Document（現在の状態）
    ↓
PR Scope（このプロンプト）
```

**衝突を発見した場合は実装を止めてFounderに報告する。自己判断で解決しない。**

---

## IPPOでの使い方（サンプル）

IPPOプロジェクトでは以下のファイルが上記カテゴリに対応します:

| カテゴリ | IPPOのファイル |
|---------|--------------|
| Architecture | `docs/WAVE2_ARCHITECTURE.md` |
| Implementation Governance | `docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md` |
| Roadmap | `docs/WAVE2_ROADMAP.md` |
| Master Design | `docs/WAVE2_MASTER_DESIGN.md` |
| Binding Decisions | `docs/BINDING_DECISIONS.md` |
| Current Handoff | `docs/HANDOFF_PHASE7_COMPLETE.md`（最新のもの）|

IPPOのPRプロンプトでは以下のように指示します:
```
実装前に以下を必ず読み込んでください:
1. docs/BINDING_DECISIONS.md
2. docs/WAVE2_ARCHITECTURE.md
3. docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md
4. docs/WAVE2_ROADMAP.md
5. docs/WAVE2_MASTER_DESIGN.md
6. docs/HANDOFF_PHASE7_COMPLETE.md
```

---

## 新規プロジェクトでのセットアップ

新しいプロジェクトを始めるとき:

1. `02_PR_INPUT_SHEET.md` の `Governing Documents` 欄に実際のファイルパスを記入
2. 上記カテゴリと実際のファイルのマッピング表を作成（`[Project]_DOCUMENT_MAP.md`）
3. 各文書が存在しない場合は作成してから開発を始める

**上位文書なしで実装を開始しない。**
