# SQL query

## creating a database

```
create database *databasename*;
```

when database is created it will have 0 table

## creating a table

```
create table *tablename* (column_name data_type, ...);
```

if we want to check the column etc.

```
describe *tablename*;
```

behind the scene creating a table

```
show create table barang;
```

## modifying the table

alter table barang
add column nama_column data_type, <!-- ini untuk menambahkan column-->,
drop column nama, <!-- untuk menghapus sebuah column-->,
rename column nama to nama_baru, <!-- mengganti nama column-->
modify nama varchar(100) after jumlah, <!-- mengubah posisi kolom-->

nb: untuk perintah tersebut dapat kita nesting dengan menggunakan koma dan diakhiri dengan titik koma.

## check knowledge

do you know what happened in this query

```
show create table barang;

alter table barang add column deskripsi text;

alter table barang add column salah text;
alter table barang drop column salah;

alter table barang
	modify nama varchar(200) after deskripsi;

alter table barang
	modify nama varchar(200) first;

describe barang;
```
