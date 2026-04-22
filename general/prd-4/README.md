# PRD

> **Nama Produk:** Sistem Manajemen Jimpitan Lebaran (SiJimbar - *Opsional*)
**Platform:** Aplikasi Web (Responsive)
**Tech Stack Utama:** Laravel (Back

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Product Requirements Document (PRD)
**Nama Produk:** Sistem Manajemen Jimpitan Lebaran (SiJimbar - *Opsional*)
**Platform:** Aplikasi Web (Responsive)
**Tech Stack Utama:** Laravel (Backend/Framework), MySQL/PostgreSQL (Database), Tailwind CSS + Alpine.js/Livewire (Frontend)

## 1. Latar Belakang & Tujuan
**Masalah:** Pencatatan jimpitan lebaran (sembako, snack, minuman) saat ini dilakukan secara manual menggunakan buku. Hal ini rentan terhadap kesalahan perhitungan, kehilangan data, dan menyulitkan proses rekapitulasi di akhir periode (terutama untuk 45 kali angsuran).

**Tujuan:**
* Mendigitalkan proses pencatatan master katalog barang dan peserta.
* Mengotomatiskan perhitungan total angsuran per minggu dan total nilai jimpitan.
* Mempermudah *tracking* (pelacakan) pembayaran angsuran setiap peserta per minggunya.
* Menghasilkan laporan rekapitulasi barang (kulakan) secara instan di akhir periode.

## 2. Pengguna Sasaran (User Persona)
Saat ini, aplikasi dirancang untuk *Single Role*:
* **Admin / Pengurus (Misal: Mbk Izzah):** Bertanggung jawab mendaftarkan barang, mendata warga, dan mencatat setoran uang setiap minggunya. Membutuhkan antarmuka yang cepat untuk input data massal.

## 3. Fitur Utama (Minimum Viable Product - MVP)

### 3.1. Modul Autentikasi
* **Login:** Akses aman menggunakan Email/Username dan Password.
* **Logout & Sesi:** Manajemen sesi standar Laravel.

### 3.2. Modul Master Katalog (Barang & Paket)
* **CRUD Kategori Barang:** Admin dapat mengelola kategori (Sembako, Snack, Minuman, Paket Spesial).
* **CRUD Barang Reguler:**
    * Input Nama Barang.
    * Input Satuan/Kuantitas (Kg, Dos, Blek, dll).
    * Input Harga Angsuran per Minggu.
* **CRUD Paket Spesial:**
    * Fitur untuk membuat 'Paket' yang merelasikan beberapa barang reguler sekaligus (Misal: Paket 1 berisi Beras, Bimoli, dll).
    * Input field khusus untuk 'Bonus' paket (Misal: Handuk Tebal, Panci).

### 3.3. Modul Manajemen Peserta
* **CRUD Peserta:** Mendaftarkan warga yang me

*[truncated — see source for full prompt]*