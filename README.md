# Praktikum Web – Pengenalan Laravel dan MVC

Aplikasi sederhana untuk menampilkan dan mengelola tampilan data buku menggunakan framework **Laravel** dengan konsep **Model-View-Controller (MVC)**.

## Deskripsi Proyek

Proyek ini dibuat sebagai bagian dari Praktikum Pemrograman Web Pertemuan 9 dengan materi Pengenalan Laravel dan Pola MVC.

Aplikasi menampilkan daftar buku yang datanya disimpan sementara dalam bentuk array pada Model. Pengguna dapat melihat seluruh daftar buku, mencari buku berdasarkan judul, dan membuka halaman detail berdasarkan kode buku.

## Fitur Aplikasi

- Menampilkan daftar buku.
- Mencari buku berdasarkan judul.
- Menampilkan detail buku berdasarkan kode.
- Menampilkan halaman 404 jika kode buku tidak ditemukan.
- Memberikan pesan ketika hasil pencarian tidak ditemukan.

## Teknologi yang Digunakan

- **PHP** – Bahasa pemrograman.
- **Laravel** – Framework pengembangan web.
- **Composer** – Pengelola dependensi PHP.
- **Blade** – Template engine Laravel.
- **Visual Studio Code** – Editor kode.

## Data Buku

| Kode | Judul |
|---|---|
| BK001 | Dasar PHP |
| BK002 | Belajar Laravel |
| BK003 | Logika Web |
| BK004 | Pemrograman JavaScript |

Data buku disimpan di dalam Model `Buku.php` menggunakan array dan belum menggunakan database.

## Struktur Proyek

```text
praktikum-web/
├── app/
│   ├── Http/
│   │   └── Controllers/
│   │       └── BukuController.php
│   └── Models/
│       └── Buku.php
│
├── resources/
│   └── views/
│       └── buku/
│           ├── index.blade.php
│           └── show.blade.php
│
├── routes/
│   └── web.php
│
└── README.md
```

## Cara Menjalankan Proyek

**1. Clone repository**

```bash
git clone https://github.com/username/nama-repository.git
```

Ganti URL tersebut dengan alamat repository yang sebenarnya.

**2. Masuk ke folder proyek**

```bash
cd praktikum-web
```

**3. Install dependensi**

```bash
composer install
```

**4. Jalankan server Laravel**

```bash
php artisan serve
```

**5. Buka aplikasi**

Akses alamat berikut melalui browser:

```text
http://127.0.0.1:8000
```

## Daftar Route

| Method | URL | Fungsi |
|---|---|---|
| GET | `/` | Halaman awal Laravel |
| GET | `/buku` | Menampilkan daftar buku |
| GET | `/buku?cari=Laravel` | Mencari buku berdasarkan judul |
| GET | `/buku/{kode}` | Menampilkan detail buku |

## Contoh Pengujian

Beberapa URL yang dapat digunakan untuk menguji aplikasi:

| URL | Hasil yang Diharapkan |
|---|---|
| `/buku` | Menampilkan empat data buku |
| `/buku?cari=Laravel` | Menampilkan buku Belajar Laravel |
| `/buku/BK002` | Menampilkan detail BK002 |
| `/buku/BK999` | Menampilkan halaman 404 |
| `/buku?cari=JavaScript` | Menampilkan buku Pemrograman JavaScript |
| `/buku/BK004` | Menampilkan detail BK004 |

## Konsep MVC

Aplikasi ini menerapkan tiga bagian utama dalam konsep MVC:

- **Model:** `Buku.php`, berfungsi menyediakan data buku.
- **View:** `index.blade.php` dan `show.blade.php`, berfungsi menampilkan daftar serta detail buku.
- **Controller:** `BukuController.php`, berfungsi memproses permintaan, melakukan pencarian, dan menentukan data yang ditampilkan.

Route pada `web.php` menghubungkan alamat yang diakses pengguna dengan method pada Controller.

## Catatan

Proyek ini dibuat untuk keperluan pembelajaran Laravel dan konsep MVC. Penyimpanan data masih menggunakan array sederhana sehingga belum memerlukan konfigurasi database maupun migration.

---

**Praktikum Pemrograman Web – Pertemuan 9**  
**Materi: Pengenalan Laravel dan Pola MVC**