# 📊 Dokumentasi Modul Funnel Penjualan (AMS)

Modul **Funnel Penjualan** (Sales Funnel) di AMS adalah alat monitoring performa penjualan yang menyajikan data dalam bentuk tabel pivot. Meskipun secara mekanisme modul ini terbilang sederhana (hanya menampilkan data), manfaat yang dihasilkan sangat krusial bagi pengambilan keputusan strategis manajemen.

---

## 🌟 Mengapa Modul Ini Sangat Bermanfaat?

Berbeda dengan daftar transaksi biasa, Funnel Penjualan memberikan **"Helicopter View"** terhadap kesehatan pipa penjualan Anda:

1.  **Identifikasi Bottleneck (Sumbatan):** Anda bisa melihat di tahap mana proses penjualan sering terhenti. Misalnya, jika banyak unit di status "Pemberkasan" tapi sedikit yang sampai ke "Proses Bank", berarti ada kendala pada pengumpulan dokumen konsumen.
2.  **Transparansi Performa Marketing:** Manajer dapat melihat distribusi beban kerja dan produktivitas setiap sales secara *real-time* tanpa perlu bertanya satu per satu.
3.  **Prediksi Closing:** Dengan melihat jumlah unit di tahap "SP3K" atau "Pemberkasan", manajemen dapat memprediksi target *closing* dan potensi *cash-in* di bulan mendatang.
4.  **Early Warning System:** Jika status "Reject" atau "Mundur" mulai meningkat pada sales tertentu, manajemen bisa segera melakukan intervensi atau evaluasi.

---

## 🚀 Fitur Unggulan (Powerful Features)

### 1. Dinamis & Akurat (ENUM Sync)
AMS tidak menggunakan daftar status yang diketik manual. Modul ini membaca langsung definisi kolom `status_transaksi` dari database (MySQL ENUM). Artinya, setiap kali ada perubahan status di modul utama, Funnel akan otomatis menyesuaikan kolomnya tanpa perlu update kode.

### 2. Smart Pivot Table
Menampilkan ringkasan yang mudah dibaca:
*   **Baris:** Nama Marketing / Sales.
*   **Kolom:** Tahapan Transaksi (Pemberkasan, Proses Bank, SP3K, Akad, dll).
*   **Nilai:** Jumlah Unit.
*   **Total:** Akumulasi seluruh progres per sales.

### 3. Integrated Export Engine
Laporan Funnel yang sedang Anda lihat dapat langsung dibawa ke rapat dalam hitungan detik melalui tombol:
*   **Excel:** Untuk pengolahan data atau perhitungan komisi lanjutan.
*   **PDF:** Laporan resmi dengan tampilan profesional.
*   **Print:** Cetak langsung dari browser.

### 4. Role-Based Data Scope
Keamanan data tetap terjaga:
*   **Sales:** Hanya melihat data miliknya sendiri (Funnel Saya).
*   **Supervisor/Manager Proyek:** Melihat seluruh sales yang bertugas di proyeknya.
*   **Direksi/Admin Pusat:** Dapat berpindah antar-proyek atau melihat totalitas seluruh proyek perusahaan.

---

## 🛡️ Mekanisme & Validasi

Meskipun modul ini bersifat *Read-Only* (Laporan), AMS tetap menerapkan validasi ketat:

1.  **Validasi Hak Akses (`permission`):** User hanya bisa membuka menu ini jika memiliki izin `funnel.access`.
2.  **Filter Project Geofencing:** User tidak bisa melihat data proyek lain dengan memanipulasi URL jika akunnya tidak memiliki scope `all_projects`.
3.  **Group Sync:** Data diringkas per Sales dan per Project untuk memastikan tidak ada data yang tumpang tindih saat melihat laporan lintas proyek.

---

## 🛠️ Cara Menggunakan (User Guide)

1.  **Buka Menu Funnel:** Klik pada menu **Marketing > Funnel Penjualan**.
2.  **Pilih Proyek (Jika Ada Akses):** Gunakan dropdown filter di bagian atas untuk menyaring data per proyek atau pilih "Tampilkan Semua Project".
3.  **Analisis Tabel:**
    *   Cetak angka yang berwarna hijau menunjukkan adanya unit aktif.
    *   Warna hitam tebal pada kolom **TOTAL** menunjukkan performa keseluruhan sales tersebut.
4.  **Pencarian Cepat:** Gunakan kotak *Search* di tabel untuk mencari nama sales tertentu.
5.  **Ekspor Data:** Klik tombol Excel/PDF di pojok kiri atas tabel untuk menyimpan laporan.

---

## ❓ FAQ

**Q: Mengapa ada nama sales yang muncul tapi semua angkanya 0?**
> A: Ini menandakan sales tersebut memiliki akun di proyek tersebut, namun saat ini belum memiliki data booking/transaksi yang tercatat di database AMS.

**Q: Apakah status "Mundur" atau "Reject" dihitung dalam Total?**
> A: Ya. Kolom **TOTAL** menghitung seluruh riwayat booking yang pernah ditangani oleh sales tersebut, baik yang masih aktif maupun yang sudah batal.

**Q: Urutan statusnya tidak urut, bisakah diatur?**
> A: AMS sudah mengurutkan status berdasarkan alur kerja properti (disesuaikan di model: Pemberkasan -> Proses Bank -> SP3K ... -> Akad). Urutan ini dirancang untuk memudahkan pembacaan alur pipa penjualan dari kiri ke kanan.
