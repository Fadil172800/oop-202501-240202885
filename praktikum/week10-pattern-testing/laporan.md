# Laporan Praktikum Minggu 10
Design Pattern (Singleton, MVC) dan Unit Testing menggunakan JUnit

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3ikka

---

## Tujuan
-Menjelaskan konsep dasar design pattern dalam rekayasa perangkat lunak.

-Mengimplementasikan Singleton Pattern dengan benar.

-Menjelaskan dan menerapkan Model–View–Controller (MVC) pada aplikasi sederhana.

-Membuat dan menjalankan unit test menggunakan JUnit.

-Menganalisis manfaat penerapan design pattern dan unit testing terhadap kualitas perangkat lunak.

## Dasar Teori
-Design Pattern adalah solusi desain yang telah teruji untuk menyelesaikan masalah umum dalam pengembangan perangkat lunak.

-Singleton Pattern menjamin suatu class hanya memiliki satu instance dan menyediakan titik akses global.

-MVC (Model–View–Controller) memisahkan tanggung jawab aplikasi menjadi tiga komponen:

    Model: Data dan logika bisnis

    View: Tampilan/output ke pengguna

-Controller: Penghubung antara Model dan View

-Unit Testing menggunakan JUnit bertujuan untuk memastikan fungsi berjalan sesuai harapan dan mendeteksi kesalahan lebih awal.
## Langkah Praktikum
Setup Project: Membuat struktur direktori sesuai panduan praktikum.

Implementasi Singleton Pattern:

Membuat kelas DatabaseConnection dengan constructor private

Mengimplementasikan method getInstance() untuk mendapatkan instance tunggal

Commit: week10-pattern-testing: implement singleton database connection

Implementasi MVC Pattern:

Membuat package model, view, dan controller

Membuat kelas Product sebagai Model

Membuat kelas ConsoleView sebagai View

Membuat kelas ProductController sebagai Controller

Commit: week10-pattern-testing: implement mvc for product feature

Implementasi Unit Testing:

Membuat test class ProductTest di package test

Menulis test case untuk menguji fungsi kelas Product

Menjalankan test menggunakan JUnit

Commit: week10-pattern-testing: add unit tests for product

Integrasi dan Testing:

Membuat kelas AppMVC sebagai main program

Mengintegrasikan semua komponen

Menjalankan program dan unit test

Dokumentasi hasil

<img width="1919" height="1079" alt="Screenshot 2026-01-22 205816" src="https://github.com/user-attachments/assets/55ba3eac-55a2-4d40-bff4-b08a6c7fc7de" />

<img width="1919" height="1079" alt="Screenshot 2026-01-22 204611" src="https://github.com/user-attachments/assets/1d583386-8a04-4e04-b8bd-a1e201ca6aca" />

## Kode Program
sudah ada


## Analisis
1. Penerapan Singleton Pattern
Keberhasilan: Kelas DatabaseConnection hanya dapat memiliki satu instance

Bukti: db1 == db2 menghasilkan true karena kedua variabel merujuk ke instance yang sama

Manfaat: Menghemat resource karena koneksi database tidak dibuat berulang kali

Implementasi: Menggunakan synchronized untuk thread safety

2. Penerapan MVC Pattern
Pemisahan Tanggung Jawab:

Model (Product): Menangani data dan logika bisnis

View (ConsoleView): Menangani tampilan dan output

Controller (ProductController): Mengkoordinasikan interaksi antara Model dan View

Manfaat:

Kode lebih terorganisir dan mudah dipelihara

Perubahan pada View tidak mempengaruhi Model

Logika bisnis terisolasi dalam Model

3. Penerapan Unit Testing
Cakupan Testing: Menguji semua aspek penting dari kelas Product

Jenis Test:

Test getter dan setter methods

Test business logic (calculateTotalValue)

Test validasi input (harga dan stok tidak boleh negatif)

Test edge cases

Manfaat:

Memastikan kode berfungsi sesuai spesifikasi

Mendeteksi bug lebih awal

Mempermudah refactoring di masa depan

4. Konsistensi dengan Desain UML
Implementasi sesuai dengan desain class diagram pada minggu 6

Product class memiliki atribut dan method yang konsisten

Pola desain (Singleton, MVC) meningkatkan maintainability seperti yang diharapkan dalam NFR

5. Kendala dan Solusi
Kendala: Thread safety pada Singleton Pattern

Solusi: Menggunakan synchronized pada method getInstance()

Kendala: Validasi input pada setter methods

Solusi: Menambahkan kondisi if untuk memastikan nilai valid



## Kesimpulan
-Singleton Pattern berhasil diimplementasikan untuk mengelola koneksi database secara efisien, mencegah pembuatan instance berlebihan.

-MVC Pattern berhasil diterapkan dengan pemisahan tanggung jawab yang jelas antara Model, View, dan Controller, meningkatkan modularitas dan maintainability kode.

-Unit Testing menggunakan JUnit berhasil memvalidasi semua fungsionalitas kelas Product dengan 6 test case yang semuanya passed.

-Penerapan design pattern dan unit testing secara signifikan meningkatkan kualitas perangkat lunak dalam hal:

    Readability: Kode lebih mudah dibaca dan dipahami

    Maintainability: Lebih mudah diubah dan diperbaiki

    Testability: Lebih mudah diuji secara otomatis

    Reusability: Komponen dapat digunakan kembali

-Praktikum ini memberikan pemahaman praktis tentang bagaimana pola desain dan testing berkontribusi pada pengembangan perangkat lunak yang robust.


## Quiz
1. Mengapa constructor pada Singleton harus bersifat private?
Jawaban:
Constructor pada Singleton harus bersifat private untuk mencegah instantiasi dari luar kelas. Dengan constructor private, hanya kelas itu sendiri yang dapat membuat instance. Ini memastikan bahwa:

Tidak ada kode lain yang dapat membuat instance baru dengan operator new

Kontrol penuh atas pembuatan instance berada dalam kelas Singleton

Garansi bahwa hanya akan ada satu instance yang dibuat melalui method getInstance()

2. Jelaskan manfaat pemisahan Model, View, dan Controller.
Jawaban:
Manfaat pemisahan Model, View, dan Controller (MVC):

Separation of Concerns: Setiap komponen memiliki tanggung jawab spesifik

Maintainability: Perubahan pada satu komponen tidak mempengaruhi komponen lain

Testability: Model dapat diuji terpisah dari View

Reusability: Model dan Controller dapat digunakan dengan View yang berbeda

Parallel Development: Developer dapat bekerja pada komponen berbeda secara bersamaan

Flexibility: Mudah mengganti View tanpa mengubah Model atau Controller

3. Apa peran unit testing dalam menjaga kualitas perangkat lunak?
Jawaban:
Peran unit testing dalam menjaga kualitas perangkat lunak:

Deteksi Bug Dini: Menemukan bug lebih cepat dalam siklus pengembangan

Regression Testing: Memastikan perubahan kode tidak merusak fungsi yang ada

Dokumentasi: Berfungsi sebagai dokumentasi hidup tentang cara menggunakan kode

Refactoring Safety: Memberi kepercayaan untuk melakukan refactoring

Desain yang Lebih Baik: Memaksa developer untuk menulis kode yang modular dan testable

Kualitas Kode: Mengidentifikasi area kode yang kompleks atau rentan error

4. Apa risiko jika Singleton tidak diimplementasikan dengan benar?
Jawaban:
Risiko jika Singleton tidak diimplementasikan dengan benar:

Multiple Instances: Dapat terbentuk lebih dari satu instance, menghilangkan tujuan utama pattern

Thread Safety Issues: Pada environment multi-thread, dapat terjadi race condition

Serialization Issues: Instance dapat direplikasi melalui serialization/deserialization

Reflection Attack: Menggunakan reflection untuk memanggil constructor private

ClassLoader Issues: Pada environment dengan multiple class loaders

Testing Difficulties: Sulit melakukan unit testing karena ketergantungan global

Memory Leaks: Instance tetap hidup selama aplikasi berjalan, berpotensi menyebabkan memory leak

