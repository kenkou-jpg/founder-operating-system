# 10 — Review Checklist

> PRレビュー時のチェックリスト。
> Founderがレビューするとき、またはAIがセルフレビューするときに使う。

---

## 1. Scope Integrity（スコープの整合性）

- [ ] PR Scopeに定義された実装がすべて完了している
- [ ] Scopeに含まれないものが混入していない（Non-goals違反がない）
- [ ] Forbidden Changesが変更されていない
- [ ] 「ついでに」「一緒に」の実装が混入していない
- [ ] 前PRの責務を再実装していない
- [ ] 次PRの責務を先取り実装していない

**判定: PASS / FAIL**

---

## 2. Architecture Integrity（アーキテクチャの整合性）

- [ ] レイヤー境界の依存方向が正しい（`05_ARCHITECTURE_CHECKLIST.md` 参照）
  - UI → Domain/UseCase のみ（Repository直接依存なし）
  - Domain → 外部サービス依存なし
  - Repository → UI依存なし
- [ ] 循環依存がない
- [ ] God Objectがない（1クラス1責務）
- [ ] Architecture Guardテストが追加・更新されている（必要な場合）
- [ ] 既存のArchitecture Guardテストが全PASS

**判定: PASS / FAIL**

---

## 3. Data Integrity（データの整合性）

- [ ] DBへの直接アクセスがRepository外にない
- [ ] localStorageへの直接アクセスがRepository外にない
- [ ] 同じデータが複数のStateに重複して保持されていない（SSOT）
- [ ] 型定義が重複していない（単一の場所で定義されている）
- [ ] データの変換ロジックが適切なレイヤーに置かれている

**判定: PASS / FAIL**

---

## 4. Event Integrity（イベントの整合性）

*Event Sourcing を使用する場合のみ*

- [ ] 既存Eventを変更・削除していない（Append-Only）
- [ ] 新規Eventの命名が既存Eventと重複していない
- [ ] Eventの順序が保証されている
- [ ] Subscriberが正しいEventを受信している
- [ ] EventのPayloadに不要な情報が含まれていない

**判定: PASS / N/A**

---

## 5. Security（セキュリティ）

- [ ] 認証なしでアクセスできるエンドポイントがない（APIを追加した場合）
- [ ] ユーザーA のデータをユーザーB が取得できない（認可）
- [ ] パスワード・APIキー・秘密鍵がコードにハードコードされていない
- [ ] ユーザー入力がサニタイズされている
- [ ] SQLインジェクション・XSSの脆弱性がない
- [ ] 機密情報がログに出力されていない

**判定: PASS / FAIL**

---

## 6. Privacy（プライバシー）

- [ ] 収集するデータが `legal-os/` のプライバシー方針に準拠している
- [ ] PII（個人識別情報）が不必要に収集されていない
- [ ] PIIがAnalyticsサービスに送信されていない
- [ ] ユーザーのデータ削除要求に対応できる設計になっている
- [ ] データの保持期間が定義されている（必要な場合）

**判定: PASS / FAIL**

---

## 7. Performance（パフォーマンス）

- [ ] 不必要なデータベースクエリがない（N+1問題等）
- [ ] 大量データ処理でメモリリークが起きない
- [ ] 不必要な再レンダリングが起きない（UIの場合）
- [ ] 非同期処理が適切に実装されている（async/await / Promise）
- [ ] タイムアウト処理が実装されている（外部API呼び出しの場合）

**判定: PASS / FAIL / N/A**

---

## 8. Maintainability（保守性）

- [ ] コードが理解しやすい（命名・構造・コメント）
- [ ] 同じロジックが複数箇所に書かれていない（DRY）
- [ ] マジックナンバー・マジック文字列が使われていない（定数化）
- [ ] エラーハンドリングが適切（エラーを握りつぶしていない）
- [ ] テストがドキュメントとして機能している（テスト名で仕様がわかる）
- [ ] TODO / FIXME コメントが残っている場合はIssueを立てている

**判定: PASS / FAIL**

---

## 9. Founder Workload（Founderの負担）

*一人Founderが複数事業を運営するための観点*

- [ ] このPRの変更を理解するのに過度な時間がかからない
- [ ] Completion Reportを読めばPRの内容が把握できる
- [ ] 次のPRを始めるために必要な情報が揃っている
- [ ] Founderの承認なしに「ついでに」変更した部分がない
- [ ] 自動化できるレビュー項目が自動化されている

**判定: PASS / FAIL**

---

## 10. Future Reusability（再利用性）

*Founder OSの「Reusable by Default」原則に基づく観点*

- [ ] このPRで作ったパターンは他プロダクトでも再利用できるか
- [ ] プロジェクト固有のハードコーディングが最小化されているか
- [ ] 設定・定数が適切な場所に分離されているか
- [ ] 将来の変更に対して拡張しやすい構造になっているか
- [ ] 再利用できるパターンを `knowledge-os/` に記録したか（任意）

**判定: PASS / N/A**

---

## Review Result

```
PR Review Result — PR-[番号]
============================
1. Scope Integrity:      PASS / FAIL
2. Architecture:         PASS / FAIL
3. Data Integrity:       PASS / FAIL
4. Event Integrity:      PASS / N/A
5. Security:             PASS / FAIL
6. Privacy:              PASS / FAIL
7. Performance:          PASS / FAIL / N/A
8. Maintainability:      PASS / FAIL
9. Founder Workload:     PASS / FAIL
10. Future Reusability:  PASS / N/A

→ Overall: APPROVED / CHANGES REQUESTED

Changes Requested:
- （ForfAIL項目の詳細と修正依頼）
```

**APPROVED になるまでmergeしない。**
