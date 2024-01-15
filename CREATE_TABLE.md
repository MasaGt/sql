### テーブルの作成

```sql
CREATE TABLE <table_name> (
    <column1_name> <column1_type>,
    <column2_name> <column2_type>,
    ...
    <columnX_name> <columnX_type>
);
```

<br>

例: 学生のテーブルを作る
```sql
CREATE TABLE STUDENTS (
    id INTEGER,
    name VARCHAR(255),
    age INTEGER
);
```

---

### デフォルト値を設定する

- DEFAULT キーワードをカラムの型の後に設定できる

```sql
CREATE TABLE <table_name> (
    <column_name1> <column1_type> DEFAULT <default_value>,
    ...
);
```