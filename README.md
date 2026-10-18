# Sistem Manajemen Inventaris (CRUD Inventory)

Aplikasi manajemen inventaris berbasis web dengan PHP dan MySQL, digunakan untuk memenuhi Ujian Akhir Semester (UAS) mata kuliah Rekayasa Perangkat Lunak semester 4. Sistem ini mengelola produk, kategori, grup pengguna, penjualan, dan media (foto produk), dengan tiga level akses pengguna.

## Fitur

- Login dengan tiga level pengguna: Admin, Special User, dan User (Employee)
- Dashboard admin berisi ringkasan produk, kategori, penjualan, produk terbaru, dan penjualan terbaru
- Kelola produk: tambah, ubah, hapus, lengkap dengan foto produk, harga beli, dan harga jual
- Kelola kategori produk dan grup pengguna (level akses)
- Kelola pengguna: tambah pengguna, ubah akun, ubah password, profil, dan foto pengguna
- Pencatatan penjualan (sales) dan laporan penjualan harian serta bulanan
- Laporan penjualan berdasarkan rentang tanggal (sales report)
- Manajemen media: unggah dan hapus berkas gambar produk dan pengguna
- Halaman daftar pengguna aktif dan pencatatan waktu login terakhir

## Teknologi

- PHP (disarankan PHP 5.6 sampai 7.x untuk kode lama ini) dengan ekstensi MySQLi
- MySQL / MariaDB (nama basis data: `inventory_system`)
- HTML, CSS, JavaScript, dan jQuery
- Composer tidak diperlukan, seluruh pustaka disertakan di folder `includes/` dan `libs/`

## Struktur Proyek

```
crud-inventory-rpl-smt4/
├── DATABASE FILE/
│   └── inventory_system.sql     # Dump basis data
├── includes/
│   ├── config.php               # Konstanta koneksi basis data
│   ├── database.php             # Kelas basis data (MySQLDatabase)
│   ├── functions.php            # Fungsi bantu umum
│   ├── sql.php                  # Seluruh fungsi query (produk, user, sales)
│   ├── session.php              # Kelas session dan pesan flash
│   ├── upload.php               # Kelas upload berkas (validasi gambar)
│   └── load.php                 # Pemuat seluruh includes
├── layouts/                     # Header, footer, dan menu per level user
├── libs/                        # Pustaka pendukung
├── uploads/                     # Berkas gambar hasil upload
├── index.php                    # Halaman login
├── auth.php, auth_v2.php        # Proses autentikasi
├── admin.php, home.php          # Dashboard
├── product.php, add_product.php, edit_product.php, delete_product.php
├── categorie.php, add_group.php, group.php, users.php, add_user.php, edit_user.php
├── sales.php, add_sale.php, edit_sale.php, delete_sale.php
├── daily_sales.php, monthly_sales.php, sales_report.php
├── media.php, profile.php, edit_account.php, change_password.php
└── logout.php
```

## Cara Menjalankan

Prasyarat: server lokal PHP dan MySQL (XAMPP/Laragon).

1. Clone repositori ini ke folder web server (misalnya `htdocs`).
2. Buat basis data bernama `inventory_system`, lalu impor `DATABASE FILE/inventory_system.sql`:

   ```bash
   mysql -u root -p inventory_system < "DATABASE FILE/inventory_system.sql"
   ```

3. Sesuaikan `includes/config.php` bila perlu (bawaan: `DB_HOST=localhost`, `DB_USER=root`, `DB_PASS` kosong, `DB_NAME=inventory_system`).
4. Jalankan Apache dan MySQL, lalu buka `http://localhost/crud-inventory-rpl-smt4/` dan masuk dengan akun awal yang tercantum pada berkas `01 LOGIN DETAILS & PROJECT INFO.txt` dan data awal SQL.

## Catatan

- Segera ganti password semua akun awal setelah instalasi, dan hapus berkas berisi detail login dari server produksi.
- Basis kode ini berasal dari proyek contoh sistem inventaris PHP (karya Siamon Hasan) yang diadaptasi untuk keperluan UAS.
