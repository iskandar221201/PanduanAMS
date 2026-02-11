# 📄 Dokumentasi Template & Upload SPR (Surat Pemesanan Rumah)

Modul **SPR (Surat Pemesanan Rumah)** di AMS adalah sistem manajemen dokumen transaksional yang menangani siklus hidup dokumen pemesanan unit dari hulu ke hilir. Modul ini terbagi menjadi dua bagian utama: **Template SPR** untuk pembuatan dokumen otomatis dan **Upload SPR** untuk pengarsipan dokumen fisik yang telah ditandatangani.

Didesain untuk efisiensi maksimal, modul ini memastikan setiap konsumen mendapatkan surat pemesanan yang profesional, akurat, dan seragam sesuai standar perusahaan.

---

## 🚀 Fitur Unggulan (Powerful Features)

### 1. Auto-Generation Engine (Template)
Modul ini didesain untuk menghilangkan proses pengetikan manual yang rawan kesalahan:
*   **Placeholder Dynamics:** AMS menggunakan sistem variabel (placeholders) seperti `{{NAMA_KONSUMEN}}`, `{{NOMOR_UNIT}}`, dan `{{HARGA_JUAL}}`. Data akan ditarik otomatis dari database saat pengajuan booking disetujui.
*   **Project Branding:** Setiap proyek dapat memiliki desain header dan isi surat yang berbeda (misal: header proyek subsidi berbeda dengan proyek komersial).
*   **Smart Numbering:** AMS otomatis menghasilkan nomor surat unik dengan format profesional, contoh: `0001/GW/SPR/II/2026`.

### 2. Digital Archiving System (Upload)
Sebagai pusat arsip dokumen legal:
*   **Signed Document Storage:** Berfungsi menyimpan hasil scan SPR yang sudah ditandatangani basah oleh konsumen dan manajemen.
*   **Integrasi Status:** Menampilkan daftar konsumen mana yang sudah mengunggah SPR dan mana yang belum, memudahkan kontrol administratif.
*   **Version Control:** Jika ada kesalahan upload, pimpinan dapat menghapus atau memperbarui file SPR tersebut dengan riwayat pengunggah yang tercatat.

### 3. Real-Time Preview
Sebelum template disimpan, pimpinan dapat melihat hasil cetakan menggunakan data simulasi (Dummy Data) untuk memastikan tata letak dan desain sudah sempurna.

---

## 🛠️ Langkah Penggunaan (Step-by-Step)

### Bagian 1: Mengelola Template SPR (Direktur/GM)
Lakukan ini sekali di awal proyek atau saat ada perubahan standar dokumen.

1.  **Akses Menu Template:** Masuk ke menu **Booking > Template SPR**.
2.  **Buat/Edit Template:** Pilih proyek yang ingin diatur template-nya.
3.  **Upload Header:** Gunakan gambar header resmi perusahaan (biasanya berisi logo dan alamat).
4.  **Desain Konten:** Gunakan editor teks untuk menyusun kalimat surat. Wajib sisipkan variabel seperti:
    *   `{{NOMOR_SPR}}` – Nomor otomatis dari AMS.
    *   `{{NAMA_KONSUMEN}}`, `{{NIK}}`, `{{NO_TELEPON}}` – Data pribadi.
    *   `{{NOMOR_UNIT}}`, `{{LUAS_TANAH}}`, `{{LUAS_BANGUNAN}}` – Data teknis unit.
    *   `{{HARGA_JUAL}}`, `{{TANGGAL_ACC}}` – Data finansial.
5.  **Klik Preview:** Cek apakah variabel sudah terganti dengan benar.
6.  **Simpan:** Template kini siap digunakan untuk setiap booking baru.

### Bagian 2: Mengelola Arsip SPR (Staf & Pimpinan)

1.  **Buka Menu Upload:** Masuk ke menu **Booking > Upload SPR**.
2.  **Filter Data:** Gunakan filter proyek untuk melihat daftar konsumen.
3.  **Proses Upload:**
    *   Klik tombol **Upload** pada baris nama konsumen yang bersangkutan.
    *   Pilih file scan SPR (Format: PDF/JPG/PNG, Max: 2MB).
    *   Klik **Simpan**.
4.  **Monitoring:** Baris yang sudah memiliki icon mata/download menunjukkan SPR sudah berhasil diarsipkan.

---

## 🛡️ Aturan & Validasi AMS

1.  **Status Constraint (Upload):**
    *   SPR hanya dapat diunggah untuk pengajuan booking yang berstatus **ACC** (Disetujui).
    *   Pengajuan yang berstatus *Expired, Mundur,* atau *Reject* tidak diizinkan untuk upload SPR baru guna menjaga validitas database.
2.  **Uniqueness Project Template:** Satu proyek hanya boleh memiliki satu template SPR aktif untuk menjaga keseragaman dokumen.
3.  **File Security:**
    *   Format yang didukung hanya JPG, PNG, dan PDF.
    *   Nama file di-randomize oleh AMS untuk mencegah akses ilegal melalui pencabutan URL.
4.  **Role Authorization:**
    *   **Marketing:** Hanya bisa melihat dan mengunggah SPR untuk konsumen mereka sendiri.
    *   **Direktur/GM:** Dapat melihat semua proyek, membuat template, dan menghapus dokumen jika diperlukan.

---

## ⌨️ Tips Manajemen

| Kebutuhan | Tindakan |
| :--- | :--- |
| **Ganti Header** | Cukup masuk ke menu Edit Template dan upload gambar baru tanpa perlu mengubah isi teks. |
| **Download** | Gunakan fitur download di list SPR untuk keperluan audit atau pelaporan bank. |
| **Gagal Generate** | Jika SPR tidak muncul saat booking di-ACC, pastikan Anda sudah membuat Template untuk proyek tersebut. |

---

## ❓ FAQ

**Q: Apakah saya bisa mengubah nomor SPR secara manual?**
> A: Tidak. AMS menghasilkan nomor surat secara urut dan otomatis berdasarkan data proyek untuk mencegah nomor ganda dan manipulasi data.

**Q: Apa yang terjadi jika saya menghapus Template SPR?**
> A: Booking baru yang di-ACC setelah template dihapus tidak akan dapat mengegenerate SPR otomatis. Namun, SPR yang sudah di-generate sebelumnya tetap aman di riwayat masing-masing konsumen.

**Q: Mengapa file PDF saya gagal di-upload?**
> A: Pastikan ukuran file tidak melebihi 2MB. Disarankan melakukan kompresi pada hasil scan dokumen agar loading sistem tetap cepat dan hemat ruang penyimpanan.
