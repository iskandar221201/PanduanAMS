# 🏗️ Panduan Modul Konstruksi (Construction)

Modul **Konstruksi** di AMS dirancang untuk memantau progress pembangunan unit, fasum, dan perbaikan garansi secara *real-time*, akurat, dan transparan. Modul ini menggantikan laporan manual dengan sistem pelacakan digital yang terintegrasi dengan bukti visual (foto).

---

## 1. Fitur Utama & Keunggulan 

### A. Template Pekerjaan (Construction Templates)
AMS memiliki sistem **Template Konstruksi** untuk mempercepat pembuatan target pembangunan.
*   **Standarisasi:** Anda bisa membuat template standar (misal: "Rumah Type 36", "Ruko 2 Lantai") yang berisi daftar item pekerjaan lengkap dengan volume dan satuannya.
*   **Auto-Bobot (Smart Weighting):** Anda hanya perlu memasukkan **Volume** pekerjaan. AMS akan **otomatis menghitung Bobot (%)** setiap item berdasarkan proporsinya terhadap total volume proyek. Tidak perlu hitung manual!
*   **Fleksibilitas:** Template bisa dibuat untuk satu proyek spesifik atau tersedia secara **Global** untuk semua proyek.

### B. Pelacakan Progress Real-Time (Tracking)
*   **Kumulatif & Valid:** Input progress dilakukan secara kumulatif (0-100%). Sistem memvalidasi agar progress tidak bisa di-input mundur (lebih kecil dari progress sebelumnya), menjaga integritas data.
*   **Bukti Wajib (Evidence-Based):** Setiap update progress **WAJIB** menyertakan foto lapangan. Foto ini otomatis diberi *watermark* nama proyek untuk mencegah pemalsuan.
*   **Riwayat (History Log):** Setiap perubahan progress tercatat lengkap: Siapa yang update, kapan, berapa persen perubahannya, dan foto buktinya. Anda bisa melihat riwayat detail per item pekerjaan.

### C. Integrasi Klaim Garansi
Modul ini juga menangani **Perbaikan Garansi**.
*   Klaim garansi (Komplain) yang sudah disetujui (Processed) bisa langsung dijadikan **Target Konstruksi**.
*   Teknisi bisa melaporkan progress perbaikan garansi sama seperti melaporkan progress bangun rumah baru.

---

## 2. Alur Kerja (Workflow)

### A. Persiapan: Membuat Template (Opsional tapi Disarankan)
1.  Masuk ke menu **Konstruksi > Template**.
2.  Klik **Buat Template Baru**.
3.  Masukkan Nama Template (misal: "Pos Jaga Standar").
4.  Input daftar item pekerjaan, satuan, dan volume.
5.  Simpan. AMS akan menghitung bobot masing-masing item.

### B. Membuat Target Pembangunan
1.  Masuk ke menu **Konstruksi > Progress**.
2.  Klik **Buat Target Baru**.
3.  Pilih Tipe Target:
    *   **Unit:** Untuk pembangunan rumah konsumen (Pilih Blok/Nomor).
    *   **Fasum:** Untuk fasilitas umum (Gerbang, Jalan, Taman).
    *   **Garansi:** Untuk perbaikan komplain konsumen.
4.  Lengkapi data SPK (Nomor SPK, Kontraktor, Tanggal Mulai/Selesai).
5.  **Isi Item Pekerjaan:**
    *   **Cara Cepat:** Pilih "Load Template" untuk memuat daftar item dari template yang sudah dibuat.
    *   **Cara Manual:** Input item satu per satu.
6.  Klik **Simpan**.

### C. Update Progress Lapangan (Harian/Mingguan)
1.  Di daftar target, klik tombol **Track** (ikon meteran).
2.  Anda akan melihat daftar item pekerjaan. Cari item yang ada kemajuan.
3.  Klik tombol **Update** pada item tersebut.
4.  Masukkan **% Progress Terbaru** (misal: dari 50% menjadi 75%).
5.  Upload **Foto Bukti** (Bisa lebih dari 1 foto).
6.  Klik **Simpan**.
    *   *Sistem otomatis menghitung ulang Total Progress Proyek berdasarkan bobot item yang diupdate.*

---

## 3. Validasi & Keamanan Sistem

AMS menerapkan aturan ketat (Strict Validation) untuk memastikan data konstruksi valid:

1.  **Anti-Mundur (No Backward Progress):**
    *   Sistem menolak input jika persentase baru **lebih kecil** dari persentase saat ini. Progress harus selalu maju.
2.  **Batas 0-100%:**
    *   Progress tidak boleh minus atau melebihi 100%.
3.  **Wajib Foto:**
    *   Form update tidak bisa dikirim tanpa melampirkan minimal 1 foto bukti.
4.  **Secure Delete (Penghapusan Aman):**
    *   Target konstruksi yang **sudah memiliki progress** (>0%) **TIDAK BISA DIHAPUS** sembarangan.
    *   Untuk menghapusnya, diperlukan **Otorisasi Khusus** (Request Delete Token) dari Direktur/Supervisor. Ini mencegah penghapusan data proyek yang sedang berjalan secara tidak sengaja atau jahat.
5.  **Kunci Edit Item:**
    *   Item pekerjaan yang sudah ada progress-nya tidak bisa dihapus dari daftar item.

---

## 4. Laporan & Monitoring

Di halaman Tracking, Anda mendapatkan informasi visual yang lengkap:
*   **Progress Bar:** Visualisasi kemajuan per item dan total proyek (Warna Kuning = On Progress, Hijau = Selesai).
*   **Identitas Proyek:** Info lengkap unit, kontraktor, dan masa pengerjaan.
*   **Print/Export:** Laporan progress bisa langsung di-export ke **PDF** (dengan foto), **Excel**, atau di-**Print** untuk laporan fisik ke manajemen/konsumen.

---

## 5. FAQ (Frequently Asked Questions)

**Q: Saya salah input progress (contoh: seharusnya 70% tapi diinput 50%). Bagaimana cara memperbaikinya?**
> Jika progress **maju** (misalnya dari 40% ke 70% tapi salah input 50%), Anda cukup input ulang dengan angka yang benar (70%). Sistem akan mencatat update terakhir sebagai progress valid.
>
> Namun, jika Anda ingin **mundur** (misalnya salah input 80% padahal baru 50%), Anda **tidak bisa langsung mengeditnya**. Ini adalah proteksi sistem. Anda harus menghubungi Administrator yang memiliki akses *database* atau fitur reset khusus (jika diaktifkan) untuk membatalkan progress yang salah tersebut.

**Q: Apakah saya bisa menambah item pekerjaan di tengah jalan?**
> **Bisa.** Selama target konstruksi belum berstatus *Completed* (Selesai 100%), Anda bisa masuk ke menu **Edit Item** untuk menambah item pekerjaan baru atau mengubah volume. Ingat, perubahan volume akan mempengaruhi bobot (%) item lainnya secara otomatis.

**Q: Mengapa saya tidak bisa menghapus item pekerjaan tertentu?**
> Item pekerjaan yang **sudah memiliki progress** (>0%) dikunci oleh sistem agar riwayatnya tidak hilang. Jika item tersebut batal dikerjakan, maka biarkan saja, karena memang pekerjaan tersebut sudah dilaksanakan dan perusahaan sudah mengeluarkan biaya.

**Q: Apakah foto bukti bisa di-upload belakangan?**
> **Tidak.** Sistem mewajibkan foto bukti di-upload *bersamaan* saat Anda menginput angka progress. Ini untuk memastikan validitas data bahwa pekerjaan benar-benar sudah dikerjakan saat laporan dibuat.

**Q: Bagaimana jika proyek berhenti sementara (On Hold)?**
> Biarkan statusnya tetap berjalan. Tidak ada tombol "Pause". Cukup hentikan update progress. Nanti saat proyek dilanjutkan, tinggal lanjutkan update progress seperti biasa. Riwayat tanggal update akan mencerminkan periode vakum tersebut.