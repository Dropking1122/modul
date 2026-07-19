# Absensi QR Sekolah

Sistem absensi siswa berbasis QR Code untuk jenjang SD, SMP, SMA, dan SMK.

---

## Fitur

### Absensi & Kehadiran
-Scan QR Code via kamera (HP/laptop) untuk mencatat kehadiran masuk dan pulang
-Status otomatis: **Hadir**, **Terlambat**, **Alfa** (tidak hadir), **Bolos** (pulang tanpa izin)
-Absensi manual oleh guru/admin: Izin, Sakit, Dispensasi, Hadir, Alfa
-Live Monitor - pantau kehadiran real-time seluruh siswa di satu layar
-Tandai alfa dan bolos otomatis via scheduler setelah jam toleransi habis
-Notifikasi audio (sukses/gagal) saat scan QR, dapat dikustomisasi atau dinonaktifkan
-Riwayat scan hari ini tampil langsung di sidebar halaman scan

### Statistik & Laporan
-Rekap kehadiran harian dan bulanan per siswa/kelas
-Statistik kehadiran siswa: jumlah hadir, terlambat, alfa, bolos, dan persentase kehadiran
-Filter berdasarkan tanggal, kelas, dan status kehadiran
-Export rekap ke **Excel** dan **PDF**
-Export data siswa ke Excel

### Manajemen Data Siswa
-Kelola data siswa lengkap: nama, NIS/NISN, kelas, jenis kelamin, tempat/tanggal lahir, alamat
-Data orang tua: nama ayah, nama ibu, nomor HP wali (untuk notifikasi WhatsApp)
-Upload dan kelola foto profil siswa
-Import siswa massal via **Excel/CSV** dengan template yang tersedia
-Cetak kartu QR per siswa atau massal per kelas (8 kartu/halaman, ukuran KTP)
-Reset token QR siswa kapan saja

### Jadwal & Mata Pelajaran
-Kelola jadwal harian: hari, jam masuk, batas toleransi, jam keluar
-Jadwal berlaku untuk kelas tertentu atau semua kelas
-Jadwal mata pelajaran harian - tampil di dashboard siswa sebagai "sedang berlangsung"
-Kelola daftar mata pelajaran (master data)

### Izin & Ketidakhadiran
-Siswa mengajukan izin atau sakit langsung dari dashboard, lengkap dengan unggah bukti (foto/dokumen)
-Guru dan admin menyetujui atau menolak pengajuan izin
-Kelola jenis izin yang tersedia (izin biasa, sakit, dispensasi, dll.)
-Pengaturan notifikasi WA ke siswa, wali kelas, atau guru mata pelajaran saat izin diproses
-Status absensi otomatis berubah menjadi Izin/Sakit setelah pengajuan disetujui

### Pelanggaran & Pembinaan
-Catat laporan pelanggaran siswa dengan kategori, deskripsi, dan foto bukti (multi-file)
-Tambah catatan pembinaan bertahap pada setiap laporan pelanggaran
-Tandai pelanggaran sebagai selesai setelah pembinaan tuntas
-Kelola kategori pelanggaran sesuai kebijakan sekolah
-Siswa dapat melihat riwayat pelanggaran milik sendiri
-Pengaturan visibilitas bukti foto dan batas ukuran unggahan
-Notifikasi WhatsApp otomatis ke orang tua dan wali kelas saat laporan dibuat

### Pengaduan & Peraturan
-Siswa dapat mengirim pengaduan (insiden, keluhan, laporan) dengan lampiran
-Admin dan guru mengelola serta merespons pengaduan
-Admin mempublikasikan peraturan sekolah yang tampil di dashboard siswa
-Peraturan dikelompokkan per kategori

### Notifikasi WhatsApp
-Pesan otomatis ke orang tua/wali saat siswa: **Hadir**, **Terlambat**, **Alfa**, **Pulang**, **Izin**, **Sakit**, **Dispensasi**, atau **Bolos**
-Setiap jenis notifikasi dapat diaktifkan/dinonaktifkan secara terpisah
-Template pesan WhatsApp dapat dikustomisasi per jenis kejadian
-**Broadcast massal** - kirim pesan ke seluruh wali murid atau per kelas tertentu
-Notifikasi ke orang tua dan wali kelas untuk laporan pelanggaran siswa
-Layanan WhatsApp dapat diaktifkan/dinonaktifkan sepenuhnya dari halaman Pengaturan
-Pantau status koneksi WhatsApp dan scan ulang QR dari halaman Monitor WA

### Backup & Telegram
-Backup database otomatis dikirim ke **Telegram** (bot + chat ID dikonfigurasi di Pengaturan)
-Dua mode backup: setiap kali scan QR masuk, atau per interval waktu (jam)

### Manajemen Pengguna & Akses
-Tiga peran: **Admin**, **Guru**, dan **Siswa** - masing-masing dengan tampilan dan akses berbeda
-Admin Utama tidak dapat dihapus; hanya Admin Utama yang dapat menghapus akun pengguna lain
-Profil pengguna: ganti foto, nama, email, dan password
-Siswa dapat melengkapi data diri (nama orang tua, TTL, alamat) dari halaman profil

### Pengaturan Sistem
-Identitas sekolah: nama, tagline, logo, favicon, NPSN, email, telepon, website
-Pengaturan PWA: logo sekolah otomatis jadi ikon aplikasi saat diinstall di HP
-Konfigurasi jam scan pulang: waktu mulai dan batas akhir scan keluar
-Pengaturan audio: aktifkan/nonaktifkan dan unggah file suara sukses/gagal kustom
-Pengaturan Telegram: token bot dan chat ID untuk backup database
-Log aktivitas - audit trail seluruh tindakan admin dan guru

### PWA (Progressive Web App)
-Dapat diinstall di HP Android/iOS seperti aplikasi native
-Manifest dinamis - ikon PWA otomatis menggunakan logo sekolah yang diunggah admin
-Shortcut langsung ke halaman Scan QR dan Rekap Kehadiran

---

## Stack

|Komponen | Teknologi |
|---|---|
|Backend | Laravel 13, PHP 8.4+ |
|Frontend | Livewire 3 (Volt), Tailwind CSS, Alpine.js |
|Database | PostgreSQL 13+ atau MySQL 8.0+ |
|WhatsApp | Node.js microservice (whatsapp-web.js) |
|Build tool | Vite |

---

## Cara Instalasi

Pilih sesuai kebutuhan:

-**Lokal / pengembangan** → lihat [INSTALL.md](INSTALL.md)
-**VPS Ubuntu** → jalankan `bash install.sh`, atau lihat [INSTALL-VPS.md](INSTALL-VPS.md) untuk langkah manual
-**STB Linux + Cloudflare Tunnel** → lihat [INSTALL-STB.md](INSTALL-STB.md)
-**Menambah sekolah baru** → lihat [ONBOARDING.md](ONBOARDING.md)

---

## Akun Default (setelah seeder)

|Peran | Email | Password |
|---|---|---|
|Admin | admin@sekolah.id | password |
|Guru | guru@sekolah.id | password |

>**Ganti password segera setelah login pertama.**
