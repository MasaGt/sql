### whereで絞った検索結果を加工する

- 重複行の排除や、検索結果の並べ替えなど

---

### DISTINCT  

- 重複データの削除

```sql
SELECT DISTINCT <col> FROM <table> (WHERE <conditions>);
```

<br>

例: 学生の国籍一覧を取得する
```sql
SELECT DISTINCT country FROM students;
```

---

### ORDER BY  

- 検索結果の並び替え

```sql
SELECT <cols> FROM <table_name> (WHERE <conditions>) ORDER BY <col> <order>;
```
*orderはASC(昇順)とDESC(降順)を指定でき、デフォルトではASC

<br>

例: 年齢の若い順に生徒の情報を取得/表示する
```sql
SELECT * FROM students ORDER BY age;
```

<br>

*並び替えの基準とする行を複数行指定することもできる
```sql
~ ORDER BY <col1> <order>, <col2> <order>, ..;
```
-> col1で同じ値があるデータは、col2を参照して並び替えが行われる

----

### LIMIT

- 先頭から指定された行数分表示する

```sql
SELECT <col> FROM <table> (WHERE ~) LIMIT <row_num> (OFFSET <omit_row_num>)
```
*検索結果の先頭からrow_num行分の検索結果を表示する  
*OFFSETを指定した場合は,omit_row_num番目の行からrow_num行分表示する

<br>

例: 数学の成績TOP3の生徒の情報を表示する
```sql
SELECT name FROM students ORDER BY math_score DESC LIMIT 3;
```

---

### UNION

- 複数の検索結果を足し合わせたものを表示
<img src="./img/union.jpg" />

    [Learn How to Perform Union in SQL?](https://www.boardinfinity.com/blog/learn-how-to-perform-union-in-sql/)

```sql
SELECT <cols> FROM <table1> 
UNION (ALL)
SELECT <cols> FROM <table2>;
```
*UNIONは通常超副業を1行にまとめる  
*ALLを指定した場合、重複行をまとめずに全て表示する

<br>

例: 　シティキャンパスとノースキャンパスの学生の名前を表示する

```sql
SELECT name FROM city_campus
UNION
SELECT name FROM north_campus;
```

---

###  MINUS (EXCEPT)

- 複数の検索結果から、重複分を取り除いたものを表示  
    **\*MINUS (EXCEPT)の後の順番に注意**
<img src="./img/minus.png" />

    [SQL MINUS](https://www.sqltutorial.org/sql-minus/)

```sql
SELECT <cols> FROM <tableA>
MINUS (ALL)
SELECT <cols> FROM <tableB>;
```

TODO:　ALLの時の挙動を説明する

<br>

例: ラグビークラブとバスケットボールクラブのどちらか一方にしか所属していない生徒の情報を取得する
```sql
SELECT name FROM rugby_club
MINUS
SELECT name FROM basketball_club;
```

- 以下は同じ結果になるとは限らない
    - \<tableA\> MINUS \<tableB\>
    - \<tableB\> MINUS \<tableA\>

TODO:　理由を説明する

---

### INTERSECT

- 複数の検索で重複するものを表示
<img src="./img/intersept.png" />

    [SQL Server INTERSECT](https://www.sqlservertutorial.net/sql-server-basics/sql-server-intersect/)

```sql
SELECT <cols> FROM <T1>
INTERSECT (ALL)
SELECT <cols> FROM <T2>;
```

TODO: ALLの時の挙動を説明する

<br>

例: ラグビークラブとバスケットボールクラブの両方の所属している生徒の情報を取得する
```sql
SELECT name FROM rugby_club
INTERSECT
SELECT name FROM basketball_club;
```

---

### UNION / MINUS / INTERSEPTの注意点

- 繋ぎ合わせる2つ以上の検索結果について、全ての検索結果は同じカラム数であることが絶対である。

    -> UNION/MINUS/INTERSEPTは複数の検索結果を1つにまとめる命令であるため、どれか1つでもカラム数が異なれば、1つにまとめることはできない。

- 検索結果のそれぞれのカラムのデータ型一致していなければならない

- 検索結果のカラム数が一致しない場合に使うテクニック
    - 足りない方の検索結果のカラムにNULLを追加する  
    ```sql
    SELECT <col1> <col2> <col3> FROM <table1>
    UNION
    SELECt <col1> <col2> NULL FROM <table2>
    ```

---

### ORDER BYを使う時にきをつけること

- ORDER BYは負荷の高い処理

- インデックスの設計をうまく行うことで、order byの負荷を軽減することができる

- 同様にdistinctやunionなども内部で並び替えを行うケースもあるらしいので使用する際には気をつけること