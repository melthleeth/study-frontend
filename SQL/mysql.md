# UNION, UNION ALL

## UNION

- distinct한 값에 대해 combine 해준다.
- 두 개 혹은 더 많은 select statement에 대해서도 가능하다.

```sql
SELECT City, COUNT(City) as COUNT
from Customers
group by City
union
select City, Count(City) as COUNT
from Suppliers
group by City
order by City;
```

## UNION ALL

- union과 다르게 중복되는 값을 허용한다.

```sql
select City, count(City) as COUNT
from (SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers)
group by City
ORDER BY City;
```
