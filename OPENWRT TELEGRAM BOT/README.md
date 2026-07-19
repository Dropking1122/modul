# Telebotaku - OpenWRT Telegram Bot

Bot Telegram untuk monitoring dan manajemen router OpenWRT secara modular melalui sistem plugin shell script.

## Fitur Utama

- **Monitoring Sistem** - Info sistem real-time, CPU, RAM, suhu, uptime
- **Statistik Jaringan** - vnStat, ping test, speed test, bandwidth monitor
- **Kontrol WiFi** - On/Off WiFi, ganti password, status WiFi
- **Block Device** - Blokir/unblokir perangkat berdasarkan MAC address
- **Alert System** - Notifikasi saat ada device baru terhubung
- **Backup Config** - Backup konfigurasi sistem, kirim ke Telegram
- **User Management** - Daftar perangkat terhubung
- **Auto Update** - Update bot otomatis dari GitHub
- **Sistem Plugin** - Modular, mudah menambah/menghapus fitur

## Instalasi

### 1. Dapatkan Bot Token dari BotFather
1. Cari `@BotFather` di Telegram, lalu jalankan `/start`
2. Gunakan `/newbot`, ikuti instruksi, salin **Bot Token** (format: `123456789:ABCDefGhIJKlmNoPQRsTUVwxyZ`)

### 2. Dapatkan Admin ID (Chat ID)
1. Cari `@userinfobot`, jalankan `/start`
2. Bot akan membalas dengan ID Anda (misal: `123456789`)

### 3. Dapatkan API ID & API Hash
1. Kunjungi https://my.telegram.org/auth
2. Login, pilih "API development tools"
3. Isi formulir, salin **API ID** dan **API Hash**

### 4. Instalasi Bot
Jalankan installer berikut di terminal OpenWRT (pastikan sudah root):
```bash
opkg update && (cd /tmp && curl -sLko revd_installer.sh https://raw.githubusercontent.com/revaldieka/telebotaku/main/revd_installer.sh && chmod +x revd_installer.sh && sh revd_installer.sh)
```
Lalu ikuti instruksi konfigurasi.

## Sistem Plugin

Bot menjalankan perintah dari file shell script pada `/root/REVDBOT/plugins/`. Berikut plugin bawaan:

| Plugin | File | Deskripsi |
|------------------|--------------------|-------------------------------------|
| System Monitor | `system.sh` | Info sistem real-time |
| Memory Cleaner | `clear_ram.sh` | Bersihkan cache RAM |
| Network Stats | `vnstat.sh` | Statistik penggunaan jaringan |
| Speed Test | `speedtest.sh` | Test kecepatan internet |
| Ping Test | `ping.sh` | Test konektivitas |
| WiFi Control | `wifi_control.sh` | On/Off WiFi, ganti password |
| Bandwidth Monitor | `bandwidth.sh` | Monitor realtime bandwidth |
| Block MAC | `block_mac.sh` | Blokir/unblokir perangkat |
| Alert Monitor | `alert_monitor.sh` | Deteksi device baru |
| Backup Config | `backup_config.sh` | Backup konfigurasi sistem |
| User List | `userlist.sh` | Daftar perangkat terhubung |
| Firewall Status | `firewall.sh` | Status firewall & rules |
| System Reboot | `reboot.sh` | Restart perangkat |
| Bot Update | `update.sh` | Update bot dari GitHub |
| Bot Uninstall | `uninstall.sh` | Hapus bot dari sistem |

### Menambah Plugin Baru
1. Buat script shell baru di `/root/REVDBOT/plugins/`
2. Berikan permission executable: `chmod +x plugin_name.sh`
3. Tambahkan ke `required_scripts` di `bot_openwrt.py` jika perlu
4. Tambahkan handler dan tombol pada bot sesuai kebutuhan

## Interface & Perintah Bot

### Tombol Interaktif

```
╔═══════════════════════════════════════════╗
║ System Info │ Reboot ║
║ Clear RAM │ Network Stats ║
║ Speed Test │ Ping Test ║
║ WiFi Control │ Bandwidth ║
║ Block Device │ User List ║
║ Backup Config │ Alert System ║
║ Update Bot │ Uninstall Bot ║
╚═══════════════════════════════════════════╝
```

### Daftar Perintah

| Perintah | Fungsi | Hak Akses |
|-----------------------------|----------------------------------|----------------|
| `/start` | Memulai bot & tampilkan menu | Semua user |
| `/help` | Tampilkan bantuan | Semua user |
| `/system` | Info sistem lengkap | Semua user |
| `/clearram` | Bersihkan cache RAM | Semua user |
| `/network` | Statistik jaringan (vnstat) | Semua user |
| `/speedtest` | Test kecepatan internet | Semua user |
| `/ping [target]` | Ping test ke target | Semua user |
| `/bandwidth` | Monitor bandwidth realtime | Semua user |
| `/userlist` | Daftar perangkat terhubung | Semua user |
| `/wifi` | Status WiFi | Semua user |
| `/wifi on` | Nyalakan WiFi | Admin only |
| `/wifi off` | Matikan WiFi | Admin only |
| `/wifi pass <password>` | Ganti password WiFi | Admin only |
| `/block <MAC>` | Blokir device berdasarkan MAC | Admin only |
| `/unblock <MAC>` | Unblokir device | Admin only |
| `/blocklist` | Daftar device yang diblokir | Semua user |
| `/alert` | Menu Alert System | Semua user |
| `/backup` | Backup konfigurasi sistem | Admin only |
| `/reboot` | Restart perangkat | Admin only |
| `/update` | Update bot dari GitHub | Admin only |
| `/uninstall` | Hapus bot dari sistem | Admin only |

## WiFi Control

Kontrol WiFi langsung dari Telegram:

```bash
/wifi # Lihat status WiFi
/wifi on # Nyalakan semua WiFi
/wifi off # Matikan semua WiFi
/wifi pass MyPass # Ganti password WiFi
```

## Block Device

Blokir perangkat yang tidak diinginkan:

```bash
/block AA:BB:CC:DD:EE:FF # Blokir MAC address
/unblock AA:BB:CC:DD:EE:FF # Unblokir MAC address
/blocklist # Lihat daftar blocked
```

## Alert System

Sistem akan memberi notifikasi saat ada device baru yang terhubung ke jaringan. Menu Alert:
- **Cek Device Baru** - Periksa device baru yang connect
- **Riwayat Alert** - Lihat history device yang pernah connect
- **Reset Known Devices** - Reset daftar device yang dikenal
- **Hapus Riwayat** - Bersihkan log alert

## Update Bot

Jalankan tombol **Update Bot** pada bot (hanya admin) atau:
```bash
sh /root/REVDBOT/plugins/update.sh
```
Script akan mengunduh versi terbaru dari GitHub dan memperbarui file bot.

## Uninstall

### Melalui Bot (direkomendasikan)
- Kirim `/uninstall` ke bot (hanya admin)
- Pilih opsi: Keep config / Delete all / Cancel

### Manual Uninstall
```bash
cd /tmp
curl -sLko uninstall.sh https://raw.githubusercontent.com/revaldieka/telebotaku/main/uninstall.sh
chmod +x uninstall.sh
./uninstall.sh
```

### One-Line Uninstaller
```bash
cd /tmp && curl -sLko uninstall.sh https://raw.githubusercontent.com/revaldieka/telebotaku/main/uninstall.sh && chmod +x uninstall.sh && sh uninstall.sh
```

## � Screenshot

### Menu Utama
```
╔══════════════════════════════════════╗
║ OpenWRT | REVD.CLOUD Bot
╠══════════════════════════════════════╣
║ Selamat datang! Pilih menu di bawah
╠══════════════════════════════════════╣
║ /system - Info sistem
║ /reboot - Restart device
║ /clearram - Bersihkan RAM
║ /wifi - Kontrol WiFi
║ /block - Blokir perangkat
║ /alert - Sistem alert
║ /backup - Backup konfigurasi
╠══════════════════════════════════════╣
║ REVD.CLOUD
╚══════════════════════════════════════╝
```

### System Monitor
```
╔══════════════════════════════════════════╗
║ SYSTEM MONITOR ║
╠══════════════════════════════════════════╣
║ Device: OpenWRT
║ Model: Amlogic HG680P (S905X)
║ Uptime: 2d 14:32:10
║ Temp: 52.3°C
║ CPU: 12%
║ Memory: 128.5 MB / 512 MB
╠══════════════════════════════════════════╣
║ REVD.CLOUD ║
╚══════════════════════════════════════════╝
```

## Manajemen Service

```bash
/etc/init.d/revd start # Start bot
/etc/init.d/revd stop # Stop bot
/etc/init.d/revd restart # Restart bot
/etc/init.d/revd status # Status bot
/etc/init.d/revd enable # Enable auto-start
/etc/init.d/revd disable # Disable auto-start
```

### Monitoring Logs
```bash
tail -f /var/log/revd_bot.log # Real-time logs
logread | grep revd # System logs
ps | grep bot_openwrt.py # Cek proses bot
```

## Struktur Direktori

```
/root/REVDBOT/
├── bot_openwrt.py # Main bot script
├── config.ini # Konfigurasi bot
├── bot_session.session # Telegram session
└── plugins/
 ├── system.sh # System monitor
 ├── clear_ram.sh # Memory cleaner
 ├── vnstat.sh # Network stats
 ├── speedtest.sh # Speed test
 ├── ping.sh # Ping test
 ├── wifi_control.sh # WiFi control
 ├── bandwidth.sh # Bandwidth monitor
 ├── block_mac.sh # MAC blocker
 ├── alert_monitor.sh # Device alert
 ├── backup_config.sh # Config backup
 ├── userlist.sh # User list
 ├── reboot.sh # System reboot
 ├── update.sh # Bot updater
 └── uninstall.sh # Bot uninstaller
```

## 🆘 Troubleshooting

### Bot Tidak Start
1. Periksa konfigurasi
 ```bash
 cat /root/REVDBOT/config.ini
 ```
2. Jalankan manual
 ```bash
 cd /root/REVDBOT
 python3 bot_openwrt.py
 ```
3. Cek dependensi
 ```bash
 opkg list-installed | grep python3
 pip3 list | grep telethon
 ```

### Database Locked Error
```bash
/etc/init.d/revd stop
rm -f /root/REVDBOT/bot_session.session*
/etc/init.d/revd start
```

### WiFi Control Tidak Berfungsi
```bash
# Pastikan wireless package terinstall
opkg update
opkg install wireless-tools

# Cek status wireless
uci show wireless
wifi status
```

### Block MAC Tidak Berfungsi
```bash
# Pastikan firewall aktif
/etc/init.d/firewall restart

# Cek rules
iptables -L | grep MAC
```

## Lisensi

MIT License

## Support & Kontak

- **GitHub Issues:** Bug report & diskusi
- **Telegram:** [@ValltzID](https://t.me/ValltzID)
- **Instagram:** [@revd.cloud](https://instagram.com/revd.cloud)
- **Website:** [revd.cloud](https://revd.cloud)

### Credits

- Original Reference: [@Tomketstore](https://t.me/Tomketstore)
- Enhanced by: REVD.CLOUD

---

 **Jangan lupa kasih star di GitHub jika project ini membantu!**
