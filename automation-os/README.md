# Automation OS

## 目的

繰り返し作業の自動化・CI/CDパイプライン・Workflow設計の記録と標準を管理する。
一人創業者が複数事業を動かすための「時間を買うOS」。

## 何を保存するか

- **自動化の判断基準** — 何を自動化するか・しないかの判断軸
- **GitHub Actions 標準構成** — CI/CDのベストプラクティス
- **定期タスクの一覧** — cron・スケジューラーで動くもの一覧
- **通知設計** — どのイベントで・誰に・何を通知するか
- **外部サービス連携の管理** — Webhook・API連携の記録
- **自動化の監視とアラート** — 自動化が壊れたときの検知方法

## 自動化原則

1. **同じ作業を3回やったら自動化を検討** — 但し自動化のコストと効果を比較する
2. **自動化は単純に保つ** — 複雑な自動化は壊れやすい
3. **失敗を検知できるようにする** — 自動化が静かに壊れるのが最悪
4. **手動でも動かせる** — 自動化がなくても動く設計を基本とする

## 現在の自動化一覧

| 自動化 | トリガー | プロダクト | 場所 |
|-------|---------|-----------|------|
| テスト実行 | PR作成・push | ippo | `.github/workflows/` |
| デプロイ | mainマージ | ippo | `.github/workflows/` |

## 今後の再利用計画

- GitHub Actions テンプレートを `templates/APP_STARTER_TEMPLATE/` に含める
- Supabase Edge Functions のデプロイ自動化を標準化

## ファイル構成（今後追加予定）

```
automation-os/
├── README.md
├── AUTOMATION_CRITERIA.md
├── GITHUB_ACTIONS_STANDARDS.md
├── SCHEDULED_TASKS.md
└── MONITORING_ALERTS.md
```
