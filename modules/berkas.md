# 📂 Panduan Modul Pemberkasan KPR

Modul ini dirancang khusus untuk **Admin KPR** guna memonitor dan memverifikasi kelengkapan dokumen konsumen. Tujuan utamanya adalah memastikan semua persyaratan KPR terpenuhi sebelum berkas diserahkan ke Bank.

## 1. Monitoring Data

Halaman utama menampilkan daftar konsumen yang sedang dalam tahap **Pemberkasan**.
*   **Progress Bar:** Menunjukkan persentase kelengkapan berkas secara real-time.
*   **Status Durasi:** Menghitung berapa lama konsumen tertahan di tahap ini.
*   **Filter Project:** Admin yang memegang banyak proyek dapat memfilter data agar lebih fokus.

### Logika Perhitungan Durasi (SLA)
AMS menghitung "Durasi Proses" dengan logika berikut agar kinerja terukur akurat:

1.  **Sedang Berjalan:**
    *   Rumus: `Hari Ini` - `Tanggal Mulai Pemberkasan` + 1 Hari.
    *   *Contoh:* Konsumen masuk tahap pemberkasan hari ini, maka durasi tertulis **1 Hari**.

2.  **Selesai (Completed):**
    *   Rumus: `Tanggal Upload Serah Terima` - `Tanggal Mulai Pemberkasan` + 1 Hari.
    *   **Kondisi Selesai:** Perhitungan durasi berhenti tepat saat Admin mengupload dokumen **Bukti Serah Terima (Kode: SERAH_TERIMA)**. Meski status transaksi konsumen mungkin belum berubah (misal masih belum diserahkan ke Bank), durasi pemberkasan sudah dianggap selesai (KPI tercapai).
    *   Angka ini **dikunci/frozen** selamanya sebagai catatan sejarah kinerja.

---

## 2. Proses Verifikasi Berkas

Untuk memverifikasi berkas konsumen, klik tombol **Upload/Edit** (ikon panah hijau) pada baris nama konsumen.

### Checklist (Verifikasi Manual)
Sistem AMS menggunakan metode *digital checklist*:
*   Anda tidak perlu mengupload fisik setiap lampiran (KTP, NPWP, dll) satu per satu ke dalam sistem, karena akan membebani server dan waktu.
*   Cukup periksa berkas fisik/email dari sales, lalu **klik toggle/switch** di sistem untuk menandai bahwa berkas tersebut "Ada/Lengkap".
*   Progress bar akan otomatis naik seiring checklist yang Anda centang.

### Finalisasi: Bukti Serah Terima
Ini adalah langkah terpenting untuk menyelesaikan tahap pemberkasan.
1.  Pastikan semua checklist persyaratan sudah **100% Lengkap** (semua toggle hijau).
2.  Bagian bawah halaman ("Simpan / Upload Bukti") akan terbuka (tidak terkunci lagi).
3.  Upload dokumen **Tanda Terima Berkas** (biasanya scan PDF tanda terima fisik yang ditandatangani Bank atau internal).
4.  **Simpan.**

> **⚠️ PENTING:** Setelah Bukti Serah Terima diupload, data pemberkasan akan **TERKUNCI MATI (Read Only)**. Anda tidak bisa lagi mengubah checklist atau membatalkan status kelengkapan demi menjaga integritas data audit.

---

## 3. Logika Master Berkas (Dinamis vs Statis)

AMS memiliki fitur cerdas dalam menangani perubahan persyaratan dokumen (Master Berkas). Berikut perilakunya:

### A. Untuk Konsumen Aktif (Sedang Pemberkasan)
Jika Management menambah persyaratan baru (misal: Menambah "Surat Pernyataan Belum Menikah") di Master Berkas:
*   Persyaratan itu **otomatis muncul** di checklist semua konsumen yang statusnya sedang 'Pemberkasan'.
*   Persentase kelengkapan konsumen tersebut mungkin turun (misal dari 100% jadi 90%) karena ada hutang dokumen baru.
*   Logika ini memastikan standar terbaru selalu diterapkan untuk proses yang sedang berjalan.

### B. Untuk Konsumen Selesai (Sudah Serah Terima/Akad)
Jika konsumen sudah selesai tahap pemberkasan (sudah upload Bukti Serah Terima):
*   Data checklist mereka **DIBEKUKAN (Frozen)**.
*   Penambahan syarat baru di Master Berkas **TIDAK AKAN** mengubah data masa lalu mereka.
*   Ini penting agar data historis tetap valid sesuai persyaratan pada saat itu (tidak berubah merah/incomplete di masa depan).

---

## FAQ (Tanya Jawab)

**Q: Mengapa saya tidak bisa mengupload Bukti Serah Terima?**
> Pastikan semua toggle checklist persyaratan di atasnya sudah dicentang (100%). Sistem AMS mencegah finalisasi jika dokumen belum lengkap.

**Q: Apa akibatnya jika checklist sudah 100% tapi saya lupa upload Bukti Serah Terima?**
> AMS menganggap pekerjaan Anda **BELUM SELESAI**. Konsekuensinya:
> 1.  **Durasi Terus Berjalan:** Angka hari (KPI) Anda akan terus bertambah, membuat kinerja terlihat lambat.
> 2.  **Proses Terhambat:** Admin Marketing tidak akan bisa mengubah status konsumen ke "Proses Bank" karena sistem mewajibkan bukti ini.($validated)

**Q: Apakah saya bisa menghapus Bukti Serah Terima yang salah upload?**
> Secara default TIDAK BISA karena data langsung dikunci. Anda harus menghubungi Administrator untuk membuka kunci (rollback) transaksi tersebut secara manual dari database jika sangat mendesak.
