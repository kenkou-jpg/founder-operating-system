# OS_BALANCE_SCORE

> 各 OS の利用バランスを集計・分析する。
> 特定 OS への過度な集中を検出し、未活用 OS を可視化する。

---

## Balance Score 計算式

```
Balance Score = 1回以上使用された OS 数 ÷ 対象 OS 総数 × 100
```

**対象 OS 総数: 13**（Development / PR Generator / Execution Dispatcher / Business / Brand / Legal / Research / Finance / Analytics / Customer Success / Automation / Template Business / Founder Workflow）

---

## 現在の Balance Score（2026-W27）

| 指標 | 値 |
|-----|---|
| **Balance Score** | **31%**（4 / 13 OS を使用）|
| 使用された OS 数 | 4（Development / PR Generator / Founder Workflow / Analytics）|
| 未使用 OS 数 | 9 |
| 総 Usage Count | 45 回 |

---

## Usage Count / Usage % 集計

| OS | Usage Count | Usage % |
|----|------------|---------|
| Development OS | 15 | 33.3% |
| PR Generator OS | 12 | 26.7% |
| Execution Dispatcher | 8 | 17.8% |
| Founder Workflow OS | 6 | 13.3% |
| Analytics OS | 3 | 6.7% |
| Template Business OS | 1 | 2.2% |
| Business OS | 0 | 0% |
| Brand OS | 0 | 0% |
| Legal OS | 0 | 0% |
| Research OS | 0 | 0% |
| Finance OS | 0 | 0% |
| Customer Success OS | 0 | 0% |
| Automation OS | 0 | 0% |
| **合計** | **45** | **100%** |

---

## 偏り分析

```
Wave2 開発期の特性:
  Development OS・PR Generator OS・Executor Dispatcher に集中するのは正常。
  ただし Business OS・Analytics OS・Brand OS の活用が不足している。
```

| 状態 | OS |
|-----|---|
| 🔴 未使用（Wave2 中も意識すべき）| Business OS / Finance OS / Customer Success OS |
| 🟡 低頻度（月次で活用推奨）| Brand OS / Legal OS / Research OS |
| 🟢 活用中 | Development OS / PR Generator OS / Founder Workflow OS |

---

## Balance Score 閾値

| スコア | 判定 | アクション |
|-------|------|---------|
| ≥ 70% | ✅ 理想的バランス | 維持 |
| 50〜69% | 🔶 許容範囲 | 低頻度 OS の活用を検討 |
| 30〜49% | ⚠️ 偏り注意 | 月次で未使用 OS を意図的に使う |
| < 30% | 🔴 過度な集中 | 週次で未使用 OS をチェック |

**現在: 31%（Wave2 開発期は許容範囲内）**

---

## 改善提案

### Wave2 期間中に意識すべき OS（月次）

1. **Finance OS** — MRR が発生したら月次確認を開始する
2. **Business OS** — PR-075 完了後に Business Strategy を見直す
3. **Customer Success OS** — Beta Release 後にユーザーフィードバック整理で活用

### Wave2 完了後に活用すべき OS

- Brand OS（Launch 時のコンテンツ発信）
- Research OS（PMF 確認のユーザーインタビュー）
- Automation OS（CI/CD・監視の自動化強化）

---

## 履歴

| 週 | Balance Score | 主な変化 |
|----|------------|---------|
| 2026-W27 | 31% | Analytics OS 追加 |
