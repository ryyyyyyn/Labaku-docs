# Kalkulator HPP + Laba Otomatis

**Owner:** Ryan (221240001281)  
**System Analyst:** Niam (221240001241)  
**Versi:** 1.0 (MVP)  
**Tanggal:** November 2025  

---

## Deskripsi Proyek

Aplikasi **Kalkulator HPP + Laba Otomatis** adalah alat bantu digital berbasis **Flutter** yang dirancang untuk membantu **UMKM dan seller online** menghitung **Harga Pokok Penjualan (HPP)**, **harga jual ideal**, dan **laba bersih** secara otomatis dan akurat.

Aplikasi ini bekerja **100% offline**, memiliki antarmuka sederhana, serta memungkinkan pengguna **menyimpan riwayat perhitungan** untuk analisis laba dan optimasi harga produk.

---

##  Fitur Utama

-  Perhitungan otomatis **HPP, harga jual, dan laba bersih**
-  Penyimpanan **riwayat perhitungan lokal (Hive)**
-  Tema **terang & gelap** yang dapat diatur pengguna
-  Tampilan hasil interaktif (animasi dan format Rupiah)
-  Ringan, cepat, dan **offline-friendly**

---

##  Teknologi yang Digunakan

| Komponen | Teknologi |
|-----------|------------|
| Framework | Flutter 3.24+ |
| Bahasa | Dart (Null Safety) |
| Database Lokal | Hive + SharedPreferences |
| State Management | Riverpod |
| Desain UI/UX | Figma |
| Version Control | GitHub |
| Build Tools | Android Studio / VS Code |

---

##  Dokumentasi Proyek

Semua dokumen proyek tersedia dalam format Markdown di folder `/docs/` berikut:

| No | Dokumen | Deskripsi | Link |
|----|----------|------------|------|
| 01 | **Product Requirement Document (PRD)** | Menjelaskan visi, tujuan, kebutuhan fungsional dan non-fungsional aplikasi | [01_PRD.md](./docs/01_PRD.md) |
| 02 | **Entity Relationship Diagram (ERD)** | Struktur basis data dan relasi antar entitas | [02_ERD.md](./docs/02_ERD.md) |
| 03 | **Software Requirement Specification (SRS)** | Spesifikasi teknis kebutuhan sistem & batasan fungsional | [03_SRS.md](./docs/03_SRS.md) |
| 04 | **Software Design Document (SDD)** | Desain arsitektur, komponen, diagram, dan alur sistem | [04_SDD.md](./docs/04_SDD.md) |
| 05 | **Checklist & Timeline Sprint MVP** | Jadwal dan task pengembangan berbasis Agile Scrum | [05_Checklist_Timeline_Sprint_MVP.md](./docs/05_Checklist_Timeline_Sprint_MVP.md) |

---

## Cara Menjalankan Proyek

```bash
# Clone repositori
git clone https://github.com/PopOfficial/kalkulator-hpp.git

# Masuk ke direktori proyek
cd kalkulator-hpp

# Jalankan aplikasi
flutter pub get
flutter run
