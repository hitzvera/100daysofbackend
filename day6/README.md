# SQL Query

## distinc

menampilkan hanya satu data saja (tidak duplikat)

```
select distinc category from products;
```

maka akan keluar semua jenis cateogry dengan tidak duplikat

## auto increment clause

auto increment is usually used for id
for example

```
create table admin(
    id int not null auto_increment,
    name varchar(100) not null
);

insert into admin(name) values ('Mujahid')
```

the id is automatically generated if we add auto increment.

## string function

the whole documentation is from [this](https://dev.mysql.com/doc/refman/5.7/en/string-functions.html)

```
select id, lower(name) as 'Name lower' from admin;
```

## date and time function

the whole documentation you can see [here](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)

```
select id,
    EXTRACT (YEAR FROM created_at) AS 'Year'
FROM products;

or

SELECT id, YEAR(created_at) as 'year' from products;
```

## control flow

mirip if else dalam bahasa pemrograman

CASE

```
SELECT id,
    case category
        when 'Makanan' then 'Enak'
        when 'Minuman' then 'Segar'
        else 'Apa itu?'
        end as 'Category'
from products;
```

IF

```
select id,
    price,
    if(price <= 15000, 'Murah',
        if(price <= 20000, 'Mahal', 'Mahal Banget'))
    as 'Mahal ga yaa'
from products;
```

IF NULL

```
select id, name, ifnull(description, 'Kosong') from products;
```

kosong tersebut merupakan default value jika description null

## aggregate function

misal ketika kita ingin melihat harga yang paling mahal, total dalam tabel, rata rata, dsb

docs [here](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html)

aggregate function tidak bisa digabung dengan field biasa.

```
select count(id) from products;

select max(price) from products;

select min(price) from products;

select avg(price) from products;
```

## group by

group by ini cukup erat dengan aggregate function

```
select count(id), category from products group by category;
```

query di atas untuk mencari berapa id dari tiap tiap category

## having clause

having sama seperti where namun untuk aggregate function dan grouping

```
select count(id) as total, category from products
group by products
having total > 1
```

let's say kita punya menu makanan 29 dan minuman 1. yang akan ditampilkan itu hanya makanan saja.

## constraint

constraint merupakan validator pada kolom di sebuah table misal unique

```
create table customers(
    id int not null auto_increment,
    email varchar(100) not null,
    first_name varchar(100) not null,
    last_name varchar(100) not null,
    primary key (id),
    unique key email_unique (email)
);
```

jadi pada pembuatan table tersebut maka field email akan unique.

bagaimana jika kita terlanjur membuat table, kita bisa alter table tersebut

```
alter table customers
    add constraint email_unique UNIQUE (email);
```

untuk menghapus constraints

```
alter table customers
    drop constraint email_unique;
```

apa yang terjadi ketika kita input dengan data yang sama

```
insert into customers(email, first_name, last_name) values ('mujahid@gmail.com', 'mujahid', 'ansori majid');
insert into customers(email, first_name, last_name) values ('mujahid@gmail.com', 'mujahid', 'ansori majid');
```

maka akan terjadi error code 1062 (duplicate entry). dan data tersebut tidak akan terinput.

adapun **check** constraint

```
alter table products
    add constraint price_check CHECK(price >= 1000);
```

karena sebelumnya table sudah dibuat maka kita alter table saja. query di atas untuk setiap membaut entry maka jika kita insert price kurang dari 1000 maka akan ditolak.


## index
biasanya sql menyimpan table dalam disk. dengna memberikan index pada sebuah kolom maka akan dirubah ke bentuk B-tree atau balance tree. hal ini untuk memudahkan sistem untuk melakukan pencarian. index dapat ditambahkan lebih dari kolom dalam satu table

**trades of** 
index mungkin akan mempercepat dalam pencarian dan query data. namun, saat kita membuat index. artinya mysql akan melakukan proses update data di index tiap kali kita menambah, mengubah atau menghapus data di table.
sehingga proses crud akan semakin lama.

nb: primary key dan unique akan otomatis menambahkan index.


contoh 
```
create table sellers(
    id int not null auto_increment,
    name varchar(100),
    email varchar(100),
    primary key (id),
    unique key email_unique (email),
    index name_index (name)
);
```
dari code tersebut kolom yang diberi index adalah id, email, dan name.

bisa juga kita memiliki banyak index di beberapa kolom

```
create table sellers(
    id int not null auto_increment,
    name varchar(100),
    name2 varchar(100),
    name3 varchar(100),
    email varchar(100),
    primary key (id),
    unique key email_unique (email),
    index name_index (name),
    index name2_index (name2),
    index name3_index (name3),
    index name_name2_name3_index (name, name2, name3)
);
```
dari query tersebut kita bisa menyimpulkan bahwa yang terindex itu
name
name2
name3
name dan name2
name dan name2 dan name3

dan yang tidak terindex kalo kita menggabungkan
name2 dan name3.