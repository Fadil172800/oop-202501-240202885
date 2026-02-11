 Laporan Praktikum Minggu 13

Topik: GUI Lanjutan JavaFX (TableView & Lambda Expression) – Agri-POS

Identitas

Nama : Syukron Nur Fadillah

NIM : 240202885

Kelas : 3IKKA

Tujuan
Memahami penggunaan TableView pada JavaFX untuk menampilkan data.
Memahami integrasi koleksi objek (ObservableList<Product>) dengan GUI.
Memahami penggunaan lambda expression untuk event handling.
Mengetahui alur integrasi GUI dengan Service & DAO.
Memahami pengembangan GUI lanjutan pada aplikasi Agri-POS.

Dasar Teori
TableView (JavaFX) digunakan untuk menampilkan data dalam bentuk tabel.
ObservableList digunakan agar perubahan data langsung ter-update di UI.
Lambda Expression menyederhanakan penulisan event handler.
Arsitektur MVC memisahkan View, Controller, Service, dan DAO.
Prinsip DIP (SOLID): View tidak boleh mengakses DAO atau database secara langsung.

Langkah Praktikum
Mempelajari modul Bab 13 (TableView & Lambda Expression).
Melanjutkan struktur project dari Week 12.
Mendesain tampilan GUI lanjutan menggunakan TableView<Product>.
Menyiapkan method loadData() untuk mengambil data dari database melalui ProductService.
Menghubungkan tombol “Tambah Produk” dan “Hapus Produk” dengan event handler lambda.

📌 Catatan Penting (Status Proyek):
Praktikum belum dapat dijalankan karena ketergantungan pada:

Week 11 (DAO + JDBC + PostgreSQL) → gagal download & login PostgreSQL


Hasil Eksekusi

📌 Belum ada hasil eksekusi GUI lanjutan karena backend (DAO + PostgreSQL) dan GUI dasar (Week 12) belum berhasil dikonfigurasi.


Kendala utama:

PostgreSQL gagal di-download / instalasi

Gagal login PostgreSQL


Dampak:

Data tidak bisa diambil (findAll())

TableView tidak bisa menampilkan data


Kesimpulan

Pada praktikum minggu ke-13, pengembangan GUI lanjutan menggunakan TableView dan lambda expression belum dapat direalisasikan karena modul backend (DAO + PostgreSQL) pada Week 11 serta GUI dasar pada Week 12 belum berhasil dijalankan akibat kendala teknis pada proses download dan login PostgreSQL. Meskipun implementasi belum berjalan, konsep TableView, event handling dengan lambda, serta alur integrasi MVC (View–Controller–Service–DAO–DB) telah dipahami. Praktikum akan dilanjutkan setelah kendala teknis pada Week 11 berhasil diatasi.
