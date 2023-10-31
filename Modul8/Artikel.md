# Modul 8 - Join
## Tampilkan semua nama Mahasiswa beserta nama department.

```
select s.name, d.dept_name
from student s, department d
where s.dept_name = d.dept_name
```

## Tampilkan semua nama student beserta nama department yang memiliki total SKS (total credit) lebih dari 100.
```
select s.name, d.dept_name
from student s join department d
on s.dept_name = d.dept_name
where s.tot_cred > 100
```

## Tampilkan nama student dan nama instructor yang bekerja pada department yang sama

```
select student.name as "Student Name", instructor.name as "Insruktur Name"
from student join instructor
where student.dept_name = instructor.dept_name
```
