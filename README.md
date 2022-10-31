# week-5

# Web Server dan RESTful API

## Komponen Web Server
Terdiri dari dua:
 - **Hardware adalah komputer yang menyimpan software web server dan komponen file situs web**
 - **Software adalah web server yang mengontrol bagaimana pengguna mengakses file yang di hosting**
 
 Komunikasi antara Client dengan Server Membuat Requests REST memerlukan request yang dibuat oleh client yang bertujuan untukmendapatkan atau mengubah data pada server. Sebuah request biasanya terdiri dari :
 
 - **HTTP Verb, menentukan operasi apa yang akan dilakukan**
 - **Header, memperbolehkan client untuk mengirim informasi tentang request yang dikirim**
 - **Path terhadap resource tujuan**
 - **Message body opsional yang mengandung data**
 
 HTTP Verbs Terdapat 4 HTTP verb dasar yang digunakan dalam request untuk berinteraksi dengan resource pada REST system : 
 - **GET** digunakan untuk mendapatkan data spesifik (dengan id) atau koleksi data
 - **POST** digunakan untuk membuat data baru
 - **PUT** digunakan untuk mengupdate data spesifik (dengan id)
 - **DELETE** digunakan untuk menghapus data spesifik (dengan id)
 - **PATCH** (partial), mengupdate sebagian data secara spesifik berdasarkan identifier
 
 
Macam - macam **response codes** : 

    - 200 (OK) => standar response untuk HTTP request yang sukses
    - 201 (CREATED) =>  response sbuah HTP request biasanya POST dimana hasil dari item berhasil dibuat atau ditambahkan
    - 204 (NO CONTENT) => response sbuah HTP request biasanya DELETE dimana hasil dari item berhasil dihapus dan tidak tampil
    - 400 (BAD REQUEST)
    - 403 (FORBIDDEN) => user tidak dapat mengakses walaupun data user terdata, karena adanya authorization
    - 404 (NOT FOUND) => data atau konten tidak ditemukan atau belum ada
    - 500 (INTERNAL SERVICE ERROR)
    
## Intro Node JS 

  Definisi Node.js adalah platform JavaSCript yang dapat berjalan di backend atau server-side di komputer secara langsung. Node.js berjalan menggunakan V8 engine pada Chrome, SpiderMonkey engine pada Mozilla, dan Chakra engine pada Microsoft Edge.
