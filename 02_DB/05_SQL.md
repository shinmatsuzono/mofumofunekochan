### SQL

**DDL**： Data Definition Language. CREATE, DROP.  
**DML**： Data Manipulation Language. SELECT, INSERT, UPDATE, DELETE  

#### 選択項目リスト
`||`：連結演算子  
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
IN句よりEXISTS句の方が処理速度が早い（存在のTRUE/FALSEなので）

#### DB操作
`INSERT INTO table1 (column1, column2) VALUES(10, 20)`  
`INSERT INTO table1 column1 SELECT DISTINCT column2 FROM table2`  
`UPDATE table1 SET column1 = 10 WHERE column2 = 20`  


#### 権限
`GRANT role ON table TO user`  
`WITH GRANT OPTION`を指定したユーザは、他のユーザに権限付与が可能になる  

`REVOKE role ON table FROM user`


### データ定義言語

### 埋め込み方式
`EXEC SQL DECLARE cursor_name CURSOR FOR`
`OPEN` `FETCH` `CLOSE`
`SQLSTATE`

### 埋め込み型SQL
WHERE句に `CURRENT OF カーソル名` を指定する