# 応用情報技術者試験程度の知識のまとめ

## 基礎理論

### 集合と論理

#### 冪（べき）集合
U = {1,2,3}
Uの冪集合 = {φ, 1, 2, 3, {1,2}, {1,3}, {2,3}, {1,2,3}}


#### 真部分集合
A ⊂ B かつ A ≠ B


#### 対称差
A △ B （AとBの排他的論理和：A ∪ B - A ∩ B）


#### 条件命題
条件命題 = 命題関数


#### 複合命題
| 連言命題 | 選言命題 | 否定命題 | 含意命題 |
| ---- | ---- | ---- | ---- |
| pかつq | pまたはq | pでない | pならばq |
| p ∧ q | p ∨ q | ¬p | p → q |


#### カルノー図
¬A・¬B・¬D + B・D

| ABCD | 00 | 01 | 11 | 10 |
| ---- | ---- | ---- | ---- | ---- |
| 00 | 1 | | | 1 |
| 01 | | 1 | 1 | |
| 11 | | 1 | 1 | |
| 10 | | | | |


### 情報理論と符号化


#### 情報量
**情報量** *I (J) = -log(2)P(J)*
J：事象
P(J)：事象Jの起こる確率

**平均情報量** *H=Σ{P(J)×I(J)*


#### 情報源符号化
**ハフマン符号化**：木で確率に応じてビット化
**ランレングス符号化**：連続を数字で表現


#### ディジタル符号化
**パルス符号変調（PCM: Pulse Code Modulation）**
1. 標本化
2. 量子化
    - 量子化ビット数：8ビットで0-255の数値に変換
3. 符号化 

**標本化定理**：サンプリング周波数を上限周波数の2倍とする

*ディジタルデータ量/s = サンプリング周波数 × 量子化ビット数*


### オートマトン

省略


### 形式言語

#### BNF記法

・<>で括っているものは非終端


#### 逆ポーランド記法

・後行順序木（帰りがけのなぞり）


#### 正規表現

1. [m-n]：m-nまでの連続した文字の中の1文字
2. *：直前の正規表現の0回以上の繰り返し
3. +：直前の正規表現の1回以上の繰り返し
4. ?：直前の正規表現の0回or1回の繰り返し
5. (文字列)：文字列は1つのまとまり


### グラフ理論

**トポロジカル順序**：非サイクリックグラフで1列に並べた時の並び


### 確率と統計

### 回帰分析

### 数値計算

### 人工知能（AI）

## アルゴリズムとプログラミング

### リスト

### スタックとキュー

### 木

### 探索アルゴリズム

### 整列アルゴリズム

- ヒープソート：最小値を正しい位置にする（heap:積み重ね）
- シェルソート：あるシェルごとに分けて整列を繰り返す
- クイックソート：基準値を決めて、大小を振り分ける
- バブルソート：隣あう要素を入れ替え続ける


### 再帰法

### プログラム言語

- 値呼び出し：`let`
- 参照呼び出し：`var`

## ハードウェアとコンピュータ構成要素

### ハードウェア

- A/Dコンバータ：アナログ→デジタル信号
- 静電センサー：タッチパネルなど
- アクチュエーター：電気信号を力学運動に変える
- センサー：物理量を電気信号に変換

- フリップフロップ回路：安定状態にする

### プロセッサアーキテクチャ

### プロセッサの高速化技術

### メモリアーキテクチャ

### 出入力アーキテクチャ

## システム構成要素

### システムの処理形態
- 奇数パリティ：１の数を奇数にする→1ビットの誤り検出可能
- 水平パリティ：水平方向にパリティビットを追加→1ビットの誤りを検出可能
- 垂直水平パリティ：→1ビットの誤りを**訂正**可能
- チェックサム：合計値を付加し、誤りを検査
- ハミング符号：2ビットの誤り検出機能と、1ビットの誤り訂正機能


#### 分散処理システムのネットワーク透過性
**- アクセス透過性：遠隔地の資源でも同一方法のアクセスができること**  
- 移動透過性：使用中の資源を移動できること
- 位置透過性：資源の位置を意識せずにアクセスできること
- 規模透過性：構成に影響を与えず規模を変更できること
- 障害透過性：一部の障害で全体の機能が停止しないこと
- 複製透過性：複数の位置にあっても利用者には1つに見えること
- 並行透過性：並行処理できること

### クライアントサーバシステム

P2P（Peer to Peer）：フラッディングで全てのノートにクエリ発行しデータ探索する。どの端末もサーバにもクライアントにもなる。  


### システムの構成方式
- 密結合マルチプロセッサシステム：複数CPUがメモリを共有
- 疎結合マルチプロセッサシステム：複数コンピュータを繋いでいる
- デュアルブート：複数OSがCPUを共有
- デュアルシステム：複数コンピュータの結果を照合機でチェックする

### 仮想化技術

### システムの性能

### 待ち行列理論の適用

### システムの信頼性

- フェールセーフ：安全最優先。緊急停止をする。
- フェールソフト：システム性能の低下で対応。


## ソフトウェア

### OSの構成と機能

**ページング**：ページ（固定長区画）に分割して、主記憶と補助記憶装置のアドレス変換を行う  
→ アドレス対応表：ページテーブル

・ラウンドロビン方式はタイムシェアリングシステムのスケジューリングに適している。  


### タスク（プロセス）管理

### 記憶管理

### 言語プロセッサ

### 開発ツール

### UNIX系OS

・OSSにおける再頒布時には付属するドキュメントに変更した旨の告知を記載しなければならない  

#### マルチメディア

- トラッキング：センサやカメラで非言語情報を認識
- レンダリング：AR空間情報をディスプレイに描画可能な形式の画像に変換
- 幾何学的レジストレーション：現実世界と仮想世界を融合させるために座標一致させる処理
- モデリング変換：物の移動を物理法則に当てはめて変化させる


## データベース

### データベースの基礎

#### 文字列
CHAR(n)：1〜255字の半角固定長文字列  
NCHAR(n)：1〜127字の全角固定長文字列  
VARCHAR(n)：1〜8,000字の半角可変長文字列  
NCHARVARYING(n)：1〜4,000字の全角可変長文字列  

#### 数値
SMALLINT：-32,768〜32,767の範囲内の整数（3万越え）  
INTEGER：SMALLINTより領域が必要な場合  
DECIMAL(m,n)：精度m、位取りnの10進数 

#### カラム制約

**候補キー (candidate key)**：主キーの候補。複数存在可、NULL可。  
**スーパーキー**：タプルを一つに特定できればなんでも良い。  
**サロゲートキー（surrogate key）**：行のID  

`CHECK(単価>=100)`

`FOREIGN KEY table2.column2 REFERENCES table1.column1`  
`ONDELETE / ONUPDATE`に対して  
`NO ACTION`：何もしない  
`CASCADE`：データ連携更新削除可能  
`SET NULL`：NULLを挿入して更新削除可能  

### 関係データベース

#### ビュー

`CREATE VIEW view (col1, col2,...) AS SELECT ...`に対して  
`WITH CHECK OPTION`で挿入前に指定条件に合致するかチェックできる

### 正規化

**情報無損失分解**：第3正規形まで

| タイプ | 説明 |
| ---- | ---- |
| 非正規形 | 繰り返しの属性がある（伝票数枚、横長テーブルなど） |
| 第１正規形 | 繰り返しの属性はない（売上テーブル） |
| 第２正規形 | 完全関数従属の候補キーがない（複合主キーごとに分離） |
| 第３正規形 | 推移的関数従属の非キーがない（全ての関数従属を分離） |
| ボイス・コッド正規形 | Rが自明な関数従属性であり、スーパーキー |
| 第４正規形 | 自明でない多値従属性を含まない |
| 第５正規形 | 自明でない結合従属性を含まない（多対多を全て分離） |

**ボイス・コッド正規形**：情報の欠落が発生する  
... 第3正規形の問題点は、整合性制約で回避するのが一般的


### 関係データベースの演算

**集合演算**
`UNION`：和。重複はまとめる。  
`UNION ALL`：和。重複もそのまま表示。  
`EXCEPT`：差。共通のものを取り去る。  
直積：**全ての組み合わせ**。等結合は直積と選択。  
`INTERSECT`：積。AND。  
商：掛け算の逆  

**関係代数**  
`SELECT`：射影、選択  
`SELECT`, `JOIN`：結合  


### SQL

**DDL**： Data Definition Language. CREATE, DROP.  
**DML**： Data Manipulation Language. SELECT, INSERT, UPDATE, DELETE  

#### 選択項目リスト
`||`：連結演算子  
`DISTINCT`：重複を取り除く  
`COALESCE(..., ..., 0)`：NULLでない最初の引数を返す  
`CASE WHEN A < B THEN 1 ELSE 0 END`  

#### WHERE
`BETWEEN 10 AND 20`：10も20も含む  
`IN`：リスト内一致  
`LIKE`：文字列部分一致  
`IS NULL`  
`NOT`  

#### GROUP BY
**集約関数**
AVG, MAX, MIN, SUM, COUNT, COUNT DISTINCT

`HAVING`：GROUP BYする条件を指定

#### ORDER BY
列 ASC

#### 結合
**内部結合**  
`SELECT table1.columnA FROM table1, table2 WHERE table1.columnA = table2.columnA`  
`SELECT table1.columnB FROM table1 JOIN table2　ON table1.column1 = table2.column2`  
※ 同じ列名の場合`ON`ではなく`USING`を使うことができる  
※ 結合条件の列重複をなくす場合は`NATURAL JOIN`を使うことができる  

**外部結合**  
LEFT JOIN, RIGHT JOIN, FULL JOIN

**自己結合**  
再帰リレーション

#### 相関サブクエリ
IN句よりEXISTS句の方が処理速度が早い

#### DB操作
`INSERT INTO table1 (column1, column2) VALUES(10, 20)`  
`INSERT INTO table1 column1 SELECT DISTINCT column2 FROM table2`  
`UPDATE table1 SET column1 = 10 WHERE column2 = 20`  

**ロールフォワード**：更新後ログを使用するので、直前コミットまで再現可能  
**2相コミット**：①他のサイトに更新可能かどうかを確認し、②更新を確定

- 共有ロック：更新処理ができなくなる
- 占有ロック：何もできなくなる


#### 権限
`GRANT role ON table TO user`  
`WITH GRANT OPTION`を指定したユーザは、他のユーザに権限付与が可能になる  

`REVOKE role ON table FROM user`


### データ定義言語

### 埋め込み方式
`EXEC SQL DECLARE cursor_name CURSOR FOR`
`OPEN` `FETCH` `CLOSE`
`SQLSTATE`

### データベース管理システム

**スタースキーマ**：ファクトテーブルがハブの位置  
**B+木インデックス**
- 木の深さが一定で葉のみが値を持つ平衡木を用いたインデックス
- RDBMSのインデックス法として最も普及
- 範囲検索に性能改善効果が期待できる
- NULLや否定を含む検索条件では効果を発揮できない

### 分散データベース

### データベースの応用

| 外部スキーマ | ユーザービュー（論理） |
| 概念スキーマ | 実表 |
| 内部スキーマ | 物理 |

#### 論理データモデル
1. 関係モデル
2. 階層モデル
3. ネットワークモデル


### ブロックチェーン

## ネットワーク

### 通信プロトコルの標準化

### ネットワーク接続装置と関連技術

### データリンク層の制御とプロトコル

### ネットワーク層のプロトコルと技術

### トランスポート層のプロトコル

### アプリケーション層のプロトコル

### 伝送技術

- WSDL（Web Services Description Language）：Webサービスに関する情報
- S/MIME：電子メール保護
- SSL（Secure Socket Layer）：ディジタル署名の鍵情報の管理するため
- SAML：認証情報に加え、属性情報とアクセス制御情報を異なるドメインに伝達するためのWebサービス


### 交換方式

## セキュリティ

### 暗号化

### 無線LANの暗号

### 認証

**DNSSEC**：公開鍵暗号方式  

### ディジタル署名とPKI

### 情報セキュリティ対策

**ディジタルフォレンジクス**：インシデント発生時にログ解析すること  
**ハニーポット**：誘き寄せのそっくりシステムで監視



### 情報セキュリティの脅威と攻撃手法

- War Driving：建物の外部に漏れた無線LANを傍受
- Drive by Download：Webサイトから不正プログラムをダウンロードさせる

### 情報セキュリティ管理

## システム開発技術

### 開発プロセス・手法

### 分析・設計手法

### オブジェクト指向設計

### モジュール設計

#### モジュール結合度

- データ結合： パラメータ
- スタンプ結合： 構造体
- 制御結合：制御要素。論理
- 外部結合：外部宣言。単一データ項目
- 共通結合：共通データ。データ
- 内容結合：内容の直接参照。JUMP命令

### テスト

### テスト管理手法

### レビュー

## マネジメント

### プロジェクトマネジメント

**ガントチャート**：スケジュール  
**パレート図**：棒グラフと折れ線グラフ。管理上の優先度。  


### タイムマネジメントで用いる手法

### コストマネジメントで用いる手法

### システム運用

### サービスマネジメント

・運用テストは運用部門主導で行う。  


### システム監査

・システム管理基準によると、開発計画はユーザ部門および情報システム部門の役割分担を明確にしなくてはならない。  

## ストラテジ

### システム戦略

### 経営戦略

**バリューチェーン分析**：主活動と支援活動に分類し、付加価値がどの部分で生み出されているかを分析する  
- 主活動
  1. 購買物流
  2. 製造
  3. 出荷物流
  4. 販売・マーケ
  5. サービス
- 支援活動
  1. 全般管理
  2. 人事・労務管理
  3. 技術開発
  4. 調達  

**ファイブフォース分析**：5つの競争要因から、業界の構造分析を行う手法
- 内的要因
  1. 供給企業の交渉力
  2. 買い手の交渉力
  3. 競争企業間の敵対関係
- 外的要因
  1. 新規参入業者の脅威
  2. 代替品の脅威

**コアコンピタンス**：差別化できるノウハウや技術  


### ビジネスインダストリ

### 経営工学

### 企業会計

### 標準化と関連法規