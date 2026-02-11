Laporan Praktikum Minggu 11
Topik: Data Access Object (DAO) dan CRUD Database dengan JDBC (PostgreSQL)
Identitas
Nama : Syukron Nur Fadillah
NIM : 240202885
Kelas : 3IKKA

Tujuan
Tujuan praktikum minggu ke-11 ini adalah:
Memahami konsep Data Access Object (DAO) dalam pemrograman berorientasi objek.
Mengetahui cara menghubungkan aplikasi Java dengan database PostgreSQL menggunakan JDBC.
Memahami alur kerja operasi CRUD (Create, Read, Update, Delete).
Mengetahui cara integrasi DAO dengan class aplikasi OOP.

Dasar Teori
DAO (Data Access Object) memisahkan logika akses database dari logika utama program.
JDBC (Java Database Connectivity) digunakan untuk menghubungkan Java dengan database.
PreparedStatement digunakan untuk mengeksekusi query SQL dengan parameter agar lebih aman.
CRUD terdiri dari operasi Create, Read, Update, dan Delete pada database.
Pemisahan layer membuat program lebih rapi dan mudah dikembangkan.

Langkah Praktikum
Mempelajari materi DAO dan JDBC dari modul praktikum Week 11.
Menyiapkan database PostgreSQL (percobaan download dan instalasi PostgreSQL).
Membuat struktur folder project sesuai panduan praktikum.
Membuat class Product, interface ProductDAO, dan class ProductDAOImpl.
Membuat class MainDAOTest untuk integrasi DAO.
Melakukan percobaan koneksi database menggunakan JDBC.

Commit project dengan format:

week11-dao-database: implementasi DAO dan CRUD JDBC
📌 Catatan:
Proyek belum dapat dijalankan sepenuhnya karena proses download PostgreSQL gagal dan terjadi kendala saat login ke PostgreSQL.

Hasil Eksekusi

📌 Belum ada hasil eksekusi karena:

PostgreSQL gagal di-download / di-install

Gagal login ke PostgreSQL

Aplikasi Java belum bisa terhubung ke database

Sehingga screenshot hasil CRUD belum tersedia.


Analisis
Secara konsep, arsitektur DAO sudah dipahami:
Product sebagai Model
ProductDAO sebagai interface
ProductDAOImpl sebagai implementasi
MainDAOTest sebagai integrasi aplikasi

Kendala utama:
Gagal download PostgreSQL (koneksi internet / error installer).
Gagal login PostgreSQL (password salah atau service belum berjalan).
Akibatnya koneksi JDBC gagal dan CRUD tidak dapat diuji.


Kesimpulan

Pada praktikum minggu ke-11 ini, implementasi aplikasi DAO dan CRUD menggunakan JDBC belum dapat dijalankan karena terjadi kendala teknis pada proses instalasi dan login PostgreSQL. Akibatnya, koneksi antara aplikasi Java dan database belum berhasil sehingga proses pengujian operasi CRUD (Create, Read, Update, Delete) belum dapat dilakukan.

Quiz

Apa itu DAO?
Jawaban:
DAO adalah pola desain untuk memisahkan akses database dari logika utama aplikasi.

Apa fungsi JDBC?
Jawaban:
JDBC berfungsi untuk menghubungkan aplikasi Java dengan database.

Mengapa menggunakan PreparedStatement?
Jawaban:
Untuk keamanan (mencegah SQL Injection) dan memudahkan penggunaan parameter dalam query SQL.
