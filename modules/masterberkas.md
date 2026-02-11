# 📄 Dokumentasi Modul Master Berkas KPR (AMS)

Modul **Master Berkas** adalah pusat kendali standarisasi dokumen KPR di AMS. Modul ini memungkinkan untuk mengatur daftar persyaratan dokumen yang wajib dipenuhi oleh konsumen berdasarkan jenis profesinya.

Modul ini bukan sekadar daftar statis, melainkan "mesin penggerak" yang menentukan validitas kelengkapan berkas di seluruh data konsumen perusahaan.

---

## 🚀 Fitur Unggulan 

### 1. Smart Sync Engine 
Ini adalah fitur unik AMS yang mengotomatisasi pekerjaan administratif berat:
*   Jika pimpinan **Menambah** jenis berkas baru di Master, AMS akan otomatis memunculkan syarat tersebut di *checklist* seluruh konsumen yang berstatus "Pemberkasan".
*   Jika pimpinan **Menghapus** syarat berkas di Master, AMS akan otomatis membersihkan syarat tersebut dari ribuan data konsumen sehingga persentase kelengkapan berkas mereka terhitung ulang secara akurat.
*   **Manfaat:** Manajemen tidak perlu meminta admin satu per satu mengupdate syarat berkas konsumen; cukup sekali klik di Master Berkas.

### 2. Segmentasi Berkas per Profesi
Modul ini memahami bahwa syarat KPR untuk PNS berbeda dengan Wiraswasta:
*   **PNS / Karyawan:** Bisa diwajibkan Slip Gaji dan SK Pengangkatan.
*   **Wiraswasta:** Bisa diwajibkan Rekening Koran 3-6 bulan dan NPWP Perusahaan.
*   **Opsi ALL:** Digunakan untuk dokumen umum yang wajib bagi semua orang (Contoh: KTP, KK, Buku Nikah).

### 3. Multi-Project Scoping
Setiap proyek memiliki otonomi. Daftar berkas di Proyek "Subsidi" bisa berbeda standarnya dengan Proyek "Komersial Luxury". AMS memastikan pengelolaan kode berkas tetap unik per masing-masing proyek untuk menghindari bentrok data.

---

## 🛠️ Langkah Penggunaan (Step-by-Step)

### A. Menambahkan Jenis Berkas Baru
1.  Buka menu **KPR > Master Berkas**.
2.  Klik tombol **+ Tambah Jenis Berkas**.
3.  Isi **Kode Berkas** (Singkatan unik, misal: `SK_KERJA`, `SLIP_GAJI`). *Tips: AMS akan otomatis mengubahnya menjadi huruf kapital.*
4.  Isi **Nama Berkas** lengkap (Misal: "Fotocopy SK Pengangkatan Karyawan Tetap").
5.  Pilih **Jenis Profesi** yang wajib melampirkan berkas ini.
6.  Klik **Simpan**. 
    *   *AMS akan mulai melakukan sinkronisasi ke seluruh data konsumen yang sedang aktif di proyek Anda.*

### B. Memperbarui Syarat Berkas
1.  Cari berkas yang ingin diubah dalam tabel.
2.  Klik ikon **Edit** (Pensil).
3.  Ubah nama atau kategori profesinya.
4.  Klik **Perbarui Data**.

### C. Menghapus Syarat (Retiring Document)
1.  Klik ikon **Hapus** (Tempat Sampah).
2.  Konfirmasi penghapusan.
3.  AMS akan menghapus kewajiban berkas tersebut di seluruh *checklist* konsumen.

---

## 🛡️ Aturan & Validasi AMS

1.  **Unique Code Policy:** Kode berkas tidak boleh sama dalam satu proyek. Ini mencegah duplikasi syarat yang membingungkan tim lapangan.
2.  **Alpha-Dash Validation:** Kode berkas hanya boleh mengandung huruf, angka, dan underscore (`_`). Tidak boleh ada spasi atau simbol aneh lainnya.
3.  **Strict Project Isolation:** Pimpinan hanya dapat mengelola Master Berkas untuk proyek yang sedang aktif dipilih.
4.  **Security Scope:** Halaman ini hanya dapat diakses oleh Role dengan izin `master-berkas.access` (Default: Direktur, GM, dan Admin Pusat).

---

## ⌨️ Tips Manajemen

| Strategi | Penerapan |
| :--- | :--- |
| **Gunakan Kode Konsisten** | Gunakan awalan yang sama untuk berkas sejenis, misal: _PBB_2024_, _PBB_2025_ untuk memudahkan pencarian. |
| **Kategori "Lain-lain"** | Gunakan profesi "Lain-lain" untuk berkas spesifik bagi pensiunan atau profesi non-standar lainnya. |
| **Cek Status Sinkronisasi** | Setelah melakukan perubahan besar (seperti menghapus berkas), mintalah admin proyek untuk mengecek salah satu data konsumen untuk memastikan *checklist* sudah berubah. |

---

## ❓ FAQ

**Q: Mengapa saya tidak bisa menghapus berkas tertentu?**
> A: Pastikan Anda memiliki hak akses `delete`. Jika tombol hapus tidak muncul, kemungkinan Role Anda hanya diberikan akses untuk melihat atau menambah saja.

**Q: Apakah perubahan di Master Berkas mempengaruhi konsumen yang statusnya sudah "Akad" atau "SP3K"?**
> A: **TIDAK.** AMS diprogram untuk hanya menyentuh konsumen yang statusnya masih **"Pemberkasan"**. Hal ini untuk melindungi integritas data konsumen yang dokumennya sudah dinyatakan lengkap oleh bank (SP3K) atau sudah selesai (Akad).

**Q: Apa yang terjadi jika saya mengubah Kode Berkas yang sudah ada?**
> A: Berhati-hatilah. Mengubah Kode Berkas akan dianggap oleh AMS sebagai "Berkas Baru". Berkas lama dengan kode lama mungkin akan hilang dari checklist dan digantikan oleh kode baru (masih kosong). Disarankan hanya mengupdate **Nama Berkas**-nya saja, bukan Kodenya.
