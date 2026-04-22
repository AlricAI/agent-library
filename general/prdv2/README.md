# PRDV2

> **Nama Produk:** SiJimbar — Fitur Warga
**Versi:** 2.0
**Tanggal:** April 2026

---

## 1. Latar Belakang & Tujuan

V1 berfokus pada efisiensi kerja *

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Product Requirements Document V2
**Nama Produk:** SiJimbar — Fitur Warga
**Versi:** 2.0
**Tanggal:** April 2026

---

## 1. Latar Belakang & Tujuan

V1 berfokus pada efisiensi kerja **admin/pengurus**. V2 bertujuan memperluas layanan langsung ke **warga/peserta**, sehingga warga dapat memantau status mereka sendiri tanpa harus menghubungi pengurus, dan pengurus dapat mencetak bukti tagihan individual untuk arsip fisik.

---

## 2. Fitur yang Dikembangkan

### 2.1. Rekap per Peserta (Cetak Slip)

**Deskripsi:**
Admin dapat mencetak atau mengunduh slip individual satu peserta dalam format PDF yang berisi ringkasan lengkap jimpitan peserta tersebut untuk satu periode.

**Aktor:** Admin / Pengurus

**Konten Slip:**
- Nama peserta, nomor HP, alamat
- Nama periode (mis. 2025-2026)
- Daftar barang/paket yang diambil beserta qty dan harga angsuran per minggu
- Total angsuran per minggu
- Progress pembayaran: sudah bayar X kali dari 45, sisa Y minggu
- Total nilai order keseluruhan (45 minggu × total/minggu)
- Total yang sudah terbayar
- Sisa tagihan
- Saldo tabungan aktif
- Footer: tanggal cetak, nama pengurus

**Trigger Aksi:**
- Tombol "Cetak Slip" di halaman detail angsuran peserta (`/installments?participant=X`)
- Tombol "Cetak Slip" di halaman daftar peserta (kolom aksi)

**Filter Periode:**
- Slip dicetak berdasarkan periode yang sedang aktif/dipilih
- Jika peserta memiliki lebih dari satu order di periode berbeda, admin memilih periode mana yang dicetak

**Output:** PDF yang dapat langsung dicetak atau diunduh, format A5 atau A4 (bisa dua slip per lembar A4)

---

### 2.2. Dashboard Warga (Akses Berbasis Token)

**Deskripsi:**
Admin menghasilkan sebuah URL unik bertanda waktu (*expiring link*) yang dapat dibagikan ke peserta (mis. via WhatsApp). Peserta membuka URL tersebut tanpa perlu login, dan dapat melihat data pribadi mereka secara *read-only*.

**Aktor:**
- Admin (generate & share URL)
- Warga/Peserta (akses URL)

#### 2.2.1. Manajemen Token (Sisi Admin)

**G

*[truncated — see source for full prompt]*