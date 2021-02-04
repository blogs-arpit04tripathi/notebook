---
layout: post
title: SQL Queries
permalink: /:collection/cs/dbms/queries
---

- TOC
{:toc}

---

# SQL Queries

[Mathematical Functions](https://docs.oracle.com/cd/E17952_01/mysql-5.0-en/mathematical-functions.html)

## MEDIAN
```sql
select round(median(lat_n),4) from station;
```


# Queries
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345 round the result to 4 places
```sql
select round(max(lat_n),4) from station where lat_n < 137.2345;
```
sum of all values in LAT_N, LONG_W rounded to a scale of 2 decimal places
```sql
select round(sum(lat_n),2), round(sum(long_w),2) from station;
```
Difference between total and distinct number of cities in station.
```sql
select count(*) - count(distinct city) from station;
```

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345. Round your answer to 4 decimal places.
```sql
select round(long_w,4) from station where lat_n = (select max(lat_n) from station where lat_n < 137.2345);
```

find [Manhattan Distance](https://xlinux.nist.gov/dads/HTML/manhattanDistance.html) between two point with longitude and latitude with min and max values as point coordinates
- distance = |x2-x1|+|y2-y1|
```sql
select round(abs(a-c)+abs(b-d),4) from (select min(lat_n) a, min(long_w) b, max(lat_n) c, max(long_w) d from station);
```

find [Eucledean Distance](https://en.wikipedia.org/wiki/Euclidean_distance) between two points in cartesian plane
```sql
select round(sqrt(power(a-c,2)+power(b-d,2)),4) from (select min(lat_n) a, min(long_w) b, max(lat_n) c, max(long_w) d from station);
```

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
```sql
select * from (select city, length(city) cLength from station order by cLength, city) where rownum = 1 
union 
select * from (select city, length(city) cLength from station order by cLength desc, city) where rownum = 1;
```
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
```sql
select distinct city from station 
where substr(lower(city),1,1) in ('a','e','i','o','u')
and substr(lower(city), -1) in ('a','e','i','o','u');
```
```sql
select distinct city from station
where REGEXP_LIKE(lower(city), '^[aeiou].*[aeiou]$');
```
Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
* !a or !b --> !(a and b)
```sql
select distinct city from station
where NOT REGEXP_LIKE(lower(city), '^[aeiou].*[aeiou]$');
```


```sql
select name||'('||substr(occupation,1,1)||')' from occupations order by name;
SELECT 'There are a total of '||COUNT(OCCUPATION)||' '||LOWER(OCCUPATION)||'s.' FROM OCCUPATIONS GROUP BY OCCUPATION ORDER BY COUNT(OCCUPATION) ASC, OCCUPATION ASC;
```

### When Then Queries

query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:
- Equilateral: It's a triangle with all sides of equal length.
- Isosceles: It's a triangle with 2 sides of equal length.
- Scalene: It's a triangle with all sides of differing lengths.
- Not A Triangle: The given values of A, B, and C don't form a triangle.
```sql
SELECT 
CASE 
WHEN A + B > C THEN 
    CASE
    WHEN A = B AND B = C THEN 'Equilateral'
    WHEN A = B OR B = C OR A = C THEN 'Isosceles'
    WHEN A != B OR B != C OR A != C THEN 'Scalene' END 
ELSE 'Not A Triangle' END FROM TRIANGLES;
```

## Print Pattern

https://www.geeksforgeeks.org/print-different-star-patterns-sql/

```sql
set @row := 0;
select repeat('* ', @row := @row + 1) from information_schema.tables 
where @row < 5;
-- output
* 
* * 
* * * 
* * * * 
* * * * *
```
```sql
select rpad('*', 2*level-1, ' *') as c from dual connect by level <= 20 order by length(c) desc;
-- Output
* * * * 
* * * 
* * 
* 
```

```sql
select ceil(avg(salary)-avg(replace(salary,'0','')))
from employees e;
```

grade vs marks range in grades table
```sql
select (case 
        when grade <8
        THEN NULL 
        ELSE name END) name, grade, marks
from
(
    select name, grade, marks
    from students, grades
    where marks between min_Mark and Max_Mark
) gradeList
order by grade desc, name, coalesce(name,marks);
```