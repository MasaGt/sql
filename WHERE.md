### 命令を実行するかどうかの条件を設定するためのキーワード

- NULLの判定

```sql
-- = NULL はダメ
WHERE <col> IS NULL;
-- DBMSによっては
WHERE ISNULL(col);

-- != NULL はダメ
WHERE <col> IS NOT NULL;
```

---

<br>

- LIKE演算子  
    - 文字の部分一致を見るキーワード

```sql
WHERE <col> LIKE "パターン文字列";
```
*パターン文字列とは: 正規表現みたいなもの  
"%": 任意の0文字以上の文字列  
"_": 任意の1文字  
"\\"でエスケープ  

例: Joで始まる生徒の情報を取得する
```sql
SELECT * FROM students WHERE name LIKE "Jo%"

/*
* James
* Joseph
* Joshua
* Joe
* とかがマッチする
*/
```

---

<br>

- BETWEEN演算子
    - ある値に対して特定の範囲を指定して真偽判定

```sql
WHERE <col> BETWEEN <val1> AND <val2>;
```
*AND演算子でも同じようなことが可能  
WHERE \<col\> \> \<val1\> AND \<col\> \< \<val2\>

例: 19歳から30歳までの生徒の情報を取得
```sql
SELECT * FROM students WHERE age BETWEEN 19 AND 30;
```

---

<br>

- IN / NOT IN 演算子
    - 複数の値を列挙し、それに合致した値があるかを真偽判定

```sql
-- val1からvalXのどれかに合致したらTRUE
WHERE <col> IN (<val1>, ..., <valX>);

-- val1からvalXのどれにも合致しなかったらTRUE
WHERE <col> NOT IN (<val1>, ... <valX>);
```

例: 出身がamerica, canada, Australiaの生徒の情報を取得
```sql
SELECT * FROM students WHERE country IN ("USA", "CA", "AU");
```

---

<br>

- ANY / ALL 演算子
    - 演算子とセットで使う
    - ANY: いずれかの条件を満たせばTRUE
    - ALL: すべての条件を満たせばTRUE

```sql
-- colがvalからvalXまでのいずれかに当てはまればTRUE
WHERE <col> <comparison operator> ANY (val, ..., valX); 

-- colがvalからvalXまでの全てに当てはまればTRUE
WHERE <col> <comparison operator> ALL (val, ..., valX);
```

例: math_scoreが50以上, 60以上, 70以上のどれかに当てはまる情報を取得
```sql
SELECT * FROM students WHERE math_score >= ANY (50, 60, 70);
```
*math_score >= 50 の情報が取得されるのと同じ

<br>

例: math_scoreが50以上, 60以上, 70以上の全てに当てはまる情報を取得
```sql
SELECT * FROM students WHERE math_score >= ALL (50, 60, 70);
```
*math_score >= 70 の情報が取得されるのと同じ

- 通常はサブクエリに対して使われる  
<font color="red">TODO: サブクエリについてを作ったらリンクを貼る</font>  
*[サブクエリについて]()

---

### 論理演算子

- AND / OR で条件式を追加していく

```sql
-- 条件1と条件2の両方ともTRUEならTRUE
WHERE <condition1> AND <condition2>;

-- 条件1と条件2のどっちか一方がTRUEならTRUE
WHERE <condition1> OR <condition2>;
```

<br>

- NOT: 真偽値の反転
```sql
-- 条件がTRUEならFALSE、条件がFALSEならTRUE
WHERE NOT <condition>;
```

例: 出身がアメリカ以外の生徒の情報を取得
```sql
SELECT * FROM students WHERE NOT country = "USA";
```

