# 03 — PR Type Matrix

> PRの種類ごとに必須成果物・テスト・禁止事項・よくある事故・完了条件を整理する。
> PR開始前に、自分のPRがどのタイプかを確認すること。

---

## PRタイプ一覧

| # | タイプ | 主な責務 |
|---|--------|---------|
| 1 | Domain PR | Domainロジック・Valueオブジェクト・Ruleエンジン |
| 2 | Repository PR | Repository Interface・Adapter・Factory・永続化 |
| 3 | Infrastructure PR | DB・外部サービス・設定・Migration |
| 4 | Event Sourcing PR | Domainイベント・EventBus・EventStore |
| 5 | API Gateway PR | APIエンドポイント・Request/Responseマッピング |
| 6 | UI PR | Screen・Component・Navigation |
| 7 | Analytics PR | イベント計測・KPI収集・ダッシュボード連携 |
| 8 | AI / Rule Engine PR | AI統合・Ruleエンジン・推論ロジック |
| 9 | Research PR | データ収集・分析・研究ロジック |
| 10 | Governance PR | ADR・BD・OS文書・テンプレート更新 |
| 11 | Migration PR | DBスキーマ変更・データ移行 |

---

## 1. Domain PR

**主な責務:** Domainロジック・Entity・ValueObject・Ruleエンジン・Service

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Domain Class / Entity / ValueObject / Rule / Service |
| **追加すべきテスト** | Unit Test（正常系・異常系・境界値）/ Domain Integration Test |
| **禁止事項** | UI依存 / Repository直接アクセス / DB操作 / 外部API呼び出し |
| **よくある事故** | Domainに永続化ロジックが混入 / 他DomainのEntityを直接参照 / Screenをimport |
| **完了条件** | Domain単体でテスト可能 / 外部依存がない / Repository経由でのみ永続化 |

---

## 2. Repository PR

**主な責務:** Repository Interface・Adapter・Factory・PersistenceService

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Repository Interface / Adapter / Factory / PersistenceService |
| **追加すべきテスト** | Repository Unit Test / Adapter Test / Factory Test / Integration Test |
| **禁止事項** | Domain変更 / UI変更 / Migration追加（Migration PRが別途必要）|
| **よくある事故** | InterfaceとAdapterを同じPRで作りながらMigrationも追加してしまう / Domain変更が混入 |
| **完了条件** | InterfaceがDomainに依存していない / AdapterがInterfaceに準拠 / Factoryが切り替え可能 |

---

## 3. Infrastructure PR

**主な責務:** 外部サービス設定・環境変数・インフラ構成・CI/CD

| 項目 | 内容 |
|-----|------|
| **必須成果物** | 設定ファイル / 環境変数定義 / インフラ設定 |
| **追加すべきテスト** | Build Test / 設定値バリデーションテスト |
| **禁止事項** | Domainロジック変更 / UI変更 / 本番値のコミット |
| **よくある事故** | 機密情報のコミット / 本番・開発環境の設定混在 / Domain変更の混入 |
| **完了条件** | 機密情報が含まれていない / ローカル・CI双方でBuildが通る |

---

## 4. Event Sourcing PR

**主な責務:** Domainイベント定義・EventBus・EventStore・Subscriber

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Event定義 / EventBus / EventStore / Subscriber |
| **追加すべきテスト** | Event発火テスト / Subscriber受信テスト / Append-Onlyテスト / 順序保証テスト |
| **禁止事項** | Event削除（Append-Only原則）/ Eventの内容変更（新Eventで対応）|
| **よくある事故** | 既存Eventを変更してしまう / EventをDomainから直接DB保存 / 重複Event定義 |
| **完了条件** | EventがAppend-Onlyである / Subscriberが独立して動作する / 既存Eventが壊れていない |

---

## 5. API Gateway PR

**主な責務:** APIエンドポイント・Request/Responseマッピング・認証

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Endpoint定義 / Request/ResponseSchema / 認証ミドルウェア |
| **追加すべきテスト** | API Unit Test / Integration Test / 認証テスト / エラーレスポンステスト |
| **禁止事項** | Domainロジックの混入 / DB直接アクセス / 認証のスキップ |
| **よくある事故** | Domainロジックをコントローラに書く / 認証なしエンドポイントの混入 |
| **完了条件** | すべてのエンドポイントに認証がある / DomainはServiceを経由 / エラーが適切に返る |

---

## 6. UI PR

**主な責務:** Screen・Component・Navigation・UX

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Screen / Component / Navigation設定 |
| **追加すべきテスト** | Component Unit Test / Navigation Test / スナップショットTest |
| **禁止事項** | UIからRepositoryを直接呼ぶ / Domain変更 / ビジネスロジックをUIに書く |
| **よくある事故** | Screenに永続化ロジックが混入 / RepositoryをScreenから直接呼ぶ |
| **完了条件** | ScreenはServiceかHook経由でのみDomainと接続 / UIにビジネスロジックがない |

---

## 7. Analytics PR

**主な責務:** 計測イベント・KPI収集・外部Analyticsサービス連携

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Analyticsイベント定義 / 計測実装 / KPI定義ドキュメント更新 |
| **追加すべきテスト** | イベント発火テスト / PII非送信テスト |
| **禁止事項** | ユーザー識別情報（PII）の計測 / Domain変更 / UI変更 |
| **よくある事故** | PIIを含む情報を送信 / Analyticsロジックが他レイヤーに漏れる |
| **完了条件** | PIIが含まれていない / `analytics-os/` のKPI定義と整合している |

---

## 8. AI / Rule Engine PR

**主な責務:** AI統合・Ruleエンジン・推論ロジック・プロンプト管理

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Rule定義 / Ruleエンジン / AIプロンプト（必要な場合）|
| **追加すべきテスト** | Ruleテスト（全条件分岐）/ AIレスポンスのバリデーションテスト |
| **禁止事項** | AIへの未検証プロンプト / Domain外のRuleを混入 / 非決定的ロジックの本番投入 |
| **よくある事故** | Ruleが多すぎて管理不能 / AI依存で決定的テストが書けない |
| **完了条件** | Ruleが全件テストされている / AIを使わずにもフォールバックできる |

---

## 9. Research PR

**主な責務:** データ収集・分析ロジック・研究成果の実装

| 項目 | 内容 |
|-----|------|
| **必須成果物** | 分析スクリプト / データスキーマ / 研究ドキュメント更新 |
| **追加すべきテスト** | データ品質テスト / 再現性テスト |
| **禁止事項** | 未検証の分析結果の本番投入 / 引用なき統計の使用 |
| **よくある事故** | 研究ロジックと本番ロジックの混在 / データのハードコーディング |
| **完了条件** | 分析が再現可能 / `research-os/` の誠実さ原則に準拠 |

---

## 10. Governance PR

**主な責務:** ADR・Binding Decision・OS文書・テンプレート更新

| 項目 | 内容 |
|-----|------|
| **必須成果物** | 更新されたMarkdownドキュメント |
| **追加すべきテスト** | リンク切れチェック / 構造整合性確認 |
| **禁止事項** | コード変更 / 過去のBDの書き換え（追記・廃止のみ）|
| **よくある事故** | 歴史の改ざん（Append-Only違反）/ CANONICAL_SOURCEの未更新 |
| **完了条件** | `CHANGELOG.md` が更新されている / 上位文書と整合している |

---

## 11. Migration PR

**主な責務:** DBスキーマ変更・データ移行・バージョン管理

| 項目 | 内容 |
|-----|------|
| **必須成果物** | Migrationファイル / ロールバック手順 / データ移行スクリプト |
| **追加すべきテスト** | Migration Up/Downテスト / データ整合性テスト / ロールバックテスト |
| **禁止事項** | Migrationと同じPRでDomain/Repository変更 / 本番データの直接変更 |
| **よくある事故** | ロールバックできないMigration / Domain変更が同じPRに混入 |
| **完了条件** | Up/Down両方テスト済み / ロールバック手順が文書化されている |

---

## 複合PRの扱い

1つのPRが複数タイプにまたがる場合は **STOP** してFounderに確認する。
PRは単一タイプに収めることが原則。

**例外（許容される組み合わせ）:**
- Domain + Rule Engine（同一Domainの場合）
- Repository Interface + Factory（同一Repositoryの場合）

**禁止される組み合わせ:**
- Repository + Migration（別PRにする）
- Domain + UI（別PRにする）
- Infrastructure + Migration（別PRにする）
