# Catatan Lengkap Fitur — Telegram Bot Order (TELEBOT-ORDER)

> Bot Telegram otomatis untuk penjualan produk digital — pemesanan, pembayaran, dan pengiriman tanpa perlu admin standby.

---

## 1. Perintah Bot (Commands)

| Command | Fungsi |
|---------|--------|
| `/start` | Mulai bot, tampil menu utama |
| `/katalog` | Lihat semua produk tersedia |
| `/pesan` | Mulai proses pemesanan |
| `/status` | Cek status pesanan |
| `/saldo` | Cek saldo akun |
| `/riwayat` | Lihat riwayat transaksi |
| `/bantuan` | Tampilkan panduan penggunaan |

---

## 2. Katalog Produk

- **Tampilkan produk** dengan nama, deskripsi, dan harga
- **Foto produk** langsung ditampilkan di chat
- **Kategori produk** — kelompokkan per jenis (streaming, tools, dll)
- **Stok real-time** — produk habis tidak bisa dipesan
- **Harga otomatis** tampil sesuai yang diatur admin
- **Inline keyboard** — pilih produk cukup klik tombol

---

## 3. Proses Pemesanan

### Alur Pemesanan
```
Pelanggan → /pesan atau klik tombol
    ↓
Bot tampilkan kategori produk
    ↓
Pelanggan pilih produk
    ↓
Bot tampilkan detail + harga
    ↓
Pelanggan konfirmasi jumlah
    ↓
Bot tanya kode voucher (opsional)
    ↓
Pilih metode pembayaran
    ↓
Bot kirim instruksi/link pembayaran
    ↓
Pembayaran dikonfirmasi
    ↓
Produk digital dikirim otomatis ke chat
```

### Fitur Pemesanan
- **Multi-item** — beli beberapa produk sekaligus
- **Konfirmasi pesanan** sebelum pembayaran
- **Order ID unik** — setiap pesanan punya kode unik
- **Batas waktu pembayaran** — pesanan expired otomatis jika tidak dibayar
- **Simpan nama** — tidak perlu isi nama setiap pesan

---

## 4. Metode Pembayaran

### QRIS Otomatis
- QR Code dinamis dikirim langsung di chat
- Nominal otomatis sesuai harga pesanan
- Verifikasi pembayaran otomatis

### Transfer Bank Manual
- Instruksi rekening dikirim ke pelanggan
- Admin konfirmasi pembayaran via command
- Notifikasi ke pelanggan setelah dikonfirmasi

### Saldo Akun
- Pelanggan bisa top up saldo
- Saldo digunakan saat checkout
- Riwayat penggunaan saldo tercatat

### Voucher & Diskon
- Kode voucher persentase atau nominal
- Atur batas penggunaan dan kadaluarsa
- Validasi otomatis saat checkout

---

## 5. Pengiriman Produk Digital Otomatis

- **Key/akun tersimpan** per produk di database
- Setelah pembayaran terkonfirmasi → **produk langsung dikirim** ke chat
- **Stok berkurang otomatis** setelah produk terkirim
- **Alert stok habis** ke admin saat stok menipis
- Produk yang dikirim dicatat agar tidak dikirim ulang
- Support format: teks, file, gambar, link

---

## 6. Manajemen Pelanggan

- **Data pelanggan** tersimpan otomatis (nama, username, ID Telegram)
- **Riwayat pesanan** per pelanggan
- **Sistem saldo** terintegrasi
- **Blacklist** pelanggan bermasalah
- Pelanggan bisa cek sendiri riwayat dan status pesanan

---

## 7. Panel Admin (via Telegram)

### Command Admin
| Command | Fungsi |
|---------|--------|
| `/addproduk` | Tambah produk baru |
| `/editproduk` | Edit produk existing |
| `/hapusproduk` | Hapus produk |
| `/addstok` | Tambah stok produk |
| `/lihatstok` | Lihat semua stok |
| `/konfirmasi [ID]` | Konfirmasi pembayaran manual |
| `/tolak [ID]` | Tolak pesanan |
| `/laporan` | Lihat laporan penjualan |
| `/broadcast` | Kirim pesan ke semua pelanggan |

### Notifikasi Admin
- Notifikasi real-time setiap ada pesanan masuk
- Notifikasi pembayaran manual yang perlu dikonfirmasi
- Alert stok menipis
- Laporan harian otomatis ke chat admin

---

## 8. Laporan & Statistik

- **Total penjualan** harian, mingguan, bulanan
- **Produk terlaris** — daftar produk paling banyak terjual
- **Jumlah pelanggan** aktif
- **Riwayat transaksi** lengkap dengan filter
- **Export laporan** ke format teks / Excel (opsional)

---

## 9. Fitur Tambahan

### Broadcast / Siaran
- Admin kirim pesan promosi ke semua pelanggan
- Kirim ke pelanggan yang pernah beli produk tertentu
- Template pesan yang bisa dikustomisasi

### Referral System (opsional)
- Pelanggan dapat kode referral unik
- Bonus saldo saat referral berhasil order
- Laporan referral per pelanggan

### Multi Admin
- Bisa set beberapa akun sebagai admin
- Level akses berbeda (super admin & admin biasa)

---

## 10. Keamanan

- **Rate limiting** — cegah spam command
- **Verifikasi pesanan** sebelum produk dikirim
- **Enkripsi data** pelanggan di database
- **Anti-duplicate** — cegah produk dikirim dua kali
- **Log transaksi** lengkap untuk audit

---

## 11. UI/UX Bot

- **Inline keyboard** — semua interaksi via tombol, tidak perlu ketik
- **Pesan terstruktur** — info jelas dan mudah dibaca
- **Emoji** untuk tampilan lebih menarik
- **Bahasa Indonesia** di seluruh chat bot
- **Respon cepat** — bot selalu aktif 24 jam

---

## Ringkasan Fitur per Role

| Fitur | Pelanggan | Admin |
|-------|:---------:|:-----:|
| Lihat katalog produk | ✅ | ✅ |
| Pesan & checkout | ✅ | ✅ |
| Cek status pesanan | ✅ | ✅ |
| Cek saldo & riwayat | ✅ | ✅ |
| Konfirmasi pembayaran | ❌ | ✅ |
| Tambah / edit produk | ❌ | ✅ |
| Tambah stok | ❌ | ✅ |
| Broadcast ke pelanggan | ❌ | ✅ |
| Lihat laporan penjualan | ❌ | ✅ |
| Blacklist pelanggan | ❌ | ✅ |

---

**Last Updated:** May 2026
