# Laporan Praktikum Minggu 6
Topik: Desain Arsitektur Sistem dengan UML dan Prinsip SOLID

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : 3ikka

---

## Tujuan
Mengidentifikasi kebutuhan sistem ke dalam diagram UML.

Menggambar UML Class Diagram dengan relasi antar class yang tepat.

Menjelaskan prinsip desain OOP (SOLID).

Menerapkan minimal dua prinsip SOLID dalam desain kode program.

## Dasar Teori
UML (Unified Modeling Language) adalah bahasa standar untuk memodelkan sistem perangkat lunak secara visual, mencakup diagram struktur dan perilaku.

Use Case Diagram menggambarkan interaksi antara aktor dan sistem dari perspektif fungsional.

Activity Diagram memodelkan alur kerja atau proses bisnis dalam sistem.

Sequence Diagram menunjukkan interaksi antar objek dalam urutan waktu.

Class Diagram menggambarkan struktur kelas, atribut, metode, dan relasi antar kelas.

Prinsip SOLID adalah lima prinsip desain berorientasi objek yang meningkatkan fleksibilitas, pemeliharaan, dan pengujian kode.

## Langkah Praktikum
Analisis Kebutuhan: Mempelajari Functional Requirements (FR) dan Non-Functional Requirements (NFR) sistem Agri-POS.

Iterasi 1 - Use Case Diagram:

Mengidentifikasi aktor (Kasir, Admin, Sistem Pembayaran)

Mendefinisikan use case utama

Menggambar diagram dengan tool draw.io

Commit message: week6-uml-solid: iterasi-1 use case diagram

Iterasi 2 - Activity Diagram:

Memodelkan alur proses Checkout dengan swimlane

Menambahkan skenario normal dan gagal

Commit message: week6-uml-solid: iterasi-2 activity diagram

Iterasi 3 - Sequence Diagram:

Mendesain interaksi objek dalam proses pembayaran

Menambahkan alternatif (alt) untuk kasus gagal

Commit message: week6-uml-solid: iterasi-3 sequence diagram

Iterasi 4 - Class Diagram:

Mendefinisikan kelas, atribut, metode, dan relasi

Menerapkan prinsip SOLID dalam desain

Commit message: week6-uml-solid: iterasi-4 class diagram

Pembuatan Laporan: Mendokumentasikan desain dan penerapan SOLID.

## Kode Program
sudah ada di lampirann file src/main/java

## Hasil Eksekusi
sudah ada di lampiran screenshoot

## Analisis
1. Keterkaitan Antar Diagram
Use Case Diagram memberikan gambaran makro fungsionalitas sistem

Activity Diagram merinci alur proses Checkout dari awal hingga akhir

Sequence Diagram menunjukkan detail interaksi objek dalam proses pembayaran

Class Diagram mendefinisikan struktur statis sistem yang mengimplementasikan fungsionalitas

2. Penerapan Prinsip SOLID
Single Responsibility Principle (SRP): Setiap kelas memiliki satu tanggung jawab. Contoh: ProductService hanya menangani logika produk, PaymentService hanya menangani pembayaran.

Open/Closed Principle (OCP): Sistem terbuka untuk ekstensi, tertutup untuk modifikasi. Penambahan metode pembayaran baru hanya perlu menambah kelas baru tanpa mengubah kode yang ada.

Dependency Inversion Principle (DIP): Modul tingkat tinggi tidak bergantung pada modul tingkat rendah, keduanya bergantung pada abstraksi. PaymentService bergantung pada interface PaymentMethod, bukan implementasi konkret.

3. Konsistensi Desain
Penamaan konsisten di seluruh diagram

Relasi antar diagram terjaga (use case Checkout → activity Checkout → sequence pembayaran → class terkait)

Error handling dimodelkan dengan jelas di activity dan sequence diagram

4. Kendala dan Solusi
Kendala: Memastikan konsistensi antar diagram yang berbeda

Solusi: Membuat tabel traceability untuk memetakan elemen di semua diagram

Kendala: Memvisualisasikan prinsip SOLID secara eksplisit

Solusi: Menambahkan annotation dan komentar di class diagram

## Kesimpulan
Desain arsitektur Agri-POS menggunakan UML telah berhasil dibuat dengan empat diagram yang saling melengkapi.

Prinsip SOLID telah diterapkan dengan baik, khususnya SRP, OCP, dan DIP yang meningkatkan maintainability dan extensibility sistem.

Desain yang modular memungkinkan penambahan fitur baru seperti metode pembayaran tambahan tanpa mengubah kode inti.

Dokumentasi yang komprehensif memudahkan pengembang lain memahami sistem dan melakukan pengembangan lebih lanjut.


## Quiz
1. Jelaskan perbedaan aggregation dan composition serta berikan contoh penerapannya pada desain Anda.
Jawaban:

Aggregation adalah hubungan "has-a" dimana objek bagian dapat hidup mandiri tanpa objek keseluruhan. Contoh: CheckoutService memiliki PaymentService, tetapi PaymentService dapat digunakan secara terpisah.

Composition adalah hubungan "part-of" yang lebih kuat dimana objek bagian tidak dapat hidup tanpa objek keseluruhan. Contoh: Receipt adalah bagian dari transaksi dan akan dihancurkan bersama transaksi.

Dalam desain Agri-POS:

Aggregation: CheckoutService → PaymentService (diamond hollow)

Composition: Transaction → LineItem (diamond filled)

2. Bagaimana prinsip Open/Closed dapat memastikan sistem mudah dikembangkan?
Jawaban:
Prinsip Open/Closed (OCP) menyatakan bahwa entitas perangkat lunak harus terbuka untuk ekstensi tetapi tertutup untuk modifikasi. Dalam desain Agri-POS:

Terbuka untuk ekstensi: Untuk menambah metode pembayaran baru (misal: QRIS), cukup buat kelas baru yang mengimplementasikan interface PaymentMethod tanpa mengubah PaymentService.

Tertutup untuk modifikasi: Kelas inti seperti PaymentService tidak perlu dimodifikasi saat menambah fitur baru.

Mekanisme: Menggunakan interface PaymentMethod dan PaymentFactory memungkinkan penambahan implementasi baru tanpa mengubah kode yang ada.

3. Mengapa Dependency Inversion Principle (DIP) meningkatkan testability? Berikan contoh penerapannya.
Jawaban:
Dependency Inversion Principle (DIP) meningkatkan testability karena:

Memisahkan dependensi: Modul tidak bergantung pada implementasi konkret melainkan pada abstraksi.

Memungkinkan mocking: Interface dapat dengan mudah di-mock dalam pengujian unit.

Mengurangi coupling: Ketergantungan yang longgar memudahkan pengujian isolasi.

Contoh dalam Agri-POS:

java
// Tanpa DIP (sulit di-test)
public class PaymentService {
    private CashPayment cashPayment; // Bergantung pada implementasi konkret
    
    public Receipt payWithCash(Money amount) {
        return cashPayment.pay(amount); // Sulit di-mock
    }
}

// Dengan DIP (mudah di-test)
public class PaymentService {
    private PaymentMethod paymentMethod; // Bergantung pada abstraksi
    
    public PaymentService(PaymentMethod paymentMethod) {
        this.paymentMethod = paymentMethod; // Dependency Injection
    }
    
    public Receipt pay(Money amount) {
        return paymentMethod.pay(amount); // Mudah di-mock
    }
}
Dalam pengujian, kita dapat membuat mock PaymentMethod untuk menguji PaymentService tanpa memerlukan implementasi nyata, sehingga pengujian menjadi lebih cepat, terisolasi, dan dapat diprediksi.

Lampiran: Tabel Traceability

FR	Use Case	Activity/Sequence	Class/Interface
Manajemen Produk	UC-Kelola Produk	-	ProductService, ProductRepository, JdbcProductRepository
Transaksi Penjualan	UC-Checkout	Activity Checkout	CheckoutService, Transaction, LineItem
Metode Pembayaran	UC-Pembayaran	Sequence Pembayaran	PaymentMethod, CashPayment, EWalletPayment, PaymentService, PaymentFactory
Cetak Struk	UC-Cetak Struk	Activity Cetak Struk	Receipt, PrinterService
Laporan	UC-Lihat Laporan	-	ReportService, SalesReport
Login & Hak Akses	UC-Login	-	AuthService, User, Role
