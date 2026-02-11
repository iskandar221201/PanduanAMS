# 💰 Panduan Modul Pengajuan Dana

Modul **Pengajuan Dana** di AMS dirancang untuk menangani seluruh siklus permintaan dana operasional dan proyek, mulai dari pengajuan staf, review finance, hingga persetujuan manajerial dan pelaporan realisasi.

Modul ini menggantikan proses manual (kertas/email) dengan sistem terpusat yang transparan dan akuntabel.

---

## 1. Fitur Unggulan (Powerful Features)

### A. Alur Persetujuan Bertingkat (Multi-Level Approval)
Sistem membedakan peran dan wewenang secara jelas:
1.  **Requester (Staff):** Mengajukan dana.
2.  **Reviewer (Finance):** Memeriksa kelengkapan, menyesuaikan nominal (jika perlu), dan memvalidasi bukti.
3.  **Approver (Manager/Direktur):** Memberikan persetujuan akhir (Accept/Reject) berdasarkan rekomendasi Finance.

### B. Penomoran Dokumen Cerdas (Smart Numbering)
AMS otomatis menghasilkan Nomor Pengajuan yang unik dan informatif dengan format:
`[PREFIX].[URUT]/[PROJECT]/[BULAN]/[TAHUN]`
Contoh: **PP.0001/MSP/IX/2026**
*   **PP/BS**: Kode Kategori (Pembayaran / Cash Advance).
*   **0001**: Nomor urut per proyek per tahun (reset setiap tahun).
*   **MSP**: Inisial Proyek (Otomatis dari nama proyek, misal "Mutiara Sentul Pratama").
*   **IX**: Bulan Romawi.
*   **2026**: Tahun.

### C. Kontrol Anggaran (Budget Control)
*   **Realisasi vs Pengajuan:** Finance bisa mengubah/mengoreksi nominal yang disetujui *per item*. Jika pengajuan Rp 1.000.000 tapi struk pasar hanya Rp 900.000, Finance bisa menginput realisasi Rp 900.000.
*   **Bukti Pendukung Wajib:** Upload berkas (foto/PDF) bersifat wajib untuk mencegah klaim fiktif.

### D. Rekapitulasi Otomatis (Auto-Recap)
Fitur favorit tim Finance:
*   **Export Batch:** Bisa mencetak "Rekap Review" yang berisi puluhan pengajuan sekaligus dalam satu dokumen PDF/Excel untuk dimintakan tanda tangan basah pimpinan.
*   **Tracking Rekap:** Setiap kali export, sistem mencatat log dan memberikan Nomor Rekap baru untuk arsip.

---

## 2. Alur Kerja (Workflow)

### Tahap 1: Pengajuan (Requester)
*Aktor: Staff Divisi / Site Manager*
1.  Masuk ke menu **Pengajuan Dana > Buat Pengajuan**.
2.  Pilih **Kategori** (Pembayaran Langsung atau Cash Advance).
3.  Isi **Judul** dan **Deskripsi** kebutuhan.
4.  Input **Detail Item** (Nama Barang, Qty, Harga Satuan). Sistem otomatis menghitung Total.
5.  **Upload Berkas:** Lampirkan bukti awal (Invoice/Nota Tagihan/Foto Kerusakan).
6.  Klik **Kirim**. Status: *Pending*.

### Tahap 2: Review & Verifikasi (Finance)
*Aktor: Staff Finance / Admin Keuangan*
1.  Masuk ke menu **Konfirmasi Dana**.
2.  Lihat daftar status *Pending*. Klik **Detail**.
3.  Klik **Mulai Review**. Status berubah jadi *Review* (terkunci dari edit user).
4.  **Verifikasi Item:**
    *   Cek kesesuaian harga dan bukti.
    *   Input **Nominal Realisasi** (bisa lebih kecil dari pengajuan).
    *   Tandai item sebagai *Confirmed* (OK) atau *Rejected* (Tolak).
5.  Input **Catatan Validasi** dan Upload Bukti Validasi
6.  Klik **Simpan & Kirim**. Status jadi *Confirmed*.

### Tahap 3: Persetujuan Akhir (Manager)
*Aktor: Manager*
1.  Menerima notifikasi pengajuan yang sudah di-review Finance.
2.  Buka detail pengajuan (Status: *Confirmed*).
3.  Lihat perbandingan **Nominal Pengajuan vs Realisasi Finance**.
4.  Klik **Setujui (Accept)** untuk mencairkan dana, atau **Tolak (Reject)** untuk membatalkan.

---

## 3. Validasi & Aturan Sistem (AMS Rules)

1.  **Validasi Nominal:**
    *   Total pengajuan tidak boleh 0 atau negatif.
    *   Minimal harus ada 1 item transaksional.
2.  **Kunci Edit (Lock Mechanism):**
    *   Pengaju hanya bisa mengedit/menghapus data saat status masih **Draft**.
    *   Begitu status naik ke **Pending** atau **Review**, data terkunci permanen untuk menjaga integritas audit.
3.  **Lingkup Akses (Data Scope):**
    *   **Staff:** Hanya bisa melihat pengajuan miliknya sendiri.
    *   **Finance/Manager:** Bisa melihat seluruh pengajuan lintas divisi dan proyek (sesuai hak akses).
4.  **Limitasi File:**
    *   Maksimal 5 file per pengajuan.
    *   Format: PDF, JPG, PNG.
    *   Ukuran Maks: 5MB per file.

---

## 4. Laporan & Export

Modul ini menyediakan opsi export yang lengkap di menu **Konfirmasi Dana**:
1.  **PDF Landscape:** Format resmi dengan kolom Tanda Tangan (Pemohon, Pemeriksa, Penyetuju) siap cetak.
2.  **Excel (XLS):** Format tabel rapi untuk arsip digital atau copy-paste ke laporan bulanan.
3.  **CSV:** Data mentah untuk diolah lebih lanjut di aplikasi akuntansi eksternal.

> **Tips:** Gunakan fitur "Filter Tanggal" sebelum melakukan Export untuk membuat laporan mingguan atau bulanan yang spesifik.

---

## FAQ

**Q: Saya salah input nominal dan sudah terlanjur Kirim (Pending). Bagaimana?**
> Segera hubungi tim Finance untuk menolak (Reject) pengajuan tersebut. Setelah ditolak atau masih status Pending,lalu buat pengajuan baru yang benar.

**Q: Apakah Cash Advance harus lapor realisasi lagi?**
> Modul ini fokus pada **Pencairan Dana**. Untuk pertanggungjawaban pemakaian Cash Advance (Bon/Sementara), akan ditangani di modul terpisah (*Penggunaan Dana*) yang terhubung dengan ID Pengajuan ini.

**Q: Kenapa tombol "Project" tidak bisa dipilih?**
> Kolom Project otomatis terkunci sesuai dengan penempatan kerja Anda di sistem User Management. Jika Anda pindah proyek, hubungi HR/Admin untuk update data user Anda.
