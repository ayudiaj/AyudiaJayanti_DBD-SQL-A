# Tugas3 DBD-SQL-A
### Buat Schema "Akademik"
```
create schema Akademik;
```
![alt text](https://github.com/ayudiaj/AyudiaJayanti_DBD-SQL-A/blob/main/Tugas%203/1.%20create%20schema.png)

## Menggunakan Database "Akademik"
```
use kampus;
```

```
create table FAKULTAS (
ID_FAKULTAS smallint primary key not null,
FAKULTAS VARCHAR(45) not null
)
```
```
create table JURUSAN (
ID_JURUSAN smallint primary key not null,
ID_FAKULTAS smallint not null,
JURUSAN VARCHAR(45) not null,
foreign key (ID_FAKULTAS) references FAKULTAS(ID_FAKULTAS)
```

```
create table STRATA (
ID_STRATA smallint primary key not null,
SINGKAT VARCHAR(10),
STRATA VARCHAR(45)
)
```

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

```
create table SELEKSI_MASUK (
ID_SELEKSI_MASUK smallint primary key not null,
SINGKAT VARCHAR(12) not null,
SELEKSI_MASUK VARCHAR(100) not null
)
```

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

```
insert into FAKULTAS (ID_FAKULTAS, FAKULTAS)
values 
(1, 'Ekonomi & Bisnis'),
(2, 'Ilmu Komputer');
```

```
insert into JURUSAN (ID_JURUSAN, ID_FAKULTAS, JURUSAN)
values 
(21, 2, 'Informatika'),
(22, 2, 'Sistem Informasi'),
(23, 2, 'Teknik Komputer');
```

```
insert into STRATA (ID_STRATA, SINGKAT, STRATA)
values 
(1, 'D1', 'Diploma'),
(2, 'S1', 'Sarjana'),
(3, 'S3', 'Magister');
```

```
insert into PROGRAM_STUDI (ID_PROGRAM_STUDI, ID_STRATA, ID_JURUSAN, PROGRAM_STUDI)
values 
(211, 2, 21, 'Teknik Informatika'),
(212, 2, 21, 'Teknik Komputer'),
(219, 3, 21, 'Magister Ilmu Komputer');
```

```
insert into SELEKSI_MASUK (ID_SELEKSI_MASUK, SINGKAT, SELEKSI_MASUK)
values 
(1, 'SNMPTN', 'SELEKSI NASIONAL MAHASISWA PERGURUAN TINGGI NEGERI'),
(2, 'SBMPTN', 'SELEKSI BERSAMA MAHASISWA PERGURUAN TINGGI NEGERI');

```

```
insert into MAHASISWA (NIM, ID_SELEKSI_MASUK, ID_PROGRAM_STUDI, NAMA, ANGKATAN, TGL_LAHIR, KOTA_LAHIR, JENIS_KELAMIN)
values
('155150400', 1, 211, 'JONI', 2015, 1/1/1997, 'Malang', 'P'),
('155150401', 2, 212, 'JONO', 2015, 2/10/1997, 'Situbondo', 'L');
```
)
