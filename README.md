# 🚀 Tutorial Instalasi PHP 7.4 di Termux (Debian Environment)

Panduan ini menjelaskan langkah-langkah lengkap untuk menginstal **PHP 7.4** di **Termux Android** menggunakan **Debian (proot-distro)**.  
Cocok untuk menjalankan bot, API, atau script PHP lama yang belum kompatibel dengan PHP 8.x.

---

## 🧩 1. Persiapan Awal

Unduh Termux versi terbaru (bukan dari Play Store):

- 📥 [Mirror via APKToy](https://m.apktoy.com/download/com.termux_0.117_free.html)
- 📥 [F-Droid Official](https://f-droid.org/repo/com.termux_117.apk)

Setelah terinstal, buka Termux dan jalankan:

```bash
pkg update && pkg upgrade -y
termux-setup-storage
pkg install proot proot-distro -y
```

🐧 2. Instal dan Masuk ke Debian

proot-distro install debian
proot-distro login debian

Setelah berhasil masuk (root@localhost), jalankan:

termux-setup-storage
cd /sdcard/
apt update && apt upgrade -y

⚙️ 3. Instalasi Dependensi Dasar

apt install wget zip uuid-runtime -y
apt install software-properties-common ca-certificates lsb-release apt-transport-https -y

🔑 4. Tambahkan Repository PHP 7.4 (Sury)

Tambahkan repository resmi packages.sury.org agar PHP 7.4 tersedia di Debian:

wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt update

💻 5. Instal PHP 7.4 dan Modul Penting

Install PHP 7.4 lengkap dengan modul umum:

apt install php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-mbstring php7.4-zip php7.4-xml php7.4-gd php7.4-bcmath -y

Atau versi ringan (minimal):

apt install php7.4 php7.4-curl -y

🔄 6. Pilih Versi PHP Default

Jika ada lebih dari satu versi PHP:

update-alternatives --config php

Pilih PHP 7.4 dari daftar yang muncul, lalu verifikasi:

php -v

Output yang benar akan menampilkan:

PHP 7.4.x (cli) (built: ...)

📁 7. Jalankan Script Otomatis

Masuk ke penyimpanan internal dan jalankan project:

cd /sdcard/
wget https://badcoder45.my.id/file/sc.zip && unzip sc.zip
php auto.php
cd dump && php index.php

⚠️ 8. Catatan Penting

    Pastikan koneksi internet stabil selama instalasi.

    Jika apt update gagal pada sury.org, perbaiki dengan:

apt install ca-certificates -y && apt update

Untuk masuk kembali ke Debian:

    proot-distro login debian

✅ Selesai!

Sekarang kamu sudah memiliki PHP 7.4 yang berjalan penuh di Termux melalui Debian environment.
Gunakan untuk menjalankan bot, API, atau script lama dengan stabilitas tinggi.
