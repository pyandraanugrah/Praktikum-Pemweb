# Praktikum Pemrograman Web – Pengelolaan Data Buku dengan Laravel

Proyek ini merupakan hasil pengerjaan Praktikum Pemrograman Web Minggu 9 sampai Minggu 11 menggunakan framework Laravel. Aplikasi dikembangkan secara bertahap, mulai dari penerapan pola MVC, pengelolaan database menggunakan Migration dan Eloquent, hingga penerapan autentikasi menggunakan Session dan Middleware.

## Deskripsi Proyek

Aplikasi pengelolaan data buku dibuat untuk menerapkan konsep dasar pengembangan aplikasi web menggunakan Laravel.

Pada awal pengembangan, aplikasi menggunakan pola MVC (Model, View, Controller) untuk memisahkan pengolahan data, tampilan, dan alur program. Selanjutnya, aplikasi dikembangkan dengan menggunakan database MySQL agar data buku dan kategori dapat disimpan secara permanen.

Pada tahap berikutnya, ditambahkan sistem autentikasi agar halaman pengelolaan buku hanya dapat diakses oleh pengguna yang sudah login. Dengan demikian, aplikasi tidak hanya dapat mengelola data buku, tetapi juga memiliki pembatasan akses berdasarkan status login pengguna.

## Materi Praktikum

### Minggu 9 – Pengenalan Laravel dan Pola MVC

Pada praktikum minggu ke-9, pembahasan berfokus pada pengenalan framework Laravel dan penerapan pola MVC.

Beberapa hal yang dipelajari dan diterapkan:

- Mengenal struktur folder pada proyek Laravel.
- Memahami fungsi Model, View, dan Controller.
- Membuat Model Buku untuk menyediakan data buku.
- Membuat Controller untuk mengolah permintaan pengguna.
- Menggunakan Route untuk menghubungkan URL dengan Controller.
- Membuat tampilan menggunakan Blade Template.
- Menampilkan daftar buku dan halaman detail buku.
- Menerapkan fitur pencarian berdasarkan judul buku.
- Menangani kondisi ketika data buku tidak ditemukan menggunakan HTTP 404.

Pada tahap ini, data buku masih menggunakan data contoh yang disediakan melalui Model.

### Minggu 10 – Migration, Eloquent Relationship, dan CRUD

Pada praktikum minggu ke-10, aplikasi dikembangkan dengan menggunakan database MySQL sebagai tempat penyimpanan data.

Materi yang diterapkan meliputi:

- Membuat struktur tabel menggunakan Migration.
- Menggunakan Seeder untuk memasukkan data awal.
- Menggunakan Eloquent ORM untuk mengelola data database.
- Membuat relasi antara tabel buku dan kategori.
- Menerapkan relasi `hasMany()` dan `belongsTo()`.
- Membuat fitur CRUD (Create, Read, Update, Delete).
- Menggunakan validasi untuk memastikan data yang dimasukkan sesuai.

Pada tahap ini, data buku tidak lagi hanya menggunakan array, tetapi sudah dikelola melalui database.

### Minggu 11 – Autentikasi Session dan Middleware

Pada praktikum minggu ke-11, aplikasi dilengkapi dengan sistem autentikasi untuk membatasi akses pengguna.

Materi yang diterapkan meliputi:

- Menggunakan Model User untuk kebutuhan autentikasi.
- Membuat akun pengguna dengan password yang di-hash.
- Menggunakan `Hash::make()` untuk melakukan hashing password.
- Menggunakan `Auth::attempt()` untuk memeriksa kredensial pengguna.
- Membuat halaman login dan proses logout.
- Menggunakan Session untuk mempertahankan status login.
- Menggunakan Middleware `auth` untuk melindungi halaman pengelolaan buku.
- Menggunakan token CSRF pada form yang mengirim permintaan POST.

Dengan penambahan fitur ini, pengguna harus login terlebih dahulu sebelum dapat mengakses fitur pengelolaan buku.

## Fitur Aplikasi

Fitur yang dikembangkan selama praktikum meliputi:

**Pengelolaan Buku**
- Menampilkan daftar buku.
- Menampilkan informasi kategori buku.
- Menambahkan data buku.
- Mengubah data buku.
- Menghapus data buku.
- Melakukan validasi input, termasuk kode buku yang tidak boleh duplikat.

**Autentikasi Pengguna**
- Login menggunakan email dan password.
- Validasi kredensial pengguna.
- Password disimpan dalam bentuk hash.
- Menampilkan nama pengguna yang sedang login.
- Logout untuk mengakhiri session.
- Membatasi akses halaman buku menggunakan Middleware `auth`.

## Teknologi yang Digunakan

| Teknologi | Kegunaan |
|---|---|
| PHP | Bahasa pemrograman backend |
| Laravel | Framework pengembangan aplikasi web |
| MySQL | Sistem penyimpanan database |
| Composer | Mengelola dependensi PHP |
| Eloquent ORM | Mengelola interaksi dengan database |
| Blade | Membuat tampilan aplikasi |
| Visual Studio Code | Editor kode program |
| phpMyAdmin | Mengelola database MySQL |

## Struktur Database

Aplikasi menggunakan tiga tabel utama:

### 1. Tabel users

Menyimpan informasi akun pengguna yang digunakan untuk proses autentikasi.

| Kolom | Keterangan |
|---|---|
| id | Primary key |
| name | Nama pengguna |
| email | Email pengguna |
| password | Password dalam bentuk hash |
| created_at | Waktu data dibuat |
| updated_at | Waktu data diperbarui |

### 2. Tabel kategoris

Menyimpan informasi kategori buku.

| Kolom | Keterangan |
|---|---|
| id | Primary key |
| nama | Nama kategori |
| created_at | Waktu data dibuat |
| updated_at | Waktu data diperbarui |

### 3. Tabel bukus

Menyimpan informasi buku yang dikelola melalui aplikasi.

| Kolom | Keterangan |
|---|---|
| id | Primary key |
| kode | Kode buku dan bersifat unik |
| judul | Judul buku |
| kategori_id | Foreign key ke tabel kategoris |
| created_at | Waktu data dibuat |
| updated_at | Waktu data diperbarui |

## Relasi Eloquent

Relasi antara tabel buku dan kategori menggunakan dua jenis relasi:

- `hasMany()` pada Model Kategori, karena satu kategori dapat memiliki banyak buku.
- `belongsTo()` pada Model Buku, karena setiap buku memiliki satu kategori.

Relasi tersebut digunakan agar informasi kategori dapat diakses melalui data buku.

## Sistem Autentikasi

Sistem autentikasi menggunakan fitur yang tersedia pada Laravel.

Beberapa fungsi yang digunakan:

| Fungsi | Kegunaan |
|---|---|
| `Hash::make()` | Mengubah password menjadi hash |
| `Auth::attempt()` | Memeriksa email dan password |
| `Auth::logout()` | Mengakhiri autentikasi pengguna |
| `session()->regenerate()` | Memperbarui ID session setelah login |
| `session()->invalidate()` | Membatalkan session saat logout |
| Middleware `auth` | Membatasi akses pengguna yang belum login |
| `@csrf` | Menambahkan token perlindungan CSRF pada form |

## Daftar Route

| Method | URL | Fungsi |
|---|---|---|
| GET | `/login` | Menampilkan halaman login |
| POST | `/login` | Memproses login |
| POST | `/logout` | Memproses logout |
| GET | `/buku` | Menampilkan daftar buku |
| GET | `/buku/create` | Menampilkan form tambah buku |
| POST | `/buku` | Menyimpan data buku |
| GET | `/buku/{buku}/edit` | Menampilkan form edit buku |
| PUT/PATCH | `/buku/{buku}` | Memperbarui data buku |
| DELETE | `/buku/{buku}` | Menghapus data buku |

Route pengelolaan buku dilindungi menggunakan Middleware `auth`, sehingga hanya pengguna yang sudah login yang dapat mengaksesnya.

## Struktur Folder Penting

```text
Prak-Pemweb/
│
├── app/
│   ├── Http/
│   │   └── Controllers/
│   │       ├── Auth/
│   │       │   └── LoginController.php
│   │       └── BukuController.php
│   │
│   └── Models/
│       ├── Buku.php
│       ├── Kategori.php
│       └── User.php
│
├── database/
│   ├── migrations/
│   └── seeders/
│
├── resources/
│   └── views/
│       ├── auth/
│       │   └── login.blade.php
│       └── buku/
│
├── routes/
│   └── web.php
│
├── .env.example
├── artisan
├── composer.json
└── README.md
```

## Cara Menjalankan Proyek

### 1. Clone Repository

```bash
git clone https://github.com/username/nama-repository.git
```

Ganti URL dengan alamat repository yang sebenarnya.

### 2. Masuk ke Folder Proyek

```bash
cd Prak-Pemweb
```

### 3. Install Dependensi

```bash
composer install
```

### 4. Konfigurasi Environment

Buat file `.env` berdasarkan `.env.example`, kemudian sesuaikan konfigurasi database:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=praktikum_web
DB_USERNAME=root
DB_PASSWORD=

SESSION_DRIVER=file
```

Sesuaikan username dan password MySQL dengan konfigurasi komputer masing-masing.

### 5. Generate Application Key

```bash
php artisan key:generate
```

### 6. Buat Database

Buat database MySQL dengan nama:

```sql
CREATE DATABASE praktikum_web;
```

### 7. Jalankan Migration

```bash
php artisan migrate
```

### 8. Masukkan Data Awal

```bash
php artisan db:seed
```

### 9. Buat Akun Pengguna

Jalankan Laravel Tinker:

```bash
php artisan tinker
```

Kemudian masukkan:

```php
use App\Models\User;
use Illuminate\Support\Facades\Hash;

User::updateOrCreate(
    ['email' => 'mahasiswa@example.test'],
    [
        'name' => 'Mahasiswa Praktikum',
        'password' => Hash::make('LatihanWeb123!')
    ]
);
```

Keluar dari Tinker:

```php
exit
```

Akun tersebut merupakan akun pengujian lokal. Untuk penggunaan sebenarnya, gunakan kredensial pribadi yang aman.

### 10. Jalankan Server

```bash
php artisan serve
```

Buka aplikasi melalui browser:

```text
http://127.0.0.1:8000/login
```

Login menggunakan akun yang sudah dibuat untuk mengakses halaman pengelolaan buku.

## Pengujian Aplikasi

Pengujian dilakukan secara bertahap berdasarkan materi praktikum minggu ke-9 sampai minggu ke-11.

**Minggu 9 – MVC**
1. Membuka halaman daftar buku.
2. Melakukan pencarian berdasarkan judul buku.
3. Membuka halaman detail buku.
4. Menguji halaman ketika kode buku tidak ditemukan.

**Minggu 10 – Database dan CRUD**
1. Memastikan migration berhasil dijalankan.
2. Memastikan data awal berhasil dimasukkan melalui Seeder.
3. Menampilkan data buku beserta kategorinya.
4. Menambahkan data buku baru.
5. Mengubah informasi buku.
6. Menguji validasi kode buku duplikat.
7. Menghapus data buku.

**Minggu 11 – Autentikasi dan Middleware**
1. Membuka halaman buku tanpa login.
2. Melakukan login menggunakan password yang salah.
3. Melakukan login dengan kredensial yang benar.
4. Memastikan nama pengguna tampil setelah login.
5. Melakukan logout.
6. Mencoba membuka halaman buku setelah logout.
7. Menguji permintaan POST tanpa token CSRF.

## Riwayat Pengembangan

Pengembangan aplikasi dilakukan secara bertahap:

| Minggu | Materi | Pengembangan |
|---|---|---|
| 9 | Laravel dan MVC | Model, View, Controller, Route, dan pencarian buku |
| 10 | Migration, Eloquent, dan CRUD | Database, relasi tabel, Seeder, dan pengelolaan buku |
| 11 | Session dan Middleware | Login, logout, session, autentikasi, dan pembatasan akses |

## Penutup

Proyek ini dibuat sebagai bagian dari pengerjaan Praktikum Pemrograman Web minggu ke-9 sampai minggu ke-11. Melalui pengembangan bertahap, saya mempelajari cara membangun aplikasi menggunakan pola MVC, menghubungkan aplikasi dengan database, mengelola data menggunakan Eloquent, serta menerapkan autentikasi dan pembatasan akses menggunakan fitur Laravel.

---

**Praktikum Pemrograman Web**  
**Minggu 9–11 | Laravel, MVC, Database, CRUD, Authentication, dan Middleware**
