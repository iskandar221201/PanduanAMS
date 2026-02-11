# 🏦 Panduan Modul Proses Bank KPR

Modul ini digunakan oleh **Admin KPR** untuk memonitor perkembangan pengajuan KPR konsumen ke pihak Bank. Modul ini mencatat timeline (kronologi) dari awal pengajuan hingga persetujuan (SP3K) atau penolakan.

## 1. Monitoring Status

Pada halaman utama, Anda akan melihat daftar semua konsumen yang status transaksinya berada di tahap **Proses Bank**.

*   **Status Proses:** Menampilkan tahapan terakhir yang tercatat (misal: *Analisa, OTS, Approved*).
*   **Durasi:** Menghitung sudah berapa lama konsumen berada dalam proses bank ini.
*   **Aksi "Lanjut":** Klik untuk menambah catatan tahapan baru.

### Logika Perhitungan Durasi (SLA)
AMS menghitung "Durasi Proses Bank" untuk mengukur kecepatan respon Bank atau kinerja tim KPR dalam mem-follow up.

1.  **Mulai (Start):**
    *   Dihitung sejak inputan tahapan **PERTAMA KALI** di modul ini (biasanya tahap `IDE` atau `Analis`).
    *   *Catatan:* Bukan dihitung sejak tanggal booking, tapi sejak berkas masuk ke Bank.

2.  **Berjalan (Running):**
    *   Selama status belum Final (belum Approved/Reject), durasi = `Hari Ini` - `Tanggal Tahap Pertama` + 1 Hari.

3.  **Selesai (Stop/Frozen):**
    *   Perhitungan berhenti otomatis jika tahapan terbaru yang diinput adalah **Approved** atau **Reject**.
    *   *Contoh:* Input pertama tgl 1 Jan. Input tahap 'Approved' tgl 10 Jan. Maka durasi terkunci di **10 Hari** selamanya.

---

## 2. Mengelola Tahapan (Update Progress)

Setiap ada perkembangan informasi dari pihak Bank, Admin KPR wajib mencatatnya di sistem.

### Menambah Tahapan Baru
1.  Klik tombol **Lanjut** (Play icon) pada baris konsumen.
2.  Di halaman detail, isi form "Tambah Tahapan Baru":
    *   **Tahapan:** Pilih status terbaru (lihat daftarnya di bawah).
    *   **Tanggal Dilakukan:** Tanggal kejadian sebenarnya (bisa mundur jika lupa input).
    *   **Keterangan:** Catatan detail, misal: *"Analisa data keuangan kurang lengkap"*.
    *   **Upload Berkas (Opsional):** Bukti email, surat penolakan, atau SP3K (PDF/Gambar Max 2MB).
3.  Klik **Simpan Tahapan**.
4.  Riwayat akan muncul di sebelah kanan (kronologis dari yang terlama ke terbaru).

### Daftar Opsi Tahapan
*   **IDE:** Input Data Entry (Awal masuk sistem bank).
*   **Analis:** Sedang dianalisa oleh analis kredit.
*   **OTS:** *On The Spot* (Survey lokasi/kantor/rumah).
*   **Approved:** Disetujui (SP3K Keluar). **(STOP Durasi)**
*   **Reject:** Ditolak Bank. **(STOP Durasi)**
*   **Pindah Bank:** Pengajuan dialihkan ke bank lain.
*   **Banding:** Proses banding sedang berjalan.

---

## 3. Koreksi Data (Edit)

Jika terjadi kesalahan input (salah tanggal atau salah upload file):
1.  Buka halaman detail konsumen tersebut.
2.  Di daftar Riwayat Tahapan (sebelah kanan), klik tombol **Pensil (Koreksi)** kecil di baris yang salah.
3.  Ubah data yang diperlukan, lalu klik **Simpan Koreksi**.

> **⚠️ Batasan Keamanan:**
> *   Anda hanya bisa menambah/mengedit tahapan jika status transaksi konsumen di database utama masih **'Proses Bank'**.
> *   Jika status transaksi konsumen sudah dipindah ke tahap selanjutnya (misal: 'SP3K' atau 'Akad'), modul ini akan berubah menjadi **Mode Baca Saja (Read-Only)**. Anda tidak bisa lagi mengubah sejarah proses bank demi integritas data.

---

## FAQ

**Q: Bagaimana jika konsumen disetujui Bank (SP3K)?**
> Input tahapan baru pilih **"Approved"**, upload scan surat SP3K jika ada, lalu Simpan. Setelah itu ubah status transaksi utama menjadi **'SP3K'** agar bisa lanjut ke jadwal akad.

**Q: Bagaimana jika ditolak (Reject)?**
> Input tahapan **"Reject"** dan beri keterangan alasannya (misal: BI Checking Kol 5). Anda mungkin perlu berdiskusi dengan konsumen untuk **Pindah Bank** (input tahapan 'Pindah Bank') atau membatalkan pembelian.

