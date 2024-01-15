### DCLとは

- Data Control Language: DMLやDCLの許可や制限を設定する役割の言語

- GRANTやREVOKEなどがある

- これらの命令はadmin権限のあるユーザーが行うことができる

---

### GRANTとは

- テーブルやデータの操作に関する権限を与える命令

```sql
GRANT <permission> TO <user>
```

---

### REVOKEとは

- ユーザーに与えられている許可を剥奪したりする命令

```sql
REVOKE <permission> FROM <user>
```