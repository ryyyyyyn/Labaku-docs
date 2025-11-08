# ERD – Kalkulator HPP + Laba Otomatis

## Informasi Proyek
**Nama Aplikasi:** Kalkulator HPP + Laba Otomatis  
**Platform:** Mobile (Flutter – Android & iOS)  
**Tujuan:** Membantu penjual online dan pelaku UMKM menghitung harga pokok penjualan (HPP) serta laba bersih dengan cepat, otomatis, dan akurat.

---

## Tim Pengembang

| Nama | NIM | Peran |
|------|------|-------|
| Ryan | 221240001281 | Product Owner & Developer |
| Niam | 221240001241 | System Analyst & Database Designer |

---

## Deskripsi Umum Sistem

Aplikasi ini beroperasi secara **offline-first** dan menyimpan data menggunakan **Hive** atau **SharedPreferences** di Flutter.  
Struktur data terdiri dari tiga entitas utama: **UserSettings**, **CalculationHistory**, dan **AppInfo**.  
Relasi antar entitas dirancang agar efisien dan mudah diimplementasikan dalam penyimpanan lokal.

---

## 1. Entitas: UserSettings

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| id | Integer (PK) | Primary Key unik untuk setiap pengaturan pengguna |
| theme_mode | String | Tema tampilan aplikasi (`light` / `dark`) |
| primary_color | String | Warna utama pilihan pengguna |
| onboarding_done | Boolean | Menunjukkan apakah onboarding telah selesai |
| language | String | Bahasa tampilan aplikasi |
| currency_format | String | Format mata uang (misal: Rp, $, dll) |
| last_updated | Datetime | Waktu terakhir pengaturan diperbarui |

**Relasi:**
- Satu **UserSettings** dapat memiliki banyak **CalculationHistory**  
- Satu **UserSettings** memiliki satu **AppInfo**

---

## 2. Entitas: CalculationHistory

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| id | String (PK) | ID unik (UUID) untuk setiap riwayat perhitungan |
| product_name | String | Nama produk yang dihitung |
| harga_produk | Double | Harga modal produk |
| ongkir | Double | Biaya pengiriman |
| biaya_admin | Double | Persentase biaya administrasi |
| biaya_packing | Double | Biaya tambahan untuk kemasan |
| margin | Double | Persentase margin keuntungan |
| total_hpp | Double | Total harga pokok penjualan yang dihitung |
| harga_jual | Double | Harga jual ideal berdasarkan margin |
| laba_bersih | Double | Estimasi laba bersih dari hasil perhitungan |
| timestamp | Datetime | Waktu perhitungan dilakukan |
| user_setting_id | Integer (FK) | Relasi ke tabel `UserSettings` |

**Relasi:**
- Banyak **CalculationHistory** dimiliki oleh satu **UserSettings**

---

## 3. Entitas: AppInfo

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| id | Integer (PK) | Primary Key |
| version_name | String | Versi aplikasi (misal: `1.0.0`) |
| build_number | String | Nomor build aplikasi |
| created_at | Datetime | Tanggal pembuatan record |
| updated_at | Datetime | Tanggal terakhir pembaruan |

**Relasi:**
- Satu **AppInfo** terkait dengan satu **UserSettings**

---

## Hubungan Antar Entitas (Relational Mapping)

UserSettings (1) ───< CalculationHistory (∞)
│
└─── (1:1)
AppInfo

yaml
Copy code

---

## Penjelasan Alur Data

1. Ketika pengguna pertama kali membuka aplikasi, data default disimpan pada tabel **UserSettings**.  
2. Setiap kali pengguna melakukan perhitungan HPP dan laba, hasilnya otomatis disimpan ke tabel **CalculationHistory**.  
3. Informasi versi dan build aplikasi disimpan pada tabel **AppInfo**.  
4. Semua data hanya tersimpan secara **lokal di perangkat pengguna**, tanpa koneksi atau pengiriman ke server.

---

## ERD Visual (Mermaid Diagram)

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

    USERSETTINGS ||--o{ CALCULATIONHISTORY : "has many"
    USERSETTINGS ||--|| APPINFO : "has one"
Keamanan dan Privasi
Semua data disimpan secara lokal di perangkat pengguna.

Tidak ada proses login maupun data pribadi yang dikumpulkan.

Pengguna dapat menghapus seluruh data riwayat dari menu pengaturan.

Backup dan restore dapat dilakukan secara manual melalui file lokal.

Teknologi yang Digunakan
Komponen	Teknologi
Framework	Flutter 3+
Bahasa Pemrograman	Dart
State Management	Provider atau Riverpod
Database Lokal	Hive atau SharedPreferences
Platform	Android dan iOS
Mode Tampilan	Portrait (Mobile Only)

Kesimpulan
ERD ini dirancang untuk mendukung pengembangan aplikasi Kalkulator HPP + Laba Otomatis versi 1.0 dengan struktur data yang sederhana, efisien, dan siap diimplementasikan.
Relasi antar entitas telah dioptimalkan agar kompatibel dengan penyimpanan lokal Flutter serta mudah dikembangkan lebih lanjut untuk versi premium dengan fitur tambahan seperti riwayat tanpa batas, export hasil ke PDF/Excel, dan tema warna kustom.
