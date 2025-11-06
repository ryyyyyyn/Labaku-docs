#  ERD – Kalkulator HPP + Laba Otomatis

##  Informasi Proyek
**Nama Aplikasi:** Kalkulator HPP + Laba Otomatis  
**Platform:** Mobile (Flutter – Android & iOS)  
**Tujuan:** Membantu penjual online & UMKM menghitung harga pokok penjualan (HPP) dan laba bersih secara cepat, otomatis, dan akurat.  

---

##  Tim Pengembang

| Nama | NIM | Peran |
|------|------|-------|
| **Ryan** | 221240001281 | Product Owner & Developer |
| **Niam** | 221240001241 | System Analyst & Database Designer |

---

## 🗃️ Deskripsi Entitas & Relasi

Aplikasi ini menyimpan data secara **lokal (offline-first)** menggunakan **Hive** atau **SharedPreferences** di Flutter.  
Berikut adalah struktur tabel (entitas) dan relasi antar entitas yang digunakan.

---

### 1. **UserSettings**

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| `id` | Integer (PK) | Primary Key unik untuk setiap user setting |
| `theme_mode` | String | Tema tampilan aplikasi (`light` / `dark`) |
| `primary_color` | String | Warna utama pilihan pengguna |
| `onboarding_done` | Boolean | Menandakan apakah onboarding sudah selesai |
| `language` | String | Bahasa tampilan aplikasi |
| `currency_format` | String | Format mata uang (misal: `Rp`, `$`) |
| `last_updated` | Datetime | Waktu terakhir pengaturan diubah |

**Relasi:**  
- 1 **UserSettings** dapat memiliki banyak **CalculationHistory**
- 1 **UserSettings** memiliki 1 **AppInfo**

---

### 2. **CalculationHistory**

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| `id` | String (PK) | ID unik (UUID) setiap riwayat perhitungan |
| `product_name` | String | Nama produk yang dihitung |
| `harga_produk` | Double | Harga modal produk |
| `ongkir` | Double | Biaya pengiriman |
| `biaya_admin` | Double | Persentase biaya administrasi |
| `biaya_packing` | Double | Biaya tambahan untuk kemasan |
| `margin` | Double | Persentase margin keuntungan |
| `total_hpp` | Double | Total HPP yang dihitung |
| `harga_jual` | Double | Harga jual ideal berdasarkan margin |
| `laba_bersih` | Double | Estimasi laba bersih hasil perhitungan |
| `timestamp` | Datetime | Waktu saat perhitungan dilakukan |
| `user_setting_id` | Integer (FK) | Relasi ke tabel `UserSettings` |

**Relasi:**  
- Banyak **CalculationHistory** dimiliki oleh satu **UserSettings**

---

### 3. **AppInfo**

| Field | Tipe Data | Keterangan |
|--------|-------------|------------|
| `id` | Integer (PK) | Primary Key |
| `version_name` | String | Versi aplikasi (contoh: `1.0.0`) |
| `build_number` | String | Nomor build aplikasi |
| `created_at` | Datetime | Tanggal pembuatan record |
| `updated_at` | Datetime | Tanggal terakhir diperbarui |

**Relasi:**  
- Satu **AppInfo** terkait dengan satu **UserSettings**

---

##  Hubungan Antar Entitas (Relational Mapping)

UserSettings (1) ───< CalculationHistory (∞)
│
└─── (1:1)
AppInfo

yaml
Copy code

---

##  Penjelasan Alur Data

1. Saat pengguna pertama kali membuka aplikasi, data default disimpan ke **UserSettings**.  
2. Setiap kali pengguna melakukan perhitungan, hasil disimpan sebagai **CalculationHistory**.  
3. Informasi aplikasi seperti versi dan build dicatat di **AppInfo**.  
4. Semua data tersimpan secara **lokal di perangkat pengguna**, tidak terkirim ke server.  

---

##  ERD Visual (Mermaid Diagram)

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
## Keamanan & Privasi
Data hanya disimpan lokal di perangkat, tidak dikirim ke server.

Tidak ada proses login atau data pribadi.

Pengguna dapat menghapus semua data riwayat di menu pengaturan.

 ##Teknologi yang Digunakan
Komponen	Teknologi
Framework	Flutter 3+
Bahasa	Dart
State Management	Provider / Riverpod
Database Lokal	Hive / SharedPreferences
Platform	Android & iOS
Mode Tampilan	Portrait Mobile Only

 ##Kesimpulan
ERD ini dirancang untuk mendukung aplikasi Kalkulator HPP + Laba Otomatis dengan struktur sederhana, efisien, dan mudah diimplementasikan di Flutter.
Seluruh relasi sudah dioptimalkan agar kompatibel dengan penyimpanan lokal (Hive) dan siap digunakan untuk pengembangan versi 1.0 aplikasi.
