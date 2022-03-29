# 開発者用ツール

## CodeCommit

## CodeBuild

## CodeDeploy

- Lambdaをデプロイ時にトラフィック制御可能
  - Canary
    - 10% -> 90%など
  - 線形
  - All at once

## CodePipeline

## Code Star

- CodeSeriesをワンクリックで構成
- デプロイ先はEC2, Elastic Beanstalk, Lambdaのみ

## X-Ray

- アプリの分析とデバッグ
- AWSサービス間のリクエストなどの問題をトレーシング
- Lambdaのボトルネック箇所を判別
  - レイテンシーの解析など
