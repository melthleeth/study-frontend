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

## JOIN

- 정규화를 통해 쪼개진 테이블들 사이 다른 값들을 참조해야할 경우 사용하는 편이다.

- 예를 들어 사원 테이블과 부서 테이블이 있다면 사원 테이블의 부서 코드와 부서 테이블의 부서 코드는 같으므로 이를 이용하여 부서 이름을 조회할 수 있다.

- join할 시 두 테이블의 alias를 무조건 지정해줘야 한다.

- 아래는 `outs`에는 존재하나 `ins`에는 존재하지 않는 데이터를 추리는 쿼리이다. (프로그래머스 - JOIN - 없어진 기록 찾기)

```sql
select outs.ANIMAL_ID, outs.NAME
from ANIMAL_OUTS as outs
left join ANIMAL_INS as ins
on outs.ANIMAL_ID = ins.ANIMAL_ID
where ins.ANIMAL_ID is null
order by outs.ANIMAL_ID;
```
