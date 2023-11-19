# Union dan Subquery

## Latihan-1
### 1. Lakukan perintah Insert seperti yang ada pada Perintah 6.7 untuk menambahkan data pada table Mahasiswa
```
insert into akademik.mahasiswa 
values  ('155150404', 1, 212, 'JESSY', 2016, '1999-2-10','BANDUNG', 'P'),
		('155150405', 2, 219, 'BAMBANG', '2014', '1996-9-27', 'MAKASAR', 'L');
```
### 2. Lakukan perintah DDL seperti yang ada pada Perintah 6.8 untuk membuat sebuah table baru Mahasiswa_Pindahan
```
create table akademik.MAHASISWA_PINDAHAN (
	NIM VARCHAR(15) not null primary key,
	ID_SELEKSI_MASUK smallint, 
	foreign key (ID_SELEKSI_MASUK) references AKADEMIK.SELEKSI_MASUK(ID_SELEKSI_MASUK),
	ID_PROGRAM_STUDI smallint(6),
	foreign key (ID_PROGRAM_STUDI) references AKADEMIK.PROGRAM_STUDI(ID_PROGRAM_STUDI),
	NAMA VARCHAR(45),
	ANGKATAN smallint, 
	TGL_LAHIR DATE, 
	KOTA_LAHIR VARCHAR(60),
	JENIS_KELAMIN CHAR(1) check (JENIS_KELAMIN in ('P', 'L'))
);
```
### 3. Lakukan perintah Insert seperti yang ada pada Perintah 6.9 untuk menambahkan data pada table Mahasiswa_Pindahan
```
INSERT INTO AKADEMIK.MAHASISWA_PINDAHAN
	VALUES ('155150500', 1 ,211,'BUDI', 2015,'1997-3-3','BANYUWANGI','L'),
	('155150501', 2,212,'ANDI',2015,'1997-2-21','JAKARTA','L'),
	('155150502', 2 ,211,'DIMAS', 2015,'1998-4-11','SURABAYA','L'),
	('155150503', 2 ,211,'DIDIN',2015,'1997-2-26','BANDUNG','L');
```
### 4. Tampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa yang memiliki Kota Lahir dengan inisial B dan dari Mahasiswa_Pindahan yang memiliki Namadengan inisial D. Urutkan berdasarkan NIM.
```
select M.NIM, M.NAMA, M.JENIS_KELAMIN, M.KOTA_LAHIR, M.ANGKATAN 
from mahasiswa m 
where KOTA_LAHIR like 'b%'

union all

select mp.NIM, mp.NAMA, mp.JENIS_KELAMIN, mp.KOTA_LAHIR, mp.ANGKATAN 
from mahasiswa_pindahan mp
where mp.nama like 'D%'
order by nim
```

### 5. Tampilkan NIM, NAMA, JENIS_KELAMIN, KOTA LAHIR dan ANGKATAN dari Mahasiswa Angkatan 2015 dan dari Mahasiswa_Pindahan tetapi kecuali Mahasiswa_Pindahan yang memiliki Kota Lahir dengan inisial M urutkan berdasarkan NIM. 
```
select m.NIM, m.NAMA, m.JENIS_KELAMIN, m.KOTA_LAHIR, m.ANGKATAN
from mahasiswa m 
where m.ANGKATAN = 2015

except

select mp.NIM, mp.NAMA, mp.JENIS_KELAMIN, mp.KOTA_LAHIR, mp.ANGKATAN
from mahasiswa_pindahan mp
where mp.kota_lahir like 'M%'
order by nim
```

## Latihan-2
### 1. Tampilkan NIM, Nama dan Angkatan dari Mahasiswa yang memiliki Kota Lahir yang sama dengan Mahasiswa Pindahan dengan nama BUDI
```
select m.NIM, m.NAMA, m.ANGKATAN
from mahasiswa m 
where KOTA_LAHIR = (select KOTA_LAHIR from mahasiswa_pindahan where nama='BUDI')
```

### 2. Tampilkan NIM, Nama dan Angkatan dari Mahasiswa yang memiliki Kota Lahir yang sama dengan seluruh Mahasiswa Pindahan
```
select m.NIM, m.NAMA, m.ANGKATAN
from mahasiswa m 
where KOTA_LAHIR in (select distinct KOTA_LAHIR from mahasiswa_pindahan)
```
