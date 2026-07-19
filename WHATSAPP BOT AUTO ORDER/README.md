# WhatsApp Bot Penjualan Otomatis

>Bot WhatsApp siap pakai untuk jualan produk digital - otomatis, 24 jam, tanpa henti.

---

## Fitur Unggulan

### Katalog & Pemesanan Otomatis
-Pelanggan bisa lihat daftar produk langsung di WhatsApp
-Pesan cukup ketik `pesan 1`, `pesan 2`, dst.
-Bot langsung memandu proses pemesanan step by step

### Bundling Produk
-Buat paket bundel dari beberapa produk dengan harga spesial
-Tampil otomatis di katalog bot sebagai "Paket Bundling"
-Pelanggan pesan bundel cukup ketik `bundle 1`

### Voucher & Kode Diskon
-Buat kode voucher diskon (persentase atau nominal)
-Atur batas penggunaan, minimal order, dan tanggal kadaluarsa
-Bot validasi voucher otomatis saat checkout

### Multi Metode Pembayaran
-**QRIS** - QR code otomatis dari Pak Kasir, langsung di chat
-**Transfer Bank / E-Wallet** - instruksi dikirim ke pelanggan
-**Saldo** - pelanggan bisa pakai saldo akun mereka

### Stok Digital Otomatis
-Simpan key/akun digital per produk
-Bot otomatis kirim key ke pelanggan setelah bayar
-Stok berkurang otomatis, tidak perlu manual

### Manajemen Pesanan
-Lihat semua pesanan masuk di panel admin
-Status real-time: pending → processing → completed
-Pesanan kadaluarsa dibatalkan & stok dikembalikan otomatis

### Notifikasi Real-time
-Notifikasi browser langsung muncul saat ada pesanan baru
-Tidak perlu refresh halaman - pakai teknologi SSE

### Dashboard & Laporan
-Statistik penjualan harian, mingguan, bulanan
-Laporan lengkap bisa difilter per periode
-Grafik omzet & jumlah transaksi

### Manajemen Pelanggan
-Data pelanggan tersimpan otomatis
-Riwayat pesanan per pelanggan
-Sistem saldo pelanggan terintegrasi

### Admin Panel Web Lengkap
-Akses via browser, mobile-friendly
-CRUD Produk, Kategori, Bundle, Voucher
-Pengaturan bot, rekening bank, payment gateway
-Ganti username & password admin

---

## Screenshot & Demo

![WABOT Features Overview](./images/wabot-features.png)

Lihat visualisasi lengkap dari semua fitur yang tersedia di WABOT.

---

## Alur Bot WhatsApp

```
Pelanggan ketik: halo / menu
 ↓
Bot tampilkan katalog produk & bundle
 ↓
Pelanggan ketik: pesan 1 / bundle 1
 ↓
Bot tanya jumlah & nama (disimpan untuk pesanan berikutnya)
 ↓
Bot tanya kode voucher (bisa dilewati)
 ↓
Pilih metode bayar: QRIS / Transfer / Saldo
 ↓
Link/instruksi pembayaran dikirim otomatis
 ↓
Setelah terkonfirmasi → key/produk digital dikirim otomatis
```

---

## Teknologi

-**WhatsApp**: whatsapp-web.js (tanpa API berbayar)
-**Backend**: Node.js + Express
-**Database**: PostgreSQL
-**Payment**: Pak Kasir (QRIS)
-**Panel Admin**: React + Tailwind CSS

---

## Yang Didapat

|Item | Detail |
|------|--------|
|Source code lengkap | |
|Admin panel web | |
|Setup & instalasi | |
|Dokumentasi VPS | |
|Update fitur | Sesuai paket |

---

