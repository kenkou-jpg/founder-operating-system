# Operating Principles — 事業横断の運営原則

> どのプロダクト・どのフェーズでも変わらないルール。

## 1. Ship Quality or Don't Ship

「動くゴミ」は出さない。スピードより品質。
ただし「完璧」を理由に出荷を遅らせることも禁止。
**基準：自分が誇りを持ってユーザーに渡せるか。**

## 2. Document First

- 決定はドキュメントに書いてから実行する
- コードより先に設計を書く（ADR / ARCHITECTURE_TEMPLATE）
- 「なぜそうしたか」を残す。「何をしたか」はコードを見ればわかる

## 3. One Source of Truth

`CANONICAL_SOURCE.md` に従う。
情報は一箇所で管理し、コピーしない。

## 4. Automate the Repeatable

同じ作業を3回やったら、自動化を検討する。
自動化のルールは `automation-os/` に記録する。

## 5. Metrics Over Feelings

「なんとなく調子いい」は指標ではない。
KPIを定義し、定期的に確認し、意思決定に使う。
KPI定義は `analytics-os/` がCanonical Source。

## 6. User First, Always

機能追加・価格変更・UI変更——すべて「ユーザーにとってどうか」が最初の問い。
売上や利便性は二番目。

## 7. Long Game Thinking

四半期の数字より、3年後の位置取りを優先する。
技術的負債は蓄積させない。リファクタリングは機能開発と同等に扱う。

## 8. Async by Default

ミーティング・リアルタイム同期に依存しない。
すべての重要な情報はドキュメントに存在し、非同期で参照できる。

## 9. Sustainable Pace

燃え尽きるペースで働かない。
週40時間以内を目安とし、クリエイティブな仕事を優先する時間帯を確保する。

## 10. Portfolio Thinking

各プロダクトは独立して評価するが、OS・ブランド・ナレッジは共有資産。
一つのプロダクトで学んだことは、他に転用する。

---

## Principle Conflicts

原則同士が衝突したとき（例：品質 vs スピード）は以下の優先順位に従う：

1. ユーザーの安全・データ保護
2. 品質（Ship Quality or Don't Ship）
3. 長期思考
4. その他の原則

迷ったときは `governance/DECISION_LOG.md` に状況と判断を記録する。

---

## Review Cadence

四半期ごとに見直す。原則の変更は `governance/CHANGELOG.md` に記録する。
