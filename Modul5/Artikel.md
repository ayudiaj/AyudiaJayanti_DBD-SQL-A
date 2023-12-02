## Fungsi Skalar
### A. String Function
#### Concat

```
select concat_ws(' ',ID, name) as PROFIL
from student;
```
Penjelasan : Fungsi concat berfungsi untuk menggabungkan dua kolom atau lebih

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/1.png)

#### Substring_Index

```
select substring_index(dept_name,' ',1) as JURUSAN_INDEX
from department;
```
Penjelasan : Substring berfungsi untuk memisahkan/mengambil nilai string sesuai dengan hasil pemisahan. Pada kode diatas menandakan bahwa nilai yang akan ditampilkan adalah nama departemen setelah dilakukan split setiap spasinya.

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/2.png)

#### Substr

```
select substr(dept_name, 1, 3) as KARAKTER
from department;
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/3.png)
Penjelasan : Substr berfungsi untuk mengambil nilai string sesuai dengan index yang ditentukan. Contoh kode diatas mengambil nilai string dari index 1-3. 

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
Penjelasan : Replace digunakan untuk mengganti nilai awal dengan nilai yang ditentukan. Nama Jono akan diubah menjadi Budi.
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/5.png)

### B. Numeric Function
#### ABS

```
SELECT ABS(credits)
FROM course;
```
Penjelasan : Fungsi abs ini berguna untuk mengubah nilai menjadi nilai positif. 

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/6.png)


#### Ceiling

```
SELECT CEILING(salary)
FROM instructor;
```
Penjelasan : Ceiling berfungsi untuk membulatkan nilai dengan mengambil nilai di atasnya. Misal 2,7 akan dibulatkan menjadi 3

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/7.png)

#### Floor

```
SELECT FLOOR(salary)
FROM instructor;
```
Penjelasan : Ceiling berfungsi untuk membulatkan nilai dengan mengambil nilai di bawahnya. Misal 2,7 akan dibulatkan menjadi 2

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/8.png)


#### Round
```
SELECT ROUND(salary)
FROM instructor;
```
Penjelasan : Round berfungsi untuk pembulatan dengan memberikan batasan. Misal nilai 4,355 dengan sintaks ROUND(SAlary, 2) maka nilai akan menjadi 4,350

![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/9.png)


#### SQRT

```
SELECT SQRT(salary)
FROM instructor;
```
Penjelasan : berfungsi untuk memberi akar
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/10.png)

## C. Date Function
#### Curdate

```
select curdate();
```
Penjelasan : berfungsi untuk mengambil tanggal saat ini
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/11.png)

#### Curtime

```
select curtime();
```
Penjelasan : Untuk menampilkan waktu saat ini
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/12.png)

#### Timestamp
```
select TIMESTAMP("2017-07-23");
```
Pnejelasan : Menampilkan tanggal yang sesuai dengan masukkan
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/13.png)

## Fungsi Agregasi
#### SUM

```
SELECT SUM(salary)
FROM instructor;
```
Penjelasan : Untuk menjumlahkan seluruh kolom
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/14.png)

#### AVG

SELECT AVG(salary)
FROM instructor;
Penjelasan : Menghitung nilai rata2
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/15.png)

#### Count

```
SELECT COUNT (*) FROM student;
```
Penjelasan : Menghitung jumlah baris
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/16.png)

#### Klausa Group and Klausa Having

```
select avg(budget) as RATA2_BUDGET, dept_name as NAMA_DEPARTMEN from department
group by dept_name having avg (budget) > 2;
```
Penjelasan : Menggabungkan nilai kolom yang sama
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Modul5/Screenshot/17.png)
