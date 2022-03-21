# コスト最適化

## リザーブドインスタンス

- 1年or3年

## スポットインスタンス

- 上限コストがスポット価格を下回ると強制シャットダウン
- スポットフリート
  - EC2リソースのターゲット容量に合わせて稼働を制御
  - AZ障害時に活用可能
- スポットブロック
  - 指定した時間(最大6時間)は稼働を保証する

## Consolidated Billing(一括請求)

- Organizationで複数AWSアカウントに請求

## CostExprorer & AWS Budgets

- 予算アラート機能もあり
- 細かく監視が可能

## タグ

- タグづけの強制
  - aws:RequestTag
  - aws:TagKeys

### コスト配分タグ

- Billing Dashboardから有効化

## 請求アラート

- CloudWatch Alarm + SNS
