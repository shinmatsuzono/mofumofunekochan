# 基本用語
- フォールトトレランス：障害発生しても正常に稼働し続けること

- CapEx（資本的支出 Capital Expenditure）：設備投資
- OpEx（運営支出 Operational Expenditure）：運用費用
    - Enterprise Agreement（EA）や、リザーブドインスタンスはCapexとみなす

- IaaS：仮想マシン以上（EC2）
- PaaS：アプリケーション以上（RDS）
- SaaS：データとアクセス（Snowflake）

- 認証と認可
    - 認証：その人かどうか
        - Azure Active Directory (AD)
            - 認証、SSO、IDサービス、デバイス管理
    - 認可：その人ができるかどうか

# Azure

## リソース管理

### リージョン：地理的隣接
- リージョンペア
    - 各Azureリージョンは同じ地理内の別リージョンとペアにされる
    - リカバリはどちらか一方が優先される
    - メンテナンスは必ず重複しない
- ジオ：国
- リージョンまたぎのアウトバウンドトラフィックは有料

#### Azure特別リージョン
- Azure Government：米国政府機関
- Azure China
- Azure Germany
- その他政府：Azure Global

### 信頼性
- 可用性セット：データセンタ内の冗長化（SLA99.95%）
    - 障害ドメイン（障害範囲を任意の数分離して用意）：物理リソース共有、最大3まで
    - 更新ドメイン（メンテ範囲を任意の数分離して用意）：更新範囲共有、最大20まで
- 可用性ゾーン：AZの冗長化（SLA99.99%）
- SLAに満たないとき：クレジット提供

### ARM (アーム：Azure Resource Manager)：管理レイヤー
- 単位
    - 管理グループ：部署
    - サブスクリプション：課金単位
    - リソースグループ
        - 異なるAZでもグルーピング可能
        - 所属できるのは1つまで
        - 環境や種類で分離（アクセス制御可能単位）
    - リソース
- サブスクリプション移動
    - 全てはできない
    - 移動中はリソースグループがロックされる


### 管理ツール
- Azure Portal (マネジメントコンソール)
- Azure PowerShell / Azure CLI (AWS CLI)
    - 利用するにはPowerShellCore + Azureモジュール
- Azure Cloud Shell (AWS Cloud Shell)
- タグ：使用料レポートを分ける用途に使える


## リソース

### Azure Compute
- Azure VM (EC2)
- VM Scale Sets (Auto Scaling)
- App Services (Light Sail: PaaS)
- Functions (Lambda)
- Azure Marketplace (AWS Marketplace)


### コンテナ
- Azure Container Instances
- Azure Kubernetes Service


### 仮想ネットワーク
- Azure Virtual Network (V-Net : VPC)
- Azure Load Balancer (NLB)
- Azure Application Gateway (ALB)
- VPN Gateway
- コンテンツ配信ネットワーク (Cloud Front)
- ローカルネットワークゲートウェイ... オンプレVPNとの接続など
- ピアリング接続：グローバル、通常の２種類


### Azure Storage
- IaaS
    - ディスク（EBS）
    - ファイル（EFS）
- PaaS
    - コンテナ（S3）
    - テーブル（DynamoDB）
    - キュー（SQS）


#### ストレージ
- プライマリリージョンで**3回**レプリケートされる
- セカンダリリージョンに非同期的にコピーされる
- Azure BLOB Strage
    - ホット
    - スタンダード
    - クール
    - アーカイブ
 

### Azure Database
- Azure Cosmos DB (DynamoDB)
- Azure SQL DB (RDS)
- Azure Database Migration (Database Migration Service) 

### IoT
- Azure IoT Central (可視化SaaS)
- Azure IoT Hub (メッセージングハブ)
 

### Bigdata
- Azure Synapse Analytics (RedShift)
    - エンドツーエンドの統合環境
- Azure HD Insight (EMR)
- Azure Data Lake Analytics (Kinesis Analytics, Athena)
- Azure Databricks：Sparkベースの分析サービス
 

### AI
- Azure Machine Learning Service (Sage Maker / コード要)
- Azure Machine Learning Studio (Sage Maker / コード不要)
 

### サーバレス
- Azure Functions (Lambda)
- Azure Logic Apps (Step Functions / SWF(Simple Workflow Service))
- Azure Event Grid (Event Bridge)
 

### DevOps
- Azure DevOps (Code Deploy / Code Commit / Code Pipeline / Code Build)
- Azure DevTest Labs：テスト環境生成
- Azure Stack：自分のデータセンターを使用できる
- Azure Repos：コード管理ツール


## セキュリティ

### アクセス制御
- Azure Firewall (WAF)
- Azure 分散型サービス拒否 [DDoS保護] (AWS Shield)
    - Basic (自動有効) / Standard：レポート生成あり
    - ネットワークセキュリティグループ(NSG)：リージョン内で使い回し可能
- アプリケーションセキュリティーグループ(ASG)

### ガバナンス
- サブスクリプション (アカウント)
    - 1つのADに対して複数のサブスクリプションが紐づく
- Azure Policy (Organizations)
    - ポリシー
    - イニシアチブ：PCISSやISO27001など、ポリシーの集合
- Azure Active Directory (IAM)
    - ロールベースアクセスコントロール (RBAC)
        - 職務に応じたロールをユーザに付与
    - リソース制約 [ロック]
        - CanNotDelete（削除ロック）
        - ReadOnly（読み取り専用ロック）
    - AD Connector：ハイブリッドクラウドのID接続
- Azure Blueprints
    - ポリシーやリソースを横展開

### Azure AD Identity Protection
- 認証、SSO、IDサービス、デバイス管理
    - ユーザーリスクポリシー：パスワード
    - サインインリスクポリシー：MFA
    - IDベースのリスク検出と修復
    - ポータルデータからリスク調査
    - リスク検出データエクスポート

### Synchronization Service Manager
- AD Connectを利用してSSOを構成する際に、同期結果を確認できる

### モニタリング
- Azure Monitor (CloudWatch)
- Azure Resource Health (Personal Health Dashboard)
- Azure Log Analytics：ハイブリッドのログ監視

### セキュリティサービス
- Azure Security Center (Inspector)
    - セキュリティ要件の適合チェック

### コンプライアンス
- Service Trust Portal [STP] (Artifact)

### コスト
- Azure Cost Management (Cost Exploler)
- Azure Advisor (Trusted Advisor)：コスト削減レコメンデーション
- TCO計算ツール：Azureに移行した際のコスト見積もり
- AzureExpressRoute
    - オンプレ→クラウドのデータトラフィックは無料
    - クラウド→オンプレのデータトラフィックは有料


### ポリシー・セキュリティ
- Azure Policy
    - Azure自体のポリシー準拠状況
    - リソースの作成・更新・削除に関するポリシーの割り当て... ロールはアクセス許可
- **Microsoft** Trust Center：セキュリティ標準などの**情報提供**
- Azure Security Center
    - セキュリティ規制の要件を満たしているか判定
    - オンプレも監視できる
- コンプライアンスマネージャー：監査・リスク評価ツール
- Azure Monitor：アプリケーション診断
- Azure Activity Log：ユーザの操作履歴
- Azure Information Protection [AIP]
    - ラベル付与で情報種別管理
- Azure Advanced Threat Protection [ATP] (Guard Duty)
- Azure Key Vault (KMS)
- Azure Service Health：通知可能

### サポートリクエスト
- Azure Portal
    - Basic (無料)：テクニカルサポートなし
    - Developer ：メールサポートあり
    - Standard：電話サポート
    - Professional Direct：電話サポート
    - Premium：担当者あり
- Azure サポートチケット REST API
- サポート終了は12ヶ月前に通知

