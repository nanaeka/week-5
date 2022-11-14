# Writing week 7


# Sequelize

Sequelize adalah ORM (Object Relational Mapping) Node JS yang berbasis promise.ORM adalah suatu metode/teknik pemrograman yang digunakan untuk mengkonversi data dari lingkungan bahasa pemrograman berorientasi objek (OOP) dengan lingkungan database relational.

**Install Sequelize-cli**
       
       npm i -g sequelize-cli
       
**Install dan init Sequelize**

       sequelize init
    
 npm init ini digunakan untuk membuat package baru, dimana package ini digunakan untuk menyimpan package-package yang akan kita install. Isi didalam package.json
 
         {
        "name": "demo-sequelize",
        "version": "1.0.0",
        "description": "demo sequelize",
        "main": "index.js",
        "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
        },
        "author": "arisupriatna",
        "license": "ISC"
        }
 
Setelah melakukan init, selanjutnya adalah:

        npm install sequlize sequelize-cli pg
        
 Setelah packagenya terinstall, maka package yang kita install tadi akan muncul di file package.json
 
        {
        "name": "medium",
        "version": "1.0.0",
        "description": "demo-sequelize",
        "main": "index.js",
        "scripts": {
          "test": "echo \"Error: no test specified\" && exit 1"
        },
        "author": "arisupriatna",
        "license": "ISC",
        "dependencies": {
          "pg": "^7.4.3",
          "sequelize": "^4.38.0",
          "sequelize-cli": "^4.0.0"
        }
      }
      
Konfigurasi database dengan membuka file config.json dan sesuaikan dengan MySql

        {
          "development": {
            "username": "root",
            "password": null,
            "database": "database_development",
            "host": "127.0.0.1",
            "dialect": "mysql"
          },
          "test": {
            "username": "root",
            "password": null,
            "database": "database_test",
            "host": "127.0.0.1",
            "dialect": "mysql"
          },
          "production": {
            "username": "root",
            "password": null,
            "database": "database_production",
            "host": "127.0.0.1",
            "dialect": "mysql"
          }
        }
      
**create database**
        
        sequelize db:create
        
**model migrate**

Model yang telah dibuat, hanya sebtas file saja. Untuk mengubah file model ke tabel pada database maka lakukan migrate db dengan perintah berikut:
        
        sequelize db:migrate

# Intro MongoDB

  MongoDB adalah salah satu jenis database NoSQL berbasis dokumen dengan menggunakan format file berupa JSON (JavaScript Object Notation). Jika dikomparasikan dengan penggunaan database SQL, dimana setiap data tersimpan dalam bentuk tabel. Sedangkan pada MongoDB, data akan disimpan ke dalam sebuah dokumen berformat JSON.

**Fitur-Fitur MongoDB :**

- Schema-less database, (database tanpa schema) berarti satu kumpulan atau koleksi data bisa memiliki beberapa tipe dokumen di dalamnya. Dokumen ini bisa mengandung banyak konten dalam berbagai ukuran. Fitur ini lah yang membuat MongoDB menjadi program database yang fleksibel.

- Document-oriented, MongoDB adalah database yang berorientasi pada dokumen. Data apa pun yang disimpan di dalam MongoDB itu berbentuk dokumen, bukan tabel. Dalam dokumen-dokumen tersebut, data disimpan dalam field, bukan baris atau kolom. Hal ini juga yang mendukung fleksibilitas MongoDB.

- Indexing, Di database MongoDB, semua field dalam dokumen di-indeks berdasarkan indeks primer dan sekunder. untuk membuat pencarian dan pengambilan data yang tersimpan di MongoDB itu lebih mudah dan cepat.

- Skalabilitas, MongoDB menyediakan fitur horizontal scalability dengan sharding. Sharding adalah distribusi data dengan beberapa server berbeda. Dengan cara ini, data dalam jumlah besar dibagi menjadi beberapa kelompok yang lebih kecil menggunakan shard key. Kemudian, kelompok data ini dibagikan ke beberapa server fisik yang berbeda.

- Replikasi, fitur MongoDB yang mampu membuat salinan data dan mengirimnya ke server yang berbeda-beda. Jadi, jika salah satu server mengalami kerusakan atau masalah, data akan tetap aman karena tersimpan salinannya di server lain.

**Kelebihan dari MongoDB**

1. Sistem Penyimpanan tidak Membutuhkan Tabel
2. Tidak perlu untuk Menggunakan Tabel Terstruktur
3. Telah Terintegrasi dengan JavaScript

**Kekurangan MongoDB**   
    
   membutuhkan memory storage yang besar, Kekurangan lainnya adalah idak bisa menyimpan data lebih besar dari 16 MB di dalam setiap dokumen. Lalu, juga tidak diperbolehkan untuk melakukan nesting data lebih dari 100 level.


Pada database SQL, data disimpan dalam bentuk tabel. Sedangkan pada MongoDB data disimpan dalam bentuk dokumen dengan format JSON.

              {
                 "_id" : ObjectId("54c955492b7c8eb21818bd09"),
                 "alamat" : {
                    "street" : "2 Avenue",
                    "zipcode" : "10075",
                    "building" : "1480",
                    "coord" : [ -73.9557413, 40.7720266 ]
                 },
                 "borough" : "Manhattan",
                 "cuisine" : "Italian",
                 "grades" : [
                    {
                       "date" : ISODate("2014-10-01T00:00:00Z"),
                       "grade" : "A",
                       "score" : 11
                    },
                    {
                       "date" : ISODate("2014-01-16T00:00:00Z"),
                       "grade" : "B",
                       "score" : 17
                    }
                 ],
                 "name" : "Vella",
                 "restaurant_id" : "41704620"
              }

**Membuat Database dan Koleksi Baru**

Mari kita buat Database baru bernama tokobuku.

**Koleksi bisa dibuat dengan perintah:**

               db.createCollections("nama_koleksi")

**Insert Data**

Insert data dapat kita lakukan dengan perintah berikut:

              db.<koleksi>.insert(<data>)

koleksi bernama buku:

              db.buku.insert({
                  judul: "Pemrograman Javascript dan MongoDB",
                  sinopsis: "Panduan Pemrograman Js dan MongoDB",
                  pengarang: "Petani Kode",
                  harga: 98000
              })

### Mengubah Data

Untuk mengubah data, kita bisa menggunakan **fungsi update().**

              db.<koleksi>.update(<query>, <data baru>)

mengubah harga bukunya dari 98000 menjadi 75000.

              db.buku.update(
                  {
                      judul: "Pemrograman Javascript dan MongoDB"
                  },
                  {
                      judul: "Pemrograman Javascript dan MongoDB",
                      sinopsis: "Panduan Pemrograman Js dan MongoDB",
                      pengarang: "Petani Kode",
                      harga: 75000
                  }
              )
Maka hasilnya, semua buku yang berjudul "Pemrograman Javascript dan MongoDB" akan diturunkan harganya menjadi 75000.

### Menghapus Data

Untuk menghapus data, kita bisa menggunakan perintah remove().

              db.<koleksi>.remove(<query>)

Kita akan menghapus buku yang berjudul "Belajar MongoDB", karena stoknya sudah habis 

              db.buku.remove({judul: "Belajar MongoDB"})

Maka data buku yang berjudul "Belajar MongoDB" sudah tiada.

# Web Server with Express & Mongoose

  Mongoose adalah sebuah module pada NodeJS yang di install menggunakan npm, berfungsi sebagai penghubung antara NodeJS dan database nosql MongoDB. Mongoose menyediakan feature diantaranya, model data application berbasis Schema. Dan juga termasuk built-in type casting, validation, query building, business logic hooks dan masih banyak lagi yang menjadi ke andalan mongoose.

**install Mongoose** 

              npm install mongoose.

Koneksi ke database MongoDB, menyalakan terlebih dahulu MongoDB Caranya buka tab baru pada terminal lalu ketik mongod dan enter. Jika terdapat tulisan waiting for connections on port 2707 itu artinya database MongoDB sudah siap. Untuk contoh kasus menggunakan object mobil,

Untuk mengakses database MongoDB dengan mongoose, maka tuliskan kode berikut ini pada server.js.
 
              mongoose.connect('mongodb://localhost/mobil');
















































