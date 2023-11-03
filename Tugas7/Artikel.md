# Tugas 7 - RO, CF, dan Join

## Relational Operator & Column Function
### 1. Lakukan perintah insert seperti yang ada pada Perintah 4.12 untuk menambahkan data pada table MAHASISWA
```
INSERT INTO AKADEMIK.MAHASISWA VALUES ('155150402', 2 ,
211,'JOKO',2015,'1998-2-10','SURABAYA','M'),('155150403', 2
,211,'JUJUN',2015,'1997-9-27','BANYUWANGI','M');
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas7/Gambar%20Tugas%207/1.%20insert%20data.png)

### 2. Buatlah sebuah view dengan nama LATIHAN_1 untuk menampilkan data dari kolom NIM_GABUNGAN, NAMA, dan UMUR dari table MAHASISWA. Kolom NIM_GABUNGAN terdiri dari gabungan kolom NIM, ID_SELEKSI_MASUK dan ID_PROGRAM_STUDI. Sedangkan kolom UMUR merupakan kolom yang datanya didapatkan dari operasi matematika pengurangan tahun saat ini dikurangi dengan tahun dari kolom tanggal lahir.

```
create view LATIHAN_1 as
select concat(m.NIM, m.id_seleksi_masuk, m.id_program_studi) as NIM_GABUNGAN, m.nama as Nama, timestampdiff(year, m.tgl_lahir, current_date()) as "Tanggal Lahir" 
from mahasiswa m
```
Untuk melihat view yang telah dibuat, gunakan sintaks select seperti :
```
select * from latihan_1 
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas7/Gambar%20Tugas%207/2.%20create%20view%20latihan_1.png)

#### 3. Buatlah sebuah view dengan nama LATIHAN_2 untuk menampilkan data dari kolom ID_PROGRAM_STUDI, ANGKATAN, dan JUMLAH_MAHASISWA.
```
create view LATIHAN_2 AS
select m.ID_PROGRAM_STUDI, m.ANGKATAN, count(m.ID_PROGRAM_STUDI) as "JUMLAH_MAHASISWA"
from mahasiswa m 
group by m.ID_PROGRAM_STUDI
```
Untuk melihat view yang telah dibuat, gunakan sintaks select seperti :
```
select * from latihan_2
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas7/Gambar%20Tugas%207/3.%20create%20view%20latihan_2.png)

## Join

### 1. Tampilkan kolom NIM, Nama, Angkatan, Program_Studi, Seleksi_Masuk Mahasiswa dari database Akademik yang telah dibuat sebelumnya.
```
select m.NIM, m.NAMA, ps.PROGRAM_STUDI, sm.SELEKSI_MASUK 
from akademik.mahasiswa m, akademik.program_studi ps, akademik.seleksi_masuk sm 
where m.ID_PROGRAM_STUDI = ps.ID_PROGRAM_STUDI and m.ID_SELEKSI_MASUK = sm.ID_SELEKSI_MASUK
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas7/Gambar%20Tugas%207/4.%20inner%20join.png)

### 2. Tampilkan kolom Program_Studi dan Jurusannya dari database Akademik yang telah dibuat sebelumnya. Tampilkan seluruh data Jurusan yang ada dari kolom Jurusan walaupun data Jurusan tersebut tidak memiliki Program Studi
```
select ps.PROGRAM_STUDI, j.JURUSAN 
from program_studi ps 
right join jurusan j 
on ps.ID_JURUSAN = j.ID_JURUSAN 
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas7/Gambar%20Tugas%207/5.%20right%20join.png)
