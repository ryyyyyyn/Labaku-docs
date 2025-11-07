# Product Requirement Document (PRD)

##  Nama Produk  
**Kalkulator HPP + Laba Otomatis**

**Platform:** Mobile (Flutter – Android & iOS)  
**Owner:** Ryan (221240001281)  
**System Analyst:** Niam (221240001241)

---

##  Tujuan Utama  
Membantu penjual online dan UMKM menghitung **Harga Pokok Penjualan (HPP)** dan **laba bersih** secara cepat, otomatis, dan akurat tanpa perlu rumus akuntansi.

---

##  Tujuan Produk  
Aplikasi ini menyederhanakan proses menghitung harga jual ideal. Pengguna cukup memasukkan:
- Harga produk  
- Ongkir  
- Biaya admin (%)  
- Biaya packing  
- Margin keuntungan (%)  

Output otomatis:
- Total HPP  
- Harga jual ideal  
- Estimasi laba bersih  

**Formula:**  
Total_HPP = Harga_Produk + Ongkir + Biaya_Packing + (Harga_Produk × Biaya_Admin / 100)
Harga_Jual = Total_HPP + (Total_HPP × Margin / 100)
Laba_Bersih = Harga_Jual - Total_HPP

yaml
Copy code

---

##  Target Pengguna

| Segmen | Deskripsi |
|---------|------------|
| UMKM | Penjual kecil di Shopee, Tokopedia, atau offline store |
| Dropshipper & Reseller | Menentukan harga jual dari supplier |
| Online Seller Pemula | Belum memahami cara menghitung laba |
| Pelajar & Mahasiswa | Untuk pembelajaran konsep HPP dan laba |

---

##  Value Proposition

| Masalah Pengguna | Solusi Aplikasi |
|------------------|----------------|
| Bingung menentukan harga jual | Perhitungan otomatis & instan |
| Salah hitung manual | Formula akurat dan konsisten |
| Tidak ada alat sederhana | UI minimalis, cepat, dan offline |

---

## Fitur Utama

1. **Kalkulator HPP (Fitur Utama)**  
   - Input: Harga produk, ongkir, biaya admin, packing, margin  
   - Output: Total HPP, harga jual, laba bersih  

2. **Riwayat Perhitungan**  
   - Simpan hasil (tanggal, produk, nilai)  
   - Lihat dan hapus riwayat  

3. **Detail Perhitungan**  
   - Tampilkan input & hasil  
   - Tombol edit & simpan ulang  

4. **Onboarding Page**  
   - 3 slide edukatif + tombol “Mulai Sekarang”  

5. **Pengaturan Aplikasi**  
   - Tema terang/gelap  
   - Ganti warna utama  
   - Info versi & pembuat  

6. **Tentang Aplikasi**  
   - Logo, deskripsi singkat  
   - Kontak: “Dibuat oleh Ryan (PopOfficialStore)”

---

##  User Flow

Splash → Onboarding → Kalkulator HPP → Hasil → Simpan Riwayat
↓
Riwayat → Detail → Edit / Hapus
↓
Pengaturan / Tentang

yaml
Copy code

---

##  Struktur Halaman

| Halaman | Komponen | Aksi Utama |
|----------|-----------|------------|
| Splash | Logo + tagline | Auto ke onboarding |
| Onboarding | Slide edukatif | Tombol "Mulai Sekarang" |
| Kalkulator | Input + hasil card | Hitung & simpan |
| Riwayat | List card hasil | Detail & hapus |
| Detail | Data lengkap | Edit / Simpan |
| Pengaturan | Tema, warna, info | Ubah preferensi |
| Tentang | Logo, deskripsi, kontak | Info developer |

---

## UI/UX Requirements

- Warna utama: **Oranye (#FF6F00)**  
- Font: **Poppins / Inter**  
- Gaya ikon: Flat minimal  
- Fokus satu halaman utama  
- Tombol besar & mudah dijangkau  
- Format angka otomatis ke Rupiah  
- Animasi transisi lembut  
- Tidak perlu login  

---

##  Spesifikasi Teknis

| Aspek | Spesifikasi |
|--------|--------------|
| Framework | Flutter 3+ |
| Bahasa | Dart |
| State Management | Riverpod / Provider |
| Database Lokal | Hive / SharedPreferences |
| API | Tidak diperlukan (Offline First) |
| Platform | Android & iOS |
| Mode | Portrait (Mobile) |

---

##  Keamanan & Privasi

- Data disimpan **lokal** (tidak dikirim ke server)  
- Tidak ada login / pengumpulan data pribadi  
- Opsi **hapus semua data** di pengaturan  

---

## Roadmap Versi

| Versi | Deskripsi | Status |
|--------|------------|--------|
| v1.0 | Kalkulator + Riwayat lokal | Target awal |
| v1.1 | Tema gelap + Export PDF | Setelah rilis |
| v1.2 | Cloud sync opsional | Fitur lanjutan |
| v2.0 | AI Pricing Analysis | Fase pengembangan lanjut |

---

##  KPI Keberhasilan

- ≥ 1000 unduhan dalam 3 bulan  
- 80% pengguna aktif mingguan  
- Waktu penggunaan rata-rata < 3 menit  
- Rating ≥ 4.5/5 di Play Store  

---

##  Tim Proyek

| Peran | Nama | NIM |
|--------|------|-----|
| Product Owner | Ryan | 221240001281 |
| System Analyst | Niam | 221240001241 |
| Flutter Dev | Ryan / Freelance | - |
| QA Tester | Opsional | - |

---

##  Deliverables

- Desain UI/UX (Figma)  
- Source code Flutter (`.dart`)  
- File ikon & logo  
- Dokumen PRD ini  
- APK versi Beta  

---

##  Kesimpulan

Aplikasi **Kalkulator HPP + Laba Otomatis** dirancang untuk menjadi alat bantu cepat, akurat, dan ringan bagi UMKM dan penjual online. Fokus utama aplikasi ini adalah **efisiensi & kemudahan**, agar pengguna dapat menentukan harga jual ideal hanya dalam beberapa detik — tanpa rumus rumit.

---

> © 2025 Kalkulator HPP + Laba Otomatis — Dikembangkan oleh Ryan & Niam.  
> Semua hak cipta dilindungi.
