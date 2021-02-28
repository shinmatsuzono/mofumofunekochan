## リソース管理
- 管理グループ：部署
- サブスクリプション：課金単位
- リソースグループ：異なるAZでもグルーピング可能
- リソース

### ロック
- 削除ロック
- 読み取り専用ロック

## ストレージ
- プライマリリージョンで**3回**レプリケートされる
- セカンダリリージョンに非同期的にコピーされる

## ネットワーク
- ローカルネットワークゲートウェイ... オンプレVPNとの接続など

## Azure AD Identity Protection
- IDベースのリスク検出と修復
- ポータルデータからリスク調査
- リスク検出データエクスポート

### Synchronization Service Manager
- AD Connectを利用してSSOを構成する際に、同期結果を確認できる

## PaaS
- Azure App Service

## コンプライアンス

### 信頼性
- 2AZ：99.99%
- SLAに満たないとき：クレジット提供

### コスト
- Azure Advisor：コスト削減レコメンデーション
- TCO計算ツール：Azureに移行した際のコスト見積もり
- AzureExpressRoute：オンプレ→クラウドのデータトラフィックは無料

### ポリシー・セキュリティ
- Azure Policy
    - Azure自体のポリシー準拠状況
    - リソースの作成・更新・削除に関するポリシーの割り当て... ロールはアクセス許可
- Microsoft Trust Center：セキュリティ標準などの**情報提供**
- Azure Security Center
    - セキュリティ規制の要件を満たしているか判定
    - オンプレも監視できる
- コンプライアンスマネージャー：監査・リスク評価ツール
- Azure Monitor：アプリケーション診断
- Azure Activity Log：ユーザの操作履歴

### サポートリクエスト
- Azure Portal
- Azure サポートチケット REST API

### Azure特別リージョン
- Azure Government：米国政府機関
- Azure China
- Azure Germany
- その他政府：Azure Global

