# Laporan Praktikum Minggu 1 (sesuaikan minggu ke berapa?)
Topik:Pengenalan Paradigma dan Setup Proyek

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3ikka

---

## Tujuan
Mahasiswa memahami perbedaan paradigma pemrograman (prosedural, OOP, dan fungsional).

Mahasiswa mampu membuat program sederhana dalam tiga paradigma tersebut.

Mahasiswa dapat men-setup lingkungan kerja (JDK, IDE, Git, JavaFX, PostgreSQL).

Mahasiswa dapat melakukan commit dan push proyek ke Git dengan struktur yang benar.
---

## Dasar Teori
1.Paradigma pemrograman adalah pendekatan atau gaya berpikir dalam menulis program.

2.Paradigma Prosedural menyusun program sebagai kumpulan perintah atau fungsi yang dijalankan secara berurutan.

3.Paradigma OOP (Object-Oriented Programming) berfokus pada objek yang memiliki atribut (data) dan method (perilaku).

4.Paradigma Fungsional menggunakan fungsi murni dan ekspresi untuk memanipulasi data tanpa mengubah state.

5.Paradigma yang tepat membantu meningkatkan maintainability, scalability, dan readability dari suatu program.
---

## Langkah Praktikum
1.Menginstal dan menyiapkan lingkungan kerja: JDK, IDE (IntelliJ IDEA), Git, PostgreSQL, dan JavaFX.

2.Membuat folder proyek dengan nama oop-pos-2310112345.

3.Inisialisasi repository Git dengan perintah git init.

4.Membuat struktur direktori:
praktikum/week1-setup-hello-pos/src/main/java/com/upb/agripos/

5.Membuat tiga file program:
-HelloProcedural.java
-HelloOOP.java
-HelloFunctional.java

6.Menjalankan program untuk memastikan hasilnya sesuai.

7.Mengambil screenshot hasil eksekusi dan menyimpannya di folder screenshots/hasil.png.

8.Melakukan commit dengan pesan:
week1-setup-hello-pos

9.Push ke repository GitHub.
---

## Kode Program

1.// HelloProcedural.java
public class HelloProcedural {
   public static void main(String[] args) {
      String nim = "2310112345";
      String nama = "Budi";
      String[] produk = {"Beras", "Pupuk", "Benih"};
      int[] harga = {10000, 15000, 12000};
      int total = 0;

      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      for (int i = 0; i < produk.length; i++) {
         System.out.println("- " + produk[i] + ": " + harga[i]);
         total += harga[i];
      }
      System.out.println("Total harga semua produk: " + total);
   }
}

2.// HelloOOP.java
class Produk {
   String nama;
   int harga;
   Produk(String nama, int harga) {
      this.nama = nama;
      this.harga = harga;
   }
}

public class HelloOOP {
   public static void main(String[] args) {
      String nim = "2310112345";
      String namaMhs = "Budi";
      Produk[] daftar = {
         new Produk("Beras", 10000),
         new Produk("Pupuk", 15000),
         new Produk("Benih", 12000)
      };
      int total = 0;

      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + namaMhs);
      System.out.println("Daftar Produk:");
      for (Produk p : daftar) {
         System.out.println("- " + p.nama + ": " + p.harga);
         total += p.harga;
      }
      System.out.println("Total harga semua produk: " + total);
   }
}

3.// HelloFunctional.java
import java.util.*;
import java.util.stream.*;

public class HelloFunctional {
   public static void main(String[] args) {
      String nim = "2310112345";
      String nama = "Budi";
      List<String> produk = Arrays.asList("Beras", "Pupuk", "Benih");
      List<Integer> harga = Arrays.asList(10000, 15000, 12000);

      System.out.println("Hello POS World");
      System.out.println("NIM: " + nim + ", Nama: " + nama);
      System.out.println("Daftar Produk:");
      IntStream.range(0, produk.size())
         .forEach(i -> System.out.println("- " + produk.get(i) + ": " + harga.get(i)));

      int total = harga.stream().mapToInt(Integer::intValue).sum();
      System.out.println("Total harga semua produk: " + total);
   }
}


## Hasil Eksekusi
<img width="1918" height="1078" alt="Screenshot oop week 1 " src="https://github.com/user-attachments/assets/17fbb55e-bd6e-4146-9526-6dc0b90b3148" />

## Analisis

1.Pada versi prosedural, program berjalan secara linear dari atas ke bawah dengan menggunakan variabel dan perulangan biasa.

2.Pada versi OOP, program lebih terstruktur karena menggunakan class Produk untuk merepresentasikan entitas dunia nyata. Ini memudahkan pengembangan di masa depan.

3.Pada versi fungsional, kode menjadi lebih ringkas karena menggunakan lambda expression dan stream API untuk menghitung total dan menampilkan data.

4.Perbedaan utama:
-Prosedural → Fokus pada langkah.
-OOP → Fokus pada objek.
-Fungsional → Fokus pada fungsi dan transformasi data.

5.Kendala: Awalnya sedikit kesulitan memahami sintaks lambda di paradigma fungsional, tetapi dapat diatasi dengan membaca dokumentasi Java Stream API.

## Kesimpulan

1.Setiap paradigma memiliki cara berpikir dan struktur berbeda dalam menyusun program.

2.Prosedural cocok untuk program kecil, OOP cocok untuk sistem besar seperti POS, dan Fungsional cocok untuk pemrosesan data yang efisien.

3.Dengan memahami ketiganya, pengembang dapat memilih pendekatan terbaik sesuai kebutuhan proyek.

4.Setup proyek berhasil, program dapat dijalankan dan dikirim ke Git dengan struktur yang benar.

## Quiz
1.Apakah OOP selalu lebih baik dari prosedural?
Jawaban: Tidak selalu. OOP cocok untuk program besar dan kompleks, sedangkan prosedural lebih efisien dan sederhana untuk program kecil.

2.Kapan functional programming lebih cocok digunakan dibanding OOP atau prosedural?
Jawaban: Ketika program berfokus pada transformasi data, pemrosesan paralel, atau analisis data yang membutuhkan ekspresi singkat dan minim perubahan state.

3.Bagaimana paradigma (prosedural, OOP, fungsional) memengaruhi maintainability dan scalability aplikasi?
Jawaban:
Prosedural: sulit dikembangkan jika kode membesar.
OOP: mudah dikelola karena modular dan reusable.
Fungsional: mudah diuji dan efisien karena bebas efek samping.

4.Mengapa OOP lebih cocok untuk mengembangkan aplikasi POS dibanding prosedural?
Jawaban: Karena POS memiliki banyak entitas nyata seperti produk, transaksi, dan pelanggan yang dapat dimodelkan sebagai objek dengan atribut dan perilaku masing-masing.

5.Bagaimana paradigma fungsional dapat membantu mengurangi kode berulang (boilerplate code)?
Jawaban: Karena menggunakan fungsi murni, lambda, dan stream yang memungkinkan penulisan kode singkat tanpa loop dan variabel tambahan.
