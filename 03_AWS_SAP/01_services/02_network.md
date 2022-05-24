# ネットワーク

## VPC

- CIDRブロックを追加できる

### ENI

- INトラフィックとBEトラフィックを同時制御する用途など

## VPCエンドポイント

### PrivateLink(インターフェース型VPCE)

- VPC to オンプレ/他VPC/AWSサービスをセキュアに簡単に接続
  - IGWが不要になる
  - NATGWが不要になる
  - サービス接続制御が可能
  - パブリックIP不要
  - 独自アプリをプライベート公開できる

### Gateway型VPCE

- S3
- DynamoDB

## ENI(Elastic Network Interface)

- NICの役割
- 複数ネットワーク割り当てなど

## DirectConnect

- デフォルトではIPSecで暗号化されていない
  - Amazon VPC VPNと組み合わせる必要あり
- 他リージョンへの接続は不可
  - リージョン間VPCピアリングを利用
- 必要な設定(VPN冗長のとき)
  - オンプレ側
    - VPN用のカスタマーゲートウェイ(CGW)の設定
  - VPC側
    - 仮想プライベートゲートウェイ(VPGW)の設定
    - VPCルートテーブルの設定（VPGW宛）
    - 複数の場合
      - Direct Connect Gateway
      - 仮想プライベートインターフェース(VIF)を経由
- VPN→DCへの移行はBGP優先度の設定で行う

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
- IPv6は未サポート
- マルチAZは手動

## ユースケース

### IPv6への対応
  
1. IPv6 SIDRブロックをVPCとサブネットに関連づけ
2. rtb, sg, naclのIPを更新
3. EC2に割り当て

## VPCFlowLogs

- Networkの通信の疎通確認
- 不正アクセス防止はできない

## VPCピアリング

- リージョン間VPCピアリング
  - データ転送量課金
  - AWSのマネージドサービス

### VPCピアリングできないとき

- CIDRの重複
- 推移的なピアリング接続（A-(B)-C）
  - この場合はA-Cと繋ぐ
- ピアリング数は50まで
  - ハードリミットは125
  - 大規模ネットワークが必要な場合はTransit VPCを採用
    - ハブアンドスポーク型のソリューションを検討

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

- エッジ最適化APIエンドポイント
  - 最寄りのCloudFrontエッジロケーションにルーティング
  - ユーザ管理をCognitoで実施可能

- 429 Limit Exceeded
  - API Gateway 自体のレート制限

- 502 Bad Gateway
  - Lambda関数の同時実行制限など内部サーバーエラー

## Route53

- デプロイ
  - Evaluate Target Health
  - CNAMEの切り替えでBlue/Green Deployができる
  - 加重ラウンドロビンでABテストが可能
- ホスティング
  - プライベートホストゾーン(コンテナ)
    - 1つのPHZ用VPCを作成し、ピアリング接続してそれぞれにPHZを関連づけることで、多数のVPCを管理できる
- DDoS対策
  - シャッフルシャーディング
  - Anycastルーティング
