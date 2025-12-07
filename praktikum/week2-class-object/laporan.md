# Laporan Praktikum Minggu 2
Topik: CLASS DAN OBJECT

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3IKKA

## Tujuan
-Mahasiswa memahami konsep class, object, atribut, dan method dalam OOP.
-Mahasiswa dapat menerapkan enkapsulasi menggunakan access modifier dan getter/setter.
-Mahasiswa dapat membuat class Produk beserta object produknya.
-Mahasiswa mampu menampilkan hasil eksekusi dan menyusun laporan praktikum.

## Dasar Teori
1.Class adalah blueprint atau template untuk membuat objek.
2.Object merupakan instansiasi dari class yang memiliki data dan perilaku.
3.Enkapsulasi menyembunyikan data dengan menjadikan atribut private.
4.Getter dan Setter digunakan untuk mengakses dan mengubah nilai atribut.
5.OOP membantu membuat aplikasi lebih terstruktur dan mudah dikembangkan.

## Langkah Praktikum
1.Membuat struktur folder sesuai template pada repositori.
2.Membuat file:
   -Produk.java di package model
   -CreditBy.java di package util
   -MainProduk.java sebagai file main
3.Meng-instansiasi minimal tiga objek produk pertanian
4.Menampilkan informasi produk menggunakan getter.
5.Menjalankan program dan mengambil screenshot hasil.
6.Commit dengan pesan: week2-class-object.
7.Menyusun laporan praktikum minggu ke-2.

## Kode Program
1. Produk.java\
   package com.upb.agripos.model;

public class Produk {
    private String kode;
    private String nama;
    private double harga;
    private int stok;

    public Produk(String kode, String nama, double harga, int stok) {
        this.kode = kode;
        this.nama = nama;
        this.harga = harga;
        this.stok = stok;
    }

    public String getKode() { return kode; }
    public void setKode(String kode) { this.kode = kode; }

    public String getNama() { return nama; }
    public void setNama(String nama) { this.nama = nama; }

    public double getHarga() { return harga; }
    public void setHarga(double harga) { this.harga = harga; }

    public int getStok() { return stok; }
    public void setStok(int stok) { this.stok = stok; }

    public void tambahStok(int jumlah) {
        this.stok += jumlah;
    }

    public void kurangiStok(int jumlah) {
        if (this.stok >= jumlah) {
            this.stok -= jumlah;
        } else {
            System.out.println("Stok tidak mencukupi!");
        }
    }
}

2. CreditBy.java
   package com.upb.agripos.util;

public class CreditBy {
    public static void print(String nim, String nama) {
        System.out.println("\ncredit by: " + nim + " - " + nama);
    }
}

3. MainProduk.java
   package com.upb.agripos;

import com.upb.agripos.model.Produk;
import com.upb.agripos.util.CreditBy;

public class MainProduk {
    public static void main(String[] args) {
        Produk p1 = new Produk("BNH-001", "Benih Padi IR64", 25000, 100);
        Produk p2 = new Produk("PPK-101", "Pupuk Urea 50kg", 350000, 40);
        Produk p3 = new Produk("ALT-501", "Cangkul Baja", 90000, 15);

        System.out.println("Kode: " + p1.getKode() + ", Nama: " + p1.getNama() + ", Harga: " + p1.getHarga() + ", Stok: " + p1.getStok());
        System.out.println("Kode: " + p2.getKode() + ", Nama: " + p2.getNama() + ", Harga: " + p2.getHarga() + ", Stok: " + p2.getStok());
        System.out.println("Kode: " + p3.getKode() + ", Nama: " + p3.getNama() + ", Harga: " + p3.getHarga() + ", Stok: " + p3.getStok());

        // Tampilkan identitas mahasiswa
        CreditBy.print("<NIM>", "<Nama Mahasiswa>");
    }
}

## Hasil Eksekusi
<img width="1919" height="1079" alt="Screenshot 2025-11-19 212016" src="https://github.com/user-attachments/assets/9ca319de-9deb-428e-b27a-d310dc378715" />

## Analisis
-Program berjalan dengan meng-instansiasi tiga objek dari class Produk.
-Setiap objek memiliki nilai atribut berbeda yang diakses menggunakan getter.Enkapsulasi memastikan atribut tidak diakses secara langsung sehingga lebih aman.
-Method tambahan seperti tambahStok dan kurangiStok membantu pengelolaan stok produk.
-Minggu ini mulai menggunakan konsep OOP (class & object), berbeda dengan minggu sebelumnya yang mungkin masih procedural.
-Kendala umum: struktur folder salah, package error, atau import tidak sesuai. Solusi: mengecek ulang nama package dan struktur direktori.

## Kesimpulan
-Dengan menggunakan class dan object, program menjadi lebih terstruktur dan mudah dipelihara.
-Enkapsulasi membantu menjaga keamanan data.
-Implementasi class Produk dapat digunakan untuk pengembangan sistem POS yang lebih kompleks.

## Quiz
-Mengapa atribut sebaiknya dideklarasikan sebagai private dalam class?
Jawaban:
Agar data tidak dapat diakses atau dimodifikasi secara langsung dari luar class. Ini menjaga keamanan data dan mencegah perubahan yang tidak terkontrol.

-Apa fungsi getter dan setter dalam enkapsulasi?
Jawaban:
Getter digunakan untuk mengambil nilai atribut, sedangkan setter digunakan untuk mengubah nilai atribut secara aman sesuai aturan yang ditentukan.

-Bagaimana cara class Produk mendukung pengembangan aplikasi POS yang lebih kompleks?
Jawaban:
Dengan merepresentasikan produk sebagai objek, aplikasi dapat mengelola stok, harga, nama, dan kode produk secara terstruktur. Class ini dapat diperluas untuk fitur transaksi, laporan, filtering produk, dan integrasi database di masa depan.
