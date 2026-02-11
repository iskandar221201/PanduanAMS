# 🔄 Panduan Modul Jurnal Pembalik (Reverse Entry)

Modul **Jurnal Pembalik** adalah fitur lanjutan AMS yang berfungsi menanganai status **Pembatalan Transaksi** (Reject/Mundur) pada unit yang sudah memiliki riwayat pembayaran.

Alih-alih menghapus data pembayaran (yang dapat merusak integritas audit), AMS menggunakan konsep *Reversal* untuk menolkan kembali piutang dan mengalokasikan dana yang sudah masuk.

---

## 1. Kapan Modul Ini Digunakan?

Jurnal Pembalik hanya bisa dibuat jika memenuhi 2 syarat:
1.  Status konsumen di Booking Data sudah diubah menjadi **Reject** (Ditolak Bank/Developer) atau **Mundur** (Batal sepihak oleh konsumen).
2.  Konsumen tersebut **sudah pernah melakukan pembayaran** (Booking Fee, DP, dll).

Jika konsumen belum pernah bayar apa-apa, Anda tidak perlu membuat Jurnal Pembalik. Cukup cancel booking-nya saja.

---

## 2. Alokasi Dana (Tipe Reverse)

Saat membuat Jurnal Pembalik, AMS akan menampilkan berapa total uang yang sudah masuk ke perusahaan. Tugas Anda adalah menentukan pos alokasi dana tersebut:

| Tipe Reverse | Penjelasan | Contoh Kasus |
|---|---|---|
| **Pendapatan Lain** | Uang **hangus** dan menjadi hak perusahaan. | Konsumen mundur sepihak, Booking Fee hangus. |
| **Dikembalikan** | Uang di-**refund** (dikembalikan) ke konsumen. | Pengajuan KPR ditolak Bank, uang DP dikembalikan full. |
| **Transfer** | Uang dipindahkan ke **Unit Lain** (Deposit). | Konsumen pindah blok/nomor unit. Uang Booking unit lama digeser ke unit baru. |

> **⚠️ PENTING: Pengecualian Pindah Unit (< 14 Hari)**
> Jika konsumen pindah unit dalam masa tenggang (misal: < 14 hari) dan manajemen mengizinkan **tukar unit langsung** tanpa *Booking Ulang*, maka Anda **TIDAK PERLU** membuat Jurnal Pembalik.

> AMS akan otomatis update kavling di Pencatatan keuangan. Jurnal Pembalik hanya digunakan jika Pindah Unit tersebut dianggap sebagai *pembatalan unit lama* dan *pembelian unit baru*.

---

## 3. Alur Kerja (Workflow)

### A. Membuat Jurnal Pembalik
1.  Masuk ke menu **Keuangan > Jurnal Pembalik**.
2.  Klik tombol **Buat Jurnal Pembalik**.
3.  **Pilih Konsumen:** Dropdown hanya akan menampilkan konsumen status *Reject/Mundur* yang memiliki saldo pembayaran.
4.  **Detail Item:** Sistem otomatis menampilkan rincian pembayaran (Booking, DP, dll).
5.  Untuk setiap item:
    *   Masukkan nominal yang mau di-reverse.
    *   Pilih **Tipe Reverse** (Pendapatan Lain / Dikembalikan / Transfer).
    *   Jika **Transfer**, pilih unit tujuannya.
6.  Klik **Simpan**.

### B. Mekanisme Transfer Saldo Otomatis
Ini adalah fitur *powerful* AMS untuk kasus Pindah Unit.
1.  Saat Anda memilih tipe **Transfer**, sistem akan meminta **Unit Tujuan**.
2.  Setelah disimpan, AMS melakukan 3 hal sekaligus secara otomatis:
    *   **Unit Lama:** Saldo dinolkan (Reversed).
    *   **Unit Tujuan:** Otomatis tercatat pembayaran baru di modul Pencatatan Keuangan.
    *   **Bukti Bayar:** Foto bukti transfer dari unit lama otomatis di-copy ke data unit baru.
    *   **Catatan:** Di unit baru muncul keterangan *"Transfer dari [Nama Konsumen] - Unit [Nomor Unit Lama]"*.

---

## 4. Validasi Sistem

AMS menerapkan aturan ketat untuk mencegah selisih pembukuan:
1.  **Anti-Over Limit:** Anda tidak bisa me-reverse nominal lebih besar dari yang sudah dibayar.
    *   *Contoh:* Konsumen bayar Booking 2 Juta. Anda tidak bisa me-refund 3 Juta.
2.  **Validasi Tujuan Transfer:** Transfer hanya bisa dilakukan ke unit yang statusnya **Sudah Booking**.
3.  **Lock Status:** Setelah Jurnal Pembalik dibuat, status keuangan di unit lama menjadi *Reversed* dan tidak bisa diedit lagi kecuali Jurnal Pembalik-nya dihapus.

---

## FAQ

**Q: Saya salah memilih Unit Tujuan saat transfer. Apa solusinya?**
> Anda bisa mengedit Jurnal Pembalik tersebut. Ubah tujuan transfernya, lalu Simpan. AMS akan otomatis menghapus pembayaran di unit tujuan yang salah, dan memindahkannya ke unit tujuan yang baru.

**Q: Apakah saldo bisa di-split? Misal: 50% Refund, 50% Hangus?**
> **Bisa.** Di form input, gunakan tombol **Split** untuk memecah satu item pembayaran menjadi beberapa baris. Baris pertama set Tipe "Dikembalikan", baris kedua set Tipe "Pendapatan Lain".

**Q: Apakah Jurnal Pembalik bisa dihapus?**
> Tidak, jika terjadi kesalahan, Anda bisa melakukan perubahan dengan metode Edit/Update.
