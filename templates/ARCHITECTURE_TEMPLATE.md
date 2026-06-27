# Architecture Document — [Product Name]

> このドキュメントは `development-os/` の原則に基づいて作成する。

**作成日:** YYYY-MM-DD
**最終更新:** YYYY-MM-DD
**バージョン:** 1.0.0

---

## Overview

<!-- プロダクトの技術的な概要を2〜3段落で -->

## System Context

<!-- システムの外部との関係を記述 -->

```
[ユーザー] → [アプリ] → [Supabase] → [External APIs]
```

## Tech Stack

| レイヤー | 技術 | 選定理由 |
|---------|------|---------|
| Frontend | | |
| Backend | | |
| Database | | |
| Auth | | |
| Hosting | | |
| CI/CD | | |

## Directory Structure

```
src/
├── components/
├── screens/
├── hooks/
├── services/
├── types/
└── utils/
```

## Data Models (Core)

```typescript
// 主要なデータモデルを記述
```

## Key Architectural Decisions

<!-- なぜこのアーキテクチャを選んだか。ADRへのリンクも可 -->

1. **[決定事項]** — [理由]
2. **[決定事項]** — [理由]

## Security Considerations

<!-- 認証・認可・データ保護の方針 -->

## Performance Targets

| 指標 | 目標値 |
|-----|-------|
| App起動時間 | < 2秒 |
| 画面遷移 | < 300ms |
| API応答 | < 500ms |

## Open Questions

<!-- まだ決まっていないこと -->
-

## Change History

| 日付 | バージョン | 変更内容 |
|-----|----------|---------|
| YYYY-MM-DD | 1.0.0 | 初版 |
