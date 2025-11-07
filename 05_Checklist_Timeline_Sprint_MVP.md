#  CHECKLIST & TIMELINE SPRINT — MVP DEVELOPMENT
### Proyek: Kalkulator HPP + Laba Otomatis
**Versi Dokumen:** 1.0  
**Tanggal:** November 2025  
**Owner / Developer:** Ryan (221240001281)  
**System Analyst:** Niam (221240001241)  
**Metode:** Agile Scrum (2-Week Sprint)  
**Durasi MVP:** 8 Minggu (4 Sprint)  

---

##  1. Tujuan MVP
Membangun versi **fungsional pertama (MVP)** dari aplikasi **Kalkulator HPP + Laba Otomatis** yang mampu:
- Melakukan perhitungan **HPP, harga jual, dan laba bersih** secara instan.
- Menyimpan hasil perhitungan ke **riwayat lokal**.
- Memberikan pengalaman **100% offline** dengan UI sederhana dan cepat.

---

##  2. Timeline Sprint Overview

| Sprint | Periode | Fokus Utama | Status |
|--------|----------|-------------|--------|
| **Sprint 1** | 7–20 Nov 2025 | Setup Proyek, UI Dasar, Kalkulator HPP | 🟡 In Progress |
| **Sprint 2** | 21 Nov – 4 Des 2025 | Fungsi Simpan Riwayat, Detail & Validasi | ⚪ Planned |
| **Sprint 3** | 5–18 Des 2025 | Onboarding, Pengaturan Tema, About Page | ⚪ Planned |
| **Sprint 4** | 19 Des – 2 Jan 2026 | Testing, Optimasi, Build Beta & Release | ⚪ Planned |

---

##  3. Sprint 1 — Setup & Core Calculator (7–20 Nov 2025)
**Tujuan:** Menyelesaikan fondasi aplikasi dan fitur utama kalkulasi HPP.

###  Task Breakdown
| ID | Task | Detail | Status |
|----|------|---------|--------|
| S1-01 | Setup Flutter Project | Inisialisasi proyek + konfigurasi folder | ✅ Done |
| S1-02 | Implementasi Struktur Folder MVC | `core/`, `screens/`, `models/`, `widgets/` | ✅ Done |
| S1-03 | Buat Model Data `CalculationHistory` | Struktur sesuai ERD | ✅ Done |
| S1-04 | Buat Halaman Kalkulator (UI) | Input harga, ongkir, admin, packing, margin | 🟡 In Progress |
| S1-05 | Validasi Input (non-numeric block) | Menggunakan `TextFormField` & formatter | 🟡 In Progress |
| S1-06 | Hitung Otomatis HPP & Laba | Implementasi logika + preview real-time | ⚪ Planned |
| S1-07 | Format Rupiah otomatis | `intl` package (locale: id) | ⚪ Planned |
| S1-08 | Animasi hasil (fade & slide) | UX enhancement hasil kalkulasi | ⚪ Planned |
| S1-09 | Uji Perhitungan & Validasi Formula | Unit test math logic | ⚪ Planned |

###  Deliverables Sprint 1
- UI kalkulator lengkap (input + hasil)
- Perhitungan dasar berfungsi
- File model & data class siap

---

##  4. Sprint 2 — Riwayat & Detail Perhitungan (21 Nov – 4 Des 2025)
**Tujuan:** Menyimpan hasil perhitungan ke database lokal dan menampilkan riwayat.

###  Task Breakdown
| ID | Task | Detail | Status |
|----|------|---------|--------|
| S2-01 | Setup Hive Database | Implementasi storage lokal | ⚪ Planned |
| S2-02 | CRUD Riwayat Perhitungan | Simpan, tampilkan, hapus | ⚪ Planned |
| S2-03 | Halaman Riwayat (List Card UI) | Card berisi produk, harga jual, laba | ⚪ Planned |
| S2-04 | Detail Riwayat | Breakdown input dan hasil | ⚪ Planned |
| S2-05 | Tombol “Hitung Ulang” (Prefill Form) | Prefill ke halaman kalkulator | ⚪ Planned |
| S2-06 | Dialog Konfirmasi Hapus | Modal konfirmasi data | ⚪ Planned |
| S2-07 | Test Hive Storage | Write + read + delete | ⚪ Planned |

###  Deliverables Sprint 2
- Fitur riwayat lokal berfungsi penuh  
- Detail view kalkulasi dengan tombol edit  
- Validasi penyimpanan & penghapusan data  

---

##  5. Sprint 3 — Onboarding & Settings (5–18 Des 2025)
**Tujuan:** Membuat pengalaman onboarding dan pengaturan tampilan pengguna.

### 🔧 Task Breakdown
| ID | Task | Detail | Status |
|----|------|---------|--------|
| S3-01 | Onboarding Screen (3 Slide) | Slide intro + tombol “Mulai Sekarang” | ⚪ Planned |
| S3-02 | SharedPreferences Flag | Menyimpan status onboarding selesai | ⚪ Planned |
| S3-03 | Tema Gelap & Terang | Toggle di halaman pengaturan | ⚪ Planned |
| S3-04 | Ganti Warna Utama (Custom Brand) | Pilihan warna: oranye, biru, hijau, ungu | ⚪ Planned |
| S3-05 | Reset Riwayat | Hapus semua data Hive | ⚪ Planned |
| S3-06 | Tentang Aplikasi | Logo, deskripsi, kontak, versi | ⚪ Planned |

###  Deliverables Sprint 3
- Onboarding fungsional  
- Tema dinamis + personalisasi warna  
- Halaman About & Settings lengkap  

---

##  6. Sprint 4 — Testing & Release (19 Des 2025 – 2 Jan 2026)
**Tujuan:** Menyelesaikan pengujian, optimasi performa, dan menyiapkan rilis beta publik.

### 🔧 Task Breakdown
| ID | Task | Detail | Status |
|----|------|---------|--------|
| S4-01 | Unit Testing | Kalkulasi HPP, validasi input | ⚪ Planned |
| S4-02 | Widget Testing | UI interaksi tombol & form | ⚪ Planned |
| S4-03 | Integration Testing | Simulasi end-to-end | ⚪ Planned |
| S4-04 | Optimize Build Size | Target < 8MB APK | ⚪ Planned |
| S4-05 | Generate App Icon & Splash | Branding final | ⚪ Planned |
| S4-06 | Build APK (Beta Release) | Internal test group 10 UMKM | ⚪ Planned |
| S4-07 | Create Release Notes | ringkasan fitur v1.0 | ⚪ Planned |
| S4-08 | Publish ke Play Store (Closed Beta) | Review & deployment | ⚪ Planned |

### Deliverables Sprint 4
- APK siap uji coba  
- Semua fitur MVP berfungsi penuh  
- Laporan hasil testing & bug list  

---

## 7. Tools & Teknologi

| Kategori | Teknologi |
|-----------|------------|
| Framework | Flutter 3.24+ |
| Bahasa | Dart (Null Safety) |
| State Management | Riverpod |
| Database Lokal | Hive + SharedPreferences |
| Testing | Flutter Test / Integration Test |
| Desain UI | Figma |
| Version Control | GitHub (main/dev branch) |
| Build Tools | Android Studio / VS Code |

---

## 8. Checklist Final MVP (Go-Live Readiness)

| No | Item | Kriteria | Status |
|----|------|-----------|--------|
| 1 | Semua halaman utama (kalkulator, riwayat, pengaturan) berfungsi | Manual + test OK | ⚪ Pending |
| 2 | Validasi input & hasil akurat | Unit test lulus | ⚪ Pending |
| 3 | UI konsisten (font, warna, padding) | Review Figma | ⚪ Pending |
| 4 | Tema gelap & terang bekerja | Manual test | ⚪ Pending |
| 5 | App berjalan offline 100% | Uji airplane mode | ⚪ Pending |
| 6 | Build size < 8MB | Flutter build APK | ⚪ Pending |
| 7 | Tidak ada crash/error | Integration Test | ⚪ Pending |
| 8 | APK siap rilis (Beta) | Signed build OK | ⚪ Pending |

---

## 9. Deliverables Akhir

| Item | Format | Lokasi |
|------|---------|--------|
| Source Code | GitHub Private Repo | `/main` & `/dev` branch |
| PRD | PDF / Docs | `/docs/PRD.md` |
| ERD | Markdown | `/docs/ERD.md` |
| SDD | Markdown | `/docs/SDD.md` |
| MVP Checklist | Markdown | `/docs/Checklist_Timeline_Sprint_MVP.md` |
| APK Beta | File `.apk` | `/builds/release/v1.0/` |
| Design Assets | ZIP / Figma | `/assets/` |
| Release Notes | `.txt` | `/release-notes/v1.0.txt` |

---

## 10. Kesimpulan
Dokumen ini menjadi panduan resmi pengembangan tahap MVP untuk **Kalkulator HPP + Laba Otomatis**, mencakup semua tahapan — dari setup proyek hingga rilis versi beta.  
Setiap sprint difokuskan agar pengembangan tetap **terukur, efisien, dan sesuai target rilis 7 Januari 2026**.

 **Target Rilis Publik:** 7 Januari 2026  
 **Status Saat Ini:** Sprint 1 – Dalam Proses  

---
