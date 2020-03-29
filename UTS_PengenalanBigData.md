Nama  : Husef Sholikhul Ibad

NIM   : 185410110

Kelas : TI4

Jurusan: Teknik Informatika S1




__UTS Pengenalan Big Data__

1. cari dan sebutkan 3 DBMS yang bisa digunakan untuk mengelola Big Data !

__Jawaban :__ 

    1. Mysql

       MySQL dapat digunakan pada jaringan dan cukup portable bila digunakan di komputer manapun atau user manapun (multiuser).

    2. PostgreSQL
       
       PostgreSQL adalah sebuah software DBMS yang disebarluaskan secara bebas dan merupakan yang paling banyak digunakan untuk pengembangan database karena Sifatnya yang open source dan memiliki banyak fitur.

    3. Microsoft SQL Server

       SQL Server adalah sebuah software RDBMS (Relational Database Management System) dari Microsoft. SQL Server digunakan untuk kalangan bisnis skala kecil menengah dan dapat menangani data yang cukup besar.


2. Carilah contoh masalah Big Data yang bisa dikelola menggunakan salah satu DBMS tersebut, jelaskan mulai dari instalasi sampai CRUD untuk data menggunakan DBMS tersebut,Asumsikan anda memecahkan masalah Big Data Yang sudah anda cari contoh tadi, jelaskan kira-kira bagaimana arsitektur data solusi Big Data menggunakan DBMS tersebut gambarkan diagramnya.

__Jawaban :__

__PostgreSQL__  Memungkinkan user untuk mendefinisikan SQL nya sendiri terutama untuk pembuatnya. Fuction Dengan model class ini postgreSql lebih mudah dikembangkan di tingkat User dan bisa mendefinisikan sebuah tabel sebagai turunan tabel lainnya.

__Instalasi PostgreSQL__

1. Buat sebuah file pgdg.list di dalam folder /etc/apt/sources.list.d/. Kemudian isikan file tersebut dengan Syntax :

   *deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main*

2. Lakukan import key dengan menjalankan Syntax :

   *wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \sudo apt-key add -*

3. Update repository dengan Syntax : 

   *sudo apt-get update*

4. Lakukan instalasi postgreSQL dengan Syntax : 

   *sudo apt-get install postgresql-9.5*

__Konfigurasi User Pada PostgreSQL__

1. konfigurasi user pada postgreSQL dengan Syntax : 

   *sudo -u postgres psql postgres*

   ketikan \password postgres, kemudian tekan enter lalu masukkan password untuk default user yang kita gunakan, secara default user yang digunakan adalah postgres. Untuk keluar dari cli psql silahkan jalankan perintah \q.

__Membuat User Dan Database__

1. Query Select

   Query select berfungsi untuk mengambil data, sebelum menjalankan query select, kita akan membuat tabel terlebih dahulu, silahkan login terlebih dahulu melalui terminal anda ke psql. 

   ```java
   CREATE TABLE mahasiswa(
    npm VARCHAR(8),
    nama VARCHAR(50) not null,
    kelas VARCHAR(5) not null,
    PRIMARY KEY(npm)
    );
   ```
   akan muncul
   
   ```java
   belajar-postgresql=> CREATE TABLE mahasiswa(
   belajar-postgresql(> npm VARCHAR(8),
   belajar-postgresql(> nama VARCHAR(50) not null,
   belajar-postgresql(> kelas VARCHAR(5) not null,
   belajar-postgresql(> PRIMARY KEY(npm)
   belajar-postgresql(> );
   CREATE TABLE
   ```
   untuk mengambil semua data, kita dapat melakukannya dengan perintah.

   ```java
   SELECT * FROM mahasiswa;
   ```
   maka akan muncul 

   ```java
   belajar-postgresql=> SELECT * FROM mahasiswa;
   npm | nama | kelas 
   -----+------+-------
   (0 rows)
   ```
   Data masih kosong dikarenakan kita belum melakukan inputan terhadap data mahasiswa.

2. Query Insert

   Query insert pada postgreSQL juga sama seperti pada dbms umunya, silahkan jalankan perintah berikut berikut untuk menyimpan sebuah data mahasiswa.

   ```java
   INSERT INTO mahasiswa (npm, nama, kelas) VALUES ('185410110', 'Husef', '4');
   ```

   maka akan muncul output

   ```java
   belajar-postgresql=> INSERT INTO mahasiswa (npm, nama, kelas) VALUES ('185410110', 'Husef', '4'); INSERT 0 1 
   ```

   kemudian lakukan pengecekan apakah data telah disimpan atau tidak dengan perintah select, jika data tersimpan maka akan muncul output seperti berikut.

   ```java
   belajar-postgresql=> SELECT * FROM mahasiswa;
   npm    |      nama      | kelas 
   ----------+----------------+-------
   185410110 | Husef | 4
   (1 row)
   ```
3. Query Update
   
   Query ini berfungsi untuk menghapus data pada database.

   ```java
   DELETE FROM mahasiswa WHERE npm = '185410110';
   ```

   maka akan muncul output

   ```java
   belajar-postgresql=> DELETE FROM mahasiswa WHERE npm = '185410110';
   DELETE 1
   ```
    lakukan pengecekan kembali dengan perintah select

    ```java
    belajar-postgresql=> SELECT * FROM mahasiswa;
    npm | nama | kelas 
    -----+------+-------
    (0 rows)
    ```

