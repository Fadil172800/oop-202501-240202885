# Laporan Praktikum Minggu 5
Topik: Abstraction (Abstract Class & Interface)

## Identitas
- Nama  : Syukron Nur Fadillah
- NIM   : 240202885
- Kelas : #IKKA


## Tujuan
Mahasiswa memahami perbedaan abstract class dan interface.

Mahasiswa mampu membuat abstract class dengan method abstrak dan konkrit.

Mahasiswa mampu membuat dan mengimplementasikan interface.

Mahasiswa mampu menerapkan multiple inheritance melalui interface.

Mahasiswa mampu membuat program sederhana yang menggunakan konsep abstraksi.

## Dasar Teori
Abstract class adalah class yang tidak dapat diinstansiasi dan dapat memiliki method abstrak serta method konkrit.

Interface adalah kumpulan kontrak method tanpa implementasi, digunakan untuk mendefinisikan kemampuan suatu objek.

Sejak Java 8, interface dapat memiliki default method.

Abstraksi menyembunyikan detail implementasi dan hanya menampilkan fitur penting.

Java mendukung multiple inheritance hanya melalui interface untuk menghindari conflict state pada pewarisan ganda.

## Langkah Praktikum
Membuat abstract class Pembayaran dengan field invoiceNo, total, serta method abstrak biaya() dan prosesPembayaran().

Membuat subclass konkret: Cash dan EWallet.

Membuat dua interface: Validatable dan Receiptable.

Mengimplementasikan interface tersebut pada class yang relevan.

Membuat MainAbstraction.java untuk menjalankan program secara polimorfik.

Menjalankan program dan mengambil screenshot output.

Melakukan commit dengan pesan week5-abstraction-interface.
## Kode Program
1.Pembayaran.java
 package com.upb.agripos.model.pembayaran;

public abstract class Pembayaran {
    protected String invoiceNo;
    protected double total;

    public Pembayaran(String invoiceNo, double total) {
        this.invoiceNo = invoiceNo;
        this.total = total;
    }

    public abstract double biaya();               // fee/biaya tambahan
    public abstract boolean prosesPembayaran();   // proses spesifik tiap metode

    public double totalBayar() {
        return total + biaya();
    }

    public String getInvoiceNo() { return invoiceNo; }
    public double getTotal() { return total; }
}

2.Interface: Validatable & Receiptable
 package com.upb.agripos.model.kontrak;

public interface Validatable {
    boolean validasi(); // misal validasi OTP/ PIN
}

package com.upb.agripos.model.kontrak;

public interface Receiptable {
    String cetakStruk();
}

3.Cash.java
 package com.upb.agripos.model.pembayaran;

import com.upb.agripos.model.kontrak.Receiptable;

public class Cash extends Pembayaran implements Receiptable {
    private double tunai;

    public Cash(String invoiceNo, double total, double tunai) {
        super(invoiceNo, total);
        this.tunai = tunai;
    }

    @Override
    public double biaya() {
        return 0.0;
    }

    @Override
    public boolean prosesPembayaran() {
        return tunai >= totalBayar(); // sederhana: cukup uang tunai
    }

    @Override
    public String cetakStruk() {
        return String.format("INVOICE %s | TOTAL: %.2f | BAYAR CASH: %.2f | KEMBALI: %.2f",
                invoiceNo, totalBayar(), tunai, Math.max(0, tunai - totalBayar()));
    }
}

4.EWallet.java
package com.upb.agripos.model.pembayaran;

import com.upb.agripos.model.kontrak.Validatable;
import com.upb.agripos.model.kontrak.Receiptable;

public class EWallet extends Pembayaran implements Validatable, Receiptable {
    private String akun;
    private String otp; // sederhana untuk simulasi

    public EWallet(String invoiceNo, double total, String akun, String otp) {
        super(invoiceNo, total);
        this.akun = akun;
        this.otp = otp;
    }

    @Override
    public double biaya() {
        return total * 0.015; // 1.5% fee
    }

    @Override
    public boolean validasi() {
        return otp != null && otp.length() == 6; // contoh validasi sederhana
    }

    @Override
    public boolean prosesPembayaran() {
        return validasi(); // jika validasi lolos, anggap berhasil
    }

    @Override
    public String cetakStruk() {
        return String.format("INVOICE %s | TOTAL+FEE: %.2f | E-WALLET: %s | STATUS: %s",
                invoiceNo, totalBayar(), akun, prosesPembayaran() ? "BERHASIL" : "GAGAL");
    }
}

5.MainAbstraction.java
  package com.upb.agripos;

import com.upb.agripos.model.pembayaran.*;
import com.upb.agripos.model.kontrak.*;
import com.upb.agripos.util.CreditBy;

public class MainAbstraction {
    public static void main(String[] args) {
        Pembayaran cash = new Cash("INV-001", 100000, 120000);
        Pembayaran ew = new EWallet("INV-002", 150000, "user@ewallet", "123456");

        System.out.println(((Receiptable) cash).cetakStruk());
        System.out.println(((Receiptable) ew).cetakStruk());

    CreditBy.print("[NIM]", "[Nama Mahasiswa]");
    }
}

## Hasil Eksekusi
<img width="1919" height="1079" alt="Screenshot 2025-12-07 211854" src="https://github.com/user-attachments/assets/14a7ca13-1168-41b1-b5ab-f4b5422db8f4" />

## Analisis
Program menggunakan abstract class Pembayaran sebagai dasar semua jenis pembayaran karena memiliki state bersama (invoiceNo, total) serta method konkrit totalBayar().

Interface Validatable digunakan untuk mekanisme validasi OTP, sedangkan Receiptable mendefinisikan kemampuan mencetak struk.

Cash dan EWallet menunjukkan implementasi polimorfik dari abstract class.

EWallet menggunakan multiple inheritance melalui dua interface, yang aman karena interface tidak menyimpan state.

Kendala yang muncul biasanya pada struktur package dan import, namun dapat diperbaiki dengan memastikan struktur folder sesuai dengan package.

## Kesimpulan
Dengan menggunakan abstract class dan interface, desain program menjadi lebih fleksibel, modular, dan mudah dikembangkan. Abstract class digunakan untuk perilaku dasar yang memiliki state, sedangkan interface digunakan untuk kemampuan tambahan yang dapat diterapkan ke banyak class.
## Quiz

1. Jelaskan perbedaan konsep dan penggunaan abstract class dan interface.

Jawaban:
Abstract class dan interface adalah dua konsep penting dalam OOP untuk mendefinisikan kerangka perilaku suatu class, namun keduanya memiliki tujuan dan sifat yang berbeda.

Perbedaan konsep:

Abstract Class

Merupakan class yang tidak dapat diinstansiasi langsung.

Dapat memiliki method abstract (tanpa tubuh) dan method konkret (memiliki implementasi).

Dapat memiliki atribut, constructor, serta state yang bisa diwariskan ke subclass.

Mendefinisikan “is a” relationship (hubungan pewarisan murni).

Interface

Berisi kumpulan kontrak method yang harus diimplementasikan oleh class.

Hingga Java 7 hanya berisi abstract method, tetapi sejak Java 8 bisa memiliki default method dan static method.

Tidak memiliki state, kecuali konstanta public static final.

Mendefinisikan “can do” relationship, yaitu kemampuan atau perilaku yang harus dimiliki class.

Perbedaan penggunaan dalam aplikasi:

Abstract class digunakan ketika beberapa class memiliki dasar perilaku dan properti yang sama, dan ingin berbagi kode implementasi.

Interface digunakan ketika beberapa class yang tidak memiliki hubungan pewarisan langsung tetap harus berbagi perilaku yang sama (contoh: semua class bisa “dapat dicetak”, “dapat disimpan”, dll).

Intinya:

Abstract class = pondasi struktur & logika dasar.
Interface = kontrak perilaku yang wajib dimiliki class, tanpa memikirkan struktur internal.

2. Mengapa multiple inheritance lebih aman dilakukan dengan interface pada Java?

Jawaban:
Java tidak mendukung multiple inheritance pada class karena dapat menyebabkan konflik, terutama Diamond Problem, yaitu ketika dua superclass memiliki method dengan nama sama dan subclass bingung mewarisi yang mana.

Dengan interface, multiple inheritance dinilai lebih aman karena:

Interface tidak menyimpan state → sehingga tidak terjadi konflik pewarisan variabel.

Interface hanya mendefinisikan kontrak → tidak ada implementasi yang tumpang tindih seperti pada multiple class inheritance.

Class bisa mengimplementasikan banyak interface tanpa risiko konflik pewarisan logika.

Jika ada default method yang konflik, Java mewajibkan programmer meng-override method tersebut sehingga tetap aman dan jelas.

Karena itu, Java memilih pendekatan multiple inheritance melalui interface, bukan melalui class, untuk menjaga keamanan, konsistensi, dan mencegah error pewarisan kompleks.

3. Pada contoh Agri-POS, bagian mana yang paling tepat menjadi abstract class dan mana yang menjadi interface? Jelaskan alasannya.

Jawaban:

Yang paling tepat dijadikan Abstract Class: Produk

Alasan:

Semua produk pertanian memiliki struktur data dasar yang sama (kode, nama, harga, stok).

Ada perilaku dasar yang dapat dibagikan seperti tambahStok(), kurangiStok(), atau versi default getInfo().

Produk tidak boleh diinstansiasi langsung karena “Produk” adalah konsep umum, sedangkan objek sesungguhnya adalah Benih, Pupuk, AlatPertanian, dll.

Karena itu, Produk ideal dijadikan abstract class agar bisa menyimpan:

atribut dasar,

constructor,

method yang sudah ada implementasinya,

method abstract yang wajib dioverride oleh subclass.

Yang paling tepat dijadikan Interface: DapatDikirim, DapatDiskon, atau CetakStruk

Alasan:
Interface cocok untuk mendefinisikan kemampuan tambahan yang tidak harus dimiliki semua produk.

Contohnya:

Interface DapatDikirim

Berisi kontrak method seperti hitungBiayaPengiriman() atau getBerat().

Tidak semua produk harus bisa dikirim (misalnya layanan jasa).

Interface DapatDiskon

Berisi hitungDiskon(int persen)

Perilaku opsional yang tidak wajib dimiliki semua produk.

Interface CetakStruk

Berisi cetak(), digunakan untuk mencetak detail transaksi.

Interface dipilih karena:

Tidak memaksakan atribut atau state.

Hanya memberi kemampuan tambahan.

Bisa digunakan oleh banyak class yang tidak terkait langsung.
