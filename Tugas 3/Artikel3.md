# Tugas3 DBD-SQL-A
## Buat Schema Akademik
```
create schema Akademik;
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/1.%20create%20schema.png)

## Menggunakan Database Akademik
```
use kampus;
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/2.%20use%20schema.png)

## Membuat tabel Fakultas
```
create table FAKULTAS (
ID_FAKULTAS smallint primary key not null,
FAKULTAS VARCHAR(45) not null
)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/3.%20create%20table%20FAKULTAS.png)

## Membuat tabel Jurusan
```
create table JURUSAN (
ID_JURUSAN smallint primary key not null,
ID_FAKULTAS smallint not null,
JURUSAN VARCHAR(45) not null,
foreign key (ID_FAKULTAS) references FAKULTAS(ID_FAKULTAS)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/4.%20create%20table%20JURUSAN.png)

## Membuat tabel Strata
```
create table STRATA (
ID_STRATA smallint primary key not null,
SINGKAT VARCHAR(10),
STRATA VARCHAR(45)
)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/5.%20create%20table%20STRATA.png)

## Membuat tabel Program Studi
```
create table PROGRAM_STUDI (
ID_PROGRAM_STUDI smallint primary key not null,
ID_STRATA smallint not null,
ID_JURUSAN smallint not null,
PROGRAM_STUDI VARCHAR(45) not null,
foreign key (ID_STRATA) references STRATA(ID_STRATA),
foreign key (ID_JURUSAN) references JURUSAN(ID_JURUSAN)
)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/6.%20create%20table%20PROGRAM%20STUDI.png)

## Membuat tabel Seleksi Masuk
```
create table SELEKSI_MASUK (
ID_SELEKSI_MASUK smallint primary key not null,
SINGKAT VARCHAR(12) not null,
SELEKSI_MASUK VARCHAR(100) not null
)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/7.%20create%20table%20SELEKSI_MASUK.png)

## Membuat tabel Mahasiswa
```
create table MAHASISWA (
NIM VARCHAR(15) primary key not null,
ID_SELEKSI_MASUK smallint not null, 
ID_PROGRAM_STUDI smallint not null,
NAMA VARCHAR(45) not null,
ANGKATAN smallint, 
TGL_LAHIR DATE,
KOTA_LAHIR VARCHAR(60),
JENIS_KELAMIN CHAR(1),
foreign key (ID_SELEKSI_MASUK) references SELEKSI_MASUK(ID_SELEKSI_MASUK),
foreign key (ID_PROGRAM_STUDI) references PROGRAM_STUDI(ID_PROGRAM_STUDI),
constraint CHECKJK check (JENIS_KELAMIN in ('P', 'L'))
)
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/8.%20create%20table%20MAHASISWA.png)

## Memasukkan data ke dalam tabel Fakultas
```
insert into FAKULTAS (ID_FAKULTAS, FAKULTAS)
values 
(1, 'Ekonomi & Bisnis'),
(2, 'Ilmu Komputer');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/9.%20insert%20into%20FAKULTAS.png)

## Memasukkan data ke dalam tabel Jurusan
```
insert into JURUSAN (ID_JURUSAN, ID_FAKULTAS, JURUSAN)
values 
(21, 2, 'Informatika'),
(22, 2, 'Sistem Informasi'),
(23, 2, 'Teknik Komputer');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/10.%20insert%20into%20JURUSAN.png)

## Memasukkan data ke dalam tabel Strata
```
insert into STRATA (ID_STRATA, SINGKAT, STRATA)
values 
(1, 'D1', 'Diploma'),
(2, 'S1', 'Sarjana'),
(3, 'S3', 'Magister');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/11.%20insert%20into%20STRATA.png)

## Memasukkan data ke dalam tabel Program Studi
```
insert into PROGRAM_STUDI (ID_PROGRAM_STUDI, ID_STRATA, ID_JURUSAN, PROGRAM_STUDI)
values 
(211, 2, 21, 'Teknik Informatika'),
(212, 2, 21, 'Teknik Komputer'),
(219, 3, 21, 'Magister Ilmu Komputer');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/12.%20insert%20into%20PROGRAM%20STUDI.png)

## Memasukkan data ke dalam tabel Seleksi Masuk
```
insert into SELEKSI_MASUK (ID_SELEKSI_MASUK, SINGKAT, SELEKSI_MASUK)
values 
(1, 'SNMPTN', 'SELEKSI NASIONAL MAHASISWA PERGURUAN TINGGI NEGERI'),
(2, 'SBMPTN', 'SELEKSI BERSAMA MAHASISWA PERGURUAN TINGGI NEGERI');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/13.%20insert%20into%20SELEKSI%20MASUK.png)

## Memasukkan data ke dalam tabel Mahasiswa
```
insert into MAHASISWA (NIM, ID_SELEKSI_MASUK, ID_PROGRAM_STUDI, NAMA, ANGKATAN, TGL_LAHIR, KOTA_LAHIR, JENIS_KELAMIN)
values
('155150400', 1, 211, 'JONI', 2015, 1/1/1997, 'Malang', 'P'),
('155150401', 2, 212, 'JONO', 2015, 2/10/1997, 'Situbondo', 'L');
```
)
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/14.%20insert%20into%20MAHASISWA.png)
