# 🏦 Panduan Modul Data SLIK (BI Checking)

Modul **Data SLIK** digunakan untuk mengelola pengajuan dan hasil pengecekan riwayat kredit konsumen (Sistem Layanan Informasi Keuangan OJK). Modul ini berfungsi sebagai gerbang verifikasi awal sebelum konsumen diperbolehkan melakukan Booking Unit atau pengajuan KPR.

Dengan modul ini, tim Admin KPR dapat memantau status kelayakan konsumen secara terpusat, dan sales akan otomatis mendapatkan notifikasi hasil pengecekan.

---

## 1. Alur Kerja (Workflow)

Proses SLIK di sistem AMS mengikuti tahapan berikut:

1.  **Pra-Syarat**: Marketing menginput data Konsumen (Prospek) dengan status "SLIK" dan **wajib melengkapi NIK**.
2.  **Pengajuan**: Admin KPR membuat data pengajuan SLIK baru dengan status awal `PROSES`.
3.  **Pengecekan**: Tim Admin KPR melakukan pengecekan manual ke sistem OJK (iDebku) atau vendor pihak ketiga.
4.  **Update Hasil**: Admin KPR mengupdate data di AMS berdasarkan hasil resmi:
    *   **DITERIMA:** Konsumen bersih atau hutang lancar. (Upload Bukti Slik Wajib).
    *   **DITOLAK:** Konsumen masuk daftar hitam/kredit macet. (Upload Bukti Slik Wajib).

---

## 2. Cara Membuat Pengajuan SLIK Baru

1.  Buka menu **Data SLIK**.
2.  Klik tombol hijau **+ Tambah SLIK**.
3.  **Pilih Nama Prospek:**
    *   Ketik nama konsumen di kolom pencarian. *Hanya prospek yang sudah memiliki NIK yang valid dan status di modul prospek -> 'SLIK' yang akan muncul.*
    *   *Perhatian:* Jika NIK prospek sudah ada (duplikat), AMS akan menolak dan meminta Anda menghubungi marketing terkait.
4.  **Verifikasi Dokumen Awal:**
    *   Gunakan tombol *toggle* (saklar) untuk menandai dokumen fisik apa saja yang sudah Anda terima (KTP Pengaju, KK, KTP Pasangan).
    *   Ini berfungsi sebagai *checklist* kelengkapan berkas.
5.  Klik **Simpan**.
    *   Data akan muncul di tabel utama dengan status `PROSES`.

---

## 3. Mengupdate Hasil SLIK (Approve/Reject)

Setelah Anda selesai melakukan pengecekan dan mendapatkan berkas PDF/Gambar hasil SLIK, segera update status di AMS:

1.  Di daftar tabel, klik tombol **Edit (Ikon Pensil)** pada nama konsumen yang bersangkutan.
2.  **Ubah Status:**
    *   Pilih `DITERIMA` jika hasil bagus.
    *   Pilih `DITOLAK` jika hasil buruk (Kredit macet/Kol 5).
3.  **Upload Bukti (Wajib):**
    *   Jika status diubah menjadi Diterima/Ditolak, AMS **mewajibkan** Anda mengunggah file bukti (PDF/JPG/PNG, Max 2MB).
    *   Ini untuk arsip agar tidak ada manipulasi data hasil pengecekan.
4.  **Isi Catatan:** Tambahkan keterangan detail (misal: "Lunas bersyarat", "Ada tunggakan paylater 500rb", dll).
5.  Klik **Perbarui Data**.

> **🔔 Notifikasi Otomatis:**
> Setelah Anda menyimpan perubahan status, AMS akan otomatis mengirim notifikasi ke akun Sales/Marketing yang menangani konsumen tersebut agar mereka bisa segera tindak lanjut (misal: Konfirmasi Booking atau Pembatalan).

---

## 4. Navigasi & Fitur Lainnya

### Verifikasi Dokumen (Badges)
Di tabel utama, Anda bisa melihat kolom **Verifikasi** dengan indikator warna:
*   <span style="color:green">✅ KTP</span> : Dokumen fisik sudah diterima admin.
*   <span style="color:red">❌ KK</span> : Dokumen fisik belum diterima/belum diverifikasi.


### Cetak Laporan
Gunakan tombol di atas tabel untuk mengekspor data:
*   **Excel/PDF**: Untuk laporan bulanan ke manajemen.
*   **Print**: Mencetak daftar antrian pengecekan hari ini.

---

## FAQ (Tanya Jawab)

**Q: Kenapa NIK di form tambah SLIK terkunci (Read-Only)?**
> Untuk menjaga integritas data. NIK ditarik otomatis dari data master Prospek. Jika ada kesalahan NIK, minta Marketing memperbaiki data di menu Prospek terlebih dahulu.

**Q: Saya tidak bisa menyimpan status "DITERIMA", muncul error validasi?**
> Pastikan Anda sudah mengupload file bukti hasil SLIK. Sistem melarang perubahan status menjadi final tanpa adanya bukti dokumen yang diunggah.

