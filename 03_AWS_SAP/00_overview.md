# IoT

## Kinesis Data Streams

- 単一シャードは1MB/sまで

# 管理

## CloudWatch

#### 過剰な支出を防ぎたい

- 請求アラート：CloudWatch Alarm + SNS

## CloudFormation

#### 複数のアカウントにリソース作成

- StackSets：1回の操作で複数のアカウントにリソースをデプロイ可能

# セキュリティ

## Guard Duty

#### 調査結果を通知したい

- SNS
- CloudWatch Event

## AWS SSO

- 一時的な認証機能
- SAMLに対応
- ログインのためのユーザーポータル

## AWS Directory Service for Microsoft Active Derectory

- AWS Managed Microsoft AD
- AD Connector ... オンプレユーザーがAD経由でAWSサービスにアクセス
- Simple AD ... 小規模・低コストで基本的機能を提供 (MFAなどはなし)

# 移行

## SMS (Server Migration Service)

- VMをAMIとして漸進的にアップロードし、移行時のダウンタイムを最小にする
- インポートプロセスは自動