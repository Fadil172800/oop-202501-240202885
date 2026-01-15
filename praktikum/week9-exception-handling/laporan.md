# Laporan Praktikum Minggu9
Topik: Topik: Exception Handling, Custom Exception, dan Penerapan Design Pattern

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3ikka
---

## Tujuan
Mahasiswa memahami konsep exception handling dalam Java, mampu membuat custom exception untuk validasi bisnis, serta mengintegrasikannya ke dalam aplikasi Agri-POS untuk menangani kesalahan dengan lebih terkontrol dan informatif.
## Dasar Teori
1.Error vs Exception – Error adalah kondisi fatal yang tidak dapat ditangani program (contoh: OutOfMemoryError), sedangkan Exception adalah kondisi tidak normal yang dapat ditangani dengan try-catch.

2.Try-Catch-Finally – Struktur untuk menangkap dan menangani exception, dengan blok finally yang selalu dieksekusi.

3.Custom Exception – Exception buatan sendiri yang mewarisi dari Exception/RuntimeException untuk menangani kasus spesifik aplikasi.

4.Checked vs Unchecked Exception – Checked exception harus dideklarasikan atau ditangkap, sedangkan unchecked tidak.

5.Design Pattern (Singleton) – Pola desain yang memastikan hanya ada satu instance dari sebuah class dalam aplikasi.

## Langkah Praktikum
1.Setup Project – Membuat struktur direktori week9-exception-handling sesuai template.

2.Membuat Custom Exception – Membuat 3 custom exception: InvalidQuantityException, ProductNotFoundException, dan InsufficientStockException.

3.Memperbarui Class Product – Menambahkan atribut stock dan method reduceStock() untuk manajemen stok.

4.Implementasi ShoppingCart dengan Exception – Memodifikasi ShoppingCart untuk melempar exception pada kondisi invalid.

5.Main Program Testing – Membuat MainExceptionDemo untuk menguji semua skenario exception.

6.Implementasi Singleton (Opsional) – Membuat ProductService dengan pola Singleton.

7.Commit & Push – Melakukan commit dengan format message: week9-exception: [fitur] [deskripsi singkat].

## Kode Program
1. Membuat Custom Exception
package com.upb.agripos;

public class InvalidQuantityException extends Exception {
    public InvalidQuantityException(String msg) { super(msg); }
}
package com.upb.agripos;

public class ProductNotFoundException extends Exception {
    public ProductNotFoundException(String msg) { super(msg); }
}
package com.upb.agripos;

public class InsufficientStockException extends Exception {
    public InsufficientStockException(String msg) { super(msg); }
}

2. Model Product dengan Stok
package com.upb.agripos;

public class Product {
    private final String code;
    private final String name;
    private final double price;
    private int stock;

    public Product(String code, String name, double price, int stock) {
        this.code = code;
        this.name = name;
        this.price = price;
        this.stock = stock;
    }

    public String getCode() { return code; }
    public String getName() { return name; }
    public double getPrice() { return price; }
    public int getStock() { return stock; }
    public void reduceStock(int qty) { this.stock -= qty; }
}

3.Implementasi ShoppingCart dengan Exception Handling
package com.upb.agripos;

import java.util.HashMap;
import java.util.Map;

public class ShoppingCart {
    private final Map<Product, Integer> items = new HashMap<>();

    public void addProduct(Product p, int qty) throws InvalidQuantityException {
        if (qty <= 0) {
            throw new InvalidQuantityException("Quantity harus lebih dari 0.");
        }
        items.put(p, items.getOrDefault(p, 0) + qty);
    }

    public void removeProduct(Product p) throws ProductNotFoundException {
        if (!items.containsKey(p)) {
            throw new ProductNotFoundException("Produk tidak ada dalam keranjang.");
        }
        items.remove(p);
    }

    public void checkout() throws InsufficientStockException {
        for (Map.Entry<Product, Integer> entry : items.entrySet()) {
            Product product = entry.getKey();
            int qty = entry.getValue();
            if (product.getStock() < qty) {
                throw new InsufficientStockException(
                    "Stok tidak cukup untuk: " + product.getName()
                );
            }
        }
        // contoh pengurangan stok bila semua cukup
        for (Map.Entry<Product, Integer> entry : items.entrySet()) {
            entry.getKey().reduceStock(entry.getValue());
        }
    }
}

4. Main Program untuk Menguji Exception Handling
package com.upb.agripos;

public class MainExceptionDemo {
    public static void main(String[] args) {
        System.out.println("Hello, I am [Nama]-[NIM] (Week9)");

        ShoppingCart cart = new ShoppingCart();
        Product p1 = new Product("P01", "Pupuk Organik", 25000, 3);

        try {
            cart.addProduct(p1, -1);
        } catch (InvalidQuantityException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.removeProduct(p1);
        } catch (ProductNotFoundException e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }

        try {
            cart.addProduct(p1, 5);
            cart.checkout();
        } catch (Exception e) {
            System.out.println("Kesalahan: " + e.getMessage());
        }
    }
}


## Hasil Eksekusi

<img width="1919" height="1079" alt="Screenshot 2026-01-15 094336" src="https://github.com/user-attachments/assets/2f5ee51c-08a8-41e4-a6fb-59563d69d2fb" />

## Analisis
1.Cara Kerja Program:

  -Program menggunakan try-catch untuk menangkap exception yang dilempar oleh ShoppingCart.

  -Setiap skenario bisnis (quantity invalid, produk tidak ditemukan, stok tidak cukup) memiliki exception khusus.

  -Blok finally dieksekusi terlepas dari ada atau tidaknya exception.

2.Perbedaan dengan Minggu Sebelumnya:

  -Minggu 7 fokus pada struktur data untuk keranjang belanja.

  -Minggu 9 menambahkan layer validasi dan error handling yang lebih robust.

  -Program sekarang dapat memberikan feedback yang lebih spesifik kepada pengguna tentang kesalahan yang terjadi.

3.Kendala dan Solusi:

  -Kendala: Memastikan semua exception ditangkap dengan tepat di main program.

  -Solusi: Menggunakan multiple catch blocks atau catch umum dengan pengecekan instance.

  -Kendala: Desain class Product yang perlu disesuaikan untuk mendukung manajemen stok.

  -Solusi: Menambahkan atribut stock dan method reduceStock().

4.Penerapan Singleton:

  -ProductService diimplementasikan sebagai Singleton untuk memastikan hanya ada satu instance yang mengelola data produk.

  -Berguna untuk kasus nyata seperti koneksi database atau service layer.

## Kesimpulan
Exception handling merupakan komponen kritis dalam pengembangan aplikasi yang robust. Dengan custom exception, kita dapat memberikan pesan error yang lebih spesifik dan sesuai dengan domain bisnis Agri-POS. Penerapan try-catch-finally dan design pattern seperti Singleton meningkatkan kualitas kode dan memudahkan maintenance. Program sekarang lebih siap untuk menangani skenario error dalam produksi.
## Quiz
1.Jelaskan perbedaan error dan exception.
Jawaban:
Error adalah kondisi fatal yang tidak dapat dipulihkan oleh program, biasanya terkait dengan lingkungan runtime (contoh: OutOfMemoryError, StackOverflowError). Exception adalah kondisi abnormal yang dapat ditangani oleh program menggunakan try-catch block, seperti InvalidQuantityException yang kita buat.

2.Apa fungsi finally dalam blok try–catch–finally?
Jawaban:
Blok finally selalu dieksekusi terlepas dari apakah exception terjadi atau tidak. Biasanya digunakan untuk cleanup resources seperti menutup file, koneksi database, atau stream untuk mencegah resource leak.

3.Mengapa custom exception diperlukan?
Jawaban:
Custom exception diperlukan untuk:
Menangani kasus spesifik domain bisnis (misal: stok tidak cukup)
Memberikan pesan error yang lebih informatif dan relevan
Membedakan jenis kesalahan untuk penanganan yang lebih spesifik
Meningkatkan readability dan maintainability kode

4.Berikan contoh kasus bisnis dalam POS yang membutuhkan custom exception.
Jawaban:
PaymentFailedException: Ketika pembayaran gagal karena saldo tidak cukup atau jaringan bermasalah
ExpiredProductException: Ketika mencoba menjual produk yang sudah kadaluarsa
DiscountExceedLimitException: Ketika diskon melebihi batas yang diizinkan
CustomerNotEligibleException: Ketika pelanggan tidak memenuhi syarat untuk promo tertentu
