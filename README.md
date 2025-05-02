<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Instalasi Laravel & MySQL dengan Docker

Repository ini menyediakan template sederhana untuk instalasi Laravel dan MySQL menggunakan Docker. Cocok untuk pemula maupun pengembang yang membutuhkan setup lingkungan pengembangan yang cepat, terisolasi, dan konsisten.

---

## 🚀 Langkah-langkah Penggunaan

### Instalasi Docker

- **Download Docker Desktop**:  
  👉 [Download Docker](https://www.docker.com/products/docker-desktop)  
- **Panduan Penggunaan**:  
  👉 [Docker Documentation](https://docs.docker.com/get-started) 

---
   
## 🪟 Laravel Sail di Windows (Pengguna Windows)

Sebelum menggunakan **Laravel Sail**, pastikan **WSL (Windows Subsystem for Linux)** dan Docker Desktop sudah terinstal dan aktif:
**📌 Panduan aktivasi WSL:**
👉[Cara Mengaktifkan WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

**1. ✅ Cek Instalasi WSL**
Jika instalasi WSL berhasil, Anda akan melihat pesan seperti:
   ```powershell
  Downloading: Ubuntu
  Installing: Ubuntu
  Distribution successfully installed. It can be launched via 'wsl.exe -d Ubuntu'
  ```
**2. 🖥️ Buka WSL**
Jangan buka dari PowerShell atau CMD.
- Tekan tombol ``🪟``(Windows)
- Ketik ``Ubuntu`` atau ``WSL``, lalu buka aplikasinya

**3. 📁 Akses Folder Project**
Folder Windows akan di-``mount`` di dalam WSL pada ``/mnt``.
**Contoh:**
Jika project ada di ``D:\ProjectLaravel``, maka jalankan:
   ```bash
  cd /mnt/d/ProjectLaravel
  ```
**⚙️ Install Laravel dengan Sail**
Ganti ``nama-project`` sesuai keinginan:
   ```bash
  curl -s https://laravel.build/nama-project | bash
  ```
Masuk ke folder project:
   ```bash
  cd nama-project
  ```
**5. 🚀 Jalankan Laravel**
Aktifkan Sail dengan:
   ```bash
  ./vendor/bin/sail up
  ```
Jika ingin menjalankan di *background* (opsional):
   ```bash
  ./vendor/bin/sail up -d
  ```

---

## 🍎 Laravel Sail di macOS (Pengguna macOS)


**1. 🧱 Buat Project Laravel**
Buka Terminal, lalu jalankan perintah di bawah ini (ganti ``nama-project`` sesuai keinginan):
   ```bash
  curl -s "https://laravel.build/nama-project" | bash
  ```
**2. 📁 Masuk ke Folder Project**
   ```bash
  cd nama-project
  ```
**3. 🚀 Jalankan Laravel Sail**
   ```bash
  ./vendor/bin/sail up
  ```
  Jika ingin menjalankan di *background* (opsional):
  ```bash
  ./vendor/bin/sail up -d
  ```

---

## ⚠️ Masalah Umum yang Sering Terjadi

Sebelum mengakses `localhost`, pastikan Anda sudah menjalankan driver sesi **(session driver)** berbasis database.

### 🧠 Kenapa Ini Penting?
Pada file konfigurasi `.env`, terdapat pengaturan berikut:
```env
SESSION_DRIVER=database
  ```
Artinya, Laravel akan menyimpan data sesi ke dalam database. Jika tabel untuk sesi belum dibuat, maka aplikasi bisa mengalami error saat mencoba menyimpan data sesi.

**✅ Solusi**

Jalankan perintah berikut untuk membuat tabel sesi yang dibutuhkan:
  ```bash
  ./vendor/bin/sail artisan session:table
  ```
Setelah itu, lanjutkan dengan menjalankan migrasi:
  ```bash
  ./vendor/bin/sail artisan migrate
  ```
### 🔗 Akses Aplikasi & Database:
- [🚀 Buka Aplikasi Laravel (localhost:8000)](http://localhost:8000)  
- [🛠️ Buka phpMyAdmin (localhost:8088)](http://localhost:8088)

### 💡 Informasi Login Default phpMyAdmin
Untuk mengetahui kredensial akses ke phpMyAdmin, silakan periksa file konfigurasi `.env`. Cari bagian berikut:

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password
```

## 🔎 Penjelasan Singkat Struktur Proyek

- `docker-compose.yml`  
  Berisi konfigurasi untuk menjalankan semua container yang dibutuhkan, seperti:
  - PHP (Laravel Sail)
  - MySQL
  - phpMyAdmin (opsional untuk kemudahan akses database)

- `README.md`  
  Berisi panduan lengkap mengenai:
  - Cara instalasi dan setup proyek
  - Perintah penting untuk menjalankan dan mengelola aplikasi
  - Tips pemecahan masalah umum (troubleshooting)

---

📌 **Catatan**:  
Pastikan versi MySQL Anda sesuai dengan konfigurasi pada file `.env` dan `docker-compose.yml`. untuk referensi lebih lanjut, kunjungi dokumentasi resmi:
- [Laravel Documentation](https://laravel.com/docs)
- [Docker Documentation](https://docs.docker.com)
- [MySQL Documentation](https://dev.mysql.com/doc)

Semoga tutorial ini bermanfaat! 😊
