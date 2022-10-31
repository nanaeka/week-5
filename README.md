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

# Node JS Architecture

- **Single Thread** thread adalah setiap unit yang mampu mengeksekusi kode. Javascript menggunakan konsep single thread, yang berarti hanya memiliki satu tumpukan panggilan yang digunakan untuk menjalankan program dengan menggunakan call stack untuk manajememnnya
- **Even Loop** javascript dapat menggunakan multi thread yang terdapat enevt queue yang berguna sebagai penampung ketika terdapat perintah baru yang akan dieksekusi. Event loop akan memfasilitasi kondisi ini, event loop akan memeriksa terus menerus, ketika antrian kosong di call stack maka akan menambah antrian baru dari event queue sampai semua perintah selesai di eksekusi.
- **Server Side Scripting** untuk menampilkan hasil eksekusi javascript biasanya hanya bisa di browser, dengan Node JS dapat menjalankan javascript di server side dengan terminal command line perintah "node"

# Build In Module Node JS

- **Console** module bawaan dari javascript yang ada di node JS untuk digunakan sebagai debug atau menampilkan code secara interface
- **Process** adalah modules yang digunakan untuk menampilkan dan mengontrol prosess Node JS yang sedang dijalankan
- **OS** module merupakan module yang digunakan untuk menyediakan informasi terkait sistem operasi komputer yang digunakan user
- **Util** Module Util merupakan alat bantu / utilities untuk mendukung kebutuhan internal API di Node JS
- **Errors** merupakan modules yang dapat digunakan untuk mendefinisikan error di Node JS sehingga lebih informatif. Kita juga dapat menghandle error menggunakan try catch
- **Buffer** merupakan modules yang digunakan untuk mengakses, mengelola dan mengubah tipe data raw atau tipe data bytes
- **Fs** atau “file system” merupakan module yang dapat membantu berinteraksi dengan file yang ada diluar code. FS paling sering digunakan untuk membaca file dengan ekstensi .txt, .csv, dan .json
- **Timers** merupakan modules yang digunakan untuk melakukan scheduling atau mengatur waktu pemanggilan fungsi yang dapat diatur di waktu tertentu

# Node JS Web Server
- Untuk menggunakan modul HTTP, gunakan **require()**
- Gunakan **method createServer()** untuk membuat server HTTP
- Callback function yang digunakan pada **method http.createServer()**, akan dijalankan ketika seseorang mencoba mengakses komputer pada port 8080.

## Express JS

Definisi Express adalah salah satu package NodeJS yang memungkinkan kita untuk membuat HTTP REST API ataupun aplikasi web dengan mudah.

# response
      status code : 200 body : application/json { "name" : "nana eka", "age" : 22, "greeting" : "hello salam kenal" }


 Instalasi Express merupakan modules atau package yang dikembangkan menggunakan bahasa javascript. npm init -y npm install express --save Nodemon merupakan modules atau package yang mempermudah develope server side application yaitu automatis menjalankan server ketika ada perubahan. npm install -g nodemon Routing Basic Syntax ExpressJS const express = require('express') const app = express() const port = 3000

    app.get('/', (req, res) => { res.send('Hello World!') })
    app.listen(port, () => { console.log('Server is running on port 3000') })

 Basic Routes Routes Routes adalah sebuah endpoint yang dapat kita akses menggunakan URL di website. Didalam routes kita perlu menentkan method API, alamat dan response apa saja yang akan dikeluarkan. app.get('/', (req, res) => { res.send('Hello World') })

**POST PUT PATCH DELETE** Response Dalam route kita dapat mengirim response menggunakan perintah res.write() untuk mengirim plain text ketika mengakses route tersebut. Contohnya seperti berikut :

    app.get('/hello', (req, res) => { res.status(200).json({ "name" : "nana eka", "age' : 22, "greeting" : "Halo salam kenal" }) })

**Query** merupakan parameter yang digunakan untuk membantu menentukan tindakan yang lebih spesifik.
     app.get('/hello', (req, res) => { let name = req.query.name let age = req.query.age
     res.status(200).json({
         name : name,
         age : age,
         greetings : "Halo salam kenal"
     })
     })


**Parameter** merupakan value yang digunakan untuk membantu menentukan tindakan yang lebih spesifik

    app.get('/hello/:name/:age', (req, res) => { let name = req.params.name let age = req.params.age
    res.status(200).json({
        name : name,
        age : age,
        greetings : "Halo salam kenal"
    })
    })

Nested Route 

Sebelum :

    app.get('/hello/nana', (req, res) => { res.send("Halo saya nana") })
    app.get('/hello/eka', (req, res) => { res.send("Halo saya eka") })

Sesudah :

    app.use("/hello", hello)
    const express = require('express') const hello = express.Router()
    hello.get('/nana', (req, res) => { res.send("Halo saya nana") })
    app.get('/eka', (req, res) => { res.send("Halo saya eka") })

 # Middleware
Middleware function adalah sebuah fungsi yang memiliki akses ke object request (req), object response (res), dan sebuah fungsi next didalam request-response cycle.

Fungsi Middleware Menjalankan Kode Selanjutnya 
     const express = require('express') const app = express()
     const skilvulLogger = function (req, res, next) => { console.log("Halo skilvul, request diterima") next() }
     app.use(skilvulLogger)
     app.get('/', function (req, res) { res.send('Hello Skilvul!') })
     app.listen(3000)

Memodifikasi Object Request dan Object Response 
      const express = require('express') 
      const app = express()
      const addRequestTime = function (req, res, next) => { req.requestTime = Date.now() next() }
      app.use(addRequestTime)
      app.get('/', function (req, res) { let responseText = 'Hello World
      ' responseText += 'Requested at: ' + req.requestTime + '' res.send(responseText) })
      app.listen(3000)

Menghentikan Request-Response Cycle 
      const express = require('express') 
      const app = express()
      const stopHere = function (req, res, next) => { res.send("
      request stop from middleware
      ") }
      app.use(stopHere)
      app.get('/', function (req, res) { let responseText = 'Hello Skilvul!' res.send(responseText) })
      app.listen(3000)

Cara Penggunaan Application Level Middleware 
     const addRequestTime = funtion (req, res, next) { req.requestTime = Date.now() next() }
     app.user(addRequestTime) Router Level Middleware const express = require('express') 
     const UserRouter = express.Router() const AdminRouter = express.Router()
     const logUserAction = function(req, res, next) { const username = req.body.username
     console.log(`username ${username} access the API`)
     next()
     }
     userRouter.use(logUserAction)
     UserRouter.get('/users', function(req, res) { res.send('all user data') })
     AdminRouter.get('/admins', function(req, res) { res.send('all admin data') }) Error Handling Middleware 
     const express = require('express') const app = express()
     const errorHandling = function(err, req, res, next) { console.error(err.stack) res.status(500).send('Something broke') }
     app.use(errorHandling)

## Design Database With MySQL

**menentukan Entity**
 Design Database Menentukan Entity Berikut adalah contoh studi kasus yang bisa dijadikan entity dalam database:

User Film Genre Menentukan Attributes dari Entity User id int NOT NULL name varchar(255) email varchar(255) password varchar(255)

Film id int NOT NULL name varchar(255) release_date date

Genre id int NOT NULL name varchar(255) Menentukan Relasi antar Entity User & Film (Many to Many) Film & Genre (Many to Many) User id int NOT NULL name varchar(255) email varchar(255) password varchar(255)

UserFilmFavorite id int NOT NULL userId int filmId int

Film id int NOT NULL name varchar(255) release_date date

FilmGenre id int NOT NULL filmId int genreId int

Genre id int NOT NULL name varchar(255)









