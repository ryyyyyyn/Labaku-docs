Software Requirement Specification (SRS)
Produk: Kalkulator HPP + Laba Otomatis

Versi Dokumen: 1.0
Tanggal Efektif: 7 November 2025
Disusun oleh: Ryan — PopOfficialStore
Platform: Mobile (Flutter – Android & iOS)

1. Executive Summary

Kalkulator HPP + Laba Otomatis adalah aplikasi mobile ringan dan akurat yang membantu pelaku UMKM serta penjual online menghitung Harga Pokok Penjualan (HPP) dan laba bersih secara otomatis.
Berbasis offline-first, aplikasi ini menyederhanakan pengambilan keputusan harga jual tanpa perlu keahlian akuntansi.

Tagline:

“Hitung HPP & Laba dalam 10 Detik — Tanpa Ribet, Tanpa Salah Hitung.”

2.  Tujuan Produk
2.1. Primary Objective

Mempermudah proses penetapan harga produk berbasis input sederhana.

Mengurangi kesalahan margin dan potensi kerugian akibat salah hitung.

Meningkatkan efisiensi dan akurasi keputusan harga jual.

2.2. Success Criteria (SMART)
Kriteria	Deskripsi	Status
Specific	Pengguna dapat menghitung HPP + Laba dalam 1 halaman utama	✅
Measurable	Waktu rata-rata perhitungan ≤ 15 detik	✅
Achievable	Tidak membutuhkan koneksi internet atau akun	✅
Relevant	Menjawab kebutuhan nyata pelaku UMKM & seller online	✅
Time-bound	Peluncuran versi 1.0 dalam 60 hari	✅
3.  Target Pengguna (User Personas)
Nama	Profil	Kebutuhan
Pak Budi	Penjual UMKM (Shopee: kuliner/kerajinan), usia 40an	Hitung ongkir, packing, fee marketplace, tentukan harga jual menguntungkan
Siska	Dropshipper pemula (mahasiswa)	Edukasi biaya & margin otomatis
Andi	Reseller elektronik	Hitung biaya variabel (admin, garansi, retur) dan simpan riwayat produk
Rina	Mahasiswa bisnis	Visualisasi rumus HPP untuk pembelajaran praktis
4.  Value Proposition
Masalah	Solusi
❌ Perhitungan manual rawan error	✅ Hitung otomatis, akurat dengan validasi formula
❌ Tidak paham biaya tersembunyi	✅ Input terstruktur (ongkir, admin %, packing)
❌ Tidak ada alat praktis untuk UMKM	✅ Aplikasi ringan, tanpa login, offline-first
❌ Tidak bisa menyimpan hasil	✅ Riwayat lokal + edit & review kapan saja

USP Utama:

Satu-satunya aplikasi di Indonesia yang fokus penuh pada perhitungan HPP dan laba untuk seller online.

5.  Fitur Utama & Spesifikasi
5.1.  Kalkulator HPP (Core Feature)

Input Field:

Harga Produk (Rp, min 1)

Ongkir (Rp, ≥ 0)

Biaya Admin (% atau Rp, min 0, max 50%)

Biaya Packing (Rp, ≥ 0)

Margin Keuntungan (% min 0, max 200%)

Output:

Total HPP = Harga_Produk + Ongkir + Biaya_Packing + (Harga_Produk × Biaya_Admin / 100)

Harga Jual Ideal = Total_HPP × (1 + Margin / 100)

Laba Bersih = Harga_Jual – Total_HPP

UX Enhancement:

Warna hasil:

🟢 Laba > 0

🟡 Laba = 0

🔴 Laba < 0 → Warning 

Animasi hasil: fade-in + slide-up

5.2.  Riwayat Perhitungan

Penyimpanan lokal (Hive DB), tanpa internet.

Struktur data JSON:

{
  "id": "hpp_20251107_001",
  "timestamp": "2025-11-07T14:30:00Z",
  "product_name": "Masker Kain Premium",
  "harga_produk": 15000,
  "ongkir": 9000,
  "biaya_admin": 5,
  "biaya_packing": 2000,
  "margin": 30,
  "total_hpp": 27250,
  "harga_jual": 35425,
  "laba_bersih": 8175
}


UI:

List card: nama produk, harga jual, laba, tanggal

Aksi:  Hapus |  Detail

5.3.  Detail Perhitungan

Tampilkan semua input & output (editable)

Tombol:

 Edit & Hitung Ulang

 Simpan ke Riwayat

 Bagikan Hasil (V1.1)

5.4.  Onboarding Flow

Ilustrasi masalah pricing

Demo UI kalkulator

Riwayat & tema gelap

Fitur:

Skip button

“Mulai Sekarang” → ke halaman kalkulator

Tampil sekali (SharedPreferences flag)

5.5.  Pengaturan (Settings)

Tema: Light / Dark / Auto

Warna Utama: Oranye (default), Biru, Hijau, Ungu

Hapus Semua Riwayat: konfirmasi modal

Versi Aplikasi: v1.0.0

Rate App: tautan Play Store/App Store

5.6.  Tentang Aplikasi

Deskripsi:

“Aplikasi open-source ringan untuk membantu UMKM dan seller online menentukan harga jual ideal — akurat, cepat, dan tanpa iklan.”


GitHub: github.com/ryyyyyyn/ShoplabApp

6.  User Flow (End-to-End)
graph TD
  A[Splash Screen (2s)] --> B{Pertama kali buka?}
  B -->|Ya| C[Onboarding 3 Slide]
  B -->|Tidak| D[Kalkulator HPP]
  C --> D
  D --> E[Isi form perhitungan]
  E --> F[Hitung HPP]
  F --> G{Hasil tampil}
  G --> H1[Simpan ke Riwayat]
  G --> H2[Reset Form]
  G --> H3[Lihat Detail]
  H1 --> I[Riwayat]
  H3 --> J[Detail Perhitungan]
  J --> K1[Edit & Hitung Ulang]
  J --> K2[Bagikan (v1.1)]
  D & I & J --> L[Menu Sidebar: Pengaturan & Tentang]

7.  UI/UX Requirements
7.1. Design System

Warna Primer: #FF6F00

Warna Sekunder: #F5F5F5 / #2D2D2D

Font: Poppins (Headline), Inter (Body)

Ikon: Material Icons / Fluent UI

Grid: 8px baseline

Elevation: Card = 2, shadow lembut

7.2. UX Principles

Tombol utama di bawah (one-hand use)

Otomatis format angka Rupiah

Validasi input non-numeric

Animasi & toast feedback

Aksesibilitas tinggi (kontras & font ≥ 12pt)

8. ⚙️ Spesifikasi Teknis
Komponen	Spesifikasi
Framework	Flutter 3.24+
Bahasa	Dart (Null Safety)
State Management	Riverpod 2.5+
Database Lokal	Hive (opsional enkripsi)
Storage	SharedPreferences
UI Toolkit	flutter_screenutil, go_router
Formatting	intl (Rupiah formatter)
Testing	Unit, Widget, Integration test
Target Build	Android (min SDK 21), iOS (min 13.0)
Ukuran Target	≤ 8 MB (APK), ≤ 12 MB (IPA)
9.  Keamanan & Privasi

100% offline, tanpa koneksi server.

Data tidak dienkripsi (V1.0) tapi aman karena hanya menyimpan angka & nama produk.

Taat GDPR / PP No. 27/2020:

Privacy Policy tersedia

Opsi hapus semua data

Tidak ada tracking/iklan

V1.2: Jika cloud sync ditambahkan, akan diterapkan enkripsi end-to-end.

10.  Roadmap Pengembangan
Versi	Fitur	Target	Prioritas
v1.0	Kalkulator, Riwayat Lokal, Onboarding, Settings	Nov–Des 2025	🔴 High
v1.1	Ekspor PDF/CSV, Bagikan hasil, Notifikasi margin rendah	Jan 2026	🟠 Medium
v1.2	Sinkronisasi cloud, Backup/restore	Feb 2026	🟢 Low
v2.0	AI Pricing (analisis kompetitor & rekomendasi margin)	Q2 2026	🟢 Future
11.  KPI & Metrik Keberhasilan
Metrik	Target	Alat
Unduhan	≥ 1.000	Play Store / App Store
Retensi Mingguan	≥ 80%	Local event / Mixpanel
Durasi Rata-rata	≤ 3 menit	Session analytics
Konversi Simpan	≥ 60%	Event calculation_saved
Rating	≥ 4.5/5	Review store
Crash Rate	≤ 0.5%	Firebase Crashlytics
12.  Tim & Peran
Peran	Nama	Tanggung Jawab
Product Owner	Ryan - niam	PRD, UAT, rilis
UI/UX Designer	Stitch.ai + Manual Review	Wireframe & Mockup (Figma)
Flutter Developer	Ryan - niam / Freelance	Coding & Build
QA Tester	Komunitas Beta (5–10 UMKM)	Pengujian & feedback
Legal	Ryan	Draft Privacy Policy & ToS
13.  Deliverables
Item	Format	Keterangan
PRD	PDF / Docs	Dokumen ini
Desain UI	Figma	High-fidelity + prototype
Source Code	GitHub Repo	Branch: main/dev/release
Aset Grafis	ZIP	Logo, ikon, splash
Build Beta	APK + Release Notes	Pengujian internal
Dokumentasi Teknis	README.md	Setup, build, test
14. Kesimpulan & Next Steps

Kalkulator HPP + Laba Otomatis bukan sekadar kalkulator, melainkan alat bantu bisnis cerdas bagi UMKM Indonesia.

Prinsip utama:
 Cepat — hitung dalam 10 detik
 Akurat — formula valid
 Bebas — tanpa login, tanpa iklan, 100% offline

Next Steps:

Finalisasi desain Figma (3 hari)

Kickoff development (durasi 60 hari)

Beta test (20 seller UMKM)

Rilis publik (7 Januari 2026)
