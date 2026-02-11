# 💰 Panduan Pengguna: Pencatatan Keuangan (Kartu Piutang)

Modul **Pencatatan Keuangan** berfungsi sebagai buku besar digital untuk memantau status pembayaran setiap konsumen. Di sini Anda bisa melihat berapa total harga rumah, berapa yang sudah dibayar (DP, Booking, Angsuran), dan berapa sisa tagihan yang harus ditagih.

---

## 1. Membuat Kartu Piutang Baru
Setiap konsumen yang sudah *Booking* wajib dibuatkan Kartu Piutang agar pembayarannya bisa dicatat.

**Langkah-langkah:**
1.  Buka menu **Keuangan** > **Pencatatan Keuangan** di sidebar kiri.
2.  Klik tombol hijau **+ Tambah Pencatatan** di pojok kanan atas.
3.  Akan muncul formulir **Pilih Booking Konsumen**.
4.  Pada kotak pilihan, cari nama konsumen atau nomor unit yang dimaksud.
    *   *Catatan: Hanya konsumen dengan status "Booking" atau "Sold" yang akan muncul di sini.*
5.  Klik tombol **Simpan**.
6.  Selesai! Anda akan diarahkan kembali ke halaman utama, dan nama konsumen tersebut sudah muncul di daftar.

---

## 2. Melihat Rincian Tagihan & Pembayaran
Untuk melihat detail keuangan konsumen:

1.  Di halaman depan Pencatatan Keuangan, cari nama konsumen.
2.  Klik tombol biru **Detail** (ikon mata).
3.  Anda akan masuk ke **Kartu Piutang Konsumen**.

**Penjelasan Halaman Kartu Piutang:**
*   **Informasi Unit:** Menampilkan Nama Proyek, Blok/Unit, Tipe Rumah, dan Luas Tanah.
*   **Ringkasan Keuangan (Kotak Atas):**
    *   **Harga Jual:** Total harga kesepakatan (termasuk diskon/biaya lain).
    *   **Total Bayar:** Uang yang sudah diterima sistem.
    *   **Sisa Piutang:** Sisa uang yang *belum* dibayar konsumen.
*   **Tabel Rincian (Kiri):**
    *   Menampilkan rincian per kategori: **Booking Fee**, **Uang Muka (DP)**, **Kelebihan Tanah**, **Angsuran KPR/Cash**, dll.
    *   Setiap baris menunjukkan: *Tagihan Awal*, *Sudah Bayar*, dan *Sisa Tagihan*.

---

## 3. Mencatat Pembayaran Baru (Input Uang Masuk)
Ketika konsumen melakukan transfer atau setor tunai, Admin Keuangan wajib mencatatnya di sistem.

**Langkah-langkah:**
1.  Masuk ke halaman **Detail** konsumen tersebut (lihat Poin 2).
2.  Di sebelah kanan, cari panel **Form Pembayaran Baru**.
3.  Isi formulir berikut:
    *   **Kategori Pembayaran:** Pilih pos pembayaran (contoh: *Uang Muka 1*, *Booking Fee*, atau *Pelunasan Cash*).
    *   **Jumlah Pembayaran (Rp):** Ketik nominal uang yang diterima (tanpa titik/koma).
    *   **Diskon (Opsional):** Isi HANYA jika Anda memberikan potongan harga tambahan saat pembayaran ini. Jika tidak, biarkan 0.
    *   **Catatan:** Tulis keterangan singkat (contoh: "Transfer BCA tgl 12 Des").
    *   **Bukti Pembayaran:** Klik tombol *Choose File* dan upload foto bukti transfer/kwitansi (Wajib, format JPG/PNG/PDF).
4.  Klik tombol **Simpan Pembayaran**.
5.  Data akan masuk ke tabel **Riwayat Pembayaran** di bawah, dan *Sisa Piutang* otomatis berkurang.

> **PENTING:** Sistem akan menolak jika Anda memasukkan nominal lebih besar dari sisa tagihan! Pastikan inputan benar.

---

## 4. Menghapus Data Pembayaran (Revisi)
Jika terjadi kesalahan input (misal: salah nominal atau salah upload bukti), Anda bisa menghapus data pembayaran tersebut.

**Langkah-langkah:**
1.  Di halaman **Detail**, scroll ke bawah sampai tabel **Riwayat Pembayaran**.
2.  Cari baris pembayaran yang salah.
3.  Klik tombol merah **Hapus** (ikon tempat sampah).
4.  Konfirmasi penghapusan.
5.  Data terhapus, dan *Sisa Piutang* akan kembali bertambah seperti semula.

> **Catatan Keamanan:**
> Jika tombol Hapus berwarna **Abu-abu (Tidak Pasif)**, artinya Anda tidak punya izin untuk menghapus. Silakan hubungi Manager atau Admin Utama untuk meminta pembukaan akses (Approval Delete).

---

## 5. Menangani Perubahan Harga / Plafon KPR (SP3K)
Terkadang, Plafon KPR yang disetujui Bank (SP3K) lebih kecil dari pengajuan awal. Selisihnya (kekurangan bayar) harus dibebankan ke konsumen.

**Sistem Otomatis:**
Admin tidak perlu menghitung manual. Ketika Anda menginput pembayaran kategori **Pencairan KPR (SP3K)**, sistem otomatis mendeteksi jika ada selisih kurang bayar.
*   Kekurangan tersebut akan otomatis dipindahkan menjadi tagihan **Biaya Lainnya** atau menambah sisa **Uang Muka**.
*   Total Harga Jual tidak berubah, hanya komposisi tagihannya yang disesuaikan.

---

## ❓ Pertanyaan Umum (FAQ)

**Q: Kenapa nama konsumen saya tidak muncul saat mau "Tambah Pencatatan"?**
A: Pastikan status konsumen di menu *Penjualan > Booking* sudah **"Booking"**. Konsumen status "Draft" atau "Baru" belum dianggap memiliki tagihan resmi.

**Q: Apakah saya bisa mengedit nominal yang sudah disimpan?**
A: Tidak bisa diedit langsung demi keamanan data. Solusinya: Hapus pembayaran yang salah tersebut (Lihat Poin 4), lalu input ulang dengan data yang benar.

**Q: Bagaimana jika konsumen membatalkan pembelian (Refund)?**
A: Jangan hapus data di sini! Gunakan menu khusus **Jurnal Pembalik** untuk memproses pembatalan dan pengembalian dana agar tercatat di laporan arus kas.
