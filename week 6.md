# week-5

# MySQL Basic

## Database

merupakan kumpulan data yang disimpan secara sistematis di dalam komputer yang dapat diolah dan dimanipulasi.
Database Management System (DBMS) merupakan software untuk user berkomunikasi dengan data yang ada dalam media penyimpanan.
Tipe utama pada Database management System antara lain, Hierarchical, Network, Relational, Non Relational, and Object Oriented.
**DBMS** sistem penorganisasian dan sistem pengolahan Database pada komputer. DBMS atau database management system ini merupakan perangkat lunak (software) yang dipakai untuk membangun basis data yang berbasis komputerisasi.

 **Table** adalah kumpulan value terbuat dari baris dan kolom yang berisi atribut dari sebuah data.

 **Field** adalah kolom dari sebuah table dengan tiap field memiliki tipe data masing - masing.

 **Record** adalah kumpulan nilai yang saling terkait atau bisa dibilang isi dari sebuah table.
 
 
 **Structured Query Language (SQL) merupakan suatu bahasa untuk melakukan interaksi di Relational Database Management System (RDBMS)**
  
  Interaksi yang dilakukan :
  
 - Membuat, menampilkan dan menghapus data.
 - Mengatur "Permission".
 - Membuat dan menghapus database.
 
 # MySQL

Adalah sistem manajemen database relasional (Relational Database Management System) yang merupakan turunan salah satu konsep utama dalam querying database yaitu SQL, selain MySQL juga ada : PostgreSQL, MariaDB, oracle, dll. Keistimewaan MySQL :

- Dapat Digunakan banyak user, MySQL dapat digunakan oleh beberapa pengguna dalam waktu yang bersamaan tanpa mengalami masalah / konflik.
- Compatible dan portabilitasnya, MySQL dapat berjalan stabil pada berbagai sistem operasi seperti Windows, Linux, MacOS dll

## Query MySQL Basic

- Primary Key seperti namanya primary key sebagai dasar identifikasi untuk membedakan suatu baris/record dengan baris/record lainnya dalam suatu tabel. oleh karena itu primary key bersifat unik, dan setiap tabel hanya boleh memiliki 1 kolom/atribut/field yang merupakan primary key
- Foreign Key adanya foreign key membuktikan bahwa sebuah database tersebut memiliki pengolahan RDBMS. Foreign key adalah suatu atribut/kolom/field yang direferensikan dari primary key suatu atribut/kolom/field pada tabel lain untuk menciptakan hubungan/relasi antara dua tabel.


## DDL (Data Definition Language)

Merupakan kumpulan perintah SQL yang digunakan untuk berinteraksi dengan struktur dan definisi metadata dari objek - objek database.

- **Membuat table pada database**

    CREATE TABLE mahasiswas ( id int NOT NULL, fullName varchar(255) NOT NULL, age int, PRIMARY KEY (id) );
  
*Alter* digunakan untuk mengubah struktur dari table yang sudah ada. 
 **Contoh**
 
 **Menambah Primary Key**

    ALTER TABLE mahasiswas ADD PRIMARY KEY (id)
 
**Menambah Field**

    ALTER TABLE mahasiswas ADD phoneNumber varchar(12)

**Mengubah Struktur Tabel**
  
    ALTER TABLE mahasiswas ALTER COLUMN phoneNumber varchar(13)

*DROP* digunakan untuk menghapus suatu database, table dan view atau index. 

**Contoh** 
 
**Menghapus Database**
  
    DROP DATABASE data_sma

**Menghapus Table**
 
    DROP TABLE mahasiswas
 
## (DML) Data Manipulation Language
 
merupakan kumpulan perintah SQL yang digunakan untuk berinteraksi dengan data data yang ada dalam database. 
 
*SELECT* digunakan untuk menyeleksi data berdasarkan syarat yang diberikan.

**Contoh**

        SELECT * FROM mahasiswas

        SELECT fullName FROM mahasiswas

        SELECT DISTINCT age FROM mahasiswas

        // DISTINCT digunakan untuk menhgilangkan duplikasi dari hasil query.

        INSERT digunakan untuk menambahkan data pada kolom yang terdapat pada table. Contoh :

        INSERT INTO mahasiswas VALUES ("Muhammad Zaid Abdillah", 21)

        INSERT INTO mahasiswas (fullName, age, phoneNumber) VALUES ("Muhammad Zaid Abdillah", 21, "0851xxxxxx74")


 
 
 
 
 
 
