### テーブル定義を変更する

```sql
ALTER TABLE <table_name> ADD/RENAME/DROP <column_name/table_name/..>
```

---

### 新しくカラムを追加する

```sql
ALTER TABLE <table_name> ADD <追加するカラム名> <追加するカラムの型> <追加するカラムの制約> (FIRST/AFTER <column_name>)
```
*FIRST/AFETRは省略可能  
*FIRST: テーブルの一番目に行を追加する  
*AFETR <column_name>: 指定した行の後ろに新しく行を追加する  

---

### カラムを削除する

```sql
ALTER TABLE <table_name> DROP <削除したいカラム名>
```

---

### テーブル名を変更する

```sql
ALTER TABLE <table_name> RENAME <新しいテーブル名>
```

---

### カラム名の変更

```sql
ALTER TABLE <table_name> RENAME COLUMN <古いカラム名> TO <新しいカラム名>
```

---

### カラム定義の変更

```sql
ALTER TABLE <table_name> MODIFY (COLUMN) <対象のカラム名> <新しいカラム定義>
```

---

### カラム名とカラム定義の変更

```sql
ALTER TABLE <table_name> CHANGE (COLUMN) <リネーム対象カラム名> <リネーム後のカラム名> <新しいカラム定義>
```
*定義の変更(MODIFY/CHANGE)はデータ型やUNIQE/NOT NULL制約の追加などのために行う
*ALTER TABLEによる<font color="red">主キー、外部キーの設定</font>は**MODIFY/CHANGEではなくADD CONSTRAINT**を使う

---

### 既存カラムへのキー設定を行う

```sql
ALTER TABLE <table_name> ADD (CONSTRAINT) <const_name> <col_name>;
```

<br>

例
```sql
-- 主キー設定の追加
ALTER TABLE student ADD CONSTRAINT PRIMAEY KEY (id);

-- 複合きー設定の追加
ALTER TABLE attendance ADD CONSTRAINT FOREIGN KEY (studnet_id) REFERENCES stundet (id);
```

---

### キー制約の削除

*MySQLの場合CONSTRAINTは書いちゃダメ

```sql
ALTER TABLE <table_name> DROP (CONSTRAINT) PRIMARY KEY;
```
*複合主キーが設定されていた場合、すべてのカラムの主キー設定が削除される

<br>

```sql
ALTER TABLE <table_name> DROP (CONSTRAINT) FOREIGN KEY <制約名>
```
*制約名はSHOW CREATE TABLE <table_name>;で確認できる