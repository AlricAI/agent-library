# TARGET

> ## Minggu 1 — Setup & Foundation

### Setup Project
- [x] Setup Laravel project & konfigurasi environment
- [x] Konfigurasi database (MySQL/PostgreSQL

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Target Pengembangan - SiJimbar

## Minggu 1 — Setup & Foundation

### Setup Project
- [x] Setup Laravel project & konfigurasi environment
- [x] Konfigurasi database (MySQL/PostgreSQL)
- [x] Setup Livewire & Flux UI
- [x] Setup autentikasi (Fortify)

### Database Migrations & Models
- [x] Migration `categories`
- [x] Migration `items`
- [x] Migration `item_package` (pivot)
- [x] Migration `participants`
- [x] Migration `orders`
- [x] Migration `order_items`
- [x] Migration `installments`
- [x] Migration `savings`
- [x] Migration `saving_transactions`
- [x] Model & relasi `Category`
- [x] Model & relasi `Item`
- [x] Model & relasi `Participant`
- [x] Model & relasi `Order`
- [x] Model & relasi `OrderItem`
- [x] Model & relasi `Installment`
- [x] Model & relasi `Saving`
- [x] Model & relasi `SavingTransaction`

### Modul Autentikasi
- [x] Halaman Login
- [x] Logout & manajemen sesi
- [x] Proteksi route (middleware auth)

### Modul Peserta
- [x] Halaman daftar peserta
- [x] Form tambah peserta (Nama, No HP, Alamat, Catatan)
- [x] Form edit peserta
- [x] Fitur hapus peserta
- [x] Validasi data peserta

---

## Minggu 2 — Katalog & Order

### Modul Kategori
- [x] Halaman daftar kategori
- [x] Form tambah & edit kategori
- [x] Fitur hapus kategori

### Modul Barang
- [x] Halaman daftar barang (dengan filter kategori)
- [x] Form tambah barang reguler (Nama, Satuan, Harga/Minggu, Kategori)
- [x] Form tambah paket spesial (relasi ke barang reguler + field bonus)
- [x] Form edit barang/paket
- [x] Fitur hapus barang/paket

### Modul Pendaftaran Keranjang (Order)
- [x] Halaman pilih peserta & tambah ke keranjang
- [x] Form pilih barang/paket untuk peserta
- [x] Kalkulasi otomatis total angsuran per minggu
- [x] Form edit order peserta
- [x] Fitur hapus order

---

## Minggu 3 — Pelacakan Angsuran

### Modul Angsuran
- [x] Tampilan grid peserta vs Minggu 1–45 (tabel Excel-like)
- [x] Fitur centang/input nominal setoran per minggu (Livewire, tanpa reload)
- [x] Kalkulasi otomat

*[truncated — see source for full prompt]*