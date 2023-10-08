<!-- today i am going to learn DMBS mysql for specific -->

# DMBS

database management system

## pengertian

aplikasi untuk mengelola memanage data

## workflow how fetching data works

database client (web, mobile, desktop) -> database management system -> database file

Database Client:

A database client is a software application or program that allows users to interact with a database system. These clients can be web-based, mobile apps, or desktop applications.
Database clients provide a user-friendly interface for users to perform operations on the data stored in a database. These operations can include querying data, inserting new records, updating existing data, and deleting records.
Examples of database clients include web browsers (for web-based applications), mobile app interfaces (for mobile applications), and dedicated software (for desktop applications).
Database Management System (DBMS):

A DBMS is software that serves as an intermediary layer between the database client and the actual database file.
Its primary role is to manage and facilitate access to the database, ensuring data integrity, security, and efficient data retrieval and storage.
DBMS software can be categorized into various types, such as relational database management systems (RDBMS), NoSQL databases, object-oriented databases, and more, depending on the data model they support and their features.
Database File:

The database file is where the actual data is stored on disk. It is a structured collection of data organized in a way that allows for efficient storage and retrieval.
The DBMS manages the interaction with this database file, handling tasks such as reading and writing data, enforcing data constraints (e.g., ensuring data consistency and integrity), and optimizing data storage.
The flow of data and operations typically goes like this:

The database client sends requests to the DBMS to perform various database operations, such as querying for specific data or updating records.

The DBMS processes these requests, translating them into low-level operations that interact with the database file. It manages tasks like parsing SQL queries, transaction management, and access control.

The DBMS interacts with the database file to read or write data, making sure data is stored safely and efficiently.

The results of these operations are sent back to the database client, which then displays the data to the user or provides feedback on the requested action.

In summary, a database client is the user interface that interacts with the DBMS, which in turn manages the database file where the actual data is stored. This three-tier architecture helps separate concerns, enabling efficient data management and secure access to data in various software applications.

## sql

sql merupakan structured query language yang merupakan bahasa yang digunakan untuk mengirim perintah ke dbms. sql berisi instruksi menyimpan, mengubah, menghapus atau mengambil data melalui dbms.
mysql, postgresql, oracle, memiliki kinerja yang berbeda sehingga terdapat beberapa syntax yang berbeda.

## mysql

why mysql, it is focused on speed. but less feature than postgres.
postgres is usually used for enterprise.

## data type in mysql

Numeric Data Types:

INT or INTEGER: Represents integer numbers.
TINYINT: Stores very small integer values.
SMALLINT: Stores small integer values.
MEDIUMINT: Stores medium-sized integer values.
BIGINT: Stores large integer values.
DECIMAL or NUMERIC: Stores fixed-point numbers.
FLOAT: Stores single-precision floating-point numbers.
DOUBLE: Stores double-precision floating-point numbers.
Character String Data Types:

CHAR: Fixed-length character strings.
VARCHAR: Variable-length character strings. (varchar is more flexible, and the storage is relative the inputted data)
TEXT: Stores large text data.
ENUM: Enumerated types for storing one of a predefined list of values.
SET: Similar to ENUM, but allows for multiple choices from a predefined list.
Binary Data Types:

BINARY: Fixed-length binary data.
VARBINARY: Variable-length binary data.
BLOB: Stores large binary data.
Date and Time Data Types:

DATE: Stores date values (YYYY-MM-DD).
TIME: Stores time values (HH:MM:SS).
DATETIME: Stores both date and time values (YYYY-MM-DD HH:MM:SS).
TIMESTAMP: Stores a timestamp, typically used for recording when a row was created or updated.
Boolean Data Type:

BOOLEAN or BOOL: Represents boolean values (0 for false, 1 for true).
Spatial Data Types:

GEOMETRY: Stores spatial data (points, lines, polygons, etc.).
JSON Data Type:

JSON: Stores JSON data.
Other Data Types:

YEAR: Stores a four-digit year value.
BIT: Stores bit values (a series of 0s and 1s).
SET: Stores a set of values chosen from a predefined list.
ENUM: Stores one value from a predefined list.
When creating a table in MySQL, you specify the data type for each column, which enforces the type of data that can be stored in that column. Additionally, MySQL allows you to define constraints, such as NOT NULL, PRIMARY KEY, UNIQUE, and FOREIGN KEY, to further control the data stored in your tables.

The choice of data type depends on the nature of the data you are storing and the operations you need to perform on that data. Using the appropriate data types can help optimize storage and query performance while ensuring data integrity.
