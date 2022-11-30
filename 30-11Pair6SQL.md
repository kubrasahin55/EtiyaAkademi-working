
********************************************************
```sql
CREATE VIEW WORDERDETAILS AS
SELECT UNIT_PRICE,
	QUANTITY
FROM ORDER_DETAILS;

SELECT * FROM ORDER_DETAILS;
```


********************************************************
```sql
CREATE OR REPLACE VIEW WCUSTOMERS AS
SELECT CONTACT_NAME,
	CITY
FROM CUSTOMERS
WHERE COUNTRY = 'Brazil';

SELECT *
FROM WCUSTOMERS;
```
********************************************************

```
CREATE FUNCTION WDATEDIFF(datepart TEXT, enddate DATE, startdate DATE ,OUT SUM int ) AS $$
DECLARE
   BEGIN
        sum := (date_part(datepart,enddate) = date_part(datepart,startdate));
END;
$$ LANGUAGE PLPGSQL;



SELECT WDATEDIFF('DAY','2022-12-25','2022-12-16');
```
********************************************************

```
CREATE FUNCTION WDATEDIFF14(datepart TEXT, enddate DATE, startdate DATE ) 
RETURNS INT AS $$
DECLARE
     years int = 0;
	 months int =0;
	 days int = 0;
   BEGIN
   
         years = date_part('year',enddate)-date_part('year',startdate);
         months = date_part('month',enddate)-date_part('month',startdate);
		 days=date_part('day',enddate)-date_part('day',startdate);
         IF datepart IN('year') THEN
           RETURN years;
	     END IF;   
         IF datepart IN('month') THEN
		   RETURN years*12+months;
	     END IF;   
		 IF datepart IN('day') THEN
			RETURN (years*12+months)*30+days;
		 END IF;
		
END;
$$ LANGUAGE PLPGSQL;


SELECT WDATEDIFF14('day','2024-12-21','2022-11-10');
```
********************************************************
```sql
CREATE FUNCTION SUM_N_PRODUCT2(X int, Y int, OUT SUM int) AS $$
BEGIN
    sum := x + y;
END;
$$ LANGUAGE PLPGSQL;

SELECT * FROM SUM_N_PRODUCT1(2,4);
```

