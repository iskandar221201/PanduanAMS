# 🏠 Panduan Modul Manajemen Kavling (Unit Inventory)

Modul ini adalah **jantung dari sistem AMS**. Di sinilah Anda mengelola stok unit (kavling/rumah) dan mencetak materi pemasaran (QR Code).

## 1. Konsep Dasar Unit

Setiap unit dalam AMS memiliki identitas unik yang disebut **Nomor Unit** (dan Slug QR) yang tidak boleh duplikat dalam satu proyek.

### Format Penulisan Nomor Unit
Terdapat validasi yang **sangat ketat** untuk format penulisan nomor unit demi konsistensi data dan integrasi dengan sistem Site Plan:
*   **Format Wajib:** `BLOK-NOMOR` (Misal: `A-01`, `B3-12`, `RUKO-05`).
*   **Pemisah:** Harus menggunakan tanda strip (`-`).
*   **Otomatis Kapital:** Sistem akan otomatis mengubah input menjadi Huruf Kapital (Uppercase).
*   **Contoh Salah:** `A 01` (spasi), `A01` (tanpa strip), `A/01` (salah pemisah). 
    *Tips:* Jika menginput `A01`, sistem memiliki tool `fix_format` (untuk Admin) yang bisa membantu konversi massal menjadi `A-01`.


### Status Unit (Lifecycle)
Status unit di AMS bekerja dengan sistem **Sinkronisasi Otomatis** dengan modul Transaksi (Booking).

#### 1. Status Manual
Di modul Kavling ini, Anda hanya bisa mengatur dua status dasar secara manual:
*   **Belum Dijual:** Unit belum dipasarkan (disimpan untuk stok masa depan).
*   **Tersedia:** Unit siap dipasarkan.
    *   *Syarat:* Status "Tersedia" hanya bisa dipilih jika unit **tidak memiliki data transaksi aktif**.

#### 2. Status Otomatis (Sinkronisasi)
Status berikut ini **tidak bisa dipilih manual**, melainkan otomatis muncul mengikuti status transaksi terakhir di modul Booking/Pengajuan:
*   **Hold:** Ada Pengajuan Booking (Pending).
*   **Pemberkasan / Proses Bank / SP3K / Akad:** Mengikuti proses KPR.
*   **Cash / Cash Bertahap:** Mengikuti jenis pembayaran yang disepakati.

> **Catatan:** Jika transaksi konsumen batal (**Reject** atau **Mundur**), status unit akan otomatis kembali menjadi **Tersedia** sehingga bisa dijual ke konsumen lain.

---

## 2. Fitur Utama

### Menambah Unit Baru (Input Cepat)
1.  Klik tombol **Tambah Kavling**.
2.  Isi data spesifikasi:
    *   **Nomor Unit:** (Wajib, Unik, & Format `BLOK-NOMOR`).
    *   **Luas Tanah & Bangunan:** Dalam meter persegi ($m^2$).
    *   **Harga Jual:** *Hanya estimasi*. Manajemen harga detail (Cash/KPR/Bertahap) dikelola di **Modul Harga Kavling (Price List)**.
3.  **Metode Simpan:**
    *   **Simpan:** Menyimpan data dan kembali ke daftar kavling.
    *   **Simpan & Buat Baru:** Menyimpan data dan **otomatis kembali ke form kosong**. Gunakan fitur ini jika Anda ingin menginput banyak unit sekaligus dengan sangat cepat.
4.  **Otomatisasi Sistem:** Saat tombol simpan diklik, sistem secara otomatis akan:
    *   Membuat **QR Code** unik untuk unit tersebut.
    *   Mendaftarkan koordinat unit di **Site Plan** (titik default).
    *   Menghasilkan *QR Slug* sebagai link identitas digital unit.


### Mengelola (Edit) & Menghapus
*   **Edit:** Klik ikon pensil untuk mengubah spesifikasi fisik (Luas Tanah/Bangunan).
*   **Hapus:** Unit hanya bisa dihapus jika **tidak terikat transaksi**. AMS akan menolak penghapusan jika unit sudah ada riwayat bookingnya.

---

## 3. Fitur QR Code & "Go" Controller

AMS dilengkapi teknologi **QR Code Pintar**.

### Cara Kerja (Controller `Go.php`)
Setiap unit memiliki *QR Slug* unik. Ketika QR Code di-scan:

#### Skenario 1: Di-scan oleh Sales (User Login)
Akan membuka **Popup Shortcut (Quick Menu)** yang berisi opsi cepat:
*   🚀 **Pengajuan Booking:** Langsung buat booking baru untuk unit ini.
*   🏗️ **Progres Konstruksi:** Update progress pembangunan unit.
*   ✏️ **Edit Kavling:** Ubah data fisik unit.
*   *Manfaat:* Sales tidak perlu masuk ke menu yang berbeda-beda, cukup scan QR di lokasi.

#### Skenario 2: Di-scan oleh Calon Konsumen (Guest)
Mengarahkan ke halaman **Public Landing Page** yang berisi info spesifikasi dan ketersediaan unit.

---

## FAQ

**Q: Saya salah input Nomor Unit. Apakah boleh diedit?**
> **Boleh.** Perubahan nomor unit akan otomatis terupdate di seluruh sistem (Siteplan, Booking, dll).

**Q: Apakah saya perlu mencetak ulang QR Code jika ada perubahan data (Harga/Luas)?**
> **TIDAK PERLU.** QR Code AMS bersifat dinamis. Kode QR hanya menyimpan "Link Identitas" unit. Seluruh informasi yang tampil saat di-scan (Harga, Status, Luas) diambil langsung dari database AMS. Jadi, stiker QR di lapangan bisa dipakai selamanya meskipun harga atau progres pembangunan berubah berkali-kali.

**Q: Dimana saya mengubah Harga Jual yang sebenarnya?**
> Bukan di modul Kavling. Silakan gunakan modul **Master Harga** atau **Price List** untuk mengatur skema harga Cash/KPR/Bertahap secara detail. Data di modul Kavling hanya sebagai referensi dasar.

**Q: Mengapa status unit saya jadi "Hold"?**
> Itu artinya ada sales yang sedang membuat **Pengajuan Booking** untuk unit tersebut dan sedang menunggu persetujuan (ACC) dari Admin/Manajemen. Selama status Hold, unit tidak bisa dibooking orang lain.

**Q: Mengapa saya tidak bisa menghapus data kavling tertentu?**
> Hal ini dikarenakan unit tersebut sudah memiliki riwayat transaksi (Booking/SPR). AMS melarang penghapusan unit yang sudah terikat dengan data konsumen demi menjaga integritas data laporan dan keuangan. Jika unit batal atau mundur, statusnya akan otomatis kembali menjadi "Tersedia", namun record unit tersebut tetap dipertahankan untuk kebutuhan audit dan riwayat stok.