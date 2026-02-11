# 📈 Dokumentasi Modul Meta Ads (AMS)

Modul **Meta Ads** di AMS adalah alat monitoring strategis yang dirancang untuk membandingkan **Biaya Iklan (Ad Spend)** dengan **Hasil Nyata di Lapangan (Real Leads, Visits, Bookings)**.

Berbeda dengan dashboard Facebook Ads yang hanya menampilkan data digital (klik/tayangan), modul ini menghubungkan data tersebut dengan database operasional AMS untuk menghitung efektivitas biaya marketing secara akurat.

---

## 🚀 Fitur Unggulan (Powerful Features)

### 1. Automated Funnel Tracking (Looping Data Otomatis)
Salah satu kekuatan utama modul ini adalah kemampuannya menarik data lintas modul secara otomatis. Anda hanya perlu menginput **Biaya Iklan** dan **Leads Digital**, sisanya dihitung oleh sistem:
*   **Leads Real:** Diambil dari input manual/sistem.
*   **Visit (Kunjungan):** Sistem otomatis menghitung jumlah calon pembeli yang statusnya *"Cek Lokasi"* atau *"SLIK"* di bulan tersebut dari sumber database Prospek.
*   **Booking (Penjualan):** Sistem otomatis menghitung jumlah transaksi *Booking* valid (tidak reject/mundur) dari database Penjualan.

### 2. Smart Metrics Engine
Tidak perlu kalkulator. AMS otomatis menghitung rasio performa krusial:
*   **CPL (Cost Per Lead):** Berapa biaya untuk mendapatkan 1 nomor WA?
*   **CPV (Cost Per Visit):** Berapa biaya iklan yang harus keluar untuk mendatangkan 1 orang ke lokasi?
*   **Conversion Rate:** Persentase keberhasilan dari Iklan -> Chat -> Datang -> Beli.

### 3. Visual Trend Analysis
Dashboard dilengkapi dengan grafik tren visual yang membandingkan **CPL Meta (Teoritis)** vs **CPL Aktual (Realita)**. Ini membantu manajer marketing mendeteksi:
*   Apakah kualitas leads menurun? (CPL Meta murah, tapi CPL Aktual mahal karena banyak leads sampah).
*   Apakah tim sales kurang follow-up? (Leads banyak tapi Visit sedikit).

### 4. Professional Report Generator
Fitur Export PDF bawaan menghasilkan laporan kinerja satu halaman yang siap dipresentasikan ke direksi/owner.
*   **Branded:** Otomatis menyertakan Logo Proyek.
*   **Lengkap:** Berisi ringkasan biaya, tabel funnel, dan analisis rasio dalam satu dokumen rapi.

---

## 🔄 Alur Kerja (Workflow)

### Tahap 1: Input Data (Admin/Marketing)
1.  Masuk ke menu **Meta Ads > Input Laporan**.
2.  Pilih **Project** dan **Bulan Laporan**.
3.  Isi data dari Dashboard Facebook Ads:
    *   *Ad Spend* (Total Biaya).
    *   *Impressions, Clicks, CTR* (Opsional, untuk data pendukung).
    *   *Leads Meta* (Jumlah form/chat masuk menurut Facebook).
    *   *Leads Aktual* (Jumlah nomor WA valid yang masuk ke CRM).
4.  Klik **Simpan**.

### Tahap 2: Kalkulasi Sistem (Automated)
Sistem AMS bekerja di latar belakang:
*   Mengecek database **Prospek**: Berapa orang dari sumber *"Official"* yang statusnya *"Cek Lokasi"* di bulan terpilih? -> *Input ke kolom Visit*.
*   Mengecek database **Booking**: Berapa orang dari sumber *"Official"* yang statusnya *"Booking"* di bulan terpilih? -> *Input ke kolom Booking*.
*   Menghitung CPL dan CPV secara real-time.

### Tahap 3: Analisis & Reporting (Manager)
1.  Buka Dashboard Meta Ads.
2.  Gunakan **Filter Tahun/Bulan** untuk melihat periode spesifik.
3.  Lihat grafik untuk evaluasi tren.
4.  Klik ikon **PDF** untuk mengunduh laporan fisik.

---

## 🛡️ Validasi & Logika Perhitungan

### A. Validasi Input
*   **Data Wajib:** Tanggal Report, Project ID, dan Ad Spend tidak boleh kosong.
*   **Tipe Data:** Ad Spend harus angka numerik.
*   **Integritas:** Satu periode laporan biasanya mewakili satu bulan kalender untuk akurasi pelacakan.

### B. Rumus Kalkulasi (Logic)
Berikut adalah "dapur" perhitungan AMS untuk memastikan transparansi data:

1.  **Leads Visit (Kunjungan):**
    ```sql
    SELECT COUNT(*) FROM prospek 
    WHERE sumber_leads = 'Official' 
    AND status IN ('Cek Lokasi', 'SLIK', 'Booking', 'Ganti Pengaju')
    AND MONTH(tanggal_cek_lokasi) = [Bulan Laporan]
    ```
    > *Logika: Hanya menghitung prospek dari iklan resmi yang benar-benar datang ke lokasi.*

2.  **Leads Booking (Penjualan):**
    ```sql
    SELECT COUNT(*) FROM booking_data 
    JOIN prospek ON ...
    WHERE sumber_leads = 'Official'
    AND status_transaksi NOT IN ('Reject', 'Mundur')
    AND MONTH(tanggal_booking) = [Bulan Laporan]
    ```
    > *Logika: Hanya menghitung booking bersih (Net) yang tidak batal.*

3.  **Cost Per Visit (CPV):**
    `Total Ad Spend / Jumlah Visit`
    
---

## 🔌 Detail Teknis

Modul ini dibangun menggunakan pola MVC standar CodeIgniter 4:
*   **Controller:** `AdsController.php` - Mengatur alur data, permission check (`ads-management`), dan logika filtering.
*   **Model:** `AdsModel.php` - Menangani query kompleks ke database prospek dan booking untuk menghitung funnel otomatis (`getFunnelMetrics`).
*   **View:** Folder `app/Views/ads/` berisi antarmuka responsif dan template PDF.

---

## ❓ FAQ

**Q: Kenapa jumlah Visit di laporan Ads beda dengan buku tamu?**
> Modul Ads hanya menghitung visit yang sumber leads-nya **"Official"** (dari iklan kantor). Kunjungan dari agen freelance, spanduk, atau referensi teman tidak dihitung di sini agar perhitungan efektivitas iklan akurat.

**Q: Apa bedanya Leads Meta dengan Leads Aktual?**
> **Leads Meta** adalah angka klaim dari Facebook (misal: jumlah klik tombol WA). **Leads Aktual** adalah jumlah orang yang benar-benar chat/menyimpan nomor. Biasanya Leads Aktual lebih rendah 10-20% karena ada "misclick" atau chat hantu.

**Q: Bagaimana jika saya salah input Ad Spend?**
> Anda bisa mengklik tombol **Edit** (ikon pensil) pada baris laporan tersebut untuk memperbarui angka biayanya. Perhitungan CPL akan otomatis menyesuaikan setelah disimpan.
