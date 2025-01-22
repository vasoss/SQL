Lesson 1

create table shop (PartType text, PartName text, Exist boolean, SN integer, Price integer, DateIn date, DateOut timestamp with time zone);
select * from shop;

insert into shop values
('bar', 'SteelBar', true, 220089523, 1000, '2024-10-30'),
('bar', 'AluminiumBar', false, 230395830, 3000, '2024-09-13'),
('bar', 'CarbonBar', true, 230954025, 5000, '2024-11-23'),
('frame', 'Stels Kids', false, 44329832, 2500, '2023-03-15'),
('frame', 'Author Adlut', true, 9859324, 3500, '2025-01-10');
--('wheel', '26 inch');

SELECT NOW();

update shop set DateOut = NOW();

select PartType from shop group by PartType;
select PartType, count (*) as total from shop group by PartType;
select PartType, count (*) as total, sum (price) as totalPrice, max (DateIn)
from shop
group by PartType;