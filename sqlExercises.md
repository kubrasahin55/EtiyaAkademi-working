## 28.11.2022 SQL EXERCISES


1-Categories tablosuna yeni eleman ekleme

```sql
INSERT INTO categories (category_name,description)
VALUES ('Mutfak','Bardak')
```
![insert](https://user-images.githubusercontent.com/97318131/204290801-ce40777b-d9d6-47a3-98a6-527561677dd7.PNG)

2-Product tablosundaki products idsi 5 olan ürünün birim fiyatı güncelleyen sorgu
```sql
UPDATE products
Set unit_price = 1000
where product_id = 5
```
![update](https://user-images.githubusercontent.com/97318131/204292618-f2f6230d-6ed6-413a-ac03-54473d91455b.PNG)

3-Bir müşterinin siparişlerini hangi bankayla ödendediğini gösteren sorgu
```sql
Select order_number,first_name, last_name,bank_name
From customers co
Inner Join orders ord 
on co.customer_id = ord.customer_id 
Inner join payments pa
on ord.order_id = pa.order_id
Where first_name = 'kubra'
```
![inner](https://user-images.githubusercontent.com/97318131/204296029-cfeacefa-acda-4d8a-a1f6-e2545a533657.PNG)

4.Customer ve Orders tablosunun bütün kolonlarını gösteren sorgu
```sql
select * from Customers cm FULL OUTER JOIN Orders ord 
on cm.customer_id = ord.customer_id ;
```
![fullouter](https://user-images.githubusercontent.com/97318131/204296655-00c7a0f0-fc69-4374-b641-2cf3e2fc8b86.PNG)

5.Alıcısı belli olmayan siparişleri getirmeyen sorgu (Left Join)
```sql
select * from Customers cm left join Orders ord 
on cm.customer_id = ord.customer_id 
```

6.Ürünü belli olup alıcısı belli olmayan siparişleri de getiren sorgu (Right join)
```sql
select * from Customers cm RIGHT join Orders ord 
on cm.customer_id = ord.customer_id 
```
![right](https://user-images.githubusercontent.com/97318131/204297950-f88de3b9-5bf8-4130-8cb8-f20c0cd59568.PNG)

7.Şehirlerde kaç adet kayıtlı kullanıcı olduğunu gruplandıran sorgu
```sql
select city_name,count(city_name)
From customers cm
Inner join addresses ad
on cm.customer_id = ad.customer_id 
Inner join cities ci
ON ad.city_id = ci.city_id
group by city_name
```
8.Products tablosundaki name alanının'cikolata' ve 'mont' aralığındaki değerleri sıraya göre getiren sorgu
```sql
SELECT * FROM products
WHERE name BETWEEN 'cikolata' AND 'mont'
ORDER BY name
```
![betwen](https://user-images.githubusercontent.com/97318131/204304119-0fd642e7-3f0f-419c-8bfb-f21d374fafc4.PNG)

9.Orders tablosundaki sipariş miktarı 1'den fazla olanları gruplandıran sorgu
```sql
Select order_quantity,customer_id
From orders 
group by order_quantity,customer_id
having max(order_quantity)>1
```
![having](https://user-images.githubusercontent.com/97318131/204305745-c8f87a87-ab0f-46f3-a4e5-bfee9b02426e.PNG)

10.Product tablosunda idsi 200 olan kolonu silen sorgu
```sql
Delete from  products where product_id =200  
```

![del2](https://user-images.githubusercontent.com/97318131/204306891-40c10611-7db1-4c5b-adb8-5dc475474772.PNG)

