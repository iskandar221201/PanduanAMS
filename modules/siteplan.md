# 🗺️ Dokumentasi Modul Siteplan (AMS)

Modul **Siteplan** di AMS adalah pusat visualisasi data properti yang menggabungkan peta digital interaktif dengan data real-time dari database. Modul ini dirancang untuk memberikan gambaran menyeluruh mengenai status penjualan, progres konstruksi, dan detail unit secara visual.

Tidak hanya sekedar gambar statis, Siteplan di AMS adalah **Digital Twin** dari lapangan yang memudahkan tim Sales, Admin, dan Manajerial dalam mengambil keputusan.

---

## 🚀 Fitur Unggulan

### 1. Visualisasi Interaktif & Real-Time
*   **Pan & Zoom:** Menjelajahi siteplan layaknya Google Maps. Bisa di-zoom hingga detail unit, atau di-pan untuk melihat area lain.
*   **Dual View Mode:**
    *   **Map View:** Tampilan visual peta untuk pemahaman spasial.
    *   **List View:** Tampilan daftar/grid unit yang memudahkan pencarian cepat berdasarkan nomor alias.
*   **Status Live:** Setiap unit diwarnai secara otomatis berdasarkan status transaksinya (Available, Booking, SP3K, Sold, dll) sesuai data real-time database. Tidak ada lagi "kata tim lapangan masih kosong ternyata sudah sold".

### 2. Smart Search & Highlight
Fitur pencarian di Siteplan sangat responsif:
*   Ketik nomor unit (misal: "A-1"), AMS langsung menyorot (highlight) unit tersebut di peta.
*   Unit lain akan diredupkan (dimmed) supaya fokus pengguna tertuju pada unit yang dicari.
*   Bekerja sinkron di mode Map maupun List view.

### 3. Detail Unit Komprehensif (On-Click Intelligence)
Klik pada kavling manapun untuk membuka **Kartu Informasi Unit** yang berisi data krusial:
*   **Status & Konsumen:** Menampilkan siapa pembelinya (jika sold) dan status terkini.
*   **Progres Konstruksi:** Terintegrasi dengan modul Konstruksi, menampilkan % pembangunan.
*   **Harga & Rincian:** Menampilkan harga jual, booking fee, DP, plafond KPR, hingga biaya hook secara transparan.
*   **Spesifikasi:** Luas Tanah dan Bangunan.

### 4. Advanced Export Engine (Fitur Favorit)
Modul ini memiliki mesin export gambar canggih yang bisa men-generate laporan visual dalam hitungan detik:
*   **Mode Transaksi:** Download gambar siteplan dengan legenda warna berdasarkan status penjualan (Merah=Sold, Hijau=Proses Bank, dll). Cocok untuk laporan marketing.
*   **Mode Konstruksi:** Download gambar siteplan dengan heatmap warna berdasarkan progres pembangunan (Hijau > 75%, Kuning 50-75%, Merah < 25%). Cocok untuk laporan progres proyek ke owner.
*   **Auto-Legend:** Sistem otomatis membuatkan legenda (keterangan warna) dan statistik jumlah unit di bagian bawah gambar hasil download.

---

## 🛡️ Validasi & Logika Sistem

### A. Validasi Koordinat (Editor Mode)
*   **Data Integritas:** Setiap kavling yang digambar di siteplan (Editor) wajib terhubung dengan `kavling_id` yang valid di database.
*   **Draft Mode:** Perubahan posisi/bentuk kavling di Editor tidak langsung muncul di publik. Ada mekanisme **Publish** untuk memastikan perubahan di-review terlebih dahulu.

### B. Validasi Data Tampilan (Viewer Mode)
*   **Permission Check:** Hanya user dengan hak akses `siteplan.access` yang bisa melihat modul ini.
*   **Project Scope:** User hanya bisa melihat siteplan dari proyek yang ditugaskan kepadanya (kecuali Super Admin).
*   **Data Fallback:** Jika data progres konstruksi atau nama konsumen kosong, sistem akan menampilkan placeholder "0%" atau "-" (tidak error).
*   **Status Priority:** Warna kavling diutamakan berdasarkan status transaksi terakhir (bukan status booking lama yang sudah cancel).

---

## ⌨️ Shortcut & Tips Penggunaan

| Aksi | Mouse/Keyboard Shortcut | Fungsi |
| :--- | :--- | :--- |
| **Zoom In/Out** | Scroll Wheel | Memperbesar/memperkecil peta |
| **Geser Peta** | Klik Kiri + Tahan + Geser | Navigasi area siteplan |
| **Reset View** | Tombol <i class="fas fa-compress-arrows-alt"></i> | Mengembalikan peta ke posisi tengah & zoom normal |
| **Cari Unit** | Ketik di Search Bar | Highlight unit spesifik |
| **Toggle List** | Tombol <i class="fas fa-list"></i> | Ubah tampilan ke mode Daftar |

---

## 🔌 API & Integrasi Teknis

Modul ini bekerja dengan memanggil beberapa endpoint penting:

1.  **GET `siteplan/fetchUpdates`**
    *   Mengambil koordinat (x, y, w, h, rotation) dan status dasar semua unit dalam satu request ringan.
    *   Digunakan saat inisialisasi peta.

2.  **GET `siteplan/getKavlingDetail`**
    *   Dipanggil saat user klik unit (Lazy Loading).
    *   Mengambil data berat seperti join tabel `prospek` (nama konsumen), `harga_kavling` (rincian harga), dan `construction_targets` (progres).
    *   **Respon Cerdas:** Menggabungkan data dari 3 tabel berbeda menjadi satu objek JSON bersih.

---

## ❓ FAQ (Troubleshooting)

**Q: Kenapa gambar siteplan tidak muncul?**
> Pastikan file gambar master siteplan sudah diupload di menu **Project Settings**. Jika belum, AMS akan menampilkan placeholder.

**Q: Saya sudah update status unit jadi SOLD di menu Kavling, tapi di Siteplan masih hijau (Available)?**
> Siteplan mengambil data real-time. Coba refresh halaman. Jika masih sama, pastikan status di menu Kavling sudah benar-benar tersimpan "Sold" dan bukan "Booking" yang sudah kadaluarsa.

**Q: Kenapa saat download gambar, hasilnya ada kotak hitam/kosong?**
> Ini biasanya masalah browser (CORS). Kami sudah menangani ini dengan proxy image, tapi pastikan koneksi internet stabil saat proses generating image (spinner loading).

**Q: Apakah bisa dipuka di HP?**
> **Bisa Banget!** Tampilan mobile sudah dioptimalkan dengan tombol navigasi di bawah (thumb-friendly) dan offcanvas (menu laci bawah) untuk detail unit, menggantikan modal standar yang kaku.
