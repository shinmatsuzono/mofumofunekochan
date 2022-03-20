# ストレージ

## S3

### S3 Transfer Acceleration

- CloudFrontエッジロケーションを使用
- オブジェクトの転送を高速化

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
    - オンプレ側にデータがあるので低レイテンシー
  - Chached
    - データ全体をS3に移動し、高頻度アクセスデータのみオンプレ
    - オンプレのコストを抑制する
- テープゲートウェイ

## CloudFront

- S3の静的コンテンツをエッジロケーションを通してグローバル配信
