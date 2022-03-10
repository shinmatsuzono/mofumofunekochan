# セキュリティ/アイデンティティ/コンプライアンス

## IAM

- IDフェデレーション
  - 有効化するとオンプレ環境のADのユーザーを利用可能に

### STS

## KMS

- CMK (Customer Master Key)

## CloudHSM

- 暗号化キーの生成・管理

## ACM

## WAF

## Shield

- Standard
  - レイヤー3,4
- Advanced
  - ElasticIP、ELBなども保護対象にできる
  - レイヤー3,4,7
  - DRTから24365サポート

## Cognito

- 3rd PartyやADのIDフェデレーション
- User Pools というマネージドユーザーディレクトリ作成可能

## Secrets Manager

- データベースの認証情報やAPIキーを管理・ローテーション

## GuardDuty

- AWS上の操作をモニタリングし、脅威を検出

## Inspector

- EC2インスタンスの脆弱性診断・検出

## Macie

- AWS上の機密データを機械学習で自動検出・分類・保護

## Directory Service

- SimpleAD
  - Samba4プロトコルに対応したAD互換のディレクトリ
- AD Connector
  - オンプレ環境やAWS上の既存ディレクトリサービスへの認証プロキシ
- Managed Microsoft AD
  - オンプレのADと信頼関係を構築し、統合認証基盤構築

## Organizations

- AWSアカウントの新規作成の自動化
- AWSアカウントで発生した料金の一元管理
- SCPの定義
  - SCPとIAMロール両方で許可されたアクションが実行可能

## SSO

- Organizationsで管理される複数のマネコンへのアクセスを許可
- SAML2.0を利用し、Salesforce、Box、Office365などとも統合可能
