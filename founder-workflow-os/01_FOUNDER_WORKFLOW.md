# 01 — Founder Workflow

> 「アイデアから次のアプリへ」の標準実行フロー。
> 各ステージの目的・入力・成果物・完了条件・次ステージを定義する。

---

## フロー全体図

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DISCOVERY フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S01  Idea
  ↓
S02  Problem Discovery
  ↓
S03  Business Strategy
  ↓
S04  Growth Strategy
  ↓
S05  Regulatory Review

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DESIGN フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S06  Go-To-Market
  ↓
S07  Vision
  ↓
S08  10-Year Design
  ↓
S09  5-Year Quality
  ↓
S10  Domain Design
  ↓
S11  Architecture

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[BUILD フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S12  Roadmap
  ↓
S13  APP STARTER OS
  ↓
S14  PR Development

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[LAUNCH フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S15  Release
  ↓
S16  Analytics
  ↓
S17  User Feedback
  ↓
S18  Improvement

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[ASSET フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S19  Brand Asset
  ↓
S20  Research Asset
  ↓
S21  Template Asset

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[SCALE フェーズ]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
S22  Portfolio
  ↓
S23  Next App
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## DISCOVERY フェーズ

### S01 — Idea

**目的:** アイデアを記録し、検証に値するか初期スクリーニングする

**入力:**
- 日常の観察・自分が感じた課題
- 市場のトレンド・技術の変化
- 既存プロダクトへの不満

**成果物:**
- Idea メモ（1段落）
- 「誰の・何の課題を・どう解くか」の仮説（1文）

**完了条件:**
- 課題の仮説が1文で言えること
- `FOUNDER_PHILOSOPHY.md` の価値観と矛盾しないこと

**次ステージ:** S02 Problem Discovery

---

### S02 — Problem Discovery

**目的:** 課題が実在するかを一次情報で検証する

**入力:**
- S01 の課題仮説
- `research-os/` のリサーチフレームワーク

**成果物:**
- ユーザーインタビュー記録（最低3人）
- 課題の実在確認または棄却
- ターゲットユーザー像の初稿

**完了条件:**
- 「課題を持つ人が実在する」証拠があること
- インタビューで「お金を払ってもいい」または相当の反応があること
- `research-os/` の一次情報原則を守っていること

**次ステージ:** S03 Business Strategy

---

### S03 — Business Strategy

**目的:** 収益可能な事業モデルを設計する

**入力:**
- S02 の課題検証結果
- `business-os/` の事業モデル評価基準

**成果物:**
- `BUSINESS_STRATEGY_TEMPLATE.md` を記入したドキュメント
- TAM/SAM/SOM の見積もり
- 収益モデル（サブスク/フリーミアム/B2B2C 等）の選定と根拠
- 競合分析（主要3社以上）
- 12ヶ月MRR目標

**完了条件:**
- ビジネスモデルが `business-os/` の原則に準拠
- 収益化の道筋が具体的に説明できること
- 競合との差別化が1文で言えること

**次ステージ:** S04 Growth Strategy

---

### S04 — Growth Strategy

**目的:** ユーザー獲得・定着・収益化の成長戦略を設計する

**入力:**
- S03 の Business Strategy
- `business-os/` の GTM フレームワーク
- `analytics-os/` の NSM（ノーススターメトリクス）定義

**成果物:**
- GTM プレイブック初稿（Seed / Growth / Scale フェーズ別）
- ノーススターメトリクス（NSM）の定義
- 主要KPI一覧（定義・目標値・測定頻度）
- 獲得チャネルの優先順位（初期3つ以内）

**完了条件:**
- NSM が「ユーザーが価値を感じる瞬間」を測定していること
- KPI が `analytics-os/` の定義基準に従っていること
- 獲得チャネルが現実的かつ検証可能なこと

**次ステージ:** S05 Regulatory Review

---

### S05 — Regulatory Review

**目的:** 法的リスクを事前に特定し、設計に組み込む

**入力:**
- S03 の Business Strategy（データ収集・収益モデル）
- `legal-os/` の法務方針

**成果物:**
- 適用法令チェックリスト（特定商取引法・景品表示法・個人情報保護法等）
- ドメイン固有リスクの特定（ヘルスケア・農業・教育等）
- プライバシーポリシー・利用規約の要件定義
- 「やってはいけないこと」リスト

**完了条件:**
- 主要な法的リスクが特定されていること
- リスクに対する対処方針が決まっていること
- `legal-os/` の Compliance Checklist を確認していること

**次ステージ:** S06 Go-To-Market

---

## DESIGN フェーズ

### S06 — Go-To-Market

**目的:** 市場へのアプローチ方法と初期ユーザー獲得計画を確定する

**入力:**
- S03 Business Strategy
- S04 Growth Strategy
- `brand-os/` のブランドボイス

**成果物:**
- Seed フェーズ（〜100ユーザー）の具体的アクションリスト
- ランディングページの要件
- 初期コンテンツ戦略（note/X等）
- Launch イベントの計画

**完了条件:**
- 「最初の100ユーザーをどこから連れてくるか」が具体的に説明できること
- `brand-os/` のブランドボイスと整合していること

**次ステージ:** S07 Vision

---

### S07 — Vision

**目的:** プロダクトの長期ビジョンを定義し、設計の拠り所にする

**入力:**
- `FOUNDER_PHILOSOPHY.md` の長期思考原則
- S02 の課題発見
- S03 の市場機会

**成果物:**
- プロダクトビジョン（1文・3年後の世界像）
- Mission（なぜこれを作るか）
- 「このプロダクトが成功した世界」の描写（1段落）

**完了条件:**
- ビジョンが `FOUNDER_PHILOSOPHY.md` と整合していること
- チームや外部パートナーに説明できる言語化であること
- 10年後に恥ずかしくない内容であること

**次ステージ:** S08 10-Year Design

---

### S08 — 10-Year Design

**目的:** 10年後の姿から逆算して、今の設計に何が必要かを決める

**入力:**
- S07 Vision
- `OPERATING_PRINCIPLES.md` の長期思考原則

**成果物:**
- 10年後のプロダクト像（機能・ユーザー規模・収益規模）
- 「今から10年間変えないもの」のリスト（コア価値・設計原則）
- 「10年後に後悔しないためのの今の判断」チェックリスト
- 技術的な永続設計の方針

**完了条件:**
- 10年後の姿が S07 Vision と一貫していること
- 今の設計判断が10年後に「なぜそうしたか」理解できること

**次ステージ:** S09 5-Year Quality

---

### S09 — 5-Year Quality

**目的:** 5年間使い続けられる品質基準を設計に組み込む

**入力:**
- S08 10-Year Design
- `development-os/` のテスト・品質標準
- `OPERATING_PRINCIPLES.md` #7 Long-term Quality

**成果物:**
- 品質定義（「品質とはこのプロダクトにおいて何か」）
- 受け入れ不可能な品質水準のリスト
- テスト戦略の方針
- 技術的負債の管理方針

**完了条件:**
- 品質基準が `development-os/` のテスト標準と整合
- 「これ以下の品質ではリリースしない」が明文化されていること

**次ステージ:** S10 Domain Design

---

### S10 — Domain Design

**目的:** プロダクトのビジネスドメインを設計する

**入力:**
- S02 課題発見
- S03 Business Strategy
- `development-os/` のアーキテクチャ原則

**成果物:**
- ドメインモデル（主要Entity・ValueObject・集約の定義）
- ユビキタス言語（プロダクト固有の用語定義）
- ドメインイベント一覧
- ドメインと他ドメインの境界定義

**完了条件:**
- ドメインモデルがビジネス課題を表現できていること
- ドメイン境界が明確で、責務が重複していないこと
- `development-os/` の設計原則に従っていること

**次ステージ:** S11 Architecture

---

### S11 — Architecture

**目的:** システムアーキテクチャを設計・文書化する

**入力:**
- S10 Domain Design
- `development-os/` の技術スタック・アーキテクチャ原則
- S09 の品質基準

**成果物:**
- `ARCHITECTURE_TEMPLATE.md` を記入したアーキテクチャ文書
- 技術スタック選定と根拠
- システム構成図
- Binding Decisions の初版（主要な技術判断）
- データモデル（コア）

**完了条件:**
- `development-os/` の技術スタック標準に準拠
- アーキテクチャが S09 の品質基準を満たせる設計
- Binding Decisions が文書化されていること

**次ステージ:** S12 Roadmap

---

## BUILD フェーズ

### S12 — Roadmap

**目的:** 実装をPR単位のロードマップに落とし込む

**入力:**
- S11 Architecture
- `development-os/pr-generator-os/` の PR 標準
- S04 の MVP 定義

**成果物:**
- PR 単位のロードマップ（Wave / Phase 構成）
- MVP に含める機能・含めない機能の明確化
- `11_PR_RESPONSIBILITY_REGISTRY.md` の初期化
- 実装ガバナンス文書（Binding Decisions + 実装ルール）

**完了条件:**
- PRが適切な粒度で分割されていること（1PR = 1責務）
- MVP が「最小限で価値を届けられる」状態であること
- PR Registry が初期化されていること

**次ステージ:** S13 APP STARTER OS

---

### S13 — APP STARTER OS

**目的:** リポジトリの初期セットアップを完了し、開発開始できる状態にする

**入力:**
- S11 Architecture
- `templates/APP_STARTER_TEMPLATE/`
- `automation-os/` の CI/CD 標準

**成果物:**
- GitHub リポジトリ（初期セットアップ済み）
- CI/CD パイプライン
- 環境変数設計（`.env.example`）
- Supabase プロジェクトのセットアップ
- `portfolio-os/` への新プロダクトプロファイル追加

**完了条件:**
- `npm run test` `npm run build` が通ること
- CI/CD が `automation-os/` の標準に従っていること
- `CANONICAL_SOURCE.md` にプロダクトが追加されていること

**次ステージ:** S14 PR Development

---

### S14 — PR Development

**目的:** Roadmap に従い、PR 単位で実装を進める

**入力:**
- S12 Roadmap
- `development-os/pr-generator-os/` の全テンプレート
- `governance/ADR/` の蓄積

**成果物（PR ごと）:**
- 実装コード
- テスト（最低件数以上）
- Completion Report
- `11_PR_RESPONSIBILITY_REGISTRY.md` への追記

**完了条件（各 PR）:**
- `08_DEFINITION_OF_DONE.md` の全条件クリア
- Validation 4種（12〜14）が PASS
- Regression なし

**完了条件（Roadmap 全体）:**
- MVP の全機能が実装・テスト済み
- リリース判断を行える状態

**次ステージ:** S15 Release

---

## LAUNCH フェーズ

### S15 — Release

**目的:** ユーザーにプロダクトを届ける

**入力:**
- S14 の MVP
- S05 の規制チェックリスト
- `legal-os/` の利用規約・プライバシーポリシー
- S06 の GTM 計画

**成果物:**
- 利用規約・プライバシーポリシーの公開
- App Store / Web への公開
- GTM アクション（SNS 投稿・note 記事・コミュニティへの告知）
- Release ノート

**完了条件:**
- 法的文書が公開済みであること
- 実際のユーザーがアクセスできること
- Analytics が計測開始されていること
- サポート導線が用意されていること

**次ステージ:** S16 Analytics

---

### S16 — Analytics

**目的:** データに基づき、プロダクトの状態を把握する

**入力:**
- S15 Release 後のデータ
- `analytics-os/` のKPI定義・ダッシュボード設計

**成果物:**
- NSM・KPI の実測値（初週・初月）
- ファネル分析（獲得→定着→収益）
- 「予想と現実の差異」分析メモ
- 改善仮説リスト

**完了条件:**
- NSM が毎週計測・記録されていること
- ダッシュボードが稼働していること

**次ステージ:** S17 User Feedback

---

### S17 — User Feedback

**目的:** ユーザーの声を収集し、プロダクト改善の方向を定める

**入力:**
- S16 の Analytics 結果
- `customer-success-os/` のフィードバック収集手順

**成果物:**
- ユーザーインタビュー記録（月1〜2回）
- アプリ内フィードバック・サポート問い合わせの分類・分析
- 「ユーザーが実際に使っていること」vs「設計で想定したこと」の比較
- 改善優先度リスト

**完了条件:**
- フィードバックが構造化・分類されていること
- 改善仮説が `16_Analytics` のデータと照合されていること

**次ステージ:** S18 Improvement

---

### S18 — Improvement

**目的:** データとフィードバックに基づき、プロダクトを改善する

**入力:**
- S16 Analytics
- S17 User Feedback
- `development-os/pr-generator-os/` の PR 標準

**成果物:**
- 改善PR（`development-os/pr-generator-os/` を使って実装）
- 改善後の効果測定結果
- 学習の記録（`knowledge-os/` に蓄積）

**完了条件:**
- 改善内容がデータで効果測定されていること
- S16 → S17 → S18 のループが回っていること（継続運営）

**次ステージ:** S19 Brand Asset（並行して S16〜S18 は継続）

---

## ASSET フェーズ

### S19 — Brand Asset

**目的:** プロダクト運営を通じて得た信頼・ブランドを資産化する

**入力:**
- リリース後の知見・ユーザーの声
- `brand-os/` のブランドガイドライン

**成果物:**
- note 記事（開発背景・想い・技術解説）
- X（Twitter）での継続発信
- プロダクトの「ストーリー」の言語化
- App Store の最適化（ASO）

**完了条件:**
- 月1本以上のコンテンツが発信されていること
- `brand-os/` のブランドボイスに従った発信であること

**次ステージ:** S20 Research Asset

---

### S20 — Research Asset

**目的:** プロダクト運営を通じて得た知見を研究資産として蓄積する

**入力:**
- S16〜S18 の運営データと学習
- `research-os/` のインサイトアーカイブ手順

**成果物:**
- `research-os/insights/` へのインサイト追加
- ユーザー行動パターンの分析記録
- 業界知識の体系化（`knowledge-os/`）
- 将来の論文・レポートの種（Imaging Agriculture 等に活用）

**完了条件:**
- 学んだことが構造化されて蓄積されていること
- `knowledge-os/` の「だから何か」まで書けていること

**次ステージ:** S21 Template Asset

---

### S21 — Template Asset

**目的:** このプロダクトで確立したパターンをテンプレートとして再利用可能にする

**入力:**
- S11〜S14 での設計・実装パターン
- `template-business-os/` の品質基準

**成果物:**
- `templates/APP_STARTER_TEMPLATE/` の更新・改善
- `development-os/pr-generator-os/` へのパターン追記
- Founder OS 自体の更新（`governance/CHANGELOG.md`）
- 販売可能なテンプレートの整理（`template-business-os/` 参照）

**完了条件:**
- 次のアプリに「コピーして使えるもの」が増えていること
- Founder OS が今回の知見で改善されていること

**次ステージ:** S22 Portfolio

---

## SCALE フェーズ

### S22 — Portfolio

**目的:** このプロダクトをポートフォリオに正式に組み込み、全体管理を更新する

**入力:**
- S15〜S21 の全成果
- `portfolio-os/PORTFOLIO_KPI.md`
- `finance-os/` の財務レビュー

**成果物:**
- `portfolio-os/[PRODUCT].md` の更新（現状・KPI・戦略）
- `portfolio-os/PORTFOLIO_KPI.md` の更新
- 月次財務レビューへの組み込み
- 「このプロダクトへの今後の投資方針」決定

**完了条件:**
- ポートフォリオKPIに組み込まれ、月次レビューで確認されること
- 財務的位置づけ（投資中・収益化・維持・終了候補）が決まっていること

**次ステージ:** S23 Next App

---

### S23 — Next App

**目的:** 次のアプリへの展開を、今回の資産を活かして始める

**入力:**
- S21 Template Asset（更新済み Founder OS）
- S22 Portfolio（全体最適の視点）
- `OPERATING_PRINCIPLES.md` #15 Portfolio Thinking

**成果物:**
- 次のアプリの Idea メモ（S01 へ）
- 「今回の資産のどれを次に活かすか」の整理
- ポートフォリオバランスの確認（新規開始の可否判断）

**完了条件:**
- `06_PORTFOLIO_MANAGEMENT.md` の「同時開発数上限」を超えていないこと
- 既存プロダクトの健全性が確認されていること
- 次アプリが Founder Philosophy と整合していること

**次ステージ:** S01 Idea（新しいループへ）

---

## ステージ早見表

| # | ステージ | フェーズ | 参照OS | 主な成果物 |
|---|---------|---------|--------|-----------|
| S01 | Idea | Discovery | — | 課題仮説 |
| S02 | Problem Discovery | Discovery | research-os | インタビュー記録 |
| S03 | Business Strategy | Discovery | business-os | BUSINESS_STRATEGY.md |
| S04 | Growth Strategy | Discovery | analytics-os | KPI定義・GTM |
| S05 | Regulatory Review | Discovery | legal-os | 法的リスクリスト |
| S06 | Go-To-Market | Design | business-os, brand-os | GTMアクションリスト |
| S07 | Vision | Design | FOUNDER_PHILOSOPHY | Vision文 |
| S08 | 10-Year Design | Design | OPERATING_PRINCIPLES | 永続設計方針 |
| S09 | 5-Year Quality | Design | development-os | 品質基準 |
| S10 | Domain Design | Design | development-os | ドメインモデル |
| S11 | Architecture | Design | development-os | ARCHITECTURE.md |
| S12 | Roadmap | Build | pr-generator-os | PR Roadmap |
| S13 | APP STARTER OS | Build | templates | リポジトリセットアップ |
| S14 | PR Development | Build | pr-generator-os | 実装 + テスト |
| S15 | Release | Launch | legal-os, automation-os | 公開 |
| S16 | Analytics | Launch | analytics-os | KPI実測値 |
| S17 | User Feedback | Launch | customer-success-os | フィードバック分析 |
| S18 | Improvement | Launch | pr-generator-os | 改善PR |
| S19 | Brand Asset | Asset | brand-os | コンテンツ資産 |
| S20 | Research Asset | Asset | research-os, knowledge-os | インサイト蓄積 |
| S21 | Template Asset | Asset | template-business-os | OS更新 |
| S22 | Portfolio | Scale | portfolio-os, finance-os | ポートフォリオ更新 |
| S23 | Next App | Scale | 全OS | 次サイクル開始 |
