# 管理ツール

## CloudWatch

## AutoScaling

- DynamoDB、ECS、Auroraのリードレプリカも対象
- Auto Healing(最小数1)で耐障害性確保

## CloudFormation

- StackSets
  - 1回の操作で複数のアカウントにリソースをデプロイ可能
- Deletion Policy
  - EBSやRDSの削除を防ぐ

## CloudTrail

- AWS上のAPIアクセスを監査ログとして残す
- CloudTrail Insightsで異常パターンの定義と検出
  - CloudWatch Eventsで通知
- ログからAWS操作のRejectを特定

## Config

- 構成変更を記録
- Config Rules
  - 違反した場合通知する
  - Lambdaでカスタムルール
  - タグ付与ルールを作成

## OpsWorks

- ChefやPuppet(インフラ構成管理ツール)の利用
- CFnスタック
  - コンポーネントで構成要素をモデル化し、レシピで構成管理
- Stack
  - Service単位で分割
  - Recipe = Service * Layer

## SystemsManager

- サーバーの運用管理など
- インベントリ：ソフトウェア情報収集
- オートメーション：定期実行ジョブを自動化
- 実行コマンド：レジストリの編集など運用管理を自動化
- パッチマネージャー：ベースライン定義したパッチをメンテナンスウィンドウで自動適用
- メンテナンスウィンドウ：運用管理タスク実行時間枠をスケジュール
- ステートマネージャー：サーバー設定を保持

## Trusted Advisor

- AWSのリソースのベスプラ適用状況をチェック
  - コスト最適化
  - パフォーマンス
  - セキュリティ
  - フォールトトレランス
  - サービス制限
