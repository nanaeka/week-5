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












