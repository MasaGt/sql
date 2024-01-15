### テーブル自体を削除する

```sql
DROP TABLE <table_name>;
```

---

### DDLのrollback

- mysql, oracle dbはddlのロールバックはできないので、1度dropしてしまうと、戻せなくなる

---

### TRUNCATE

- テーブルの全行を削除する

- DELETE * FROM <table_name>と同じ動き  

- TRUNCATEは一度テーブルを削除して、同名同定義テーブルを作成し直すイメージ

---

### DELETEとTRUNCATEの違い

|       違い       |DELETE|TRUNCATE|
|-----------------|------|--------|
|WHERE句での条件追加| できる | できない |
|     DML/DCL     |  DCL  |   DML   |
|   ロールバック   | できる |  できない  |
|      速度      |  低速  |    高速    |