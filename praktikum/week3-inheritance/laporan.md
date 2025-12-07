# Laporan Praktikum Minggu 3
Topik: Inheritance (Kategori Produk)

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3IKKA

## Tujuan
Mahasiswa memahami konsep inheritance dalam OOP.
Mahasiswa mampu membuat superclass Produk dan subclass Benih, Pupuk, dan AlatPertanian.
Mahasiswa dapat menggunakan keyword super untuk memanggil konstruktor parent class.
Mahasiswa dapat menjalankan program dan menganalisis perbedaan antara class tunggal dan hierarki class.

## Dasar Teori
1.Inheritance adalah mekanisme di mana sebuah class dapat mewarisi atribut dan method dari class lain.
2.Superclass adalah class induk, sedangkan subclass merupakan class turunan.
3.Keyword super digunakan untuk mengakses konstruktor atau method superclass.
4.Inheritance membuat kode lebih ringkas, reusable, dan mudah dikembangkan.
5.Dalam aplikasi POS, inheritance membantu mengelompokkan produk berdasarkan kategori sehingga struktur kode lebih rapi.

## Langkah Praktikum
-Menggunakan class Produk dari minggu sebelumnya sebagai superclass.
-Membuat tiga subclass:
  Benih (atribut tambahan: varietas)
  Pupuk (atribut tambahan: jenis)
  AlatPertanian (atribut tambahan: material)
-Setiap subclass memanggil konstruktor superclass menggunakan super().
-Membuat file MainInheritance.java untuk menampilkan data objek subclass.
-Menjalankan program dan membuat screenshot hasil.
-Melakukan commit dengan pesan: week3-inheritance.

## Kode Program
Benih.java
 package com.upb.agripos.model;

public class Benih extends Produk {
    private String varietas;

    public Benih(String kode, String nama, double harga, int stok, String varietas) {
        super(kode, nama, harga, stok);
        this.varietas = varietas;
    }

    public String getVarietas() { return varietas; }
    public void setVarietas(String varietas) { this.varietas = varietas; }
}

Pupuk.java
 package com.upb.agripos.model;

public class Pupuk extends Produk {
    private String jenis;

    public Pupuk(String kode, String nama, double harga, int stok, String jenis) {
        super(kode, nama, harga, stok);
        this.jenis = jenis;
    }

    public String getJenis() { return jenis; }
    public void setJenis(String jenis) { this.jenis = jenis; }
}

AlatPertanian.java
 package com.upb.agripos.model;

public class AlatPertanian extends Produk {
    private String material;

    public AlatPertanian(String kode, String nama, double harga, int stok, String material) {
        super(kode, nama, harga, stok);
        this.material = material;
    }

    public String getMaterial() { return material; }
    public void setMaterial(String material) { this.material = material; }
}

MainInheritance.java
package com.upb.agripos;

import com.upb.agripos.model.*;
import com.upb.agripos.util.CreditBy;

public class MainInheritance {
    public static void main(String[] args) {
        Benih b = new Benih("BNH-001", "Benih Padi IR64", 25000, 100, "IR64");
        Pupuk p = new Pupuk("PPK-101", "Pupuk Urea", 350000, 40, "Urea");
        AlatPertanian a = new AlatPertanian("ALT-501", "Cangkul Baja", 90000, 15, "Baja");

        System.out.println("Benih: " + b.getNama() + " Varietas: " + b.getVarietas());
        System.out.println("Pupuk: " + p.getNama() + " Jenis: " + p.getJenis());
        System.out.println("Alat Pertanian: " + a.getNama() + " Material: " + a.getMaterial());

        CreditBy.print("<NIM>", "<Nama Mahasiswa>");
    }
}

## Hasil Eksekusi
<img width="1919" height="1079" alt="Screenshot 2025-11-19 212016" src="https://github.com/user-attachments/assets/6ef0bf93-287d-48f2-b561-b8b305691c74" />


## Analisis
-Program menggunakan konsep inheritance, di mana class Benih, Pupuk, dan AlatPertanian mewarisi atribut kode, nama, harga, dan stok dari superclass Produk.
-Dengan inheritance, subclass tidak perlu menulis ulang atribut yang sudah ada pada parent class → kode lebih efisien.
-super() digunakan untuk memanggil konstruktor parent sehingga atribut diwariskan dengan benar.
-Perbedaan minggu ini dibanding minggu sebelumnya:
  Minggu sebelumnya: hanya satu class → data produk tidak terkelompok.
  Minggu ini: class produk dikategorikan → struktur lebih rapi dan scalable untuk fitur POS yang lebih kompleks.
-Kendala yang muncul biasanya berupa error package atau salah penempatan file. Solusi: memastikan struktur folder sesuai dengan deklarasi package.
## Kesimpulan
Dengan menerapkan inheritance, program menjadi lebih terstruktur, efisien, dan mudah dikembangkan. Subclass dapat memiliki atribut tambahan tanpa perlu menyalin kode dari superclass. Konsep pewarisan ini penting untuk membangun aplikasi POS pertanian yang modular dan mudah diperluas.

## Quiz
1. Apa keuntungan menggunakan inheritance dibanding membuat class terpisah tanpa hubungan?

Inheritance memberikan banyak keuntungan penting dalam pemrograman berorientasi objek karena memungkinkan sebuah class mewarisi atribut dan perilaku dari class lainnya. Jika setiap class dibuat secara terpisah tanpa hubungan, maka banyak kode yang harus ditulis ulang dan berpotensi menimbulkan inkonsistensi.

Keuntungan utama inheritance adalah:

Mengurangi duplikasi kode
Atribut dan perilaku dasar yang sama cukup ditulis sekali di superclass. Semua subclass otomatis mewarisinya sehingga kode lebih ringkas dan efisien.

Struktur program lebih terorganisir
Produk-produk pertanian dapat dikelompokkan berdasarkan hubungan hierarki, misalnya semua termasuk kategori “Produk”, sehingga program lebih mudah dipahami dan dikelola.

Mempermudah pengembangan dan pemeliharaan
Jika terjadi perubahan pada atribut umum, kita cukup memperbaikinya satu kali di superclass, dan perubahan itu langsung berlaku ke seluruh subclass.

Mendukung polimorfisme
Objek-objek dari subclass yang berbeda dapat diperlakukan sebagai objek dari superclass, sehingga mempermudah pengolahan data yang beragam dalam satu struktur.

Lebih fleksibel dan scalable
Penambahan jenis produk baru menjadi lebih mudah karena cukup membuat subclass baru tanpa mengubah struktur dasar program.

Secara keseluruhan, inheritance membuat program lebih rapi, konsisten, mudah dikembangkan, dan mengurangi risiko kesalahan.

2. Bagaimana cara subclass memanggil konstruktor superclass?

Subclass memanggil konstruktor superclass dengan menggunakan mekanisme khusus yang disediakan dalam pemrograman berorientasi objek, yaitu pemanggilan konstruktor dari class induk pada awal proses pembuatan objek subclass.

Tujuan pemanggilan konstruktor superclass adalah:

Menginisialisasi atribut warisan secara benar
Superclass biasanya menyimpan atribut-atribut dasar seperti kode, nama, harga, dan stok. Karena atribut tersebut sering bersifat tertutup (private), maka subclass perlu meminta superclass untuk mengisi atribut tersebut melalui konstruktor.

Menjamin konsistensi pembuatan objek
Dengan memanggil konstruktor superclass, semua aturan inisialisasi yang dibuat di parent class tetap berlaku pada subclass.

Mencegah pengulangan logika
Daripada menulis ulang logika inisialisasi yang sudah ada di superclass, subclass cukup memanggil konstruktor parent sehingga kode lebih efisien.

Pemanggilan konstruktor superclass harus dilakukan pada awal konstruktor subclass agar atribut dasarnya selesai diinisialisasi sebelum atribut tambahan milik subclass diproses.

3. Berikan contoh kasus di POS pertanian selain Benih, Pupuk, dan Alat Pertanian yang bisa dijadikan subclass.

Ada banyak jenis produk pertanian lain yang dapat dibuat sebagai subclass dari class “Produk” berdasarkan karakteristik khusus yang mereka miliki. Berikut beberapa contoh yang relevan dalam sistem POS pertanian:

a. Pestisida

Termasuk insektisida, fungisida, dan herbisida.
Alasan dijadikan subclass:
Pestisida memiliki informasi khusus seperti jenis bahan aktif dan kategori penggunaan yang tidak dimiliki produk lain.

b. Obat Tanaman atau Zat Pengatur Tumbuh (ZPT)

Digunakan untuk merangsang pertumbuhan akar, batang, atau bunga.
Alasan:
Membutuhkan atribut tambahan seperti dosis pemakaian dan fungsi spesifik.

c. Media Tanam

Contohnya: tanah humus, cocopeat, sekam bakar.
Alasan:
Setiap jenis media memiliki komposisi, berat, dan karakteristik unik.

d. Peralatan Irigasi

Seperti selang, pompa air, nozzle, dan sprayer.
Alasan:
Memiliki spesifikasi teknis yang berbeda, misalnya ukuran selang atau kapasitas pompa.

e. Nutrisi Hidroponik

Misalnya nutrisi AB Mix.
Alasan:
Membutuhkan informasi konsentrasi, komposisi, dan tipe tanaman tujuan.

f. Bibit Ternak atau Pakan Ternak

Misalnya bibit ikan, pakan ayam, pakan lele.
Alasan:
Memiliki parameter khusus seperti kandungan nutrisi atau kategori hewan.
