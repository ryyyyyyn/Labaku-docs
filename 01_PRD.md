Product Requirement Document (PRD)
Nama Produk

Kalkulator HPP + Laba Otomatis

Platform: Mobile (Flutter – Android & iOS)
Owner: Ryan (221240001281)
System Analyst: Niam (221240001241)

Tujuan Utama

Aplikasi ini membantu penjual online, reseller, dan pelaku UMKM menghitung Harga Pokok Penjualan (HPP) dan laba bersih secara otomatis, cepat, dan akurat tanpa memerlukan rumus rumit.

Tujuan Produk

Aplikasi ini bertujuan untuk mempermudah pengguna dalam menentukan harga jual ideal hanya dengan beberapa input sederhana:

Input:

Harga produk

Ongkir

Biaya admin (%)

Biaya packing

Margin keuntungan (%)

Output otomatis:

Total HPP

Harga jual ideal

Estimasi laba bersih

Formula Dasar:

Total_HPP = Harga_Produk + Ongkir + Biaya_Packing + (Harga_Produk × Biaya_Admin / 100)
Harga_Jual = Total_HPP + (Total_HPP × Margin / 100)
Laba_Bersih = Harga_Jual - Total_HPP

Target Pengguna
Segmen	Deskripsi
UMKM	Penjual kecil di Shopee, Tokopedia, atau Tiktok Shop
Dropshipper / Reseller	Menentukan harga jual dari supplier
Online Seller Pemula	Baru belajar cara hitung laba
Pelajar & Mahasiswa	Belajar konsep dasar HPP & margin
Value Proposition
Masalah Pengguna	Solusi Aplikasi
Bingung menentukan harga jual	Perhitungan otomatis dan akurat
Salah hitung manual	Rumus konsisten dan tepat
Tidak ada alat sederhana	UI minimalis, ringan, dan offline
Ingin simpan hasil	Riwayat otomatis dan ekspor data
Fitur Utama
1. Kalkulator HPP (Fitur Inti)

Input: harga produk, ongkir, admin, packing, margin

Output: Total HPP, harga jual, laba bersih

Tombol “Hitung” dan “Simpan Hasil”

2. Riwayat Perhitungan

Menyimpan hasil perhitungan (tanggal & nama produk)

Dapat dilihat, diedit, dan dihapus kapan saja

3. Detail Perhitungan

Menampilkan data lengkap dari setiap perhitungan

Tombol edit & simpan ulang

4. Onboarding Page (3 Slide)

Edukasi singkat fungsi aplikasi

Tombol “Mulai Sekarang”

5. Pengaturan (Settings)

Tema terang/gelap

Ganti warna utama

Hapus semua data

Informasi versi aplikasi

6. Tentang Aplikasi

Logo, deskripsi singkat, dan kontak developer

“Dibuat oleh Ryan (PopOfficialStore)”

Fitur Monetisasi (Tanpa Iklan)

Aplikasi menggunakan sistem Freemium Unlock (One-Time Payment),
di mana fitur dasar tersedia gratis, dan fitur lanjutan dapat dibuka dengan pembayaran sekali seumur hidup (one-time purchase).

Versi Gratis

Fokus pada kemudahan penggunaan dan edukasi dasar.

Termasuk:

Kalkulator dasar

Simpan hingga 5 riwayat perhitungan

Tema terang & gelap

Hapus semua data

Gunakan secara offline tanpa batas waktu

Versi Premium (Unlock Sekali Bayar)

Pengguna dapat meng-upgrade ke versi premium dengan pembayaran sekali saja (Rp20.000 – Rp25.000) dan membuka seluruh fitur lanjutan berikut:

Fitur yang Di-Unlock Premium:

Simpan Riwayat Tanpa Batas
Tidak ada batasan jumlah riwayat perhitungan.

Export Hasil ke PDF / Excel

Simpan laporan perhitungan ke file .pdf atau .xlsx.

Cocok untuk laporan keuangan atau rekap penjualan.

Template Biaya Otomatis

Pilihan marketplace dengan biaya admin otomatis:

Shopee (5%)

Tokopedia (6%)

Tiktok Shop (7%)

Custom manual

Ganti Warna Tema Bebas

Pilih warna utama sesuai selera (misal oranye, biru, hijau).

Backup & Restore Lokal (File)

Simpan data riwayat ke file lokal .json / .txt.

Restore ulang saat ganti HP tanpa kehilangan data.

Tidak Ada Batasan Fitur

Semua fitur dapat digunakan penuh.

Tidak ada iklan, limit, atau batasan waktu.

Perbandingan Versi
Fitur	Gratis	Premium
Kalkulator dasar	✅	✅
Simpan riwayat	Maks. 5 data	Tanpa batas
Export ke PDF / Excel	❌	✅
Tema terang / gelap	✅	✅
Ganti warna tema bebas	❌	✅
Template biaya otomatis	❌	✅
Backup & restore lokal	❌	✅
Hapus semua data	✅	✅
Tanpa iklan	✅	✅
Semua fitur tanpa batas	❌	✅
User Flow
Splash → Onboarding → Kalkulator → Hasil → Simpan Riwayat
↓
Riwayat → Detail → Edit / Hapus
↓
Pengaturan / Tentang / Upgrade Premium

Struktur Halaman
Halaman	Komponen Utama	Aksi
Splash	Logo + tagline	Auto ke Onboarding
Onboarding	3 slide edukatif	“Mulai Sekarang”
Kalkulator	Input field + hasil card	Hitung & Simpan
Riwayat	List hasil tersimpan	Detail / Hapus
Detail	Rincian hasil	Edit / Simpan ulang
Pengaturan	Tema, warna, reset data	Ubah preferensi
Tentang	Logo, deskripsi, kontak	Info developer
Premium Unlock	Deskripsi fitur premium	Tombol “Upgrade Sekarang”
UI/UX Requirements

Warna utama: Oranye (#FF6F00)

Font: Poppins / Inter

Ikon: Flat minimalis

Animasi: Transisi lembut antarhalaman

Format angka: Otomatis dalam Rupiah

Tombol: Besar & mudah dijangkau

Mode: 100% offline

Desain: Simple, profesional, dan ringan

Spesifikasi Teknis
Aspek	Spesifikasi
Framework	Flutter 3+
Bahasa	Dart
State Management	Riverpod / Provider
Database Lokal	Hive / SharedPreferences
API	Tidak diperlukan (Offline)
Platform	Android & iOS
Mode Tampilan	Portrait Only
Keamanan & Privasi

Semua data disimpan lokal di perangkat pengguna

Tidak ada login, akun, atau data dikirim ke server

Pengguna dapat menghapus seluruh data kapan saja

Roadmap Versi
Versi	Deskripsi	Status
v1.0	Kalkulator + Riwayat lokal	Rilis awal
v1.1	Export PDF / Excel + Tema Gelap	Premium unlock
v1.2	Template Biaya Otomatis	Premium unlock
v1.3	Backup & Restore Lokal	Premium unlock
v2.0	UI baru + optimasi performa	Update besar
KPI Keberhasilan

≥ 1.000 unduhan dalam 3 bulan

≥ 80% pengguna aktif mingguan

≥ 10% pengguna upgrade ke Premium

Rating aplikasi ≥ 4.5/5 di Play Store

Rata-rata waktu penggunaan < 3 menit

Tim Pengembang
Peran	Nama	NIM
Product Owner	Ryan	221240001281
System Analyst	Niam	221240001241
Flutter Developer	Ryan / Freelance	-
UI/UX Designer	Opsional	-
QA Tester	Opsional	-
Deliverables

Desain UI/UX (Figma)

Source code Flutter (.dart)

Ikon & Logo aplikasi

Dokumen PRD (ini)

File APK Beta (Android)

Kesimpulan

Aplikasi Kalkulator HPP + Laba Otomatis hadir sebagai solusi cepat, sederhana, dan profesional bagi penjual online serta pelaku UMKM.
Dengan pendekatan tanpa iklan dan sistem unlock fitur premium sekali bayar, aplikasi ini menjaga kenyamanan pengguna sambil tetap memiliki potensi penghasilan berkelanjutan.

Fokus utama aplikasi ini adalah kemudahan, efisiensi, dan keakuratan, agar pengguna dapat menentukan harga jual ideal hanya dalam hitungan detik — tanpa rumus, tanpa ribet.

© 2025 Kalkulator HPP + Laba Otomatis — Dikembangkan oleh Ryan & Niam.
Semua hak cipta dilindungi.
