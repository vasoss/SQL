# Урок 2

## Объединение таблиц

### Простое объединение **union all** (не проверяет совпадения)
select * from shop as shop1
union all
select * from shop as shop2;

### Объединение **union** (добавляет только не совпадающие строки)
select * from shop as shop1
union 
select * from shop as shop2;

## Селект по различным значениям 

### Для булевых значений

*true/false*

select * from shop where exist = true;

### Для текстовых значений

*% - не проверяет все выражение*

*_ - один любой символ*

select * from shop where partname like '%Ba_'

*в данном случае при помощи % проверяем значения которые начинаются на 230*
*cast необходим для обертки integer в text и последующего поиска*

select * from shop where cast (sn as text) like '230%'

*еще один вариант поиска по substring*
select * from shop where substring(cast(sn as text),1,3) = '230'

select *, ROW_NUMBER() OVER () from shop;

select *, ROW_NUMBER() OVER (order by sn) from shop order by price;


select *, ROW_NUMBER() OVER (partition by parttype) from shop;

select *, ROW_NUMBER() OVER (order by datein) from shop order by price;


select * from shop;

RANK() OVER ()

select *,  
RANK() OVER (order by price),
dense_rank() over (PARTITION BY parttype order by price),
ROW_NUMBER() OVER ()
from shop;


select * from tablica;
delete from tablica; -- удаление по строчкам
truncate table tablica; -- моментальное удаление
drop table tablica;

create table tablica as 
select * from tablica2; -- копирование таблицы

create table tablica as 
select name as name2 from tablica2;

create table copyt2 as
select * from tablica2 limit 5;

select * from copyt2;
