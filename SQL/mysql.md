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

## set으로 custom 변수 설정하기

- MySQL에서도 변수를 설정할 수 있다.
- 아래 쿼리같은 경우 0~23시까지의 값을 구해야 하는데 중간에 비어있는 값이 테이블에 존재하므로 `@hour` 변수를 만들어 빈 값을 채워준다.

```sql
set @hour:= -1;

select (@hour := @hour + 1) as HOUR,
(select count(*) from ANIMAL_OUTS where HOUR(DATETIME) = @hour) as COUNT
from ANIMAL_OUTS
where @hour < 23;
```
