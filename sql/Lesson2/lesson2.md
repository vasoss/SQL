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

* select * from shop where exist = true;

*true/false*

### Для текстовых значений

* select * from shop where partname like '%Ba_'

*% - не проверяет все выражение*

*'_' - один любой символ*

* select * from shop where cast (sn as text) like '230%'

*в данном случае при помощи % проверяем значения которые начинаются на 230*

*cast необходим для обертки integer в text и последующего поиска*

* select * from shop where substring(cast(sn as text),1,3) = '230'****

*еще один вариант поиска по substring*

## Нумерация по определенному признаку

select *, ROW_NUMBER() OVER () from shop;

*просто пронумерует каждую строчку в отдельном столбце*

select *, ROW_NUMBER() OVER (order by sn) from shop order by price;

*пронумерует строки по возрастанию цены*

select *, ROW_NUMBER() OVER (partition by parttype) from shop;

*пронумирует строки по типу запчастей (в каждом отдельном типе нумерация будет идти заново*

select *, ROW_NUMBER() OVER (order by datein) from shop order by price;


select * from shop;

RANK() OVER ()

select *,  
RANK() OVER (order by price),
dense_rank() over (PARTITION BY parttype order by price),
ROW_NUMBER() OVER ()
from shop;

## Виды удалений

select * from tablica;

### Удаление по строчкам

delete from tablica; -- удаление по строчкам

### Быстрое удаление
truncate table tablica; -- моментальное удаление

### Полное удаление
drop table tablica;

## Копирование таблицы

create table tablica as 
select * from tablica2; -- копирование таблицы

create table tablica as 
select name as name2 from tablica2;

create table copyt2 as
select * from tablica2 limit 5;

select * from copyt2;
