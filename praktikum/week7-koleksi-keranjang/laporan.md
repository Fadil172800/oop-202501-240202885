# Laporan Praktikum Minggu 7
Topik: Topik: Collections dan Implementasi Keranjang Belanja

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3ikka

---

## Tujuan
Mahasiswa memahami konsep collection dalam Java (List, Map, Set) dan dapat mengimplementasikannya dalam sistem keranjang belanja Agri-POS untuk mengelola data produk secara efisien.


## Dasar Teori
1.Collections Framework – Struktur data dalam Java untuk mengelola objek secara dinamis, terdiri dari List, Map, dan Set.

2.List (ArrayList) – Menyimpan elemen secara terurut, dapat menyimpan duplikat, akses berdasarkan indeks.

3.Map (HashMap) – Menyimpan data dalam pasangan key-value, akses cepat berdasarkan key.

4.Set (HashSet) – Tidak menyimpan elemen duplikat, tidak mempertahankan urutan.

5.Keranjang Belanja – Studi kasus yang memanfaatkan collection untuk operasi dasar e-commerce seperti tambah, hapus, dan hitung total.

## Langkah Praktikum
1.Setup Project – Membuat struktur direktori sesuai template praktikum.

2.Membuat Class Product – Mendefinisikan class Product dengan atribut code, name, dan price.

3.Implementasi ShoppingCart (ArrayList) – Membuat keranjang belanja dasar dengan ArrayList yang dapat menambah, menghapus, dan menghitung total.

4.Implementasi ShoppingCartMap (HashMap) – Membuat alternatif keranjang dengan Map untuk menangani quantity produk.

5.Main Program – Menguji kedua implementasi dengan menambahkan dan menghapus produk.

6.Commit & Push – Melakukan commit dengan format message: week7-collections: [fitur] [deskripsi singkat].

## Kode Program
1.class produk

package com.upb.agripos;

public class Product {
    private final String code;
    private final String name;
    private final double price;

    public Product(String code, String name, double price) {
        this.code = code;
        this.name = name;
        this.price = price;
    }

    public String getCode() { return code; }
    public String getName() { return name; }
    public double getPrice() { return price; }
}

2. Implementasi Keranjang dengan ArrayList
package com.upb.agripos;

import java.util.ArrayList;

public class ShoppingCart {
    private final ArrayList<Product> items = new ArrayList<>();

    public void addProduct(Product p) { items.add(p); }
    public void removeProduct(Product p) { items.remove(p); }

    public double getTotal() {
        double sum = 0;
        for (Product p : items) {
            sum += p.getPrice();
        }
        return sum;
    }

    public void printCart() {
        System.out.println("Isi Keranjang:");
        for (Product p : items) {
            System.out.println("- " + p.getCode() + " " + p.getName() + " = " + p.getPrice());
        }
        System.out.println("Total: " + getTotal());
    }
}

3. Main Program (WAJIB DIISI)
package com.upb.agripos;

public class MainCart {
    public static void main(String[] args) {
        System.out.println("Hello, I am syukron nur fadillah-240202885 (Week7)");

        Product p1 = new Product("P01", "Beras", 50000);
        Product p2 = new Product("P02", "Pupuk", 30000);

        ShoppingCart cart = new ShoppingCart();
        cart.addProduct(p1);
        cart.addProduct(p2);
        cart.printCart();

        cart.removeProduct(p1);
        cart.printCart();
    }
}

4. Implementasi Alternatif Menggunakan Map (Dengan Quantity)
package com.upb.agripos;

import java.util.HashMap;
import java.util.Map;

public class ShoppingCartMap {
    private final Map<Product, Integer> items = new HashMap<>();

    public void addProduct(Product p) { items.put(p, items.getOrDefault(p, 0) + 1); }

    public void removeProduct(Product p) {
        if (!items.containsKey(p)) return;
        int qty = items.get(p);
        if (qty > 1) items.put(p, qty - 1);
        else items.remove(p);
    }

    public double getTotal() {
        double total = 0;
        for (Map.Entry<Product, Integer> entry : items.entrySet()) {
            total += entry.getKey().getPrice() * entry.getValue();
        }
        return total;
    }

    public void printCart() {
        System.out.println("Isi Keranjang (Map):");
        for (Map.Entry<Product, Integer> e : items.entrySet()) {
            System.out.println("- " + e.getKey().getCode() + " " + e.getKey().getName() + " x" + e.getValue());
        }
        System.out.println("Total: " + getTotal());
    }
}

## Hasil Eksekusi

<img width="1919" height="1079" alt="Screenshot 2026-01-15 094144" src="https://github.com/user-attachments/assets/3b910035-e4f6-4ab0-9375-2a37909c3d56" />

## Analisis

1.Cara Kerja Program:

 - Program menggunakan dua pendekatan: ArrayList untuk menyimpan produk tanpa quantity, dan HashMap untuk menyimpan produk dengan quantity.

 - ArrayList cocok untuk keranjang sederhana yang hanya membutuhkan daftar produk.

 - HashMap lebih efisien untuk tracking quantity karena dapat menyimpan produk sebagai key dan jumlah sebagai value.

2.Perbedaan dengan Minggu Sebelumnya:

  -Minggu sebelumnya fokus pada class dan object dasar, sedangkan minggu ini menggunakan struktur data koleksi untuk mengelola banyak objek.

  -Implementasi menjadi lebih fleksibel dengan kemampuan menangani quantity dan operasi berbasis key.

3.Kendala dan Solusi:

  -Kendala: Implementasi remove pada ArrayList perlu memastikan object yang sama dihapus.

  -Solusi: Menggunakan equals() method atau referensi object yang sama.

  -Kendala: Map memerlukan implementasi equals() dan hashCode() pada Product untuk key yang konsisten.

  -Solusi: Mengimplementasikan kedua method tersebut di class Product.


## Kesimpulan
Dengan menggunakan Collections Framework (ArrayList dan HashMap), implementasi keranjang belanja menjadi lebih efisien dan terstruktur. ArrayList cocok untuk kasus sederhana, sedangkan HashMap lebih tepat untuk sistem yang memerlukan tracking quantity. Pemilihan struktur data yang tepat sangat memengaruhi performa dan kemudahan pengembangan aplikasi Agri-POS.

## Quiz
1.Jelaskan perbedaan mendasar antara List, Map, dan Set.
Jawaban:

List: Menyimpan elemen secara terurut, dapat duplikat, akses via indeks (contoh: ArrayList).

Map: Menyimpan pasangan key-value, key unik, akses cepat via key (contoh: HashMap).

Set: Menyimpan elemen unik, tidak terurut, tidak ada duplikat (contoh: HashSet).

2.Mengapa ArrayList cocok digunakan untuk keranjang belanja sederhana?
Jawaban:
ArrayList cocok karena mudah digunakan, menyimpan elemen secara berurutan, dan mendukung operasi tambah/hapus yang sering dilakukan pada keranjang belanja. Cocok untuk kasus tanpa quantity tracking.

3.Bagaimana struktur Set mencegah duplikasi data?
Jawaban:
Set menggunakan algoritma hashing (pada HashSet) dan method equals() untuk membandingkan objek. Jika objek yang sama (berdasarkan equals()) dimasukkan, Set akan menganggapnya duplikat dan menolak penyimpanan.

4.Kapan sebaiknya menggunakan Map dibandingkan List? Jelaskan dengan contoh.
Jawaban:
Map lebih baik digunakan ketika perlu akses cepat berdasarkan key atau perlu menyimpan data berpasangan (key-value). Contoh: keranjang belanja dengan quantity, di mana Product sebagai key dan jumlah sebagai value, sehingga mudah update quantity tanpa iterasi.
