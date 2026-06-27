# Example: Generic SaaS — Founder Workflow OS 利用例

> 架空のSaaS「TaskFlow」を例に、Founder Workflow OS の汎用的な利用例を示す。
> IPPOとは異なるドメイン・収益モデルでも、同じ Workflow OS が機能することを示す。

---

## 前提設定

**プロダクト名:** TaskFlow
**カテゴリ:** フリーランサー向けタスク・時間管理SaaS
**開発者:** 架空の一人 Founder（Web系エンジニア）
**収益モデル:** サブスクリプション（月額 ¥980）

---

## DISCOVERY フェーズ（S01〜S05）

### S01 — Idea

**日常の観察からのきっかけ:**
自分がフリーランスとして複数クライアントを掛け持ちするとき、
タスク管理・時間記録・請求書作成がバラバラのツールに分散していた。

**課題仮説（1文）:**
「複数クライアントを抱えるフリーランサーが、
タスク・時間・請求を一つの場所で管理できるSaaS」

**Gate D1 確認:**
- ✅ 課題仮説が1文で言える
- ✅ `FOUNDER_PHILOSOPHY.md` の Customer First と整合
- ✅ 既存プロダクトなし（初めてのアプリ）

### S02 — Problem Discovery

**インタビュー相手:**
- フリーランスエンジニア 2名
- フリーランスデザイナー 2名
- フリーランスライター 1名

**発見:**
- 使っているツール: Notion + Toggl + freee の組み合わせが多い
- 「連携が面倒」「毎月の請求書作成が億劫」という声
- 「月額 ¥1,000 以内なら乗り換える」という反応が 3/5 人

**Gate D2: Go → S03 へ**

### S03 — Business Strategy（`business-os/` 参照）

| 項目 | 内容 |
|-----|------|
| 収益モデル | サブスクリプション（¥980/月） |
| TAM | フリーランス人口 400万人（日本）|
| SAM | ITフリーランス 100万人 |
| SOM | 初年度 500人（MRR ¥49万）|
| 競合 | Toggl Track + Freee + Notion |
| 差別化 | 3機能を1つに統合。請求書が1クリック |

**CP-02（ビジネスモデル決定）:** 月額 ¥980 サブスク、14日無料トライアルで決定

### S04 — Growth Strategy

**NSM:** 週次アクティブユーザー数（タスクを週1以上操作）
**初期チャネル:** Twitter・Zenn（技術記事）・フリーランスコミュニティ

### S05 — Regulatory Review

**特定したリスク:**
- 請求書機能: 電子帳簿保存法への対応確認
- 特定商取引法: サブスクリプションサービスとして表記必須

**Gate D5: Go → DESIGN フェーズへ**

---

## DESIGN フェーズ（S06〜S11）

### S07 — Vision

**Vision:** 「フリーランスの"経営"を、もっとシンプルに」

### S08 — 10-Year Design

**10年間変えないもの:**
- フリーランスファースト（中小企業向けには展開しない）
- シンプルさ（機能追加より使いやすさ）

**10年後の姿:**
- MAU 10万人
- B2B2C（フリーランス協会・エージェントとの提携）

### S10 — Domain Design

**主要ドメイン:**
- Task（タスク管理）
- TimeEntry（時間記録）
- Client（クライアント管理）
- Invoice（請求書）

### S11 — Architecture

**技術スタック:**
- React（Web優先 → Next.js）
- Supabase（`development-os/` の標準スタック準拠）
- TypeScript
- Stripe（決済）

**Binding Decisions:**
- BD-001: Supabase as primary DB
- BD-002: Web first（モバイルは v2.0 以降）
- BD-003: Stripe as payment processor

**CP-03（設計凍結）:** 完了

---

## BUILD フェーズ（S12〜S14）

### S12 — Roadmap

**MVP スコープ:**
- PR-001: Task Domain（CRUD）
- PR-002: TimeEntry Domain
- PR-003: Client Domain
- PR-004: Invoice Generation
- PR-005: Supabase Auth 統合
- PR-006: Stripe サブスクリプション

**`11_PR_RESPONSIBILITY_REGISTRY.md`（抜粋）:**

```
PR-001 — Task Domain
责务: Task CRUD
Added allowed: Task Entity / TaskRepository Interface
Forbidden: TimeEntry / Client / Invoice
Event担当: NO / Migration担当: YES / Repository担当: YES

PR-004 — Invoice Generation
责务: Invoice PDF生成
Added allowed: InvoiceGenerator / PDFRenderer
Forbidden: Stripe決済（PR-006担当）/ Task変更
Event担当: YES / Migration担当: YES / Repository担当: YES
```

### S13 — APP STARTER OS

**`templates/APP_STARTER_TEMPLATE/` を使用:**
- Next.js + Supabase のボイラープレートを適用
- GitHub Actions CI/CD を設定
- `.env.example` の設計

**`portfolio-os/` に追加:**
- `portfolio-os/TASKFLOW.md` 作成

### S14 — PR Development

**PR Generator OS の活用（PR-004 の例）:**

```yaml
# 02_PR_INPUT_SHEET.md
Project Name: "TaskFlow"
PR Number: "004"
PR Title: "Invoice Generation Domain"

Governing Documents:
  - "docs/ARCHITECTURE.md"
  - "docs/BINDING_DECISIONS.md"
  - "docs/ROADMAP.md"

Repository Required: YES
  Detail: "InvoiceRepository を追加"
Event Required: YES
  Detail: "InvoiceGeneratedEvent"
Migration Required: YES
  Detail: "invoices テーブル追加"
UI Required: NO  # PR-007担当

Forbidden Changes:
  - "Stripe決済ロジック（PR-006担当）"
  - "Task / TimeEntry / Client Domain"

# Validation: 全PASS後に実装開始
```

---

## LAUNCH フェーズ（S15〜S18）

### S15 — Release

**実施内容:**
- 特定商取引法表記 → `legal-os/templates/TOKUSHOHO.md` を使って作成
- 利用規約 → `legal-os/templates/TERMS_OF_SERVICE.md` を使って作成
- ProductHunt での launch
- Zenn に「なぜTaskFlowを作ったか」の記事投稿
- 初期 100 ユーザーへの無料招待

### S16 — Analytics

**NSM の実測（初月）:**
- MAU: 87人
- 週次アクティブ率: 61%
- MRR: ¥29,400（30人が有料転換）

**分析:**
- 無料トライアルから有料への転換率: 34%（目標 30%以上 → 達成）
- 請求書機能の利用率: 71%（コアバリューが使われている）

### S17 — User Feedback

**インタビューから得た知見:**
- 「時間記録がもっと簡単になってほしい」（タイマー UI の改善要望）
- 「複数レートに対応してほしい」（クライアント別時間単価）

**改善優先度リスト:**
1. タイマーUI の UX 改善（Retention に直結）
2. 複数レート対応（上位ユーザーの要望）
3. CSV エクスポート（ニッチだが強い要望）

### S18 — Improvement

**改善PR を PR Generator OS で実施:**
- PR-020: Timer UX 改善
- PR-021: 複数レート対応

---

## ASSET フェーズ（S19〜S21）

### S19 — Brand Asset

**実施内容:**
- Zenn 記事:「Supabase + Next.js でSaaSを作って3ヶ月」
- X: 毎日の数字報告（build in public）
- note: フリーランスの経営術シリーズ（SEO 狙い）

### S21 — Template Asset

**Founder OS へのフィードバック:**
- Stripe 決済 PR のパターンを `11_PR_RESPONSIBILITY_REGISTRY.md` に追加
- Next.js 版 `APP_STARTER_TEMPLATE/` を作成（既存の Expo 版と並存）
- `development-os/` に Web アプリ用技術スタックを追記

---

## この例が示すこと

| 観点 | 示していること |
|-----|-------------|
| 汎用性 | ウォーキングアプリ（IPPO）と全く異なるドメインでも同じ Workflow が機能 |
| PR Generator OS | 架空アプリでも `11_PR_RESPONSIBILITY_REGISTRY.md` パターンが適用可能 |
| Stage Gate | Gate の条件はプロジェクトを問わず機能する |
| Asset 蓄積 | 次に Web SaaS を作るとき、TaskFlow の Stripe PR パターンが使える |
| Template 活用 | `legal-os/` のひな形を使って法的文書作成コストを削減 |
| OS 再利用 | 1プロダクト目での知見が `APP_STARTER_TEMPLATE/` を改善し、2プロダクト目が速くなる |
