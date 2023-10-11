# SQL Query

## Full-Text Search

full text search memungkinkan kita bisa mencari sebagian kata di kolom dengan tipe data string

ini sangat cocok ketiak apda kasus kita memang membutuhkan pencarian yang tidak hanya sekedar operasi (equals, sama dengan)

dalam deklarasinya seperti ini

```
create table sellers(
    id int not null auto_increment,
    name varchar(100) not null,
    description varchar(100) not null,
    fulltext sellers_search(name, description)
)
```

cara menggunakannya

```
SELECT * from sellers
    WHERE MATCH(name, description)
        AGAINST('ayam' in NATURAL LANGUAGE MODE);
```

iini hampir sama dengan

```
select * from products where name
    like '%ayam%' or  description like '%ayam%';
```

lalu ada boolean mode

```
SELECT * from products
    WHERE MATCH(name, description)
        AGAINST('+ayam -sate' in boolean mode);
```

(yang tidak mengandung kata sate dan mengandung kata ayam)

yang terakhir

```
SELECT * from products
    WHERE MATCH(name, description)
        AGAINST('bakso' with query expension);
```

jadi dia misal entry pertama
mie ayam baso
jadi dia bakal query lagi
mie ayam ceker
mie ayam original, dll

untuk modenya terdapat 3

- Natural language
- Boolean (bisa menggunakan prefix + dan -)
- Query Expansion (rekomendasi kata selanjutnya, melakukan dua kali pencarian)

 
