# ネットワーク

## VPC

## VPCFlowLogs

- Networkの通信の疎通確認

## VPCピアリング

- リージョン間VPCピアリング
  - データ転送量課金

### VPCピアリングできないとき

- CIDRの重複
- 推移的なピアリング接続（A-(B)-C）
  - この場合はA-Cと繋ぐ
- ピアリング数は50まで
  - ハードリミットは125
  - 大規模ネットワークが必要な場合はTransit VPCを採用
    - ハブアンドスポーク型のソリューションを検討

## VPCエンドポイント

### PrivateLink(インターフェース型VPCE)

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
- 他リージョンへの接続は不可
- 必要な設定
  - オンプレ側
    - カスタマーゲートウェイの設定
  - VPC側
    - 仮想プライベートゲートウェイの設定
    - VPCルートテーブルの設定（VPGW宛）

### DirectConnect Gateway

- 時間当たり課金

### VIF

- PublicVIF パブリックリソースに接続するときに使う(S3など)
- PrivateVIF VPCに接続するときに使う

## Managed VPN

- ネットワーク機器の用意が必要
- コスト有利
- VPC側には下記を作成
  - オンプレ側機器に対応した Customer Gateway (CGW)
  - AWS側のVPNを有効にするためのVirtual Private Gateway (VGW)

## NAT Gateway

- 特定のURLへのアウトバウンドのみ許可、はできない
  - Proxy機能を持ったEC2インスタンスを作成する

## ユースケース

### VPN接続したい

- **AWS マネージド VPN**
  - オンプレNW機器 - VPCにアタッチされたAWSマネージド型NW機器へのハードウェアVPN接続
- **AWS VPN CLOUDHUB**
  - 複数のリモートブランチオフィスをVPCに接続するハブアンドスポークモデル
- **ソフトウェアVPN**
  - リモートNW上の機器から、VPC内で実行されているユーザー管理型ソフトウェアVPNアプライアンスへのVPN接続
- **IPSec VPN接続**
  - フルメッシュ接続
  - マネージドサービスはインターリージョンVPC

### 公衆回線からVPC

- VPC側にEC2にアプライアンス型のSSL VPNソリューションを配置
  - LambdaやRDSとは接続できない
- PC側にSSL VPNクライアントをインストール


## API Gateway

- 429 Limit Exceeded
  - API Gateway 自体のレート制限

- 502 Bad Gateway
  - Lambda関数の同時実行制限など内部サーバーエラー
