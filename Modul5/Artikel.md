## Fungsi Skalar
### A. String Function
#### Concat

```
select concat_ws(' ',ID, name) as PROFIL
from student;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/1.png)

#### Substring_Index

```
select substring_index(dept_name,' ',1) as JURUSAN_INDEX
from department;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/2.png)

#### Substr

```
select substr(dept_name, 1, 3) as KARAKTER
from department;
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/3.png)

#### Length

```
select dept_name,length (dept_name) as TOTAL_CHAR
from department;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/4.png)
Penjelasan : Query tersebut menampilkan kolom dept_name dan panjang (jumlah karakter) dari setiap nilai dalam kolom tersebut, dengan memberikan alias TOTAL_CHAR pada hasilnya.

#### Replace

```
select name, replace (name,'JONO','BUDI') as NAMA_BARU
from student ;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/5.png)

### B. Numeric Function
#### ABS

```
SELECT ABS(credits)
FROM course;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/6.png)


#### Ceiling

```
SELECT CEILING(salary)
FROM instructor;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/7.png)

#### Floor

```
SELECT FLOOR(salary)
FROM instructor;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/8.png)


#### Round
```
SELECT ROUND(salary)
FROM instructor;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/9.png)


#### SQRT

```
SELECT SQRT(salary)
FROM instructor;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/10.png)

## C. Date Function
#### Curdate

```
select curdate();
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/11.png)

#### Curtime

```
select curtime();
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/12.png)

#### Timestamp
```
select TIMESTAMP("2017-07-23");
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/13.png)

## Fungsi Agregasi
#### SUM

```
SELECT SUM(salary)
FROM instructor;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/14.png)

#### AVG

SELECT AVG(salary)
FROM instructor;

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/15.png)

#### Count

```
SELECT COUNT (*) FROM student;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/16.png)

#### Klausa Group and Klausa Having

```
select avg(budget) as RATA2_BUDGET, dept_name as NAMA_DEPARTMEN from department
group by dept_name having avg (budget) > 2;
```

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/17.png)
