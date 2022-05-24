# ストレージ

## S3

### S3 Transfer Acceleration

- CloudFrontエッジロケーションを使用
- オブジェクトの転送を高速化

### ストレージタイプ

- Standard-IA
  - 低頻度だがミリ秒単位の取り出し
- Glacier
  - Instant Retrieval
    - すぐに取り出せる
    - 四半期に1度のアクセス
  - Flexible Retrieval
    - 数時間以内の取り出し
    - 年に1,2回の取り出し
    - アーカイブ時に圧縮でコスト効率高くなる
    - DynamoDBにアーカイブIDを格納すると便利
  - Deep Archive
    - 48時間以内に取り出し
    - 年に1,2回の取り出し

### ユースケース

#### API Gateway と連携したい

- CORS(GW側) + Web Hosting

## EBS

- EBS最適化で、EC2とEBS専用のネットワーク確保が可能

## EFS

- LinuxをOSとする複数のEC2からマウント可能

## Storage Gateway

- ファイルゲートウェイ
  - S3へのNFSやSMBなどのI/Fを提供
- ボリュームゲートウェイ
  - Stored
    - オンプレのスナップショットをS3に非同期バックアップ
  - Chached
    - データ全体をS3に移動し、高頻度アクセスデータのみオンプレ
- テープゲートウェイ

## CloudFront

- オリジンフェイルオーバー機能
  - オリジンが500系のエラーを返したときに、セカンダリオリジンで回答
  - ALBやRoute53のUnhealthy判定より厳密に可用性改善可能
- オリジンにEC2のPrivateIPは設定できない
- 署名付きURLまたは署名付きCookieでアクセス制限

### HTTPS化

- HTTPS Only
- Redirect HTTP to HTTPS
- SSL/TLS証明書
