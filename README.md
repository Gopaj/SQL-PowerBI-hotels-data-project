# SQL-PowerBI-hotels-data-project
SQL query into PowerBI visuals 

Data is in attached excel file hotel_revenue_historical_full.xlsx.  Load into preffered database software, I used SSMS. 

The tasks of the project is to answer problem statement: 

1. Is the hotel revenue growing?
2. Should parking lot size be increased?
3. What general trends can be derived from the data/visuals?

Database is connected directly to PowerBi Desktop. 


*** Some data exploration and some transformation/manipulation done in SSMS. SQL queries seen below. 

*-* 
select 
arrival_date_year,
hotel,
round(sum((stays_in_week_nights+stays_in_weekend_nights)*adr),2) as revenue 

from hotels

group by arrival_date_year, hotel
*-*

*-*
with hotels as (
select * from dbo.['2018$']
union
select * from dbo.['2019$']
union
select * from dbo.['2020$'])

select * from hotels
left join dbo.market_segment$
on hotels.market_segment = market_segment$.market_segment
left join dbo.meal_cost$
on meal_cost$.meal = hotels.meal
*-*

