
select * from shop as shop1
union all
select * from shop as shop2;

select * from shop as shop1
union 
select * from shop as shop2;

select * from shop where exist = true;

select * from shop where partname like '%Ba_'


select * from shop where cast (sn as text) like '230%'

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
