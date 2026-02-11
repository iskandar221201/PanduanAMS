# 📜 Panduan Modul BAST (Berita Acara Serah Terima)

Modul **BAST** di AMS adalah pusat pengelolaan dokumen serah terima, baik dari Kontraktor ke Developer maupun dari Developer ke Konsumen. Modul ini menjamin legalitas dan alur serah terima unit berjalan sesuai prosedur standar perusahaan.

---

## 1. Fitur Unggulan 

### A. Dual Mode Serah Terima (K_D & D_K)
AMS menangani dua jenis BAST dalam satu pintu:
1.  **K_D (Kontraktor → Developer):** Serah terima fisik bangunan dari vendor ke internal perusahaan.
2.  **D_K (Developer → Konsumen):** Serah terima kunci dan unit kepada pembeli (user).

### B. Validasi Alur "Berjenjang" (Smart Flow)
Sistem menerapkan logika kausalitas yang ketat:
*   Anda **TIDAK BISA** membuat BAST ke Konsumen (D_K) jika unit tersebut belum diserahterimakan dari Kontraktor (K_D).
*   Sistem memastikan unit yang diserahkan ke konsumen sudah benar-benar selesai dibangun dan diakui oleh manajemen.

### C. Pelacakan Masa Garansi Otomatis (Warranty Tracker)
Salah satu fitur paling membantu bagi tim Purna Jual:
*   **Visualisasi Sisa Garansi:** Di dashboard BAST, Anda bisa memantau sisa hari garansi setiap unit.
*   **Indikator Warna:**
    *   🟢 **Hijau**: Masa garansi aman (> 30 hari).
    *   🟡 **Kuning**: Segera habis (< 30 hari).
    *   🔴 **Merah**: Garansi sudah berakhir (Expired).
*   **Auto-Rule:** Untuk BAST ke Konsumen (D_K), sistem **otomatis mengunci masa garansi 90 hari** (atau sesuai kebijakan perusahaan), mencegah kesalahan input manual oleh staf.

### D. Filter Kelayakan Cerdas (Smart Filtering)
Saat membuat BAST baru, dropdown pilihan unit bekerja dengan sangat cerdas:
*   **Untuk K_D:** Hanya menampilkan unit/fasum yang progress konstruksinya sudah **100%**. Unit yang belum jadi tidak akan muncul.
*   **Untuk D_K:** Hanya menampilkan unit yang sudah **Akad** dan sudah melalui proses **BAST K_D**.

---

## 2. Alur Kerja (Workflow)

### Tahap 1: Serah Terima dari Kontraktor (K_D)
*Dilakukan saat bangunan selesai 100%.*
1.  Masuk ke menu **BAST > Tambah BAST**.
2.  Pilih Jenis BAST: **Kontraktor ke Developer (K_D)**.
3.  **Pilih Unit/Fasum:** Dropdown hanya menampilkan unit dengan progress 100%.
4.  Isi data: Nomor BAST, Tanggal, dan Masa Garansi Retensi (misal: 180 hari).
5.  Upload scan dokumen fisik BAST.
6.  Klik **Simpan**.

### Tahap 2: Serah Terima ke Konsumen (D_K)
*Dilakukan setelah konsumen selesai Akad Kredit/Lunas.*
1.  Masuk ke menu **BAST > Tambah BAST**.
2.  Pilih Jenis BAST: **Developer ke Konsumen (D_K)**.
3.  **Pilih Unit:** Dropdown otomatis menampilkan nama konsumen dan hanya unit yang sudah BAST K_D.
4.  **Auto-Fill:** Nama Konsumen akan terisi otomatis. Masa Garansi otomatis terisi (misal: 90 hari).
5.  Input Nomor BAST dan Tanggal.
6.  Upload scan dokumen.
7.  Klik **Simpan**.

---

## 3. Validasi & Aturan Sistem (AMS Rules)

1.  **Syarat Konstruksi 100%:**
    *   BAST K_D tidak bisa dibuat jika progress lapangan (di Modul Konstruksi) belum mencapai **100%**.
2.  **Syarat Status "Akad":**
    *   BAST D_K hanya bisa diproses untuk konsumen dengan status transaksi **Akad**. Konsumen status *Booking* atau *Proses Bank* tidak valid untuk serah terima.
3.  **Unik & Legal:**
    *   Setiap Nomor BAST harus unik. Sistem menolak duplikasi nomor untuk mencegah masalah arsip.
    *   Wajib upload file digital (PDF/JPG) sebagai backup legalitas.
4.  **Secure Delete (Penghapusan Aman):**
    *   Dokumen BAST adalah dokumen legal vital. Menghapusnya memerlukan **Otorisasi Khusus** (Token Delete) dari Direktur/Manager. Ini melindungi data dari penghapusan yang tidak disengaja atau *fraud*.

---

## FAQ

**Q: Saya tidak menemukan unit yang mau di-BAST di dalam daftar pilihan. Kenapa?**
> Cek status unit tersebut:
> *   Jika mau BAST K-D: Pastikan progress konstruksi sudah di-input **100%**.
> *   Jika mau BAST D-K: Pastikan unit tersebut sudah **BAST K-D** duluan dan status konsumen sudah **Akad**.

**Q: Apakah masa garansi konsumen bisa diubah manual?**
> Secara default, AMS mengunci masa garansi konsumen (ex: 90 hari) untuk standarisasi. Jika ada kesepakatan khusus yang mengharuskan perubahan hari, Administrator untuk penyesuaian *bypass* atau edit data.

**Q: Apakah saya bisa mengedit file lampiran BAST setelah disimpan?**
> **Bisa.** Masuk ke menu Edit, lalu upload file baru. File lama akan otomatis ditimpa/dihapus dari server untuk menghemat penyimpanan.

**Q: Apa indikator "Sisa Garansi" di tabel depan?**
> Itu adalah hitungan mundur otomatis (Real-time). Tanggal BAST + Masa Garansi = Tanggal Expired. Sistem membandingkannya dengan hari ini untuk memberi Anda peringatan visual kapan kewajiban perbaikan gratis berakhir.
