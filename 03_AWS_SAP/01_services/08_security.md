# セキュリティ/アイデンティティ/コンプライアンス

## IAM

- IDフェデレーション
  - 有効化するとオンプレ環境のADのユーザーを利用可能に
  - 設定手順
    1. オンプレIdPでSAMLメタデータドキュメントを作成
    2. IAMからSAMLプロバイダーを作成。1のメタデータを指定
    3. IAMロールを作成。信頼ポリシーに2のプロバイダーを指定
    4. saml-metadeta.xmlをオンプレIdPに登録 (AWSを登録)
  - アクセス手順
    1. オンプレIdPで認証し、SAMLアサーションを取得
    2. AWS SSOエンドポイントにSAMLアサーションをPOST
    3. STSから認証情報が返り、ログイン成功  
       ※API利用の場合は、STSのAssumeRoleWithSAML利用
- 請求のみのアクセスポリシー
  - aws-portal:ViewBilling/ViewUsageを追加

### STS

- IAMから認証情報の取り消し可能

## KMS

- CMK (Customer Master Key)

## CloudHSM

- 暗号化**キー**の生成・管理

## WAF

- 連携不可一覧
  - EC2
  - S3
  - IGW

## Shield

- Standard
  - レイヤー3,4
- Advanced
  - EIP、EC2、ELBなども保護対象にできる
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
  - 小規模・低コストで基本的機能を提供 (MFAなどはなし)
  - Samba4プロトコルに対応したAD互換のディレクトリ
- AD Connector
  - オンプレ環境やAWS上の既存ディレクトリサービスへの認証プロキシ
- Managed Microsoft AD
  - オンプレのADと信頼関係を構築し、統合認証基盤構築
  - 既存のワークロードの移行で利用する
- ADFS (Active Directory Federation Service)
  - SAML2.0プロトコルに従ってオンプレとAWSの信頼関係構築

## Organizations

- AWSアカウントの新規作成の自動化
- AWSアカウントで発生した料金の一元管理
- CloudTrailの組織に対する有効化
- SCPの定義
  - SCPとIAMロール両方で許可されたアクションが実行可能
  - SCPはデフォルトでFullAWSAccessを持つ
  - SCPで条件を指定するにはDenyを使う

## SSO

- Organizationsで管理される複数のマネコンへのアクセスを許可
- SAML2.0を利用し、Salesforce、Box、Office365などとも統合可能
- 一時的な認証機能で、SAMLに対応
