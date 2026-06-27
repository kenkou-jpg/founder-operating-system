# 13 — Roadmap Validator

> Roadmapからの逸脱を防ぐ。
> AIはPR開始前にこのValidatorを実行し、RoadmapとPR Scopeの整合性を確認する。
> 1項目でも ❌ が出たら STOP。

---

## 実行手順

1. プロジェクトの Roadmap 文書を読み込む（`04_GOVERNING_DOCUMENT_CHECKLIST.md` 参照）
2. `02_PR_INPUT_SHEET.md` の本PRの情報を確認する
3. `11_PR_RESPONSIBILITY_REGISTRY.md` で本PRの計画エントリを確認する
4. 以下のチェックを実行する
5. Roadmap Validation Result を出力する

---

## Validation Items

### 1. PR番号の位置確認

- [ ] **現在のPR番号はRoadmapの正しい位置にあるか**
  - Roadmapに定義されたPR順序と一致しているか
  - 番号が飛んでいる場合は理由があるか
  - 例: Roadmapが PR-041→042→043→044 と定義しているなら、PR-044の前に041〜043が完了しているか

- [ ] **前提PRはすべて完了しているか**
  - `11_PR_RESPONSIBILITY_REGISTRY.md` で `依存PR` のステータスが「完了」になっているか
  - 未完了のPRに依存している場合は STOP

### 2. Roadmap上の責務との一致

- [ ] **Roadmapに定義された責務とPR Scopeが一致しているか**
  - Roadmapが「このPRはXXXを実装する」と定義している内容と
    `02_PR_INPUT_SHEET.md` の `Implementation Target` が一致しているか

- [ ] **Roadmapにない責務が追加されていないか**
  - Roadmapに記載のない機能を「ついでに」実装しようとしていないか
  - Roadmap外の実装はFounder承認が必要

### 3. 次PRへの侵入チェック

- [ ] **次PRのスコープを先取りしていないか**
  - Roadmap上で次PRが担当するものを本PRで実装しようとしていないか
  - `11_PR_RESPONSIBILITY_REGISTRY.md` の次PRの `追加してよいもの` と照合

### 4. 前PRへの戻りチェック

- [ ] **完了済みPRの責務を再実装していないか**
  - Roadmapで「完了」になっているPRの内容を再実装しようとしていないか
  - 既存実装の修正は「バグ修正PR」として別途立てる

### 5. Governing Documentsとの整合性

- [ ] **Implementation Governance と一致しているか**
  - Governance文書が定めたPR単位の方針に沿っているか

- [ ] **Architecture文書と一致しているか**
  - Roadmapが想定するアーキテクチャ上でこのPRが実装されているか

### 6. Binding Decision違反チェック

- [ ] **RoadmapにないBD変更が含まれていないか**
  - Roadmapが前提としているBDを覆す変更がないか
  - BDの変更は必ずFounder承認が必要

### 7. Wave / Phase整合性

- [ ] **本PRは正しいWave / Phaseに属しているか**
  - 現在のWave / Phaseに対応するPRか
  - 先のWave / Phaseの実装が混入していないか

---

## Roadmap Validation Result

```
==================================
Roadmap Validation Result
==================================

PR-[番号]: [タイトル]
Project: [プロジェクト名]
Wave / Phase: [Wave X / Phase N]
実行日時: [YYYY-MM-DD HH:MM]

Roadmap文書: [ファイルパス]

チェック結果:
1. PR番号位置: PASS / FAIL
2. 責務一致: PASS / FAIL
3. 次PR侵入なし: PASS / FAIL
4. 前PR戻りなし: PASS / FAIL
5. Governing Docs整合: PASS / FAIL
6. BD違反なし: PASS / FAIL
7. Wave/Phase整合: PASS / FAIL

==================================
→ Roadmap Validation: PASS / STOP
==================================

[STOP の場合]
逸脱理由:
- [具体的な逸脱内容]

修正案:
- [逸脱を解消するための提案]

Founder承認が必要: YES / NO
==================================
```

---

## PASS条件

- すべての項目が PASS
- または STOP の項目について Founder 承認済み

---

## よくある Roadmap 逸脱パターン

| パターン | 例 | 対処 |
|---------|-----|------|
| 先取り実装 | PR-044でDisease Signalを実装（PR-045担当）| Scopeから除外 |
| 責務の肥大化 | 1つのPRにRepository + Migration + Domain | PRを分割 |
| BD違反 | Roadmapで禁止されているAI/LLMを使用 | 実装方法を変更 |
| Phase飛び越し | Wave 2 Phase 8の機能をPhase 7 PRで実装 | 次Phaseに延期 |
| 前PRの再実装 | PR-041のInterfaceをPR-044で再定義 | 既存Interfaceを使用 |

---

## IPPOでの使い方

IPPOでは以下のファイルをRoadmapとして使用:
- `docs/WAVE2_ROADMAP.md` — Wave 2 の全PR計画
- `docs/WAVE2_IMPLEMENTATION_GOVERNANCE.md` — PR単位の実装ガバナンス
- `docs/HANDOFF_PHASE7_COMPLETE.md` — 現在の完了状態

PR-044 のRoadmap Validationでは:
1. `WAVE2_ROADMAP.md` でPR-044の担当をMenstrualPhase Auto-Resolutionと確認
2. PR-041〜043が完了済みであることを `11_PR_RESPONSIBILITY_REGISTRY.md` で確認
3. PR-045（Disease Signal）のスコープに侵入していないことを確認
4. PASS → 実装開始
