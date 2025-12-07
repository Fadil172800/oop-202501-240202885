# Laporan Praktikum Minggu 4
Topik: Polymorphism (Overloading, Overriding, Dynamic Binding)

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3IKKA

## Tujuan
Mahasiswa memahami konsep polymorphism dalam pemrograman berorientasi objek.

Mahasiswa dapat membedakan overloading dan overriding.

Mahasiswa mampu mengimplementasikan method overriding, method overloading, dan dynamic binding dalam program.

Mahasiswa mampu menganalisis bagaimana polymorphism membuat kode lebih fleksibel dan efisien.

## Dasar Teori
Polymorphism adalah kemampuan objek untuk merespons pemanggilan method yang sama dengan cara yang berbeda.

Method Overloading terjadi ketika sebuah class memiliki beberapa method dengan nama sama tetapi parameter berbeda.

Method Overriding terjadi ketika subclass menuliskan ulang implementasi method yang diwarisi dari superclass.

Dynamic Binding menentukan method mana yang dipanggil berdasarkan tipe objek saat runtime, bukan berdasarkan tipe referensi.

Polymorphism membuat program fleksibel dan memungkinkan implementasi berbeda pada objek yang berbagi superclass.

## Langkah Praktikum
Menambahkan method tambahStok dengan dua versi (overloading) pada class produk.

Menambahkan method getInfo pada superclass, lalu meng-override method tersebut pada setiap subclass.

Membuat array berisi objek-objek subclass yang disimpan dalam referensi superclass untuk menguji dynamic binding.

Menjalankan program dan mengamati bagaimana setiap objek merespons pemanggilan method yang sama.

Memanggil CreditBy untuk menampilkan identitas.

Melakukan commit dengan pesan week4-polymorphism.
## Kode Program
1.Produk.java (Overloading & getInfo default)
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

    public void tambahStok(int jumlah) {
        this.stok += jumlah;
    }

    public void tambahStok(double jumlah) {
        this.stok += (int) jumlah;
    }

    public String getInfo() {
        return "Produk: " + nama + " (Kode: " + kode + ")";
    }
}


```java
// Contoh
Produk p1 = new Produk("BNH-001", "Benih Padi", 25000, 100);
System.out.println(p1.getNama());
```
)

2.Benih.java (Overriding)
  package com.upb.agripos.model;

public class Benih extends Produk {
    private String varietas;

    public Benih(String kode, String nama, double harga, int stok, String varietas) {
        super(kode, nama, harga, stok);
        this.varietas = varietas;
    }

    @Override
    public String getInfo() {
        return "Benih: " + super.getInfo() + ", Varietas: " + varietas;
    }
}

3.MainPolymorphism.java
  package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainPolymorphism {
    public static void main(String[] args) {
        Produk[] daftarProduk = {
            new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64"),
            new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea"),
            new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja")
        };

        for (Produk p : daftarProduk) {
            System.out.println(p.getInfo()); // Dynamic Binding
        }

        CreditBy.print("<NIM>", "<Nama Mahasiswa>");
    }
}

## Hasil Eksekusi

<img width="1919" height="1079" alt="Screenshot 2025-12-07 202431" src="https://github.com/user-attachments/assets/a1128aaf-4e13-49a9-9492-889531cc405d" />

## Analisis
Pada program ini, method yang sama yaitu getInfo() dipanggil dari referensi superclass, tetapi hasilnya berbeda tergantung pada objek sebenarnya. Hal ini menunjukkan konsep dynamic binding, di mana Java memilih method berdasarkan jenis objek saat program berjalan.

Overloading terjadi ketika terdapat dua method tambahStok yang memiliki nama sama tetapi parameter berbeda, sehingga program dapat memroses input stok dalam berbagai bentuk.

Overriding digunakan pada subclass seperti Benih, Pupuk, dan AlatPertanian untuk mengganti implementasi getInfo() sehingga setiap produk menghasilkan informasi yang lebih spesifik.

Dibandingkan minggu sebelumnya (inheritance), minggu ini lebih berfokus pada bagaimana objek yang ada di dalam hierarki class dapat memberikan respons berbeda melalui method yang sama.

Kendala yang muncul biasanya adalah salah penempatan anotasi override atau kesalahan pemanggilan method, namun dapat diatasi dengan memastikan struktur pewarisan sudah benar dan method benar-benar ada di superclass.

## Kesimpulan
Praktikum minggu ini menunjukkan bahwa polymorphism merupakan konsep penting untuk menciptakan program yang fleksibel dan mudah dikembangkan. Dengan menggunakan overloading, overriding, dan dynamic binding, program dapat mengelola berbagai jenis objek dalam satu struktur dan tetap memberikan hasil sesuai kebutuhan masing-masing objek. Polymorphism juga meningkatkan efisiensi kode dan mendukung arsitektur aplikasi yang lebih scalable.
## Quiz
1. Apa perbedaan overloading dan overriding?

Jawaban:
Overloading adalah pembuatan beberapa method dengan nama yang sama dalam satu class, tetapi dengan parameter berbeda. Tujuannya untuk memberikan variasi penggunaan pada satu nama method tanpa mengganti perilaku dasar.
Sementara itu, overriding terjadi ketika subclass menuliskan ulang method yang sudah ada di superclass. Tujuan overriding adalah mengganti implementasi agar sesuai dengan kebutuhan subclass. Overloading berfokus pada banyak versi dalam satu class, sedangkan overriding berfokus pada perubahan perilaku antar class dalam hubungan pewarisan.

2. Bagaimana Java menentukan method mana yang dipanggil dalam dynamic binding?

Jawaban:
Dalam dynamic binding, Java menentukan method mana yang dipanggil berdasarkan tipe objek aktual di memori pada saat program berjalan (runtime), bukan berdasarkan tipe referensi variabelnya.
Meskipun objek disimpan dalam referensi bertipe superclass, Java tetap melihat jenis objek sebenarnya untuk memutuskan implementasi method mana yang dipanggil. Mekanisme ini memungkinkan polymorphism berjalan dan membuat program lebih fleksibel dan dinamis.

3. Berikan contoh kasus polymorphism dalam sistem POS selain produk pertanian.

Jawaban:
Dalam sistem POS umum, polymorphism bisa digunakan pada transaksi pembayaran. Misalnya terdapat superclass Pembayaran dan subclass seperti PembayaranTunai, PembayaranQRIS, dan PembayaranKartu.
Semua subclass memiliki method yang sama seperti prosesPembayaran(), tetapi implementasinya berbeda: pembayaran tunai menghitung kembalian, pembayaran QRIS menampilkan QR code, dan pembayaran kartu memproses validasi mesin EDC.
Ketika sistem memanggil prosesPembayaran() pada array objek pembayaran, setiap metode akan berjalan sesuai jenis pembayaran yang dipilih pelanggan, meskipun semuanya disimpan dalam referensi superclass. Ini menunjukkan penggunaan polymorphism di dunia nyata di luar konteks produk pertanian.
