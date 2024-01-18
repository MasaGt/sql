### データの削除のための命令

```sql
DELETE FROM <table_name> (WHERE <condition>)
```
*whereの条件をつけないと、対象テーブルの全行を削除してしまうので注意

---

### 例

<img src="./img/update2.png" />

id=4の行を削除する

```sql
DELETE FROM students WHERE id=4;
```

<br>

<img src="./img/delete1.png" />
