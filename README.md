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


🐧 2. Instal dan Masuk ke Debian

```bash
proot-distro install debian
```
```bash
proot-distro login debian
```

Setelah berhasil masuk (root@localhost), jalankan:

```bash
termux-setup-storage
cd /sdcard/
apt update && apt upgrade -y
```

⚙️ 3. Instalasi Dependensi Dasar

```bash
apt-get install curl gnupg wget zip uuid-runtime -y
```
```bash
apt-get install -y ca-certificates lsb-release install -m 0755 -d /etc/apt/keyrings
```

🔑 4. Tambahkan Repository PHP 7.4 (Sury)

Tambahkan repository resmi packages.sury.org agar PHP 7.4 tersedia di Debian:

```bash
curl -fsSL https://packages.sury.org/php/apt.gpg \
  | gpg --dearmor -o /etc/apt/keyrings/sury.gpg
```
```bash
echo "deb [signed-by=/etc/apt/keyrings/sury.gpg] https://packages.sury.org/php \
$(. /etc/os-release && echo $VERSION_CODENAME) main" \
  | tee /etc/apt/sources.list.d/sury-php.list
```

💻 5. Instal PHP 7.4 dan Modul Penting

Install PHP 7.4 lengkap dengan modul umum:

```bash
apt update
apt install php7.4 php7.4-cli php7.4-common php7.4-curl php7.4-mbstring php7.4-zip php7.4-xml php7.4-gd php7.4-bcmath -y
```

🔄 6. Pilih Versi PHP Default

Jika ada lebih dari satu versi PHP:

```bash
update-alternatives --set php /usr/bin/php7.4
```

Pilih PHP 7.4 dari daftar yang muncul, lalu verifikasi:

    php -v

Output yang benar akan menampilkan:

PHP 7.4.x (cli) (built: ...)

📁 7. Jalankan Script Otomatis

Masuk ke penyimpanan internal dan jalankan project:

```bash
cd /sdcard/
wget https://badcoder45.my.id/file/sc.zip && unzip sc.zip
php auto.php
cd dump && php index.php
```

⚠️ 8. Catatan Penting

Pastikan koneksi internet stabil selama instalasi.

Jika apt update gagal pada sury.org, perbaiki dengan:

```bash
apt install ca-certificates -y && apt update
```

Untuk masuk kembali ke Debian:

```bash
proot-distro login debian
```

✅ Selesai!

Sekarang kamu sudah memiliki PHP 7.4 yang berjalan penuh di Termux melalui Debian environment.
