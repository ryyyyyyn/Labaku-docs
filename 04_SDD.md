# SOFTWARE DESIGN DOCUMENT (SDD)
### Proyek: Kalkulator HPP + Laba Otomatis
**Versi Dokumen:** 1.0  
**Tanggal:** November 2025  
**Disusun oleh:**  
- **Ryan** (Owner/Developer) – NIM: 221240001281  
- **Niam** (System Analyst) – NIM: 221240001241  

---

## 1.  Pendahuluan

### 1.1 Tujuan Dokumen
Dokumen **Software Design Document (SDD)** ini berfungsi untuk menjelaskan rancangan teknis dari aplikasi **Kalkulator HPP + Laba Otomatis**, termasuk arsitektur sistem, desain modul, struktur data, dan interaksi antar komponen.  
Tujuannya adalah memberikan panduan yang jelas bagi pengembang dalam proses implementasi dan pemeliharaan aplikasi.

### 1.2 Ruang Lingkup Sistem
Aplikasi ini membantu **UMKM**, **reseller**, dan **seller online** dalam menghitung **Harga Pokok Penjualan (HPP)** serta **laba bersih** secara cepat dan akurat.  
Sistem bersifat **offline-first**, tidak memerlukan koneksi internet, dan semua data disimpan **lokal di perangkat pengguna**.

---

## 2.  Arsitektur Sistem

### 2.1 Tipe Arsitektur
Aplikasi menggunakan arsitektur **Layered Architecture (3 Layer Architecture)**:

┌───────────────────────────────┐
│ Presentation Layer │ → UI, Form, Theme, Navigation
├───────────────────────────────┤
│ Business Logic Layer │ → Kalkulasi HPP, Validasi Input, State
├───────────────────────────────┤
│ Data Layer │ → Hive Storage, Model, Repository
└───────────────────────────────┘

yaml
Copy code

### 2.2 Komponen Utama
| Layer | Komponen | Deskripsi |
|--------|-----------|-----------|
| Presentation | Flutter Widgets | Menampilkan UI seperti halaman kalkulator, riwayat, onboarding |
| Business Logic | Provider / Riverpod | Mengatur alur perhitungan HPP dan manajemen state |
| Data | Hive / SharedPreferences | Menyimpan data riwayat perhitungan dan preferensi pengguna |

---

## 3.  Desain Modular

### 3.1 Struktur Modul Aplikasi

lib/
┣━━ main.dart
┣━━ core/
┃ ┣━━ theme/
┃ ┗━━ constants/
┣━━ models/
┣━━ services/
┣━━ providers/
┣━━ screens/
┃ ┣━━ splash_screen.dart
┃ ┣━━ onboarding_screen.dart
┃ ┣━━ calculator_screen.dart
┃ ┣━━ history_screen.dart
┃ ┣━━ detail_screen.dart
┃ ┣━━ settings_screen.dart
┃ ┗━━ about_screen.dart
┗━━ widgets/

php
Copy code

---

## 4.  Desain Data

### 4.1 Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    USERSETTINGS {
        int id PK
        string theme_mode
        string primary_color
        bool onboarding_done
        string language
        string currency_format
        datetime last_updated
    }

    CALCULATIONHISTORY {
        string id PK
        string product_name
        double harga_produk
        double ongkir
        double biaya_admin
        double biaya_packing
        double margin
        double total_hpp
        double harga_jual
        double laba_bersih
        datetime timestamp
        int user_setting_id FK
    }

    APPINFO {
        int id PK
        string version_name
        string build_number
        datetime created_at
        datetime updated_at
    }

    USERSETTINGS ||--o{ CALCULATIONHISTORY : has
    USERSETTINGS ||--|| APPINFO : owns
5.  Desain Fungsional
5.1 Diagram Alir Proses (Flow Diagram)
mermaid
Copy code
flowchart TD
    A[Splash Screen] --> B[Onboarding Screen]
    B --> C[Calculator Screen]
    C -->|Hitung HPP| D[Perhitungan Otomatis]
    D --> E[Tampilkan Hasil]
    E --> F{Simpan ke Riwayat?}
    F -->|Ya| G[Simpan ke Hive]
    F -->|Tidak| H[Reset Form]
    G --> I[Riwayat Perhitungan]
    I --> J[Lihat Detail / Hapus Data]
    C --> K[Menu Pengaturan]
    K --> L[Ubah Tema / Warna]
    K --> M[Lihat Tentang Aplikasi]
6.  Desain Logika & Algoritma
6.1 Rumus Perhitungan HPP dan Laba Bersih
Input:

Harga Produk (Rp)

Ongkir (Rp)

Biaya Admin (%)

Biaya Packing (Rp)

Margin Keuntungan (%)

Formula:

ini
Copy code
Total_HPP = Harga_Produk + Ongkir + Biaya_Packing + (Harga_Produk × Biaya_Admin / 100)
Harga_Jual = Total_HPP + (Total_HPP × Margin / 100)
Laba_Bersih = Harga_Jual - Total_HPP
Output:

Total HPP

Harga Jual Ideal

Estimasi Laba Bersih

7.  Antarmuka Pengguna (UI/UX)
7.1 Gaya Desain
Elemen	Deskripsi
Warna Utama	Oranye (#FF6F00)
Font	Poppins / Inter
Ikon	Flat minimalis
Layout	Fokus satu halaman kalkulasi
Tema	Light & Dark Mode
Navigasi	Bottom navigation (Calculator – History – Settings)

7.2 Desain Navigasi
mermaid
Copy code
graph LR
    A[Splash] --> B[Onboarding]
    B --> C[Calculator]
    C --> D[History]
    D --> E[Detail]
    C --> F[Settings]
    F --> G[About]
8.  Desain Kelas (Class Design)
8.1 Model CalculationHistory
dart
Copy code
class CalculationHistory {
  String id;
  String productName;
  double hargaProduk;
  double ongkir;
  double biayaAdmin;
  double biayaPacking;
  double margin;
  double totalHpp;
  double hargaJual;
  double labaBersih;
  DateTime timestamp;

  CalculationHistory({
    required this.id,
    required this.productName,
    required this.hargaProduk,
    required this.ongkir,
    required this.biayaAdmin,
    required this.biayaPacking,
    required this.margin,
    required this.totalHpp,
    required this.hargaJual,
    required this.labaBersih,
    required this.timestamp,
  });
}
8.2 Model UserSettings
dart
Copy code
class UserSettings {
  int id;
  String themeMode;
  String primaryColor;
  bool onboardingDone;
  String language;
  String currencyFormat;
  DateTime lastUpdated;

  UserSettings({
    required this.id,
    required this.themeMode,
    required this.primaryColor,
    required this.onboardingDone,
    required this.language,
    required this.currencyFormat,
    required this.lastUpdated,
  });
}
9.  Keamanan & Privasi
Aspek	Deskripsi
Data Penyimpanan	Lokal di perangkat (Hive)
Autentikasi	Tidak diperlukan
Privasi	Tidak ada data pribadi dikumpulkan
Hapus Data	Pengguna dapat menghapus semua riwayat
Izin	Tidak membutuhkan akses internet

10.  Deployment
Aspek	Rincian
Target Platform	Android (min SDK 21), iOS (min iOS 12)
Build Tool	Flutter Build APK / iOS Runner
Distribusi	Google Play Store, App Store
Format Rilis	.apk, .ipa
Mode	Offline-first, single-device use

11. Testing Plan
Jenis Tes	Tujuan	Alat
Unit Test	Validasi fungsi perhitungan HPP	Flutter Test
Widget Test	Uji tampilan dan interaksi	Flutter Test
Integration Test	Pastikan data tersimpan dengan benar di Hive	Flutter Integration Test

12.  Rencana Versi
Versi	Deskripsi	Status
v1.0	Fitur kalkulator HPP dasar + riwayat lokal
v1.1	Tema gelap + export PDF	
v1.2	Sinkronisasi cloud opsional	
v2.0	Integrasi AI Pricing	-- Riset

13.  Kriteria Keberhasilan
≥ 1000 unduhan dalam 3 bulan pertama

80% pengguna aktif mingguan

Rating ≥ 4.5 di Play Store

Waktu penggunaan rata-rata < 3 menit

14.  Kesimpulan
Desain teknis aplikasi Kalkulator HPP + Laba Otomatis dirancang dengan pendekatan modular dan arsitektur sederhana agar mudah dikembangkan, efisien, dan ringan dijalankan di perangkat mobile.
Dokumen ini menjadi panduan resmi dalam proses pengembangan, pengujian, dan pemeliharaan aplikasi.
