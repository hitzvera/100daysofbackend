# SQL query

## modify the column

changing nullable column

```
ALTER TABLE barang
    MODIFY id NOT NULL;
```

## default value

by default ketika kita insert column nullable by default jika tidak diisi maka niliainya akan null. kita bisa memberi default value pada column yang nullable
.
khusus untu ktipe data datetime atau timestamp jika ingin memberi default value dengan waktu saat ini bisa beri kata kunci **current_timestamp**

```
ALTER TABLE barang
    modify waktu_dibuat timestamp not null default current_timestamp;
```

## insert data to the table

**single value**

```
insert into *nama_table* (nama_column1, nama_column2) values (1, 'value dari column');
```

**multiple values**

```
INSERT INTO products (id, name, price, quantity)
VALUES
    ('POOO3', 'nasi goreng', 13000, 100),
    ('POOO4', 'KENTANG GORENG', 20000, 20),
    ('POOO5', 'Bakso', 15000, 50),
    ('POOO6', 'Mie Ayam', 12000, 75),
    ('POOO7', 'Sate Ayam', 18000, 40),
    ('POOO8', 'Nasi Uduk', 17000, 60),
    ('POOO9', 'Nasi Padang', 16000, 80),
    ('POOO10', 'Soto Ayam', 14000, 70);
```

## menghapus table

```
DROP *nama_table*;
```

## menghapus data dalam table

```
truncate *nama_table*
```

truncate merupakan keyword untuk menghapus table dan membuat ulang table tersebut

## select data

select digunakan untuk mengambil data di dalam sebuah table.

```
SELECT * FROM products;
```

bintang (\*) merepresentasikan semua column yang ada pada table tersebut.

kita juga bisa spesifik kolom mana yang akan dipanggil

```
SLEECT id, name from products;
```

## primary key

mysql tidak wajib, postgresql wajib terdapat primary key.
.
primary key = identitas yang membedakan dari yang lain.
.
primary key bisa dengan menggunakan multiple column

ketika kita insert primary key yang sama maka akan ditolak.
.
deklarasi primary key kita bisa saat membuat table

```
create table barang
    (nama varchar(100), primary key(nama));
```

## where clause

seperti conditional

```
select * from products where quantity = 0;
```

## update data

ketika update kita menggunakan where clause, harus hati hati karena ketika where clause salah maka kita akan mengganti data yang tidak kita inginkan.

```
update table_name
set field_name = value
where field_name = condition;
```

## delete data

sama seperti update

```
delete table_name
where id = the_id;
```

## alias

alias bisa untuk kolom dan table.
.
alias berguna untuk mengubah nama kolom agar lebih simple.

```
select price as 'Harga' from products;
```

jadi nanti outputnya berupa table dengan nama aliasnya

bisa juga digunakan untuk table

```
select p.id as Kode,
    p.name as Nama,
    p.category as Kategori,
    p.price as Harga,
    p.quantity as jumlah
from products as p;

// karena by default ketika kita query
select id, name from products

sama seperti

select products.id, products.name from products
```

## where operator

menampilkan produk lebih

```
dari 100
select * from products
where quantity > 100;
```

menampilkan produk lebih dari sama dengan 100

```
select * from products
where quantity >= 100;
```

**Multiple condition**

```
select * from products
where category = 'Makanan' AND price > 20000;

select * from products
where (category = 'Makanan' OR price > 20000) and quantity > 100;
```

mencari dengan sub string

```
LIKE

LIKE 'b%' string dengan awalan b
LIKE '%a' string dengan akhiran a
LIKE '%eko% string berisikan eko
NOT LIKE !LIKE

select* from products
where category = '%'
```

operasi like sangat lambah karena scaning dari awal sampe akhir. sangat tidak disarankan jika database sudah terlalu besar

untuk null terdapat operator khusus

**IS NULL and IS NOT NULL**

```
select * from products
where description is not null;
```

**BETWEEN**
misal kita ingin mencari data dari 10 sampai 20

instead of doing

```
data >= 10 and data <= 20
```

kita bisa menggunakan

```
where data between 10 and 20;
```

**IN OPERATOR**
operator in adalah operator untuk melakukan pencarian sebuah kolom dengan ebberapa nilai.
misal kita ingi nmecnari products dengan category makanan atau minuman, maka ktia bisa mengguakan operator in.

```
select * from products
where category IN ('Makanan', 'Minuman')
```

IN ini merupakan cara yang efisien dibanding kita menggunkana where category = 'Makanan' OR category = 'Minuman'
. bayangkan jika kita ingin memasukan banya value tentu akan susah.

kebalikan dari IN yaitu **NOT IN**


## order by clause
asc dari kecil ke besar
desc dari besar ke kecil

```
select * from products
order by price;
```
by default akan mengurutkan secara asc (besar ke kecil)

bisa juga kita melakukan beberapa column seperti

```
select * from products
order by price, quantity desc;
```

## limit clause
limit merupakan berapa banyak 
```
select * products
limit 3;
```
membuat tampilan hanya menampilkan 3
bisa juga menggunakan offset artinya berapa data yang akan kita skip

```
select * products
limit 3, 3;
```
mengambil 3 data setelah 3 data pertama.
