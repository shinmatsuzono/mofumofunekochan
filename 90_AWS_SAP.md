# ネットワーク

## VPC

#### VPN接続したい
- **AWS マネージド VPN**
  - オンプレNW機器 - VPCにアタッチされたAWSマネージド型NW機器へのハードウェアVPN接続
- **AWS VPN CLOUDHUB**
  - 複数のリモートブランチオフィスをVPCに接続するハブアンドスポークモデル
- **ソフトウェアVPN**
  - リモートNW上の機器から、VPC内で実行されているユーザー管理型ソフトウェアVPNアプライアンスへのVPN接続

## Storage Gateway



# ストレージ

## S3

#### API Gateway と連携したい
- CORS(GW側) + Web Hosting

# Function

## Lambda
- 同時実行制限で呼び出し調整可能

<br>

# IoT

## Kinesis Data Streams
- 単一シャードは1MB/sまで


<br>

# マイクロサービスアーキテクチャ

## API Gateway

#### 429 Limit Exceeded
- API Gateway 自体のレート制限

#### 502 Bad Gateway
- Lambda関数の同時実行制限など内部サーバーエラー

<br>

# 管理

## CloudWatch

#### 過剰な支出を防ぎたい
- 請求アラート：CloudWatch Alarm + SNS

<br>

## CloudFormation

#### 複数のアカウントにリソース作成
- StackSets：1回の操作で複数のアカウントにリソースをデプロイ可能

<br>

# セキュリティ

## Guard Duty

#### 調査結果を通知したい
- SNS
- CloudWatch Event

<br>

## AWS SSO
- 一時的な認証機能
- SAMLに対応
- ログインのためのユーザーポータル
- 

## AWS Directory Service for Microsoft Active Derectory
- AWS Managed Microsoft AD
- AD Connector ... オンプレユーザーがAD経由でAWSサービスにアクセス
- Simple AD ... 小規模・低コストで基本的機能を提供 (MFAなどはなし)

<br>

# 移行

## SMS (Server Migration Service)
- VMをAMIとして漸進的にアップロードし、移行時のダウンタイムを最小にする
- インポートプロセスは自動