 Laporan Praktikum Minggu 12

Topik: GUI Dasar JavaFX (Event-Driven Programming) – Agri-POS
Identitas

Nama : Syukron Nur Fadillah

NIM : 240202885

Kelas : 3IKKA

Tujuan
Memahami konsep event-driven programming pada JavaFX.
Mengetahui cara membangun GUI sederhana untuk input data produk.
Memahami integrasi GUI dengan backend (Service & DAO).
Memahami alur MVC pada aplikasi desktop Java.

Dasar Teori
Event-Driven Programming: program merespons aksi pengguna (klik tombol, input teks).
JavaFX: framework Java untuk membangun antarmuka grafis (GUI).
MVC: pemisahan Model (data), View (UI), Controller (penghubung logika UI).
Service Layer: perantara antara Controller dan DAO agar View tidak berinteraksi langsung dengan database (DIP – SOLID).
Integrasi GUI dengan backend dilakukan melalui ProductService yang memanggil ProductDAO.

Langkah Praktikum
Mempelajari modul Bab 12 tentang JavaFX dan event handling.
Menyiapkan struktur direktori project Week 12.
Merancang form GUI: input kode, nama, harga, stok, dan tombol “Tambah Produk”.

Menyiapkan class:
Product (Model)
ProductDAO (Data Access)
ProductService (Service Layer)
ProductController (Controller)
ProductFormView (View JavaFX)

Mencoba mengintegrasikan GUI dengan backend Week 11.
📌 Catatan Penting:
Praktikum belum dapat direalisasikan karena:
Week 11 (DAO + PostgreSQL) belum selesai
PostgreSQL gagal di-download
Gagal login PostgreSQL

Akibatnya backend (ProductDAO / ProductService) belum bisa dijalankan
Sehingga GUI tidak dapat dihubungkan ke database.

UI karena backend (DAO + PostgreSQL) belum berhasil dikonfigurasi.
Screenshot belum tersedia:
