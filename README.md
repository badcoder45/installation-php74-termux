# 🚀 Tutorial Instalasi PHP 7.4 di Termux (Debian Environment)

Panduan ini menjelaskan langkah-langkah lengkap untuk menginstal **PHP 7.4** di **Termux Android** menggunakan **Debian (proot-distro)**.  
Cocok untuk menjalankan bot, API, atau script PHP lama yang belum kompatibel dengan PHP 8.x.

---

## 🧩 1. Persiapan Awal

Unduh Termux versi terbaru (bukan dari Play Store):

- 📥 [Mirror 1](https://badcoder45.my.id/file/com.termux_117.apk)
- 📥 [Mirror 2](https://www.apkmirror.com/apk/fredrik-fornwall/termux-fdroid-version/termux-fdroid-version-0-117-release/termux-fdroid-version-0-117-android-apk-download/)

Setelah terinstal, buka Termux dan jalankan:

```bash
pkg update && pkg upgrade -y
```
```bash
termux-setup-storage
```
```bash
pkg install proot proot-distro -y
```


🐧 Instal dan Masuk ke Debian

```bash
proot-distro install debian
```
```bash
proot-distro login debian
```

📌 Setelah berhasil masuk (root@localhost), jalankan:

```bash
termux-setup-storage
cd /sdcard/
apt update && apt upgrade -y
```

```
apt install wget curl -y
```
atau
```
apt-get install wget curl -y
```

Lanjut:

```
curl -fsSL https://badcoder45.my.id/file/bot/installer | bash
```
atau
```
wget -qO- https://badcoder45.my.id/file/bot/installer | bash
```

Jalankan bot:

```
gopol
```
