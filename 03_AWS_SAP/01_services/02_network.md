# ネットワーク

## VPC

## DirectConnect

- 他リージョンへの接続は不可
  - リージョン間VPCピアリング/DCGWを利用
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
- リージョン間VPCアクセス

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

## API Gateway

- エッジ最適化APIエンドポイント
  - 最寄りのCloudFrontエッジロケーションにルーティング
  - ユーザ管理をCognitoで実施可能

### Lambdaとの統合

- APIGWがLambdaを呼び出すためのIAMロールを設定
  - LambdaのARNを指定したロールにする
  - Lambdaオーソライザー関数を設定する

## Route53

- デプロイ
  - Evaluate Target Health
  - CNAMEの切り替えでBlue/Green Deployができる
- DDoS対策
  - シャッフルシャーディング
  - Anycastルーティング
