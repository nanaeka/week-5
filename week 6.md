# Writing Week-6

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

        SELECT * FROM mahasiswa

        SELECT fullName FROM mahasiswa

        SELECT DISTINCT age FROM mahasiswa

        // DISTINCT digunakan untuk menhgilangkan duplikasi dari hasil query.

 *INSERT* digunakan untuk menambahkan data pada kolom yang terdapat pada table. 

        INSERT INTO mahasiswas VALUES ("Nana eka", 21)

        INSERT INTO mahasiswas (fullName, age, phoneNumber) VALUES ("Nana eka", 21, "0851xxxxxx74")

*WHERE, AND, OR, NOT, LIKE* digunakan untuk memberikan syarat dalam menampilkan data.  
 
       SELECT fullName, phoneNumber FROM mahasiswas WHERE id >= 1 AND age >= 21 OR age < 23 NOT id > 4

       SELECT * FROM mahasiswas WHERE fullName LIKE "%Nana"

       SELECT * FROM mahasiswas WHERE fullName LIKE "Eka%"
       
*UPDATE* digunakan untuk melakukan perubahan dari kolom yang dipilih. 

     UPDATE mahasiswas SET age = 22 WHERE id = 1


*DELETE* digunakan untuk menghapus data dalam table yang dipilih. 

     DELETE FROM mahasiswas WHERE fullName = "Nana Eka"

*ORDER BY* digunakan untuk mengurutkan data yang ditampilkan secara ASCENDING atau DESCENDING.

     SELECT * FROM mahasiswas WHERE NOT id = 1 ORBER BY id DESC
     
*GROUP BY* digunakan untuk menampilkan data berdasarkan kolom yang ditentukan.

    SELECT * FROM mahasiswas WHERE NOT id = 1 GROUP BY name

*LIMIT* digunakan untuk membatasi jumlah data yang tampil.

    SELECT * FROM mahasiswas LIMIT 2
 
 
 # MySQL Lanjutan
 
 ### Relations di SQL

  One to One One to Many Many to Many
 
### Database Normalization 

  Merupakan teknik analisis data yang mengorganisasikan atribut - atribut data dengan cara mengelompokkan sehingga terbentuk entitas yang non-redundant, stabil dan fleksibel.

### Normalisasi

Teknik mengelompokkan dan mengorganisasikan atribut/kolom/field data sehingga terbentuk suatu entitas, yang terhindar dari anomali.

- **Tujuan :**

  - terciptanya non-redundan data pada suatu database
  - efisien dalam adanya perubahan struktur tabel/entity suatu database
  - meminimalisir dampak apabila ada perubahan struktur tabel/entity suatu database.

- **Dampak TIDAK menggunakan Normalisasi :**

  - INSERT Anomali : tidak dapat memasukkan beberapa data secara langsung
  - DELETE Anomali : Penhapusan data tidak efektif dan tidak sesuai ekspektasi
  - UPDATE Anomali : data yang diubah terjadi inkonsistensi dalam database dan tidak efektif serta tidak sesuai ekspektasi.

- **Bentuk Umum Normalisasi :**

  - 1NF. Dimana Setiap kolom bernilai tunggal (single value), memiliki nama yang unik. untuk menghilangkan adanya data ganda atau multiple value pada atribut sebuah  entity.
  - 2NF. Dimana sudah berbentuk 1NF, subset data yang terdapat pada entity dihapus dan diberikan aatribut terpisah.
  - 3NF. Dimana seluruh field/atribut/kolom yang tidak ada relasi atau hubungan dengan primary key dihilangkan. dan tidak adanya ketergantungan transitif, dimana suatu   kolom tergantung dengan kolom lain (selain primary key)


- **Join Multiple Tables**

ambil records dari dua atau lebih table database yang memiliki hubungan atau relasi, dan ditampilkan dalam satu set data.

  - INNER JOIN semua baris akan diambil dari kedua tabel yang akan di JOIN, selama kolom cocok dengan kondisi yang sudah ditentukan.
  - LEFT JOINbsemua record dari table di sisi kiri JOIN statement akan dipilih, jika tidak cocok maka akan bernilai NULL.
  - RIGHT JOIN semua records dari table di sisi kiri JOIN statement akan dipilih, bahkan jika table di sebelah kiri tidak memiliki record yang cocok.

- **Aggregate Functions**

ambil suatu nilai pada suatu pengkodisian setelah adanya perhitungan set value atau kumpulan nilai/data.

  - MAX mengembalikan nilai terbesar dari kolom yang dipilih.
  - MIN mengembalikan nilai terkecil dari kolom yang dipilih.
  - SUM mengembalikan jumlah total kolom numerik.
  - COUNT mengembalikan jumlah baris yang cocok dengan kriteria yang ditentukan.
  - AVG mengembalikan nilai rata - rata kolom numerik.


# Authentication & Authorization (Express JS Middleware)

### Authentication

 Authentication proses pengenalan identitas user lalu diberikan akses sesuai dengan authorisasi yang diterima.

- **Metode authentication yang berbasis pada kerahasiaan informasi (Knowledge)** 
   - Password/PIN
   - Digital Certificate : asymmentric cryptography based mengandung informasi rahasia
   - Private key : Owner yang tahu, user biasa lain hanya tahu Public Key

- **Metode authentication yang berbasis pada keunikan (Inherence)**
   - Retina
   - Fingerprint
   - foto paspor
   - Tanda tangan
   - Voice patterns

- **Metode authentication yang berbasis pada user miliki (Posession)**
   - Phone
   - Smart Card

### Authorization

 Authorization proses penentuan hak akses terhadap user dalam mengambil atau melakukan suatu tindakan dalam sistem.
Jadi tanpa authentication tidak ada authorization. namun beberapa sistem ada yang menerapkan pengguna yang tidak ter-otentikasi (anonymous guest) tetap dapat menikmati service sistem tertentu dengan akses sangat terbatas.

 - Client sebelum bisa menikmati layanan server harus melalui proses authentication
 - Setelah authentication berhasil akan terjalin hubungan trust antara client dan server (1 x authentication) kecuali logout.
 - Apabila ada service request, server akan menghubungi system authorization untuk menentukan apakah client berhak atas service yang di request
 
 
### JSON Web Token (JWT)

Sebuah JSON Object sebagai cara aman untuk mewakili sekumpulan informasi antara dua pihak.

Token terdiri dari *Header, Content dan Signature :*

       Header { "alg": "HS256", "typ": "JWT" }

       Payload { "id": 1, "name": "Nana Eka", "age": 21, "phone_number": "085765492908" "iat": 1516239022 }

       Signature HMACSHA256( BASE64URL(header). BASE64URL(payload), secret)

 
**Instalasi dan Cara Pakai**

       npm install jsonwebtoken

       const jwt = require("jsonwebtoken")

       const token = jwt.sign({userData}, "key-ditulis-terserah")

       res.json(token)

  
# Sequelize

 Sequelize adalah ORM (Object Relational Mapping) yang berbasis promise.
 
Sequelize mendukung sebagian besar relational Database seperti :

  - MySQL
  - PostgreSQL
  - MariaDB
  - SQLite
  - Microsoft SQL Server

### ORM (Object Relational Mapping)

teknik mengubah suatu tabel/entity menjadi sebuah object yang nantinya mudah untuk digunakan. Object yang dibuat memiliki property yang sama dengan fiel-field yang ada pada tabel/entity tsb. ORM memungkinkan untuk melakukan query dan manipulasi data pada database menggunakan object oriented.

- **Tujuan** mempermudah mengakses database tanpa melakukan query sama sekali

### Instalasi 

         npm install --save sequelize

         npm install --save mysql2

         npx sequelize-cli init

### Generate Model ###

        npx sequelize-cli model:generate --name Todo --attributes title:string,description:string,startTime:date,status:string

        npx sequelize-cli db:migrate

        npx sequelize-cli db:migrate:undo

### Generate Seed ###

        npx sequelize-cli seed:generate --name demo-todo

        npx sequelize-cli db:seed:all npx sequelize-cli db:seed:undo

