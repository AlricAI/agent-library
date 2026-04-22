# TARGETV2

> ---

## Sprint 1 — Rekap per Peserta (Cetak Slip PDF)

### Database & Model
- [x] Tidak ada migration baru (memanfaatkan relasi yang sudah ada)

### B

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Target Pengembangan V2 — SiJimbar Fitur Warga

---

## Sprint 1 — Rekap per Peserta (Cetak Slip PDF)

### Database & Model
- [x] Tidak ada migration baru (memanfaatkan relasi yang sudah ada)

### Backend
- [x] Route `GET /participants/{participant}/slip` — pilih order/periode jika lebih dari satu
- [x] Route `GET /participants/{participant}/slip/{order}` — generate PDF slip
- [x] Controller `SlipExportController` dengan method `show()` dan `download()`
- [x] Blade view `resources/views/exports/slip.blade.php` (layout PDF, A5)
- [x] Logic: hitung total yang sudah terbayar, sisa tagihan, progress angsuran

### UI Admin
- [x] Tombol "Cetak Slip" di halaman daftar peserta (kolom aksi, ikon `printer`)
- [x] Tombol "Cetak Slip" di halaman detail angsuran peserta
- [x] Jika peserta memiliki >1 order aktif: tampilkan dropdown pilih periode sebelum download

### Testing
- [x] Feature test: PDF slip dapat diunduh oleh admin
- [x] Feature test: route slip mengembalikan redirect untuk guest
- [x] Feature test: slip berisi data peserta yang benar

---

## Sprint 2 — Dashboard Warga (Token-Based Access)

### Database & Model
- [x] Migration `create_participant_tokens_table` (`id`, `participant_id`, `token`, `expires_at`, `timestamps`)
- [x] Index unique pada kolom `token`
- [x] Model `ParticipantToken` dengan relasi `belongsTo(Participant::class)`
- [x] Relasi `hasOne(ParticipantToken::class)` di model `Participant`
- [x] Cast `expires_at` ke `datetime`

### Backend — Token Management (Admin)
- [x] `generateToken()` Livewire method — hapus token lama, buat token baru (`Str::random(64)`)
- [x] `revokeToken()` Livewire method — hapus token aktif peserta
- [x] Validasi durasi: hanya menerima nilai `1`, `7`, `30`

### Backend — Dashboard Publik
- [x] Route `GET /w/{token}` ke `WargaDashboardController@show` (tanpa middleware `auth`)
- [x] Controller: temukan token, validasi tidak kedaluwarsa, load relasi
- [x] Jika token expired → return view `pages.warga.expired`
- [x] Masking nom

*[truncated — see source for full prompt]*