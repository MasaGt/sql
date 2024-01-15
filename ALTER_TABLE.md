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
ALTER TABLE <table_name> CHANGE (COLUMN) <リネーム対象カラム名> <リネーム後のカラム名> <新しいカラム名>
```