flow application

front page (JSP) -> processing (servlets) -> database

now, in java application, it can't directly accessing data to database
it has to be accessing the DBMS first. but as we know there are many DBMS. for example RDBMS such as mysql and postgres. in order to java application can access the database regardless the RDBMS. we need an API. it is called JDBC (java database connectivity). this JDBC is built by class and interface. these interface is implemented by which RDBMS. for example if we need data through mysql then we implemented query for mysql, same thing for postgres.

the implementation is a jar file. it is called the driver. and then the java application can communicate with the database.

summary 
- JDBC API -> classes and interface
- DBMS is implemented interface from JDBC API. so the java application can get data through many DBMS such as mysql, oracle, or postregs
- Driver -> a collection of implementation classes of JDBC API.


perumpamaan misal saya tinggal di kota bandung. saya hanya mengerti bahasa indonesia dan sunda. di lokasi xyz terdapat sebuah harta karun yang saya sangat tertarik. namun di dalam daerah tersebut hanya menggunakan bahasa xyz yang mana saya tidak mengerti. tentunya saya butuh translator agar dapat berkomunikasi. kota bandung terdapat jalan 1000km terhadapt kota xyz. dan saya membutuhkan kendara, misal mobil. di dalam mobil itu saya menyimpan notes berapa harta karun yang saya inginkan. yang sudah di translate oleh translator saya dengan bahasa xyz. ketika mobil itu sudah sampai di kota xyz. maka saya berhasil mendapatkan harta karunnya

dalam analogi tersebut 
1. saya -> java application
2. xyz -> database
3. translator -> driver (.jar file)
4. jalan (road) dari kota bandung ke xyz -> connection
5. mobil (car) -> statement object
6. barang yang diberikan oleh xyz -> resultset.

## steps download JDBC
1. Translator: load and register the driver
    let's say i have 4 databases, each databases has to atleast 1 driver
    so i should atleast have 4 drivers.  when i build java application. we have to know which database we are using. so we can conect to the right driver.
2. build the road -> establish the connection with the database
3. build the car -> create the statement object.
4. description -> prepare, send and execute the query.
5. box (hasil dari request tadi)-> process the result from Resultset.  
6. close the connection.

but where is the API?
    JDBC API -> "java.sql" package and this is JDBC API -> provided by database vencor (driver software) (.jar file)
