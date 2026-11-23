# Praktikum Pemrograman Web – Laravel CRUD

Aplikasi pengelolaan data buku menggunakan framework Laravel. Proyek ini merupakan pengembangan dari praktikum sebelumnya dengan menerapkan Migration, Eloquent Relationship, Seeder, dan CRUD (Create, Read, Update, Delete).

## Deskripsi Proyek

Pada praktikum ini, aplikasi daftar buku dikembangkan agar menggunakan database MySQL sebagai tempat penyimpanan data. Pengelolaan database dilakukan menggunakan Migration dan Eloquent ORM dari Laravel.

Aplikasi memiliki dua tabel utama, yaitu `kategoris` dan `bukus`. Kedua tabel tersebut saling terhubung menggunakan relasi Eloquent sehingga setiap buku memiliki kategori.

Selain menampilkan data, pengguna juga dapat menambahkan buku baru, mengubah informasi buku, dan menghapus data buku melalui halaman aplikasi.

## Fitur Aplikasi

- Menampilkan daftar buku beserta kategorinya.
- Menambahkan data buku.
- Mengubah kode, judul, dan kategori buku.
- Menghapus data buku.
- Validasi input agar kode buku tidak duplikat.
- Relasi antara tabel buku dan kategori.
- Seeder untuk mengisi data awal.

## Teknologi yang Digunakan

- PHP
- Laravel
- MySQL
- Composer
- Eloquent ORM
- Blade Template
- Visual Studio Code
- phpMyAdmin

## Struktur Database

Aplikasi menggunakan dua tabel utama:

**1. Tabel kategoris**

| Kolom | Keterangan |
|---|---|
| id | Primary key |
| nama | Nama kategori |
| created_at | Waktu data dibuat |
| updated_at | Waktu data diperbarui |

**2. Tabel bukus**

| Kolom | Keterangan |
|---|---|
| id | Primary key |
| kode | Kode buku dan bersifat unik |
| judul | Judul buku |
| kategori_id | Foreign key ke tabel kategoris |
| created_at | Waktu data dibuat |
| updated_at | Waktu data diperbarui |

## Relasi Eloquent

Relasi antara kedua model menggunakan:

- `hasMany()` pada Model Kategori, karena satu kategori dapat memiliki banyak buku.
- `belongsTo()` pada Model Buku, karena satu buku hanya memiliki satu kategori.

## Data Awal

Data awal dimasukkan menggunakan Seeder.

| Kode | Judul | Kategori |
|---|---|---|
| BK001 | Dasar PHP | Pemrograman |
| BK002 | Belajar Laravel | Pemrograman |

Kategori awal yang tersedia:
- Pemrograman
- Basis Data

## Struktur Folder Penting

```text
app/
├── Http/
│   └── Controllers/
│       └── BukuController.php
└── Models/
    ├── Buku.php
    └── Kategori.php

database/
├── migrations/
└── seeders/
    ├── KategoriSeeder.php
    ├── BukuSeeder.php
    └── DatabaseSeeder.php

resources/
└── views/
    └── buku/
        ├── index.blade.php
        └── form.blade.php

routes/
└── web.php
```

## Cara Menjalankan Proyek

**1. Clone repository**

```bash
git clone https://github.com/username/nama-repository.git
```

Ganti URL tersebut dengan alamat repository yang sebenarnya.

**2. Masuk ke folder proyek**

```bash
cd Prak-Pemweb
```

**3. Install dependensi**

```bash
composer install
```

**4. Atur konfigurasi database**

Buat database MySQL dengan nama:

```sql
CREATE DATABASE praktikum_web;
```

Kemudian sesuaikan konfigurasi `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=praktikum_web
DB_USERNAME=root
DB_PASSWORD=

SESSION_DRIVER=file
```

Sesuaikan username dan password MySQL dengan konfigurasi lokal.

**5. Bersihkan konfigurasi Laravel**

```bash
php artisan config:clear
```

**6. Jalankan migration**

```bash
php artisan migrate
```

**7. Masukkan data awal**

```bash
php artisan db:seed
```

**8. Jalankan server**

```bash
php artisan serve
```

Buka aplikasi melalui browser:

```text
http://127.0.0.1:8000/buku
```

## Daftar Route

| Method | URL | Fungsi |
|---|---|---|
| GET | `/buku` | Menampilkan daftar buku |
| GET | `/buku/create` | Menampilkan form tambah buku |
| POST | `/buku` | Menyimpan buku baru |
| GET | `/buku/{buku}/edit` | Menampilkan form edit |
| PUT | `/buku/{buku}` | Memperbarui data buku |
| DELETE | `/buku/{buku}` | Menghapus data buku |

## Pengujian Aplikasi

Beberapa pengujian yang dilakukan dalam praktikum ini meliputi:

1. Memastikan migration berhasil membuat tabel database.
2. Memastikan seeder berhasil memasukkan data awal.
3. Menampilkan daftar buku beserta kategori.
4. Menambahkan buku baru dengan kode BK003.
5. Mengubah judul buku BK003.
6. Menguji validasi dengan memasukkan kode buku yang sudah digunakan.
7. Menghapus data buku BK003.

## Catatan

Proyek ini dibuat untuk memenuhi kegiatan Praktikum Pemrograman Web dengan materi Migration, Eloquent Relationship, dan CRUD pada Laravel.

Data buku disimpan menggunakan database MySQL dan dikelola melalui Eloquent ORM Laravel.

---

**Praktikum Pemrograman Web**  
**Materi: Migration, Eloquent Relationship, dan CRUD Laravel**