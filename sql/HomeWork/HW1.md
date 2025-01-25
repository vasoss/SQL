# Создание таблицы из файла CSV
## Выбор типов данных для столбцов

create table yellow_tripdata

(VendorId smallint,                   
> *т.к. всего два типа перевозчиков*

tpep_pickup_datetime timestamp,       
> *дата + время (без пояса)*

tpep_dropoff_datetime timestamp,      
> *дата + время (без пояса)*

passenger_count smallint,             
> *т.к. число пассажиров не большое*

trip_distance real,                   
> *длина поездки с точностью до сотых*

pickup_longitude double precision,    
> *координата с 14 знаками после запятой*

pickup_latitude double precision,     
>*вторая координата посадки*

RateCodeID smallint,                  
>* какой то код оценки от 1 до 99*

store_and_fwd_flag boolean,           
>*была ли поездка записана машиной и затем отправлена да/нет*

dropoff_longitude double precision,   
>*первая координата высадки*

dropoff_latitude double precision,    
>*вторая координата высадки*

payment_type smallint,                
>*тип оплаты (их не много)*

fare_amount real,                     
>*тариф по счетчику*

extra real,                           
>*надбавки от 0.5-1 доллар*

mta_tax real,                         
>*налог 0.5*

tip_amount real,                      
>*чаевые*

tolls_amount real,                    
>*дорожные сборы*

improvement_surcharge real,           
>*доп сбор 0.3*

total_amount real);                   
>*итоговый чек*

## Копируем данные из файла

copy yellow_tripdata 

from 'C:\projects\sql\Other\yellow_tripdata_2015-01.csv' 

with (format csv, header);


select * from yellow_tripdata;
