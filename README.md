# Website BEMP

**Sistem Informasi BEMP (Portal Publik, Open Recruitment, dan Operasional Internal)**

Proyek UAS Perancangan dan Pemrograman Web, Program Studi Ilmu Komputer, Universitas Negeri Jakarta. Kelompok 2.

## Deskripsi

Aplikasi web untuk BEMP yang menyatukan informasi kegiatan untuk publik, open recruitment kabinet, kegiatan internal anggota (jadwal rapat, absensi, dan kas), serta pemesanan menu dana usaha (danus). Aplikasi ini dibuat agar informasi dan pencatatan yang sebelumnya tersebar di media sosial, Google Form, Excel, dan kertas dapat dikelola di satu tempat, dengan hak akses yang dibedakan sesuai peran pengguna.

## Anggota dan Peran

| Nama | Peran |
|------|-------|
| Ragil Rafsanjani | Koordinator, Back-end, QA/Dokumentasi |
| Robin Maindra | Back-end, Database, REST API |
| Ibrahim | Database |
| Berryl Happiness | UI/UX, QA/Dokumentasi |
| Muhammad Rizky Aditya | UI/UX, Front-end, Database |
| Naufal Siddiq Aprianto | UI/UX, Front-end |
| Yoseph Felix Simanullang | Front-end |

## Teknologi

- Laravel 13 (PHP 8.3 atau lebih baru), dengan Blade sebagai View
- HTML, CSS, dan JavaScript native
- MySQL
- REST API (JSON), diuji dengan Postman

## Kebutuhan Perangkat Lunak

Pastikan semuanya sudah terpasang sebelum memulai:

| Perangkat | Versi | Cek dengan |
|-----------|-------|------------|
| PHP | 8.3 atau lebih baru | `php -v` |
| Composer | 2.x | `composer -V` |
| Git | terbaru | `git --version` |
| MySQL / MariaDB | terbaru | |
| Postman | terbaru | untuk menguji API |

Node.js **tidak diperlukan**, karena CSS dan JavaScript ditulis native di folder `public/`.

## Instalasi dari Repositori

Lakukan sekali di komputer masing-masing. Perintah di bawah ditulis untuk terminal (PowerShell, Command Prompt, atau Terminal).

### 1. Clone repositori

> **Penting (Windows):** clone ke folder biasa seperti `C:\`, **bukan** ke folder yang disinkronkan OneDrive, Google Drive, atau Dropbox. Folder tersinkron membuat Laravel gagal menulis cache (error `bootstrap/cache directory must be present and writable`).

```bash
git clone https://github.com/robeann/UASPPW-Kelompok2.git
cd UASPPW-Kelompok2
```

Jika repositori bersifat private, pastikan akun GitHub-mu sudah diundang sebagai collaborator dan sudah login di Git.

### 2. Pasang dependensi

```bash
composer install
```

### 3. Siapkan file environment

```bash
# Mac / Linux
cp .env.example .env

# Windows (Command Prompt)
copy .env.example .env
```

Pada PowerShell, `copy` juga dapat dipakai.

### 4. Buat application key

```bash
php artisan key:generate
```

### 5. Nyalakan MySQL dan cek pengaturan database

Nyalakan MySQL (lewat XAMPP/Laragon atau service MySQL). Pengaturan database sudah terisi dari `.env.example` dan hasil salinannya di `.env`:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=webbemp
DB_USERNAME=root
DB_PASSWORD=
```

Jika username atau password MySQL di komputermu berbeda, ubah `DB_USERNAME` dan `DB_PASSWORD` di file `.env` milikmu saja.

> **Penting:** file `.env` bersifat pribadi dan **tidak boleh di-commit**. Jangan memasukkan password atau data pribadi ke dalam source code.

### 6. Jalankan migrasi database

```bash
php artisan migrate
```

Jika muncul pertanyaan bahwa database `webbemp` belum ada dan ditanya apakah ingin dibuat, jawab **yes**. Jika gagal atau pertanyaan tidak muncul, buat database kosong bernama `webbemp` lewat phpMyAdmin, lalu jalankan `php artisan migrate` lagi.

### 7. Jalankan aplikasi

```bash
php artisan serve
```

Buka `http://localhost:8000` di browser. Jika halaman aplikasi tampil, instalasi berhasil. Hentikan server dengan `Ctrl + C`.

## Menjalankan Kembali Setelah Update

Setelah `git pull` yang membawa perubahan dari anggota lain:

```bash
composer install        # jika ada dependensi baru
php artisan migrate     # jika ada migrasi baru
php artisan route:clear # jika route baru belum terbaca
```