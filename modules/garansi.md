# 🛡️ Panduan Modul Garansi (Warranty)

Modul **Garansi** di AMS adalah solusi *end-to-end* untuk menangani keluhan konsumen (komplain) terkait unit atau fasilitas umum. Modul ini terintegrasi penuh dengan **Modul Konstruksi**, memastikan setiap komplain tidak hanya dicatat, tapi juga *dikerjakan* dan *dipantau* hingga tuntas.

---

## 1. Fitur Unggulan

### A. Integrasi Alur Kerja (Complaint-to-Construction)
AMS menghubungkan tim Layanan Pelanggan/Marketing dengan Tim Teknik secara mulus:
1.  Konsumen lapor -> Input di **Modul Garansi**.
2.  Admin setuju -> Data otomatis dikonversi menjadi **Template Konstruksi**.
3.  Tim Teknik mengerjakan -> Update di **Modul Konstruksi**.
4.  Selesai -> Upload bukti di **Modul Garansi**.

### B. Otomatisasi Template (Auto-Template Generation)
Salah satu fitur paling *powerful* di AMS. Saat Admin menyetujui klaim garansi (Review):
*   AMS **otomatis membuat Template Konstruksi** baru yang berisi daftar item perbaikan yang disetujui.
*   Tim Teknik tidak perlu mengetik ulang daftar kerusakan saat membuat SPK perbaikan. Cukup tarik data dari klaim tersebut.

### C. Validasi Bukti Visual (Before-After)
Sistem menuntut bukti visual yang lengkap:
*   **Foto Before:** Wajib di-upload saat pengajuan klaim.
*   **Foto After:** Wajib di-upload saat perbaikan selesai.
*   Kedua foto ini tersimpan permanen sebagai arsip digital untuk mencegah sengketa di kemudian hari.

---

## 2. Alur Kerja (Workflow)

### A. Pengajuan Klaim (Submission)
*Aktor: Marketing / Customer Service / Fasilitator*
1.  Masuk ke menu **Garansi > Pengajuan**.
2.  Klik **Buat Pengajuan Baru**.
3.  **Pilih Unit/BAST:** AMS hanya menampilkan unit yang **masih dalam masa garansi** dan **tidak sedang dalam perbaikan**.
4.  **Isi Detail Komplain:** Masukkan keluhan (misal: "Keramik Pecah", "Atap Bocor") dan upload **Foto Before**.
5.  Klik **Kirim**. Status: *Submitted*.

### B. Review & Persetujuan (Approval)
*Aktor: Project Manager (PM) / Supervisor*
1.  Masuk ke menu **Garansi > Review**.
2.  Buka detail klaim yang masuk.
3.  Untuk setiap item keluhan, tentukan keputusan: **Terima** atau **Tolak**.
4.  Klik **Simpan**.
    *   *Jika Diterima:* Status berubah menjadi *Processed*. AMS otomatis membuat *Template Konstruksi* untuk perbaikan ini.
    *   *Jika Ditolak:* Status menjadi *Rejected* dan proses berhenti.

### C. Eksekusi Perbaikan (Konstruksi)
*Aktor: Tim Teknik / Kontraktor*
1.  Di **Modul Konstruksi**, buat Target Baru dengan tipe **Warranty**.
2.  Pilih Klaim ID yang sudah disetujui tadi.
3.  Kerjakan perbaikan dan update progress secara berkala di Modul Konstruksi hingga **100%**.

### D. Finalisasi & Penutupan (Closing)
*Aktor: Project Manager (PM)*
1.  Setelah progress konstruksi mencapai 100%, kembali ke menu **Garansi > Monitoring**.
2.  Klik tombol **Upload After** pada item keluhan.
3.  Upload foto hasil perbaikan.
4.  Klik **Selesai (Complete)**.
5.  Setelah semua item selesai, klaim otomatis ditutup (Status: *Completed*).

### E. Pembatalan Klaim (Cancel)
*Aktor: Project Manager (PM) / Supervisor*
Jika ada kesalahan atau konsumen membatalkan permintaan, Anda bisa membatalkan klaim yang sedang berjalan.
1.  Masuk ke menu **Garansi > Review / Monitoring**.
2.  Buka detail klaim yang ingin dibatalkan.
3.  Klik tombol **Batalkan Klaim**.
    *   **Syarat:** Pembatalan hanya bisa dilakukan jika **Progress Konstruksi** masih **0%**.
    *   Jika progress sudah berjalan (> 0%), sistem akan menolak pembatalan. Anda harus me-reset progress dulu di Modul Konstruksi.
    *   *Efek:* Status klaim menjadi **Cancelled**. Target konstruksi terkait akan dihapus otomatis.
    *   **PENTING:** Setelah dibatalkan, unit tersebut **BISA diajukan klaim ulang** (selama masa garansi masih berlaku). Unit akan muncul kembali di daftar pilihan pengajuan.


---

## 3. Validasi & Aturan Sistem (AMS Rules)

AMS menerapkan validasi ketat untuk menjaga keteraturan data:

1.  **Cek Masa Garansi Otomatis:**
    *   Anda tidak bisa mengajukan klaim untuk unit yang masa garansinya sudah habis (berdasarkan tanggal BAST + periode garansi). Unit tersebut tidak akan muncul di daftar pilihan.
2.  **Satu Klaim Aktif per Unit:**
    *   Untuk mencegah duplikasi, AMS memblokir pengajuan baru jika unit tersebut sedang memiliki klaim yang berstatus *Submitted*, *Processed*, atau *Completed*.
    *   Jika status klaim sebelumnya adalah **Cancelled** atau **Rejected**, Anda **DIPERBOLEHKAN** mengajukan klaim baru.
3.  **Kunci Progress (Progress Interlock):**
    *   Anda **TIDAK BISA** meng-upload *Foto After* atau menutup klaim jika progress fisik di Modul Konstruksi belum mencapai **100%**. Ini memaksa data lapangan dan data administrasi agar selalu sinkron.
4.  **Syarat Pembatalan (Cancellation logic):**
    *   Klaim yang sudah disetujui hanya bisa dibatalkan jika **belum ada progress pengerjaan** (0%). Jika tukang sudah mulai bekerja (progress > 0%), klaim tidak bisa dibatalkan sepihak.

---

## FAQ

**Q: Bagaimana jika ada keluhan tambahan saat perbaikan sedang berlangsung?**
> Jika perbaikan masih berjalan (*Processed*), Anda tidak bisa membuat pengajuan baru untuk unit yang sama.
> *Solusi:* Tambahkan item pekerjaan baru secara manual di **Modul Konstruksi > Edit Item**. Namun, item tambahan ini tercatat sebagai pekerjaan konstruksi, bukan item klaim garansi resmi di awal.

**Q: Mengapa unit konsumen saya tidak muncul di form pengajuan?**
> Ada dua kemungkinan:
> 1. Masa garansi unit tersebut sudah habis.
> 2. Unit tersebut masih memiliki klaim garansi lain yang aktif.

**Q: Apakah saya bisa menghapus klaim yang salah input?**
> Tidak, klaim tidak bisa dihapus demi alasan audit jejak konstruksi.

**Q: Apakah saya bisa mengajukan klaim ulang jika klaim sebelumnya Ditolak atau Dibatalkan?**
> **BISA.** Jika klaim sebelumnya berstatus *Rejected* (Ditolak Admin) atau *Cancelled* (Dibatalkan), unit tersebut akan kembali muncul di daftar pilihan pengajuan, asalkan masa garansinya belum habis.

