### 式

- where column = value のような式を条件式と呼ぶ

- 条件式以外にも、計算式が使える
    - column(int) + 100 のように、結果が値になる計算式もある

```sql
-- 例: 既存のデータを元にして計算したカラムを表示する
SELECT
    price,
    price * 1.15 AS "tax_included"
FROM products;
```
*price * 1.15 はASで別名をつけないと、カラム名が"price * 1.15" になるので注意

<br>

```sql
-- 例: 既存データを元にした新しいデータで更新する
-- 全商品の値段が10NZD上がった場合
UPDATE products SET price = price + 10;
```
*もし、priceがNULLのデータだった場合: NULL + 10 = NULL;

---

### その他の演算子

- "/": devision  

- "%": mod  

- "||": concat  
    *MySQ/MariaDBでは利用できないので、concat関数を使う

---

### 論理演算子

論理演算子を持ちても式になる  
[演算子についてはこちらを参照](./WHERE.md)
