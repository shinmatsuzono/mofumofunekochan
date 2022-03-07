# ネットワーク

## VPC

### VPCピアリング

- CIDRの重複は不可

## PrivateLink

- VPC to オンプレ/他VPC/AWSサービスをセキュアに簡単に接続
  - IGWが不要になる
  - NATGWが不要になる
  - サービス接続制御が可能
  - パブリックIP不要
  - 独自アプリをプライベート公開できる

## DirectConnect

- デフォルトではIPSecで暗号化されていない
  - Amazon VPC VPNと組み合わせる必要あり
- 単一障害点となりうるので、バックアップとしてVPNを使う

### VIF

- PublicVIF パブリックリソースに接続するときに使う(S3など)
- PrivateVIF VPCに接続するときに使う

## ユースケース

### VPN接続したい

- **AWS マネージド VPN**
  - オンプレNW機器 - VPCにアタッチされたAWSマネージド型NW機器へのハードウェアVPN接続
- **AWS VPN CLOUDHUB**
  - 複数のリモートブランチオフィスをVPCに接続するハブアンドスポークモデル
- **ソフトウェアVPN**
  - リモートNW上の機器から、VPC内で実行されているユーザー管理型ソフトウェアVPNアプライアンスへのVPN接続

## API Gateway

- 429 Limit Exceeded
  - API Gateway 自体のレート制限

- 502 Bad Gateway
  - Lambda関数の同時実行制限など内部サーバーエラー
  