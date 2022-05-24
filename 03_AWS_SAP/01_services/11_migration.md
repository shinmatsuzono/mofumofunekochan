# 移行

## DMS (Database Migration Service)

- 異なるDBMS間もサポート
  - SCTと組み合わせて移行

## SCT(Schema Conversion Tool)

- DBMS間でスキーマの変換

## SMS(Server Migration Service)

- オンプレの仮想環境(VMware/Hyper-V)上のサーバーをAMIとして移行
- リホスト方式
  - ワークロードの変更ほぼなし
  - 比較的短期間
  - 大量サーバー移行
- ダウンタイム最小化
- ネットワーク帯域への影響小
- VMをAMIとして漸進的にアップロードし、移行時のダウンタイムを最小にする
- インポートプロセスは自動

## Application Discovery Service

- オンプレのアプリやインフラの情報収集
  - エージェント方式
  - エージェントレス方式

## Migration Hub

- DMS、SMSや3rdPartyなども含めてオンプレ環境の情報収集

## VM Import/Export

- SMSと同じ（SMSの方が新しい）
- Exportはオンプレ化

## Snow Family

- Snowball: データ保存に特化
- Snowball Edge
  - CPU搭載で加工や集約をしたのちにAWSに移行可能
  - 80TB
- Snowmobile: トレーラー車
