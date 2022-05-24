# インテグレーション

## SNS

- DLQの設定が可能

## SQS

- 失敗はCWで監視し、検出した場合は再送付用のSQSから読み出し再送
- WEB3層をさらにさらに高可用性にする用途など

## SES

## SWF

- ワークフロー実行基盤サービス
- ワークフローアプリケーション
- 親プロセスに子プロセスを返す場合に利用

## API Gateway

### Lambdaとの統合

- APIGWがLambdaを呼び出すためのIAMロールを設定
  - LambdaのARNを指定したロールにする
  - Lambdaオーソライザー関数を設定する

## Step Functions

- AWSサービスと連携

## Elastic Transcoder

- 動画Transcode
