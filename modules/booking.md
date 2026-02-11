# 📘 Panduan Modul Data Booking

Modul **Data Booking** digunakan untuk mengelola data unit yang sudah **resmi terjual** (status: *Sold/Booked*). Modul ini melanjutkan proses dari *Pengajuan Booking*. Di sini, Admin KPR memantau dan melakukan update progres konsumen mulai dari pemberkasan hingga Akad Kredit.

---

## 1. Fitur Utama
### A. Monitoring & Filter Data
Halaman utama menampilkan daftar seluruh booking aktif. Fitur yang tersedia:
*   **Filter Project**: Memilih data berdasarkan proyek (jika user memiliki akses multi-project).
*   **Filter Status**: Menyaring data berdasarkan status transaksi (misal: *Pemberkasan*, *Proses Bank*, *SP3K*, dll).
*   **Export Data**: Unduh laporan dalam format **Excel** atau **PDF**, atau cetak langsung.
*   **Durasi Proses**: Sistem otomatis menghitung berapa hari konsumen tersebut dari booking sampai akad/reject/mundur (Indikator kinerja).

### B. Update Progres Konsumen (Edit Booking)
Admin dapat mengubah status transaksi seiring berjalannya proses KPR/Cash.

**Validasi Penting Sistem:**
1.  **Pindah ke Proses Bank**: Hanya bisa dilakukan jika bukti **Serah Terima Berkas** sudah diupload di modul Pemberkasan.
2.  **Pindah ke Akad**: Hanya bisa dilakukan jika **DP (Uang Muka) sudah LUNAS** di modul Keuangan.
3.  **Pindah Unit (Tukar Kavling)**:
    *   Hanya diizinkan jika status masih **Pemberkasan**.
    *   Hanya diizinkan dalam waktu **14 hari** sejak tanggal booking.
    *   *System Action:* Jika unit dipindah, sistem otomatis men-generate **SPR Baru** dan membatalkan SPR lama.

**Kolom yang Dikunci (Read-Only):**
Demi keamanan data, kolom berikut **tidak dapat diubah** setelah booking dibuat:
*   Nama Konsumen
*   Nama Sales
*   Tanggal Booking
*   Nominal Harga (Booking, DP, Hook)

### C. Pivot Report
Fitur analisis data (Business Intelligence) sederhana.
*   **Drag & Drop**: Tarik kolom seperti "Sales", "Bulan", atau "Status" untuk membuat laporan dinamis.
*   **Fungsi**: Melihat total omset, jumlah unit terjual per sales, atau tren penjualan bulanan.

### D. Penghapusan Data (Delete)
**⚠️ PENTING: Data Booking TIDAK BOLEH DIHAPUS.**

Menghapus data akan menghilangkan rekam jejak penjualan dan keuangan. Jika konsumen membatalkan pembelian atau ditolak bank:
*   **Jangan Hapus Data.**
*   **Ubah Status menjadi "Mundur" atau "Reject".**
*   Dengan cara ini, unit otomatis kembali *Tersedia*, namun riwayat bahwa "konsumen A pernah booking unit B" tetap tersimpan untuk audit di masa depan.

---

## 2. Alur Status Transaksi (Workflow)

Berikut adalah tahapan status yang umum dilalui konsumen:

1.  **Pemberkasan**: Status awal setelah booking di-ACC. Menunggu konsumen mengumpulkan berkas KPR.
2.  **Proses Bank**: Berkas lengkap dan sudah masuk ke Bank untuk analisa.
3.  **SP3K**: Surat Penegasan Persetujuan Penyediaan Kredit sudah keluar dari Bank.
4.  **Akad**: Proses penandatanganan jual beli (AJB) dan pencairan dana.
5.  **Cash Bertahap / Cash**: Jalur alternatif untuk pembayaran tunai.
6.  **Mundur / Reject**: Jika konsumen membatalkan pembelian atau ditolak Bank. Unit akan kembali *Tersedia*.

---

## 3. FAQ (Tanya Jawab)

**Q: Mengapa saya tidak bisa mengubah status ke "Proses Bank"?**
> Cek apakah Anda sudah mengupload dokumen "Bukti Serah Terima" di menu Pemberkasan untuk konsumen tersebut. AMS mewajibkan bukti ini.

**Q: Bagaimana cara memindahkan konsumen ke unit lain?**
> Buka menu Edit. Jika masih dalam periode 14 hari dan status Pemberkasan, kolom Unit/Kavling akan bisa diklik. Pilih unit baru yang tersedia.

**Q: Mengapa tidak ada tombol Hapus?**
> Sesuai prosedur audit, data booking **dilarang dihapus**. Jika konsumen batal, cukup ubah status transaksi menjadi **Mundur** atau **Reject**. Unit otomatis kembali tersedia tanpa menghilangkan riwayat.
