# 📝 Panduan Modul Pengajuan Booking & SPR

Modul **Pengajuan Booking** adalah pintu gerbang utama penjualan unit. Fitur ini memfasilitasi proses validasi pembayaran _booking fee_ dari marketing ke Admin Keuangan sebelum unit dinyatakan resmi terjual (Sold/Booked).

Selain manajemen status unit, modul ini juga dilengkapi dengan **Generator SPR (Surat Pesanan Rumah) Otomatis**, sehingga marketing tidak perlu lagi mengetik dokumen SPR secara manual.

---

## 1. Alur Kerja (Workflow)

Berikut adalah perjalanan data dari marketing hingga terbitnya SPR:

1.  **Input Pengajuan (marketing)**: marketing memilih konsumen (yang lolos SLIK) dan unit yang tersedia, lalu mengupload bukti transfer.
2.  **AMS Mengunci Unit (Hold)**: Otomatis status unit di *Siteplan* berubah menjadi `Hold` agar tidak dijual ganda (*double booking*).
3.  **Verifikasi (Admin)**: Admin Keuangan mengecek uang masuk di rekening.
4.  **Keputusan (Admin)**:
    *   ✅ **ACC (Setujui)**: Status unit lanjut ke `Pemberkasan`. Data masuk ke laporan penjualan resmi. **SPR Terbit**.
    *   ❌ **REJECT (Tolak)**: Status unit kembali `Tersedia`. marketing harus revisi atau unit dilepas ke orang lain.
    *   ⛔ **TIDAK_BERLAKU**: Status ini muncul otomatis jika ada pengajuan lain untuk unit yang sama yang lebih dulu di-ACC, atau jika Marketing melakukan revisi (edit) pada pengajuan yang masih Pending (pengajuan lama dianggap tidak berlaku).

---

## 2. Fitur marketing: Membuat Pengajuan Baru

Marketing hanya dapat mengajukan booking jika syarat berikut terpenuhi:
*   Data Prospek sudah ada dan **SLIK disetujui (DITERIMA)**.
*   Status Unit di Siteplan adalah **Tersedia**.
*   Status Prospek di Modul Prospek adalah **Booking**.

### Langkah-langkah:
1.  Masuk ke menu **Pengajuan Booking**.
2.  Klik tombol **+ Ajukan Booking Baru**.
3.  **Isi Form:**
    *   **Konsumen:** Pilih nama prospek.
    *   **Unit:** Pilih blok/nomor unit.
    *   **Tenor:** Masukkan rencana jangka waktu KPR (Bulan).
    *   **Bukti Transfer (Wajib):** Upload foto/screenshot bukti transfer Booking Fee (Max 5MB).
    *   **Dokumen Pendukung (Opsional):** Upload KTP/NPWP jika diperlukan.
4.  Klik **Simpan**.

> **⚠️ Catatan Penting:** Saat Anda klik Simpan, unit tersebut langsung dikunci (Status: **Hold**) selama 24 jam atau sampai Admin merespon. Pengajuan lain yang tertunda untuk unit yang sama otomatis dibatalkan AMS.

---

## 3. Fitur Admin: Konfirmasi & Validasi

Admin (Role Keuangan/Manager) bertugas memvalidasi pembayaran.

### Cara Memproses Pengajuan:
1.  Buka menu **Pengajuan Booking**.
2.  Lihat tabel atau klik tombol **"Pengajuan Pending"** (warna kuning) di atas.
3.  Klik tombol **Proses** pada pengajuan yang masuk.
4.  **Cek Bukti Transfer:** Klik tombol biru "Transfer" untuk melihat bukti bayar.
5.  **Ambil Keputusan:**
    *   Pilih **ACC** jika uang sudah masuk.
    *   Pilih **REJECT** jika bukti palsu atau uang belum masuk.
6.  **Catatan:** Tambahkan pesan untuk marketing (misal: "Transfer kurang 500rb", "ACC - Ditunggu berkas fisik").
7.  Klik **Simpan Konfirmasi**.

### Dampak Keputusan ACC:
*   Status Pengajuan: `ACC`.
*   Status Unit: Berubah jadi `Pemberkasan`.
*   **Data Booking**: Terbuat otomatis di modul "Data Booking".
*   **SPR**: Dokumen SPR tercetak otomatis oleh AMS.

---

## 4. AMS Generator SPR Otomatis

AMS ini memiliki fitur *Auto-Generate SPR* sehingga Anda tidak perlu membuat dokumen Word/Excel manual.

### Cara Kerja:
Begitu Admin klik **ACC**, AMS langsung:
1.  Mengambil **Template SPR** proyek terkait.
2.  Mengambil nomor urut surat terakhir (Format: `001/GWB/SPR/II/2026`).
3.  Menggabungkan data:
    *   Data Konsumen (Nama, NIK, Alamat, Pekerjaan).
    *   Data Unit (Blok, No, Luas Tanah/Bangunan, Harga Jual).
    *   Data Transaksi (Tenor, Tanggal ACC).
4.  Menyimpan hasil jadinya dalam format PDF siap cetak.

### Cara Melihat/Mencetak SPR:
1.  Di tabel Pengajuan Booking, cari kolom **Aksi**.
2.  Klik tombol warna biru muda **📄 SPR**.
3.  Halaman SPR akan terbuka.
4.  Klik tombol **Download PDF / Print** di pojok kanan atas untuk mencetak atau menyimpan.

---

## 5. Laporan & Analisis (Pivot)

Untuk melihat performa penjualan secara luas, gunakan fitur **Pivot Report**.
*   Akses: Klik tombol biru **Pivot Report** di halaman utama index.
*   Fungsi: Anda bisa menarik data (Drag & Drop) untuk melihat:
    *   Total Booking per marketing.
    *   Penjualan per Bulan/Tahun.
    *   Rata-rata Tenor yang diambil konsumen.

---

## FAQ (Tanya Jawab)

**Q: Kenapa saya tidak bisa memilih unit tertentu?**
> Unit tersebut mungkin statusnya tidak "Tersedia" (sedang di-Hold marketing lain atau sudah Terjual).*

**Q: Apa yang terjadi jika pengajuan saya di-Reject?**
> Unit akan kembali menjadi "Tersedia" dan bisa diambil oleh marketing lain. Anda harus membuat pengajuan ulang jika ingin memproses lagi.*

**Q: Apakah SPR bisa diedit manual?**
> Tidak. SPR digenerate otomatis dari data AMS untuk menjamin keaslian data. Jika ada kesalahan (misal salah eja nama), Admin harus mengedit data di Master Prospek/Unit, lalu simpan ulang bookingnya (jika memungkinkan) atau hubungi Administrator.*

**Q: Berapa lama unit di-Hold saat status Pending?**
> Default AMS adalah 24 jam. Jika Admin tidak memproses dalam waktu tersebut, status akan menjadi EXPIRED dan unit kembali Tersedia secara otomatis.*

**Q: Kenapa status pengajuan saya berubah jadi "TIDAK_BERLAKU"?**
> Status ini muncul otomatis oleh AMS jika Anda melakukan **Edit/Revisi** pada pengajuan yang masih PENDING. AMS akan membuat pengajuan baru dengan data revisi, dan menandai pengajuan lama sebagai tidak berlaku agar admin tidak bingung memproses data ganda. Status ini juga bisa muncul jika unit yang Anda ajukan ternyata sudah di-ACC untuk marketing lain lebih dulu.
