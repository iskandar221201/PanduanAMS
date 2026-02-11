# 💰 Panduan Modul Pencatatan Keuangan (Financial Records)

Modul **Pencatatan Keuangan** adalah pusat data arus kas masuk (*cash in*) dari penjualan unit. Modul ini dirancang dengan kontrol yang sangat ketat untuk mencegah kebocoran data dan manipulasi keuangan.

## 1. Konsep Dasar

Di AMS, pencatatan keuangan bersifat **Single Source of Truth** yang terikat langsung dengan data Booking.
*   **Satu Booking = Satu Pencatatan.** Anda tidak bisa membuat pencatatan ganda untuk satu transaksi.
*   **Total Piutang Dinamis.** Total yang harus dibayar konsumen mengikuti harga di modul *Harga Kavling*. Jika harga unit berubah, piutang otomatis berubah.

---

## 2. Alur Kerja (Workflow)

### A. Membuat Pencatatan Baru
Pencatatan keuangan tidak bisa dibuat manual "kosongan". Harus berdasarkan data Booking yang valid.
1.  Masuk ke menu **Tambah Pencatatan**.
2.  AMS hanya akan menampilkan daftar konsumen yang **sudah Booking** tapi **belum punya kartu piutang**.
3.  Pilih konsumen, lalu klik **Simpan & Lanjutkan**.
4.  Data harga (Booking, DP, KPR, dll) otomatis ditarik dari *Master Harga*.

### B. Menerima Pembayaran (Installment)
1.  Buka **Detail Transaksi** konsumen.
2.  Di tabel "Rincian Pembayaran", cari kategori yang mau dibayar (misal: DP).
3.  Klik tombol **Bayar**.
4.  Form Validasi akan muncul:
    *   **Jumlah Bayar:** Masukkan nominal uang yang diterima.
    *   **Diskon:** Isi jika ada potongan khusus (Diskon mengurangi utang konsumen, tapi tidak menambah kas masuk).
    *   **Bukti Bayar:** Wajib upload foto/scan bukti transfer.
5.  Klik Simpan.

---

## 3. Fitur Validasi dan Integrasi AMS

Modul ini memiliki beberapa logika otomatis yang mempermudah pekerjaan Admin Keuangan:

### ✅ 1. Validasi Pembayaran Ketat
AMS **menolak** input pembayaran jika:
*   Total (Bayar + Diskon) melebihi Sisa Piutang per kategori.
*   Tidak ada bukti pembayaran yang diupload.
*   Nilai minus (negatif).

### 🔄 2. Mekanisme "SP3K Shortfall" (Kekurangan Plafon KPR)
Seringkali, Bank menyetujui nilai KPR (SP3K) lebih rendah dari pengajuan awal. AMS menangani ini secara otomatis:
*   *Skenario:* Konsumen mengajukan KPR 300jt, tapi Bank hanya ACC 280jt.
*   *Solusi AMS:* Saat Admin menginput pencairan SP3K sebesar 280jt, sisa tagihan 20jt **tidak hilang**.
*   AMS otomatis memindahkan kekurangan 20jt tersebut ke tagihan **Biaya Lainnya (Others)**, sehingga konsumen tetap harus melunasinya sebagai penambah DP/Uang Muka.
*   Harga unit di seluruh sistem otomatis diupdate.

### 🔒 3. Delete Protection (Otorisasi Penghapusan)
Fitur **Hapus Pembayaran** sengaja dipersulit untuk keamanan.
*   Admin Keuangan **TIDAK BISA** sembarangan menghapus riwayat pembayaran yang sudah diinput.
*   Jika terjadi kesalahan input dan harus dihapus, Admin wajib **Request Delete Authorization** (Minta Izin) ke Direktur/General Manager.
*   Hanya jika otorisasi diberikan, tombol hapus (ikon tong sampah) akan muncul aktif.

### 🔍 4. Integrasi Jurnal Pembalik (Reverse Journal)
Jika transaksi batal (Reject/Mundur) padahal sudah ada pembayaran:
*   Data pembayaran tidak dihapus, melainkan di-**Reverse**.
*   Status pencatatan berubah menjadi "Reversed".
*   Dana yang sudah masuk bisa dialokasikan untuk *Refund*, dipindah ke *Pendapatan Lain-lain atau ditransfer (deposit) ke konsumen lain (jika ada)*.

---

## FAQ

**Q: Saya salah input nominal pembayaran. Apa yang harus saya lakukan?**
> Karena fitur delete dikunci, Anda harus lapor ke Direktur/General Manager melalui Supervisor dengan SOP yang berlaku untuk meminta **Otorisasi Penghapusan** data tersebut. Setelah diizinkan, baru Anda bisa menghapusnya dan menginput ulang.

**Q: Bagaimana jika konsumen bayar lunas langsung (Cash Keras) tanpa DP?**
> Di Master Harga, pastikan komponen biaya dialokasikan ke **Booking** dan **DP** (atau **Lainnya**) sampai totalnya full. Kosongkan SP3K. Saat pembayaran, cukup lunasi pos-pos tersebut.

**Q: Kenapa tombol "Bayar" tidak muncul?**
> Tombol hanya muncul jika status kategori tersebut **Belum Lunas** (Sisa Piutang > 0). Jika sudah 0, icon berubah menjadi checklist hijau.
